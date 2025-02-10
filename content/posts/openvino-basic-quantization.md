---
title: "Openvino Basic Quantization"
date: 2025-02-10T16:43:04+08:00
draft: false
---

## Prepare a Calibration Dataset

量化后的模型性能高度依赖于校准数据的分布。`transform_fn` 负责数据转换，因为 OpenVINO 处理的数据一般是 NumPy 数组。

```python
data_transform = transforms.Compose(
    [transforms.Resize(256),
     transforms.CenterCrop(224),
     transforms.ToTensor(),
     transforms.Normalize([0.485, 0.456, 0.406], [0.229, 0.224, 0.225])])

validate_dataset = datasets.ImageFolder(
    root=os.path.join('/home/knd/公共/刀具代码/deep-learning-for-image-processing/data_set/flower_data', "val"),
    transform=data_transform)

calibration_loader = torch.utils.data.DataLoader(validate_dataset,
                                                 batch_size=1, shuffle=False)


def transform_fn(data_item):
    images, _ = data_item
    return images.numpy()


calibration_dataset = nncf.Dataset(calibration_loader, transform_fn)

```
## Quantize a Model

`nncf.quantize(model, calibration_dataset)` 的主要作用是：

1. 自动分析模型结构，找到可以量化的层（如 Convolution、MatMul、Add）。
2. 使用校准数据集（calibration_dataset）计算合适的 scale factor 和 zero point。
3. 替换 FP32 运算为 INT8 运算，生成 INT8 版本的 OpenVINO IR 模型。

```python

model = ov.Core().read_model("quantized_model.xml")

quantized_model = nncf.quantize(model, calibration_dataset)

# compile the model to transform quantized operations to int8
model_int8 = ov.compile_model(quantized_model)

# Read input image
img = Image.open('rose.jpg').convert('RGB')
# [N, C, H, W]
img = data_transform(img)
# expand batch dimension
img = torch.unsqueeze(img, dim=0)
img = np.array(img)


res = model_int8(img)
output_layer_ir = next(iter(model_int8.outputs))
print(res[output_layer_ir])

# save the model
ov.save_model(quantized_model, "quantized_model.xml")
```

## 测试推理速度

测试结果表示FP32 - > int8,速度大概提升2倍。

```shell
benchmark_app -m quantized_model.xml -d CPU -api async -i rose.jpg -b 1
```


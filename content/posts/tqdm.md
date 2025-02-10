---
title: "Tqdm"
date: 2024-11-20T15:48:30+08:00
draft: false
---

`tqdm`库在深度学习中可以显示训练过程的进度条。

```python
    for epoch in range(epochs):
        # train
        ...
        train_bar = tqdm(train_loader, file=sys.stdout)
        for step, data in enumerate(train_bar):
            ...
            train_bar.desc = "train epoch[{}/{}] loss:{:.3f}".format(epoch + 1,
                                                                     epochs,
                                                                     loss)

        # validate
        net.eval()
        acc = 0.0  # accumulate accurate number / epoch
        with torch.no_grad():
            val_bar = tqdm(validate_loader, file=sys.stdout)
            for val_data in val_bar:
                ...
        val_accurate = acc / val_num
        print('[epoch %d] train_loss: %.3f  val_accuracy: %.3f' %
              (epoch + 1, running_loss / train_steps, val_accurate))
```
## 基本用法
```python
from tqdm import tqdm
import time

# 示例：显示一个简单的进度条
for i in tqdm(range(100), desc="Processing"):
    time.sleep(0.1)  # 模拟耗时操作
```
- `desc="Processing"`：设置进度条的描述。

## 自定义进度条
```python
for i in tqdm(range(100), desc="Custom Progress", unit="item", ncols=80, colour="green"):
    time.sleep(0.05)
```
- `unit="item"`：自定义单位。
- `ncols=80`：设置进度条的宽度。
- `colour="green"`：改变进度条的颜色。


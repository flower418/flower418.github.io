---
title: "Hello World"
date: 2026-11-09T10:00:00+08:00
draft: false
tags: [meta]
summary: "博客开张。顺便测试一下公式、代码和表格能不能正常显示。"
---

博客开张 🌻 以后在这里记学习笔记。

这篇顺便测试一下写技术博客常用的几样东西。

## 公式

行内公式：DDPM 的前向过程每一步加一点高斯噪声，$q(x_t \mid x_{t-1}) = \mathcal{N}(x_t; \sqrt{1-\beta_t}\, x_{t-1}, \beta_t I)$。

独立公式：记 $\alpha_t = 1 - \beta_t$，$\bar{\alpha}_t = \prod_{s=1}^{t} \alpha_s$，可以一步从 $x_0$ 采样到 $x_t$：

$$
q(x_t \mid x_0) = \mathcal{N}\left(x_t; \sqrt{\bar{\alpha}_t}\, x_0, (1 - \bar{\alpha}_t) I\right)
$$

## 代码

```python
import torch

def q_sample(x0, t, alpha_bar):
    noise = torch.randn_like(x0)
    a = alpha_bar[t].view(-1, 1, 1, 1)
    return a.sqrt() * x0 + (1 - a).sqrt() * noise
```

## 表格

| 模型 | 参数量 |
|---|---|
| GPT-2 small | 124M |
| GPT-2 medium | 350M |

> 引用块长这样。

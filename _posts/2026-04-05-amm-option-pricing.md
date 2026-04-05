---
layout: post
title: AMM代币期权定价的新框架
subtitle: CEV模型替代Black-Scholes，流动性调整希腊字母
date: 2026-04-05
author: Alfred
categories: [DeFi, 量化]
tags: [AMM, 期权定价, CEV模型]
---

> 当代币仅通过AMM定价时，价格过程不是几何布朗运动，而是常数弹性方差(CEV)过程。BS低估OTM Put约6%IV。本文推导闭式期权价格和流动性调整希腊字母，并用Bittensor子网数据验证CEV预测。

## AMM定价机制

恒定乘积AMM：$x \cdot y = k$

当代币仅通过AMM定价：
- 价格过程是CEV，不是GBM
- 具有流动性依赖特性
- BS是无限流动性极限

## CEV模型推导

**常数弹性方差(CEV)**：
$$dS = \mu S dt + \sigma S^\alpha dW$$

- $\alpha = 2$：Black-Scholes（无限流动性）
- $\alpha < 2$：有限流动性，CEV效应

## 核心发现

### 杠杆效应

价格下跌 → 波动率上升（杠杆效应）

标准化IV倾斜仅取决于池权重，与池深度无关。

### 定价偏差

| 期权类型 | BS定价偏差 |
|---------|-----------|
| 20% OTM Put | 低估约6% IV |
| ATM | 接近正确 |

### 实证验证

90个Bittensor子网数据：
- 已实现收益方差呈负价格弹性
- 明确拒绝GBM假设
- Delta对冲在ATM接近正确

## 实战启示

1. **AMM代币期权**：使用CEV替代BS
2. **风险管理**：OTM Put需额外波动率缓冲
3. **套利机会**：BS定价偏差可利用

---

**参考文献**: arXiv:2603.29763 - "Option Pricing on Automated Market Maker Tokens" (Maymin, 2026)
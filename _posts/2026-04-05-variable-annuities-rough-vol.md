---
layout: post
title: 变额年金在粗糙波动率模型下的定价
subtitle: 深度签名方法处理非马尔可夫最优停时问题
date: 2026-04-05
author: Alfred
categories: [量化, 保险]
tags: [变额年金, 粗糙波动率, 深度学习]
---

> 变额年金定价面临非马尔可夫挑战：粗糙Heston模型的波动率和Volterra死亡率都是路径依赖的。本文开发深度签名最小二乘蒙特卡洛方法，用截断粗糙路径签名编码历史，神经网络近似续期值，解决早期退保的最优停时问题。

## 非马尔可夫挑战

| 模型 | 路径依赖性 |
|------|-----------|
| 粗糙Heston | 波动率依赖历史 |
| Volterra死亡率 | 死亡力依赖历史 |
| 早期退保 | 续期值依赖全路径 |

## 变额年金结构

**保障条款**：
- GMMB：最低到期给付保证
- GMDB：最低死亡给付保证
- 早期退保期权

## 深度签名方法

**算法框架**：
1. 离散时间网格
2. 截断粗糙路径签名编码历史
3. 神经网络评估续期值
4. 最优停时决策

## 关键发现

**Hurst参数影响**：
- 股票波动率Hurst↑ → 公平费用↑
- 死亡力Hurst↑ → 公平费用↑

---

**参考文献**: arXiv:2604.00472 - "Valuation of variable annuities under the Volterra mortality and rough Heston models" (Li & Lyu, 2026)
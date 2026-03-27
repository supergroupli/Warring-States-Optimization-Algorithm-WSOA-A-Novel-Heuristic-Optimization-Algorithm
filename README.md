# 战国优化算法 (Warring States Optimization Algorithm, WSOA)

**一种受中国战国历史启发的全新启发式优化算法**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.8+](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)

[English](README_EN.md) | [中文](README.md)

## 引用

如果您在研究中使用了WSOA，请引用以下论文：

> **Chaoqun Li.** Warring States Optimization Algorithm (WSOA): A Novel Heuristic Optimization Algorithm Inspired by the Chinese Warring States Period History. *DOI: 即将发布*

**BibTeX:**

```bibtex
@article{li2026wsoa,
  title   = {Warring States Optimization Algorithm (WSOA): A Novel Heuristic Optimization Algorithm Inspired by the Chinese Warring States Period History},
  author  = {Li, Chaoqun},
  year    = {2026},
  note    = {DOI: coming soon}
}
```

> DOI正式分配后，请更新上述BibTeX条目。

---

## 简介

WSOA是一种基于种群的元启发式优化算法，灵感来源于中国战国时期（公元前475年—前221年）的历史博弈。算法中7个子种群分别代表战国七雄（秦、齐、楚、燕、赵、魏、韩），在搜索空间中既竞争又合作，通过"变法图强"、"合纵连横"、"征伐吞并"等机制驱动寻优，最终"大一统"收敛到全局最优解。

## 算法概述

### 五大阶段

| 阶段 | 名称 | 机制 |
|------|------|------|
| 一 | **七国初立** | 初始化7个子种群 + 反向学习增强多样性 |
| 二 | **变法争雄** | 7种搜索策略（Lévy飞行 / 多教师学习 / 柯西变异 / 双精英引导 / 自适应差分 / DE变异 / 正弦余弦）+ 策略自适应机制 |
| 三 | **合纵连横** | 弱国联盟共享信息（合纵）；强国吸引人才（连横）；间谍机制；远交近攻 |
| 四 | **征伐吞并** | 最弱国被灭，资源分配给强国；动态种群资源再分配 |
| 五 | **大一统** | 合并所有种群，多算子混合精细搜索 |

### 测试套件

支持4个IEEE CEC标准测试套件：

| 套件 | 函数数 | 标准维度 | 年份 |
|------|--------|---------|------|
| CEC2005 | 25 | 10, 30 | 2005 |
| CEC2014 | 30 | 10, 30, 50 | 2014 |
| CEC2017 | 29 | 10, 30, 50 | 2017 |
| CEC2022 | 12 | 10, 20 | 2022 |

### 对比算法（11种）

| 算法 | 全称 | 年份 |
|------|------|------|
| PSO | 粒子群优化 (Particle Swarm Optimization) | 1995 |
| DE | 差分进化 (Differential Evolution) | 1997 |
| GA | 遗传算法 (Genetic Algorithm) | 1975 |
| ABC | 人工蜂群 (Artificial Bee Colony) | 2007 |
| GWO | 灰狼优化 (Grey Wolf Optimizer) | 2014 |
| WOA | 鲸鱼优化 (Whale Optimization Algorithm) | 2016 |
| SCA | 正弦余弦算法 (Sine Cosine Algorithm) | 2016 |
| HHO | 哈里斯鹰优化 (Harris Hawks Optimization) | 2019 |
| MPA | 海洋捕食者算法 (Marine Predators Algorithm) | 2020 |
| AO | 天鹰优化 (Aquila Optimizer) | 2021 |
| DBO | 蜣螂优化 (Dung Beetle Optimizer) | 2023 |

## 项目结构

```
├── README.md                   # 中文说明（默认）
├── README_EN.md                # English documentation
├── CITATION.bib                # 引用文件
├── run.py                      # 启动脚本（命令行入口）
├── warring_states_algorithm.py # WSOA 核心算法
├── benchmark_functions.py      # CEC测试函数（基于opfunu）
├── comparison_algorithms.py    # 11种对比算法
├── plotting.py                 # 可视化模块
├── run_experiment.py           # 实验运行 + CSV导出
└── results/                    # 实验结果输出
    └── <SUITE>/
        ├── results_summary.csv     # 汇总统计 (Best/Worst/Mean/Median/Std)
        ├── results_ranking.csv     # 排名表 + 平均排名
        ├── results_raw.csv         # 每次运行原始数据
        ├── results_convergence.csv # 收敛曲线数据
        ├── convergence_F*.png      # 收敛曲线图
        ├── summary_comparison.png  # 柱状对比图
        ├── ranking_radar.png       # 排名雷达图
        └── experiment_*.log        # 实验日志
```

## 环境依赖

```bash
pip install numpy matplotlib opfunu
```

## 快速开始

```bash
# 快速测试（dim=10, 3次运行, 100次迭代）
python run.py --quick

# 默认运行（CEC2022, dim=10, 200次迭代, 5次运行）
python run.py

# 指定测试套件和维度
python run.py --suite CEC2017 --dim 30

# 运行全部4个CEC套件
python run.py --all_suites --dim 10 --runs 5

# 自定义参数
python run.py --suite CEC2014 --dim 30 --runs 10 --max_iter 500
```

## CSV输出说明（论文用）

| 文件 | 内容 | 论文用途 |
|------|------|---------|
| `results_summary.csv` | Best/Worst/Mean/Median/Std | 主结果表 (Table) |
| `results_ranking.csv` | 各函数排名 + 平均排名 | Friedman检验 |
| `results_raw.csv` | 每次运行原始适应度值 | Wilcoxon秩和检验 |
| `results_convergence.csv` | 收敛曲线数据 | 用Origin/MATLAB重绘收敛图 |

## 许可证

本项目采用MIT许可证 — 详见 [LICENSE](LICENSE) 文件。

## 联系方式

- **作者：** Chaoqun Li（李超群）
- **GitHub：** [supergroupli](https://github.com/supergroupli)

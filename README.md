# README.md
```markdown
# JCP v6.0.3 - TwoStage-Proj PINN Solver
Journal of Computational Physics 期刊级实验代码
自适应约束投影物理信息神经网络，求解四类非线性偏微分方程

## 项目概述
本代码实现 **TwoStage-Proj** 双阶段投影PINN算法，对比多种经典PINN变体，完成KdV、Burgers、NLS、KS四类方程求解。
包含完整模型训练、多种子统计、守恒性验证、性能评估、SCI标准可视化全套流程，结果可直接用于论文绘图与数据分析。

## 运行环境
Python >= 3.8
核心依赖
```bash
pip install torch numpy scipy matplotlib
```

## 目录结构
```
├── main.py                # 主训练代码
├── plot_final.py          # 论文可视化绘图脚本
├── README.md              # 项目说明文档
└── jcp_results_v6_0_3/    # 自动生成结果目录
    ├── checkpoints/       # 模型权重与损失记录
    ├── fields/            # 数值解与守恒量数据
    ├── figures_science/   # 高清论文图表(PDF/PNG/EPS)
    └── paper_tables/     # 量化指标数据表
```

## 支持算法
- Vanilla：基础物理信息神经网络
- Penalty：固定惩罚权重PINN
- Fixed-λ：常数权重约束PINN
- SA-PINN-pos：自适应权重PINN
- TwoStage-Proj：本文提出方法

## 求解方程
Korteweg-de Vries(KdV)、Burgers、Nonlinear Schrödinger(NLS)、Kuramoto-Sivashinsky(KS)

## 核心超参数
- 训练总迭代：2000
- 预热迭代：60
- 随机种子：42~46 共5组
- 输出分辨率：1000 DPI 期刊标准画质

## 快速运行
### 1. 启动模型训练
```bash
python main.py
```
自动完成多方法、多方程、多种子训练，保存权重、数值场、统计指标表。

### 2. 一键生成全部论文图表
```bash
python plot_final.py
```
自动绘制所有对比图像，终端输出完整量化指标与算法提升幅度。

## 图表清单
1. fig1_conservation_main：物理守恒误差演化曲线
2. fig2_pareto_frontier：精度-约束Pareto最优前沿
3. fig3_projection_l2：投影前后L2误差对比
4. fig4_projection_residual：投影前后PDE残差对比
5. fig5_projection_params：投影约束参数统计
6. fig6_training_loss_kdv：KdV方程分项损失收敛
7. fig8_training_cost：训练时长与GPU显存开销
8. fig9_total_loss_convergence：全局损失收敛趋势

## 输出内容
1. 多格式高清图片：PDF/PNG/EPS，满足期刊投稿要求
2. 全维度量化指标：L2误差、Linf误差、约束违反、PDE残差、耗时、显存
3. 算法提升统计：相比基准模型约束优化率、训练加速比

## 常见问题
1. 绘图提示无数据：优先执行主训练脚本生成结果文件
2. 服务器无图形界面：脚本已启用离线绘图后端，可正常出图
3. 曲线线条密集：内置降采样优化，兼顾趋势与视觉效果

## 版本信息
代码版本：v6.0.3
适用期刊：Journal of Computational Physics
```

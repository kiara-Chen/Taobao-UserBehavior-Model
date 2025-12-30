# 预训练模型说明 (Pre-trained Models)

本目录存放经过 **GridSearchCV（网格搜索）** 调优后的最优模型权重文件。这些模型是 Stacking 集成学习框架的基础。

## 1. 模型列表 (Model List)

| 文件名 | 模型类型 | 说明 |
| :--- | :--- | :--- |
| `best_lgb_model.pkl` | **LightGBM** | 经过 5 折交叉验证调优后的最优 LightGBM 基模型。 |
| `best_xgb_model.pkl` | **XGBoost** | 经过代价敏感学习（scale_pos_weight）配置后的最优 XGBoost 基模型。 |
| `meta_model.joblib` | **元模型 (LR)** | 用于融合基模型预测结果的逻辑回归元模型（建议上传）。 |

## 2. 调优参数概览
所有模型均针对 **类别不平衡 (1:4.6)** 进行了优化：
- **LightGBM**: 使用 `is_unbalance=True` 或自定义 `scale_pos_weight`。
- **XGBoost**: `scale_pos_weight` 设置为约 4.6。
- **调参方法**: 5-Fold Cross Validation + GridSearchCV。

## 3. 如何加载模型 (Usage)

您可以使用 `joblib` 或 `pickle` 库在 Python 中快速加载这些模型进行推理：

```python
import joblib

# 加载 LightGBM 模型
model = joblib.load('../models/best_lgb_model.pkl')

# 进行预测
# y_pred = model.predict(test_features)

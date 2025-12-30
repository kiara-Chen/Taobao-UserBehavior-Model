# 数据集说明 (Data Description)

本目录用于存放项目所需的原始数据链接及预处理后的数据样本。

## 1. 原始数据集 (Raw Dataset)
由于原始数据体积巨大（约 3.5GB），本项目不直接在仓库中上传原始文件。
* **数据集名称**: 天池 UserBehavior (淘宝用户行为数据集)
* **下载地址**: [阿里巴巴天池官网 - UserBehavior](https://tianchi.aliyun.com/dataset/649)
* **数据量**: 约 1 亿条用户行为记录。
* **字段说明**:
    * `User_ID`: 用户唯一标识
    * `Item_ID`: 商品唯一标识
    * `Category_ID`: 商品类目唯一标识
    * `Behavior_Type`: 行为类型（pv: 浏览, buy: 购买, cart: 加购, fav: 收藏）
    * `Timestamp`: 行为发生的时间戳

## 2. 预处理数据说明 (Processed Samples)
为了方便复现代码逻辑，本目录下提供了格式对齐的小规模样本数据（200条）：
* `daily_user_sample.csv`: 经过初步清洗（如日期转换、异常过滤）后的每日用户行为统计样本。
* `train_final_sample.csv`: 经过 `UserDatasetBuilder` 类处理后，生成的带有 25 个特征维度的训练集样例，未过滤pv<=5的全量数据。
* `test_final_sample.csv`: 经过 `UserDatasetBuilder` 类处理后，生成的带有 25 个特征维度的测试集样例，未过滤pv<=5的全量数据。

## 3. 复现说明
1.  请前往天池官网下载原始数据并解压为 `UserBehavior.csv`。
2.  将该 CSV 文件放置于项目根目录。
3.  运行 `notebooks/` 中的代码，程序将根据原始数据重新生成全量特征矩阵。

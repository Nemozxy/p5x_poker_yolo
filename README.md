# p5x_poker_yolo
一个训练失败的yolo_v8模型，用于识别p5x中的扑克牌

本来是看着快手开源的斗地主AI，很馋，想学习一下整出个适用于P5X中更改了部分规则的斗地主。简单看了一下，感觉OpenCV应该是不够用了，故选择了yolo v8。

数据集中包含了205张图片和28个类。包含两个版本的数据集。均在roboflow进行打标。

v14版本的数据集仅经过Auto-Orient并缩放至640x640。分配比例：

Train 73% 149 Images

Valid 19% 38 Images

Test 9% 18 Images

v13版本在v14基础上添加了±15°的旋转变化，以及-25%的亮度变化，并将每个训练样例的输出扩大至3倍。分配比例：

Train 89% 447 Images

Valid 8% 38 Images

Test 4% 18 Images


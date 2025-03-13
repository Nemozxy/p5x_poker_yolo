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

best.pt训练自v13数据集。你可以在train35中找到所有训练相关数据。在一张4060Laptop 8G上训练效果如下：

      Epoch    GPU_mem   box_loss   cls_loss   dfl_loss  Instances       Size
    173/200      2.15G      0.557     0.3839     0.8516        211        640: 100%|██████████| 28/28 [00:03<00:00,  7.19it/s]
                 Class     Images  Instances      Box(P          R      mAP50  mAP50-95): 100%|██████████| 2/2 [00:00<00:00, 10.77it/s]
                   all         38        302      0.858        0.9       0.91      0.711
                   
EarlyStopping: Training stopped early as no improvement observed in last 100 epochs. Best results observed at epoch 73, best model saved as best.pt.

To update EarlyStopping(patience=100) pass a new patience value, i.e. `patience=300` or use `patience=0` to disable EarlyStopping.

173 epochs completed in 0.189 hours.

Optimizer stripped from runs\detect\train35\weights\last.pt, 6.3MB

Optimizer stripped from runs\detect\train35\weights\best.pt, 6.3MB

Validating runs\detect\train35\weights\best.pt...

Ultralytics 8.3.85 🚀 Python-3.12.7 torch-2.6.0+cu126 CUDA:0 (NVIDIA GeForce RTX 4060 Laptop GPU, 8188MiB)

Model summary (fused): 72 layers, 3,009,353 parameters, 0 gradients, 8.1 GFLOPs

                 Class     Images  Instances      Box(P          R      mAP50  mAP50-95): 100%|██████████| 2/2 [00:00<00:00,  6.70it/s]
                   all         38        302      0.971      0.866      0.928      0.742
                    10         10         18      0.997          1      0.995      0.756
                     2         21         27          1      0.963      0.995      0.723
            3_fangkuai          3          3      0.928      0.667      0.806      0.609
              3_heitao          8          8      0.994      0.625       0.88      0.714
             3_hongxin          5          5          1      0.747      0.995      0.841
              3_meihua          3          3      0.775      0.667      0.706      0.604
                     4         13         19      0.987          1      0.995       0.81
                     5         12         23      0.957      0.966      0.983      0.776
                     6          9         11      0.988          1      0.995      0.819
                     7         12         14      0.982          1      0.995      0.863
                     8         16         21      0.945          1      0.995      0.787
                     9         13         20      0.988       0.95      0.993       0.78
                     a         24         37      0.996          1      0.995      0.801
                     j          9         20          1      0.873      0.988      0.728
                 joker          4          5      0.975          1      0.995      0.741
                     k         17         23       0.95          1      0.992      0.799
                  pass          1          1          1          0      0.332      0.265
                     q         21         29      0.994          1      0.995      0.787
                wonder         14         15       0.99          1      0.995      0.887
                
Speed: 0.3ms preprocess, 2.2ms inference, 0.0ms loss, 0.6ms postprocess per image

可能是由于缺少样本的原因，梅花3和方块3的训练效果非常差。再加上有人认为利用AI打牌是纯粹的作弊行为。故此项目搁置。

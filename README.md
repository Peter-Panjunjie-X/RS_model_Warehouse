# RS_model_Warehouse
地类识别（耕地、道路、建筑、林地、堆土区、水体等）/ 变化检测（通用变化检测、建筑变化检测等）

## 计划follow的模型

### 地类识别 (Land Cover Classification)
- **耕地** (Cropland)
  - 模型: Swin_Transformer_UPER、HRnet-OCR、segfomer、HRnet-uper、twins_svt-l_uperhead、vit-b16-ln_mln_upernet
    
    |model|模型结构|
    |:--------------|:------------------- |
    |K-Net-UPerNet-Swin-L|是一个基于 Swin-L Backbone 的语义分割网络，其中 Swin-L 负责提取层级化视觉特征，UPerNet 通过 PPM 和 FPN 进行多尺度上下文特征融合，K-Net 则通过可学习 Kernel 与图像特征交互，并迭代更新 Kernel 来生成更加精细的分割 Mask。整体属于 Transformer Backbone + 多尺度特征融合 + Kernel 迭代预测的语义分割架构。 |
    |HRnet-uper | 是一个基于 HRNet-W48（HR48）Backbone 的语义分割网络，其中 HRNet-W48 通过并行维护不同分辨率的特征分支，并反复进行跨分辨率信息交互，在保持高分辨率空间信息的同时提取多尺度语义特征；UPerNet 则通过 PPM 和 FPN 对不同层级的特征进行多尺度上下文融合，最终生成像素级分割结果。整体属于 CNN 高分辨率 Backbone + 多尺度特征融合 + 解码预测 的语义分割架构。|
    |HR48-OCR | 是一个基于 HRNet-W48（HR48）Backbone 的语义分割网络，其中 HRNet-W48 通过并行的多分辨率特征分支持续提取和融合高、低分辨率信息，保持较强的空间细节；OCR（Object Contextual Representation） 则根据初步分割结果聚合不同目标区域的上下文信息，再通过注意力机制将目标级上下文反馈到像素特征中，从而进一步增强像素分类能力。整体属于 CNN 高分辨率 Backbone + Object Context 上下文建模 + 注意力细化预测 的语义分割架构。|
    |Twins-PCPVT-L-UPer|是一个基于 Twins-PCPVT-Large（PCPVT-L）Backbone 的语义分割网络，其中 Twins-PCPVT-L 是一种层级化 Vision Transformer，通过金字塔结构逐步降低特征分辨率、提升特征维度，并结合空间注意力机制提取不同尺度的视觉特征；UPerNet 则利用 PPM 和 FPN 对 Backbone 不同阶段的特征进行多尺度上下文融合，最终生成分割结果。整体属于 层级化 Transformer Backbone + 多尺度特征融合 + 解码预测 的语义分割架构。|
    |Twins-SVT-L-UPer|是一个基于 Twins-SVT-Large（SVT-L）Backbone 的语义分割网络，其中 Twins-SVT-L 采用层级化 Vision Transformer，通过 局部子窗口注意力（LSA） 捕获局部空间细节，并利用 全局子采样注意力（GSA） 建模更大范围的长距离依赖，在控制计算量的同时获得多尺度上下文特征；UPerNet 则通过 PPM 和 FPN 对不同阶段的特征进行多尺度融合，并恢复空间细节，最终输出像素级分割结果。整体属于 层级化 Transformer Backbone + 局部/全局注意力建模 + 多尺度特征融合 的语义分割架构。|
    |ViT-B16-LN_MLN-UPerNet|是一个基于 ViT-B/16（Vision Transformer Base，16×16 Patch）Backbone 的语义分割网络，其中 ViT-B/16 将输入图像划分为固定大小的 16×16 Patch，并通过 Transformer 的自注意力机制建立不同图像区域之间的全局关系；LN 表示在 ViT 特征处理中使用 Layer Normalization，MLN 则用于对 ViT 提取的特征进行进一步的归一化/特征变换，以适配后续分割任务；UPerNet 再利用多尺度特征融合结构对 Backbone 特征进行处理，最终生成像素级分割结果。整体属于 纯 Transformer Backbone + 特征归一化/变换 + 多尺度特征融合 的语义分割架构。 |
    
    


  - 数据集:2.1w张- 512×512影像- 重叠度10% - 标签占比>5% -  |  train-8.5 / test-1.5
  - 状态: 训练中
    
    |model|mIoU|Acc|Fscore| Precision|Recall|
    |:---|:--- |:--- | :------| :------|:----------|
    | Swin_Transformer_UPER|80.48|90.51 | 90.48 |  90.46 | 90.51 |
    |HRnet-OCR|79.27|89.21 | 89.75  |  90.29   | 89.21  |
    |segfomer-b5|81.07|90.77 |  90.8  |   90.82   | 90.77  |
    |HRnet-uper|76.65| 88.5 | 88.38  |   88.27   |  88.5  |
    | twins_svt-l_uperhead|0000| 0000 |0000  |0000 |0000|
    | twins_pcpvt-l_uperhead|0000| 0000 |0000  |0000 |0000|
    | vit-b16-ln_mln_upernet|0000| 0000 |0000  |0000 |0000|

- **道路** (Road)
  - 模型: SegFormer
  - 状态: 规划中

- **建筑** (Building)
  - 模型: (待选择)
  - 状态: 待完善
 
- **建筑用地** (construction_land)
  - 模型: (待选择)
  - 状态: 待完善
  - 
- **林地** (Forest)
  - 模型: (待选择)
  - 状态: 待完善

- **堆土区** (Soil Dump)
  - 模型: 
  - 状态: 待完善

- **水体** (Water Body)
  - 模型:
  - 状态: 待完善

### 变化检测 (Change Detection)
- **通用变化检测** (General Change Detection)
  - 模型: TinyCD、OpenCD
  - 数据： LEVIR-CD / WHU-CD
  - 状态: 规划中
  
- **建筑变化检测** (Building Change Detection)
  - 模型: DTCDNet、A2Net、SNUNet
  - 数据： LEVIR-CD / WHU-CD
  - 状态: 规划中

## 项目结构 (待建立)


## 地类图斑要素选取
- **耕地**：水田 0101 √、旱地0102 √、水浇地0103 √
  - **筛选机制**：DLBM = '0101' OR DLBM = '0102' OR DLBM = '0103' 

- **道路**：铁路用地1001 ×、轨道交通用地1002 ×、公路用地1003 √、城镇村道路1004 √、交通服务场站用地1005 ×, 农村道路1006√、 管道运输用地1009 ×
  - **筛选机制**：DLBM = '1003' OR DLBM = '1004' OR DLBM = '1006'

- **水体**：河流水面1101 √ 、水库水面1103 √、坑塘水面1104 √、可调整养殖坑塘1104k √、内陆滩涂1106 ×、沟渠1107 ×、干渠1107K  ×、水工建筑用地1109 ×
11
  - **筛选机制**：DLBM = '1101' OR DLBM = '1103' OR DLBM = '1104' OR DLBM = '1104k'

- **林地**：乔木林地0301 、可调整乔木林地0301K、竹林地0302、可调整竹林地0302K、灌木林地0305、其他林地0307、可调整其他林地0307K、
  - **筛选机制**：DLBM = '0301' OR DLBM =  '0301K' OR DLBM = '0302' OR DLBM = '0302K' OR DLBM = '0305' OR DLBM = '0307' OR DLBM = '0307K'

- **建筑用地**：城镇住宅用地0701、农村宅基地0702、机关团体新闻出版用地08H1、科教文卫用地08H2、公用设施用地0809、特殊用地09、工业用地
0601 商业服务业设施用地 05H1、物流仓储用地 0508
  - **筛选机制**：DLBM = '0701' OR DLBM =  '0702' OR DLBM = '08H1' OR DLBM = '08H2' OR DLBM = '0809' OR DLBM = '09' OR DLBM = '0601' OR DLBM = '05H1' OR DLBM = '0508'


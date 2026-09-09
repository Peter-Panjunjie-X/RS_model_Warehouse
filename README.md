# RS_model_Warehouse
地类识别（耕地、道路、建筑、林地、堆土区、水体等）/ 变化检测（通用变化检测、建筑变化检测等）

## 计划follow的模型

### 地类识别 (Land Cover Classification)
- **耕地** (Cropland)
  - 模型: Swin Transformer UPER、HRnet-OCR、segfomer
  - 数据集:
  - 状态: 规划中
  
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
耕地：水田 0101 √、旱地0102 √、水浇地0103 √
DLBM = '0101' OR DLBM = '0102' OR DLBM = '0103' 

道路：铁路用地1001 ×、轨道交通用地1002 ×、公路用地1003 √、城镇村道路1004 √、交通服务场站用地1005 ×, 农村道路1006√、 管道运输用地1009 ×
DLBM = '1003' OR DLBM = '1004' OR DLBM = '1006'

水体：河流水面1101 √ 、水库水面1103 √、坑塘水面1104 √、可调整养殖坑塘1104k √、内陆滩涂1106 ×、沟渠1107 ×、干渠1107K  ×、水工建筑用地1109 ×
11
DLBM = '1101' OR DLBM = '1103' OR DLBM = '1104' OR DLBM = '1104k'

林地：乔木林地0301 、可调整乔木林地0301K、竹林地0302、可调整竹林地0302K、灌木林地0305、其他林地0307、可调整其他林地0307K、
DLBM = '0301' OR DLBM =  '0301K' OR DLBM = '0302' OR DLBM = '0302K' OR DLBM = '0305' OR DLBM = '0307' OR DLBM = '0307K'

建筑用地：城镇住宅用地0701、农村宅基地0702、机关团体新闻出版用地08H1、科教文卫用地08H2、公用设施用地0809、特殊用地09、工业用地
0601 商业服务业设施用地 05H1、物流仓储用地 0508
DLBM = '0701' OR DLBM =  '0702' OR DLBM = '08H1' OR DLBM = '08H2' OR DLBM = '0809' OR DLBM = '09' OR DLBM = '0601' OR DLBM = '05H1' OR DLBM = '0508'


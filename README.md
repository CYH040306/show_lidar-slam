# LiDAR SLAM Multi-Session

> 本仓库仅用于个人技术能力展示与公开方向探索，主要展示多传感器 SLAM、多趟建图、多源数据融合、动态场景处理和自动驾驶场景重建相关实验结果。  
> 仓库不包含公司内部代码、内部数据、模型权重、业务文档或可直接复现的完整工程实现。展示内容仅用于技术交流。

## 项目简介

本项目围绕自动驾驶与移动机器人场景下的多趟建图、多传感器融合和三维场景重建进行探索，重点关注以下问题：

1. 如何基于 LiDAR、IMU、GNSS/GPS、RGB 等多源传感器构建稳定的三维场景地图；
2. 如何将多次采集、多起点、多时间段的数据融合为统一地图；
3. 如何在存在动态物体、轨迹差异、局部不重叠和复杂道路结构的情况下提升建图鲁棒性；
4. 如何为后续数据合成、生成式仿真、世界模型数据构建提供高质量三维场景底座。

整体目标不是单纯完成单趟建图，而是探索一种面向自动驾驶数据闭环的三维场景构建能力，使其能够支撑：

- 单趟 LiDAR-IMU 建图；
- 多趟 Multi-Session 地图融合；
- 跨时间、跨起点、局部不重叠数据的统一建图；
- 动态目标检测、跟踪与场景净化；
- 多传感器数据对齐与统一读取；
- 大范围道路场景与室内停车场等复杂环境建图；
- 面向后续数据合成与生成式仿真的场景底座构建。

## 当前能力展示

目前已完成若干多传感器建图与多趟场景融合实验，主要包括：

### 1. LiDAR-IMU 单趟建图

支持基于 LiDAR 与 IMU 的基础建图流程，包括点云运动补偿、位姿估计、局部地图维护与结果保存等能力。

### 2. 多趟 Multi-Session 建图

支持多次采集数据的联合建图与地图融合，适用于不同起点、不同时间、部分区域重叠或局部不重叠的采集场景。

### 3. 全局一致性优化

针对多趟数据融合过程中的累计误差和局部漂移问题，引入全局约束与局部优化机制，提升整体地图一致性。

### 4. 多源传感器数据读取与对齐

支持对 LiDAR、IMU、RGB、GNSS/GPS 等多源数据进行统一读取、时间对齐和结果导出，便于后续建图、可视化、数据合成和生成式仿真使用。

### 5. 自动化批量建图

支持对多个数据片段进行自动化处理，降低多趟建图和批量实验的人工成本。

### 6. 动态目标处理

探索了面向自动驾驶场景的动态目标检测、跟踪、分离和场景净化能力，用于减少动态物体对静态地图构建的影响，同时也可为后续目标资产构建和场景编辑提供基础。

### 7. 多 LiDAR 融合建图

探索了主 LiDAR 与补盲 LiDAR 的融合建图能力，用于提升近车区域、侧向区域或遮挡区域的点云覆盖质量。

### 8. 复杂场景建图

已在道路场景、城市区域和室内停车场等场景中进行验证，关注跨区域、跨层、复杂结构和多趟数据融合下的地图一致性。

### 9. 视觉辅助约束探索

实现了在 LiDAR-IMU 建图基础上引入视觉信息二阶段优化的可行性，用于增强局部几何约束、提升特定场景下的位姿估计稳定性。
其中视觉展示结果如下所示
<img width="430" height="287" alt="GACRT025_1752455187_rgb" src="https://github.com/user-attachments/assets/4324b462-bd65-4893-a1f2-8e1de9f4e25e" />

### 10. IMU 鲁棒性增强

针对车辆经过减速带、坑洼路面或剧烈振动场景下可能出现的 IMU 异常波动，探索了异常检测与鲁棒处理机制，以提升运动补偿和位姿估计稳定性。

## 技术方向

本项目主要关注以下技术方向：

- LiDAR-IMU SLAM；
- Multi-Session Mapping；
- 多传感器融合；
- 回环检测与全局优化；
- 动态目标检测与地图净化；
- 多 LiDAR 融合建图；
- 视觉辅助几何约束；
- 大范围道路场景重建；
- 室内停车场多层地图融合；
- 面向数据合成与生成式仿真的三维场景底座构建。

## 结果展示

### 动态目标处理示例

以下示例展示了动态目标检测、跟踪与场景分离相关实验结果，用于验证动态元素处理和静态场景净化能力。

![dynamic_object_demo](https://github.com/user-attachments/assets/52137fa4-99af-4cbb-8b12-90730511d902)

<img width="1572" height="994" alt="dynamic_object_processing" src="https://github.com/user-attachments/assets/b0275621-5eae-4bff-8521-d3070a6d487d" />

### 大范围道路场景融合示例

以下结果展示了多趟道路场景数据融合后的三维地图效果。

<img width="1622" height="1175" alt="large_scale_mapping_1" src="https://github.com/user-attachments/assets/9347017e-2d84-4a43-adeb-bbc768c87c7e" />

<img width="1125" height="1024" alt="large_scale_mapping_2" src="https://github.com/user-attachments/assets/fc584147-80e0-4931-95d5-172bdf545847" />

### 局部地图细节示例

以下示例展示了融合地图中的局部细节，用于观察道路结构、静态环境和点云分布效果。

<img width="1833" height="1092" alt="map_detail_1" src="https://github.com/user-attachments/assets/3fa24c25-598a-463c-9c33-73eaf4b241dd" />

<img width="1832" height="1058" alt="map_detail_2" src="https://github.com/user-attachments/assets/adcad76a-6574-4285-819a-dfd391267703" />

<img width="1849" height="1092" alt="map_detail_3" src="https://github.com/user-attachments/assets/04add8ba-9d01-4c8c-9d3e-6ea9ec8a0c31" />

<img width="1313" height="1047" alt="map_detail_4" src="https://github.com/user-attachments/assets/f4f69def-bd23-415f-b428-7cf9fa9b986e" />

### 室内停车场多趟融合示例

以下结果展示了室内停车场场景下的多趟地图融合效果，用于验证复杂结构、跨区域和跨层场景下的地图构建能力。

![parking_mapping_demo](images/11.gif)

<img width="1456" height="997" alt="parking_mapping_1" src="https://github.com/user-attachments/assets/cbefa1ee-17fa-47e2-b9b1-5ee3dea8bcfd" />

<img width="1641" height="952" alt="parking_mapping_2" src="https://github.com/user-attachments/assets/e73a24ee-3e2f-4b1a-bbd6-891e2e4facdd" />

## 后续探索方向

后续计划继续探索以下方向：

1. **更稳定的 Multi-Session 地图融合**  
   提升多趟数据在弱重叠、不同起点和复杂道路结构下的融合稳定性。

2. **动态目标与静态地图解耦**  
   进一步提升动态目标检测、跟踪、分离和地图净化能力，为高质量静态地图构建和场景编辑提供基础。

3. **多传感器融合增强**  
   探索 LiDAR、IMU、RGB、GNSS/GPS 等传感器在不同场景下的互补优势，提高建图鲁棒性。

4. **视觉辅助 SLAM / 几何约束**  
   继续探索视觉信息在特征丰富区域、退化场景和局部精细结构中的辅助作用。

5. **面向数据合成的三维场景底座**  
   将高质量建图结果用于 3DGS、NeRF、生成式仿真和自动驾驶数据合成任务。

6. **面向世界模型的数据构建**  
   探索将地图、轨迹、点云、相机图像、动态目标状态等组织为时序数据，为 future prediction、world model 微调和长尾场景生成提供基础。

## 声明

本仓库仅作为个人技术能力展示和公开方向探索使用。

- 不包含公司内部代码；
- 不包含公司内部数据；
- 不包含公司内部模型权重；
- 不包含公司业务文档；
- 不包含可直接复现的完整工程实现；
- 不涉及任何未公开商业项目细节。

如相关展示内容存在不适合公开的部分，将及时进行调整或移除。

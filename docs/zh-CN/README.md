# SKinLoader - 植物皮肤加载系统
**Languages:**
[English](README.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md)
植物皮肤加载器允许玩家通过简单的文件操作为游戏中的植物添加自定义皮肤。只需在指定目录创建文件夹并放入资源包文件，即可在图鉴中为对应植物添加可切换的皮肤。

## 目录结构规范

```
SkinLoader/
├── 0/               # 0代表豌豆射手在图鉴中的ID
│   └── Peashooter   # 打包好的AssetBundles资源包
├── 1/
│   └── SunFlower
├── 2/
│   └── CherryBomb
├── 3/
│   └── WallNut
└── .../             # 其他PlantID
    └── ...          # 对应植物名称的资源包
```

## 使用指南

### 准备工作

1. 获取或创建植物预制件
   - 可以从原版植物解包获取
   - 也可以自行创建
   - 必须包含两个关键组件：
     * Prefab - 植物在游戏中的实际显示
     * Preview - 卡片上的植物预览

2. 使用[AssetBundles-Browser工具](https://github.com/Unity-Technologies/AssetBundles-Browser.git)打包资源

### 快速开始示例

以豌豆射手为例：
1. 创建包含`PeaShooterPrefab`和`PeaShooterPreview`的AssetBundles包
2. 将打包文件命名为`Peashooter`
3. 放入目录结构中的对应位置：
   ```
   SkinLoader/0/Peashooter
   ```
4. 游戏将自动识别并添加换肤功能

## 详细制作流程

### 1. 构建植物预制件

在Unity中的操作步骤：

1. 新建Unity项目并安装AssetBundles-Browser插件
2. 创建植物必备组件：
   - **动画控制器**要求：
     * 必须包含idle(待机动画)和shoot(射击动画)
     * 特殊植物需添加特有动画(如大嘴花的bite动画)
     * 在控制器窗口添加Float类型的Speed参数并赋给所有动画
   - **预制件**要求：
     * 必须包含Shadow和Shoot组件
     * 多发射口植物需添加Shoot1, Shoot2等对应组件

### 2. 构建植物卡片预览

创建Preview的简单步骤：
1. 新建空对象，命名为"植物名称+Preview"(如PeashooterPreview)
2. 添加Sprite Renderer组件
3. 将所需Sprite拖拽到组件中

### 3. 打包资源

完成预制件制作后：
1. 使用AssetBundles-Browser进行打包
2. 打包结果位于：`AssetBundles/StandaloneWindows`目录下

### 4. 自动注册皮肤

最后步骤：
1. 确认AssetBundles包名称与植物名称完全一致
2. 在SkinLoader目录下创建对应植物ID的文件夹
3. 将资源包放入该文件夹
4. 启动游戏即可自动显示新皮肤

## 注意事项

- 确保所有命名准确无误
- 动画控制器参数设置必须完整
- 资源包必须包含Prefab和Preview两个关键组件
- 文件路径区分大小写
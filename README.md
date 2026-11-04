# QYP_22_1009

一个基于 **Unreal Engine 5.3** 的博物馆 / 展陈场景项目（纯蓝图工程）。

场景主体由韩国文物、美国画作等素材包搭建，包含展厅、画作陈列与可交互道具。

## 环境要求

| 项目 | 版本 |
|---|---|
| 引擎 | Unreal Engine **5.3** |
| 平台 | Windows 10 / 11（项目按 Windows 配置） |
| 编译工具 | **不需要**。本工程 `Modules` 为空，没有 `Source/`，是纯蓝图项目，双击即可打开 |

## 如何打开

1. 克隆仓库（约 7 GB，首次拉取会比较久）：

   ```bash
   git clone https://github.com/Qiu-youan/museum-ue5.3.git
   ```

2. 双击 `QYP_22_1009.uproject`，用 UE 5.3 打开。
   如果系统提示「找不到引擎版本」，右键 `.uproject` → *Switch Unreal Engine version* 选择本机的 5.3。

3. 打开后手动载入关卡 `Content/Level_QYP22.umap`。

> 说明：`Config/DefaultEngine.ini` 里的 `EditorStartupMap` 目前指向一个旧路径，
> 所以启动后不会自动进入关卡，需要手动打开一次；这不影响工程本身。

## 目录结构

```
QYP_22_1009.uproject     工程入口
Config/                  工程配置（引擎、游戏、输入、编辑器）
Content/                 全部美术与关卡资产
├─ Level_QYP22.umap      主关卡（World Partition）
├─ Level_QYP22_HLOD0_Instancing.uasset   主关卡 HLOD
├─ __ExternalActors__/   World Partition 的 Actor 数据（勿删）
├─ __ExternalObjects__/  World Partition 的 Object 数据（勿删）
├─ Map/                  其他关卡（Museum_QYP、Museum_LT 等）
├─ KoreaTreasureProp/    韩国文物素材包
├─ Paintings_USA/        美国画作素材包
├─ RPGHeroSquad/         角色素材包（含展示关卡）
├─ Characters/           角色资产
├─ player/               玩家相关资产
└─ LevelPrototyping/     白模 /  prototyping 资产
```

## 仓库约定

- **不要提交** `Binaries/`、`Intermediate/`、`Saved/`、`DerivedDataCache/`、`.vs/`、`*.sln`
  —— 这些都是引擎和 IDE 自动生成的，已在 `.gitignore` 中忽略，克隆后由引擎重新生成。
- **必须提交** `*.uproject`、`Config/*.ini`、`Content/**`
  —— 尤其 `Content/__ExternalActors__/` 与 `Content/__ExternalObjects__/`，它们是 World Partition 关卡的本体，删了关卡就空了。

## 大文件说明

- 仓库体积约 **7 GB**，单文件最大约 **24 MB**（未超过 GitHub 100 MB 硬限制）。
- 目前**未启用 Git LFS**。后续若要加入更大的资产（单个 > 50 MB 的贴图、视频、扫描模型），建议先启用 LFS，避免仓库继续膨胀。

## 已知问题

- `Config/DefaultEngine.ini` 第 1 行有一个孤立的 `??`（历史遗留，无实际影响）。
- `EditorStartupMap` 指向 `/Game/Map/Level_QYP22`，实际关卡在 `/Game/Level_QYP22`。

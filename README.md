# PZ 独立版构建工具 / Project Zomboid Standalone Builder

把 Steam 正版《僵尸毁灭工程》(B42) 复制成一套**自包含的独立副本**：本体、模组、存档、设置全部收进一个文件夹，不再受 Steam 本体更新和创意工坊自动更新影响，同时**保留 Steam 联机**。

Turn your Steam copy of Project Zomboid into a self-contained standalone build: game files, mods, saves and settings all live inside one folder, immune to Steam / Workshop auto-updates, while Steam multiplayer still works.

---

## 功能 / Features

- 复制游戏本体，独立运行，不随 Steam 更新
- 只读自己的 `Zomboid\mods`，不扫描创意工坊目录
- 用 NTFS 目录联接（junction）挂载模组，工坊包只存一份，不占双倍空间
- 同名模组按 `modversion → versionMin → 工坊ID` 自动择优
- 完整迁移设置：选项、按键绑定、存档、模组勾选与加载顺序
- 保留联机（未使用 `-nosteam`）
- 图形化路径选择，不写死路径；构建带实时进度条
- 中英双语：启动时选语言，脚本与说明文档双语
- 配套迁移工具：换电脑/换盘一键重建联接，失效可弹窗手动指定源目录

---

## 使用前提 / Requirements

- Windows，独立版放在 NTFS 分区，整个文件夹在同一个盘
- 本机已安装 Steam 正版（工具从正版复制）
- 构建前彻底关闭游戏

---

## 快速上手 / Quick start

1. 解压 `PZ-StandaloneBuilder.zip`
2. 双击 `PZ独立版构建工具\双击运行_Run.bat`，选语言，依次指定四个目录
3. 等进度条跑完，在 Steam 里「添加非 Steam 游戏」，启动选项填：

```
-agentlib:zbNative=policy=allow-all -- -cachedir="<副本>\Zomboid" -modfolders mods
```

4. 换电脑或换盘后，运行 `PZ独立版迁移工具\迁移修复_Repair.bat` 重建联接

> `-cachedir` 必须是绝对路径；`-modfolders` 只能写关键字 `mods`，写成磁盘路径会被游戏丢弃。

---

## 注意 / Notes

- 仅供个人备份与版本固定，不修改正版文件，不绕过 Steam 验证
- 联机双方需版本一致（游戏版本 + 模组版本）
- 建议备份 `Zomboid\mods\default.txt`，它是加载顺序的唯一依据
- 不要勾选 `ModLoadOrderSorter_b42`，它会重写加载顺序

---

## 文件说明 / Files

```
PZ独立版构建工具/
  双击运行_Run.bat        入口（先选中文/English）
  builder.ps1             构建脚本（单文件双语）
  rebuild_junctions.ps1   只重建联接
  使用说明_ReadMe.txt     中英双语说明

PZ独立版迁移工具/
  迁移修复_Repair.bat     入口
  migrate.ps1             迁移修复脚本
  使用说明_ReadMe.txt     中英双语说明
```

# 碧之轨迹中文文本数据

本目录保存 Azure Vitality 中文兼容构建所需或用于校对的中文数据：

- `cn_map.json`：构建器使用的“PSV 原始字符串 → PC GBK 简体中文”精确映射，可直接传给 `--cn-map`。
- `vita_charmap.json`：索尼发行的 PS Vita Evolution 繁体中文版自定义双字节编码映射，用于复核与重建 `cn_map.json`。
- `quest125.json`、`quest138.json`、`quest157.json`–`quest159.json`：五个 Evolution 独占任务的简体中文任务表记录，包含标题、委托人、说明与阶段日志。
- `scena/*.clm`：本 MOD 修改范围内的 35 个完整简体中文场景脚本反编译稿，已包含 More Portraits 合并结果。

繁体中文文本直接取自索尼发行的 PS Vita Evolution 繁体中文版；本次由本项目从用户提供的 NoNpDrm 备份中提取。公开范围限于本 MOD 涉及的任务记录和修改脚本，不是整个游戏的数据镜像。

`cn_map.json` 为了无损写回 GBK 字节，键和值使用 Latin-1 作为逐字节容器，因此不适合作为直接阅读稿；可阅读内容请查看各 `quest*.json`。

`c0200.clm` 可以正常读取与反编译，但其中一个上游既存的 `Fork flat` 标签结构目前无法由 Calmare 源码级重新编译；最终二进制由 Azure Vitality 的结构化合并器直接生成。

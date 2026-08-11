# Azure Vitality 简体中文兼容 Fork

[English README](README_EN.md)

本 Fork 在上游 [Kyuuhachi/Azure-Vitality](https://github.com/Kyuuhachi/Azure-Vitality) 的基础上，加入 NISA PC 版《碧之轨迹》简体中文构建路径，用于兼容 zeroTool 汉化及其汉化版 More Portraits。

目前只上传源代码，**尚未发布任何 Release**。本仓库也不包含从游戏或汉化补丁提取的受版权保护数据。

## 覆盖任务

- 埋伏不当交易（ID 125）
- 面包店的叫卖（ID 138）
- 主题乐园的兼职2（ID 157）
- 克洛斯贝尔的导览（ID 158）
- 森林道的搜索（ID 159）

## 中文构建的主要变化

- 新增 `--cn-map`，使用外部的“PSV 原始文本 → GBK 简体中文”精确映射构建中文脚本。
- 传入中文映射时只生成中文脚本分支，不再同时构建英文分支。
- 以 zeroTool 汉化与汉化版 More Portraits 的中文脚本作为 PC 合并基线。
- 使用 `CALMARE_RAW_BYTES=1` 无损读取 PSV 自定义编码及 PC GBK 字节。
- Aureole 依赖锁定到 [lmaple0/Aureole](https://github.com/lmaple0/Aureole/commit/f91ecdba224d61db2ae4e46b1fcddaf98f8c7577) 的 raw-byte 支持提交，公开检出后可复现构建。

## 构建示例

```powershell
$env:CALMARE_RAW_BYTES = '1'

cargo run --release -- azure `
  --evo <evo-donor-wrapper> `
  --pc <pc-cn-wrapper> `
  --portraits <more-portraits-cn-wrapper> `
  --out <output> `
  --cn-map <azure_cn_map.json>
```

`--cn-map`、官方繁中 donor 及游戏本体文件均须由使用者在本地准备，不随仓库上传。生成目录中的 `scena`、`text` 应在最终兼容包中分别放入：

```text
data_cn/scena
data_cn/text
```

语言无关的 BGM、SE、角色和场景资源仍放在 `data/` 下。中文兼容包使用松散文件覆盖，不使用 P3A 或 `order.txt`。

## 当前状态

- 35 个任务相关脚本均已成功生成并可由 AoKai 解析器读取。
- 任务表中的五个简体中文任务名已按攻略官方译名核对。
- 14 个重叠脚本保留汉化版 More Portraits 的头像控制码。
- 已建立测试候选包，但尚未完成游戏内全流程、分支、DP、奖励、贴图与崩溃回归测试。
- 在完成游戏验证前不会发布正式 Release。

## 致谢与来源

- 原 MOD 与移植逻辑：[Kyuuhachi](https://github.com/Kyuuhachi/Azure-Vitality)。
- 中文工具与本体汉化：[zeroTool](https://github.com/J31why/zeroTool)。
- 本 Fork 所参考的繁体中文汉化补丁由科洛蒂娅公主（KloseRInz）等人基于云豹娱乐（CLE）本地化并发行的 PSV Evolution 亚洲版本提取制作。感谢公主等人制作并保存这份汉化补丁。

上游原始说明、英文安装信息与完整 Credits 请参阅 [README_EN.md](README_EN.md)。

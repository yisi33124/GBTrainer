# GBTrainer

Ground Branch 1.0（Steam 版，游戏构建号：待填写）离线单人战役修改器。

**仅限离线单人使用，请勿联机。**

## 运行要求

- Windows 10/11 64 位。
- 管理员权限。
- F2 无敌功能需要已安装 RE-UE4SS；程序可在确认后自动安装 GBProbe。

## 下载与校验

从本仓库的 Releases 页面下载 `GBTrainer.exe` 和 `SHA256SUMS.txt` 到同一目录，然后在 PowerShell 中执行：

```powershell
Get-FileHash .\GBTrainer.exe -Algorithm SHA256
Get-Content .\SHA256SUMS.txt
```

两个 SHA256 值必须一致。

## 使用顺序

1. 先启动 Ground Branch，并进入离线单人任务。
2. 运行 `GBTrainer.exe`，允许管理员权限。
3. 查看启动自检。若提示 GBProbe 文件缺失，可选择 `y` 自动安装。
4. 进入游戏后程序会自动连接。

- `F1`：开启或关闭“弹药不减”。
- `F2`：开启或关闭无敌；由 UE4SS 的 GBProbe 负责。
- `F10`：退出程序并还原弹药补丁。

音效含义：

- 高音：功能开启。
- 低音短音：功能关闭。
- 低音长音：发生错误。
- 上升两音：启动并连接游戏。
- 下降两音：按 F10 正常退出。

直接关闭窗口、按 Ctrl+C、注销或关机时，程序也会尝试还原补丁。

## 游戏更新后

游戏更新可能导致特征码失效，请等待支持新构建的版本。进阶用户可复制 `config.example.json` 为 `config.json` 并调整以下字段：

- `process_name`：游戏进程名。
- `ue4ss_log_path`：`UE4SS.log` 路径；留空时从游戏进程目录自动查找。
- `ammo.aob`：弹药特征码。
- `ammo.offset`：补丁相对特征码起点的偏移。
- `ammo.patch_bytes`：替换原指令的补丁字节。

`config.json` 中的非空日志路径优先于自动查找。配置缺失、损坏或字段类型错误时，程序会提示并使用内置默认值。

## 杀毒误报

程序使用全局键盘热键并读写游戏进程内存，因此可能被安全软件误报。是否继续使用及其风险由使用者自行判断。

## 卸载

1. 按 `F10` 退出程序。
2. 删除 `GBTrainer.exe`、可选的 `config.json`、`sounds` 和运行日志。
3. 删除游戏目录下的 `GroundBranch\Binaries\Win64\Mods\GBProbe`。

不要删除整个 `Mods` 目录，以免影响其他 UE4SS 模组。

本程序仅以可执行文件形式提供，不提供源码。

请同时阅读 [DISCLAIMER.md](DISCLAIMER.md)。

# OC2 Player Slot Mapper

玩家位置分配器 v1.0，用于 *Overcooked! 2* 的进关前玩家位置分配。

这个 Mod 只做“进入关卡前生效”的玩家位置分配，不做局内实时换人。

修改设置后，需要：

```text
退出当前关卡
在 Configuration Manager 里改位置
重新进入关卡
```

## 默认映射

```text
1号位 = 蓝色
2号位 = 红色
3号位 = 绿色
4号位 = 黄色
```

## 示例

如果想让 4号黄色玩家去 2号位，2号红色玩家去 4号位：

```text
1号位 = 蓝色
2号位 = 黄色
3号位 = 绿色
4号位 = 红色
```

然后退出当前关卡，重新进入关卡。

## 控制台配置

```text
玩家位置分配器
- 启用
- 1号位：蓝色 / 红色 / 绿色 / 黄色
- 2号位：蓝色 / 红色 / 绿色 / 黄色
- 3号位：蓝色 / 红色 / 绿色 / 黄色
- 4号位：蓝色 / 红色 / 绿色 / 黄色
- 调试日志
```

四个位置不要选择重复颜色。如果重复，插件不会应用本次换位。

## 和旧主机换位 Mod 的关系

这个版本会 patch `CampaignKitchenLoaderManager.AssignChefEntities`，并声明在旧 `dev.gua.overcooked.hostcolor` 之后执行。

但为了减少冲突，测试时建议先把旧的：

```text
OC2HostColor-主机换位.dll
```

从 `BepInEx/plugins` 里移走或改后缀禁用。

## 安装

仓库中的源码包以 Base64 分片保存。先把分片合并并解码：

```powershell
Get-Content .\archive\OC2PlayerSlotMapper_v1_0_source.zip.b64.part* | Set-Content .\OC2PlayerSlotMapper_v1_0_source.zip.b64
certutil -decode .\OC2PlayerSlotMapper_v1_0_source.zip.b64 .\OC2PlayerSlotMapper_v1_0_source.zip
```

然后解压 zip，进入有 `build.ps1` 的目录，编译安装：

```powershell
powershell -ExecutionPolicy Bypass -File .\build.ps1 -GameDir "E:\SteamLibrary\steamapps\common\Overcooked! 2" -Install
```

## 启动确认

进入游戏后，在 `BepInEx/LogOutput.log` 里应看到：

```text
Loading [玩家位置分配器 1.0.0]
玩家位置分配器 v1.0.0 loaded.
```

## Disclaimer

Unofficial fan-made mod. Not affiliated with Team17, Ghost Town Games, or the official *Overcooked! 2* developers. Use at your own risk. Do not use gameplay-altering mods in public lobbies or with players who have not agreed to modded gameplay.

# EVE New MIM LP 奖励数据

此分支只分发公开的任务名称、奖励及 1～10 人均分表，不含程序、账号、角色或收益历史。

客户端使用独立的“更新 LP 数据”按钮读取 `mission-catalog.json`，将校验通过的数据保存到本机 `data/loyalty/`。软件版本和软件安装包不参与这次更新。客户端按任务内容计算独立数据版本，下载失败继续使用上次成功的目录。

维护时保存任务报酬表格，再用软件源码中的独立脚本生成可检查的 JSON：

```powershell
python release-tools/build_lp_database.py --workbook "任务报酬.xlsx" --previous "上一版/mission-catalog.json" --output "待发布/mission-catalog.json"
```

脚本无需编译软件。确认任务名称、奖励数值与分配表后，仅更新此数据分支中的 JSON；不必创建软件 Release，也不必修改软件版本号。未填写的奖励不补造，旧任务 ID 和奖励保持。

初次发布目标分支为 `codex/lp-data`，公开读取地址：

https://raw.githubusercontent.com/Theis9/EVE-New-MIM/refs/heads/codex/lp-data/mission-catalog.json

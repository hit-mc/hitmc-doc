# PSMB 运维文档

## 实现原理

```
          PSMB-Server (消息队列)
    /     |                |         \
   /      |                |           \
  |       |                |            |
new_bot mcdr(survival) mcdr(dragon) mcdr(hit)
  |
go-cqhttp
  |
腾讯服务器
```

## 复制服务端后，通常需要更改 psmb 的设置。

```
❯ ll
total 28
drwxrwsr-x+ 17 mc mc 4096 Sep 28 17:51 config <-- 在这里改配置文件
-rw-rw-r--+  1 mc mc 3374 Sep 30 12:46 config.yml
drwxrwsr-x+  2 mc mc 4096 Sep 30 12:34 logs
-rw-rw-r--+  1 mc mc 1899 Oct  2 17:47 permission.yml
drwxrwsr-x+  2 mc mc 4096 Sep  2 22:48 plugins <-- 插件一般安装在这里
drwxrwsr-x+ 29 mc mc 4096 Sep 30 01:28 qb
drwxrwsr-x+ 10 mc mc 4096 Oct  1 21:58 server
```

我们的聊天插件叫做 `psmb_chatbridge.mcdr`，通常会被链接到`common`目录里

```
psmb_chatbridge.mcdr -> ../../common/plugins/psmb_chatbridge.mcdr
```

## MCDR 插件配置文件

### 位置

```
❯ cd config
❯ ll
total 44
-rw-rw----+ 1 mc mc 4354 Sep  2 22:52 BotKikai.json
-rw-rw----+ 1 mc mc   35 Sep  2 22:52 CarpetFeatureHelper.json
-rw-rw----+ 1 mc mc  167 Sep  2 22:52 ChatBridgeReforged_MC.json
-rw-rw----+ 1 mc mc  160 Sep  2 22:52 ChatBridge_client.json
-rw-rw----+ 1 mc mc   51 Sep  2 22:52 CrashRestart.json
-rw-rw----+ 1 mc mc 2166 Sep 28 17:51 QuickBackupM.json
drwxrws---+ 2 mc mc   71 Sep  2 22:52 StatsHelper
drwxrws---+ 3 mc mc   39 Sep  2 22:52 aluminum
drwxrws---+ 2 mc mc   25 Sep  2 22:52 auto_plugin_reloader
drwxrws---+ 2 mc mc   25 Sep  2 22:52 colored_chat
drwxrws---+ 2 mc mc   25 Sep  2 22:52 daycount_nbt
-rw-rw----+ 1 mc mc  172 Sep  2 22:52 here.json
drwxrws---+ 2 mc mc   25 Sep  2 22:52 info
-rw-rw----+ 1 mc mc  286 Sep  2 22:52 joinMOTD.json
drwxrws---+ 2 mc mc   47 Sep  2 22:52 location_marker
drwxrws---+ 3 mc mc   46 Sep  2 22:52 markit
drwxrws---+ 2 mc mc   25 Sep  2 22:52 mcdr_pycraft_bot
drwxrws---+ 2 mc mc   30 Sep  2 22:52 mcdreforged
drwxrws---+ 2 mc mc   25 Sep  3 12:55 psmb_chatbridge <-- 在这里
-rw-rw----+ 1 mc mc   36 Sep  2 22:52 rsc.json
drwxrws---+ 2 mc mc   25 Sep  2 22:52 simple_calculator
drwxrws---+ 2 mc mc   25 Sep  2 22:52 simple_op
drwxrws---+ 2 mc mc   85 Sep  2 22:52 task
-rw-rw----+ 1 mc mc   82 Sep  2 22:52 timed_quick_backup_multi.json
drwxrws---+ 2 mc mc   25 Sep  2 22:52 where_is
```

### 内容

```
{
    "psmb_host": "127.0.0.1",
    "psmb_port": 13880,
    "psmb_topic": "eDDJLE6oIuom9HDNdxRTwvpsUrG1k4EC",
    "client_id": 11, <---- 修改为一个独立的整数，服务器之间需要不一样
    "client_name": "survival" <-- 服务器名，通常和目录名一致，全部小写
}
```

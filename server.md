# 服务器管理

该章节阐述服务器管理的要点与要求。

## 登陆

进入：

```zsh
sudo -i -u mc -g mc
# 这里输入你的密码
```

## 日常管理

### 目录布局

```
❯ tree -L 1
.
├── hdd -> /var/hdd_store/srv/minecraft # 机械硬盘储存
├── hitmc                               # 各种服务器本体
├── new_bot                             # QQ 机器人
├── psmb                                # PSMB - 机器人消息队列
├── README.md                           # 你现在看的这个文件
├── scripts                             # 脚本
└── venv                                # Python 虚拟环境

6 directories, 1 file
```

### 服务器启动、管理

启动：

```zsh
sudo -u mc -g mc /srv/minecraft/scripts/start.sh
```

进入控制台：

```zsh
sudo -u mc -g mc /srv/minecraft/scripts/attach.sh
```

控制台使用 tmux 进行管理，tmux 的键盘操作可以参考:

https://github.com/tmux/tmux/wiki (en)

https://www.ruanyifeng.com/blog/2019/10/tmux.html (zh_CN)

### 禁止的操作

#### chmod 777

请不要将任何目录或文件权限改为 777

Unix 权限 https://wiki.archlinux.org/title/File_permissions_and_attributes (en)

## FAQ

### 我 cp 过来了一个目录 （或通过 SFTP 上传了一个目录），权限不对怎么办？

首先参考 Unix 权限：

https://wiki.archlinux.org/title/File_permissions_and_attributes (en)

通常 cp / SFTP / scp / rsync 过来的目录带有原来的权限，你可以用

```zsh
chmod g+w <folder>
```

来使得同组用户也具有写入权限

## `【测试仓库】自建软件源 + 编译脚本本地化试验田`
> 当前改动:
> 1. **common 脚本本地化**:`shidahuilang/common` 仓库内容已全部收编进本仓库 `common/` 目录,编译时不再从外部实时拉取(可审计、可回溯,外部仓库故障不影响编译);无用内容(common 仓库自己的 workflows、autoupdate 分支清单)已清理
> 2. **禁用上游同步**:编译时不再用主仓库 openwrt 的 build 配置覆盖本仓库,测试改动可安全保留
> 3. **自建 opkg 软件源**:新增 `scripts/feed/`(索引生成)+ `.github/workflows/publish-feed.yml`(自动发布),编译产出的全部 ipk(含 kmod)发布到 GitHub Pages,固件预置 `customfeeds.conf` 实现在线安装插件
>    - 软件源地址:`https://shidahuilang.github.io/openwrt-test/x86_64/...`
>    - 路由器上使用:`opkg update && opkg install <插件名>`

## `【大灰狼独家优化】（IPV6大全版  6.6 内核【带DOCKER】`
#### 🚩 源码拉取`coolsnowwolf` `immortalwrt`自行选择编译
- 默认IP地址：`192.168.2.1`
- 账户：`root`   密码：`空`
 
- 自行云编译固件姿势
- ssh-actions改为ssh就可以启动插件选择
- 看到ssh链接会有一个web的链接，打开就是命令行，根据下面命令进入
- 开始 ctrl+c 
- 进ssh选择插件 
``` bash
cd openwrt && make menuconfig
```
- 结束ctrl+d
- REPO_TOKEN密匙制作教程：https://git.io/jm.md
- 云编译需要 [在此](https://github.com/settings/tokens) 创建个```token```,勾选：```repo```, ```workflow```，保存所得的key
- 然后在此仓库```Settings```->```Secrets```中添加个名字为```REPO_TOKEN```的Secret,填入token获得的key


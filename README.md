








---20150923---
添加了 luci-app-shadowsocks-libev shadowsocks-libev 因为 1505 没有这个 ss

---20150924---
packages\net 里面添加了 aircrack-ptw
packages\net 里面添加了 libpcap --- 这个是可以 pin 的 1.1.12 版本

---20150929---
添加了 Gmediarender 音乐推送插件




Add this line to your feeds.conf.default.

    src-git 1983 git://github.com/openwrt-1983/1983.git 

And run

    ./scripts/feeds update -a && ./scripts/feeds install -a

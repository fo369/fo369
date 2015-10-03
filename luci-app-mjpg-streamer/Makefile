include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-shadowsocks-libev
PKG_VERSION:=1.0
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/luci-app-mjpg-streamer
SECTION:=LuCI
CATEGORY:=LuCI
SUBMENU:=3. Applications
TITLE:=LuCI Support for mjpg-streamer
DEPENDS:=+mjpg-streamer
PKGARCH:=all
endef

define Package/luci-app-mjpg-streamer/description
LuCI Support for shadowsocks
endef

define Build/Compile
endef

define Package/luci-app-mjpg-streamer/postinst
#!/bin/sh
( . /etc/uci-defaults/luci-app-mjpg-streamer ) && rm -f /etc/uci-defaults/luci-app-mjpg-streamer
exit 0
endef

define Package/luci-app-mjpg-streamer/postrm
#!/bin/sh
uci -q batch <<-EOF >/dev/null
	delete ucitrack.@mjpg-streamer[-1]
	commit ucitrack
EOF
rm -f /tmp/luci-indexcache
rm -rf /tmp/luci-modulecache
exit 0
endef

define Package/luci-app-mjpg-streamer/install
	$(CP) ./root/* $(1)
	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_BIN) ./files/luci-mjpg-streamer.uci $(1)/etc/uci-defaults/luci-mjpg-streamer
endef

$(eval $(call BuildPackage,luci-app-mjpg-streamer))

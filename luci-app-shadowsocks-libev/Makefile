include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-shadowsocks-libev
PKG_VERSION:=1.0
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/luci-app-shadowsocks-libev
SECTION:=LuCI
CATEGORY:=LuCI
SUBMENU:=3. Applications
TITLE:=LuCI Support for shadowsocks-libev
DEPENDS:=+shadowsocks-libev
PKGARCH:=all
endef

define Package/luci-app-shadowsocks-libev/description
LuCI Support for shadowsocks
endef

define Build/Compile
endef

define Package/luci-app-shadowsocks-libev/postinst
#!/bin/sh
( . /etc/uci-defaults/luci-shadowsocks ) && rm -f /etc/uci-defaults/luci-shadowsocks-libev
exit 0
endef

define Package/luci-app-shadowsocks-libev/postrm
#!/bin/sh
uci -q batch <<-EOF >/dev/null
	delete ucitrack.@shadowsocks-libev[-1]
	commit ucitrack
EOF
rm -f /tmp/luci-indexcache
rm -rf /tmp/luci-modulecache
exit 0
endef

define Package/luci-app-shadowsocks-libev/install
	$(CP) ./root/* $(1)
	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_BIN) ./files/luci-shadowsocks-libev.uci $(1)/etc/uci-defaults/luci-shadowsocks-libev
endef

$(eval $(call BuildPackage,luci-app-shadowsocks-libev))

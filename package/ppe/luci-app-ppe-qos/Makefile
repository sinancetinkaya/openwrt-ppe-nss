include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-ppe-qos
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/JuliusBairaktaris/luci.git
PKG_SOURCE_VERSION:=dd87c5f3a783e493b12183c37292b2b6ed96f54f

PKG_MAINTAINER:=Julius Bairaktaris <julius@bairaktaris.de>
PKG_LICENSE:=Apache-2.0

include $(INCLUDE_DIR)/package.mk

define Package/luci-app-ppe-qos
  SECTION:=luci
  CATEGORY:=LuCI
  SUBMENU:=3. Applications
  TITLE:=LuCI support for Qualcomm PPE hardware QoS classifiers
  URL:=https://github.com/JuliusBairaktaris/luci
  DEPENDS:=+luci-base +ppe-qos
  PKGARCH:=all
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/luci-app-ppe-qos/install
	$(INSTALL_DIR) $(1)/www
	$(CP) $(PKG_BUILD_DIR)/applications/luci-app-ppe-qos/htdocs/* $(1)/www/
	$(CP) $(PKG_BUILD_DIR)/applications/luci-app-ppe-qos/root/* $(1)/
endef

define Package/luci-app-ppe-qos/postinst
[ -n "$${IPKG_INSTROOT}" ] || {
	rm -f /tmp/luci-indexcache.*
	rm -rf /tmp/luci-modulecache/
	/etc/init.d/rpcd reload 2>/dev/null
	exit 0
}
endef

$(eval $(call BuildPackage,luci-app-ppe-qos))

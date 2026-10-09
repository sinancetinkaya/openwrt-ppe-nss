include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-qca-ppe-qos
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/JuliusBairaktaris/luci.git
PKG_SOURCE_VERSION:=5db86c77d1ed40879b0b5f15922c5557d522fd76

PKG_MAINTAINER:=Julius Bairaktaris <julius@bairaktaris.de>
PKG_LICENSE:=Apache-2.0

include $(INCLUDE_DIR)/package.mk

define Package/luci-app-qca-ppe-qos
  SECTION:=luci
  CATEGORY:=LuCI
  SUBMENU:=3. Applications
  TITLE:=LuCI support for Qualcomm PPE hardware QoS classifiers
  URL:=https://github.com/JuliusBairaktaris/luci
  DEPENDS:=+luci-base +qca-ppe-qos
  PKGARCH:=all
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/luci-app-qca-ppe-qos/install
	$(INSTALL_DIR) $(1)/www
	$(CP) $(PKG_BUILD_DIR)/applications/luci-app-qca-ppe-qos/htdocs/* $(1)/www/
	$(CP) $(PKG_BUILD_DIR)/applications/luci-app-qca-ppe-qos/root/* $(1)/
endef

define Package/luci-app-qca-ppe-qos/postinst
[ -n "$${IPKG_INSTROOT}" ] || {
	rm -f /tmp/luci-indexcache.*
	rm -rf /tmp/luci-modulecache/
	/etc/init.d/rpcd reload 2>/dev/null
	exit 0
}
endef

$(eval $(call BuildPackage,luci-app-qca-ppe-qos))

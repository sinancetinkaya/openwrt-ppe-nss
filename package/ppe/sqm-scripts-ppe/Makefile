include $(TOPDIR)/rules.mk

PKG_NAME:=sqm-scripts-ppe
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/JuliusBairaktaris/sqm-scripts.git
PKG_SOURCE_VERSION:=13a10078015b08007850a394543dbe7151e94c18


PKG_MAINTAINER:=Julius Bairaktaris <julius@bairaktaris.de>
PKG_LICENSE:=GPL-2.0-only

include $(INCLUDE_DIR)/package.mk

define Package/sqm-scripts-ppe
  SECTION:=net
  CATEGORY:=Network
  TITLE:=SQM scripts (Smart Queue Management, PPE build)
  URL:=https://github.com/JuliusBairaktaris/sqm-scripts
  DEPENDS:=+tc-full +kmod-sched-cake +kmod-sched-core +kmod-sched-flower \
	+kmod-sched-mqprio +kmod-ifb +nftables-json
  PROVIDES:=sqm-scripts
  PKGARCH:=all
endef

define Package/sqm-scripts-ppe/description
  Traffic shaping scripts (cake, fq_codel, etc.) with OpenWrt hotplug,
  init and UCI integration. Drop-in replacement for sqm-scripts.
endef

define Package/sqm-scripts-ppe/conffiles
/etc/config/sqm
/etc/sqm/sqm.conf
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/sqm-scripts-ppe/install
	$(MAKE) -C $(PKG_BUILD_DIR) \
		PLATFORM=openwrt \
		PREFIX=/usr \
		DESTDIR=$(1) \
		install
endef

define Package/sqm-scripts-ppe/postinst
#!/bin/sh
[ -n "$${IPKG_INSTROOT}" ] || {
	/etc/init.d/sqm enable
}
exit 0
endef

define Package/sqm-scripts-ppe/prerm
#!/bin/sh
[ -n "$${IPKG_INSTROOT}" ] || {
	/etc/init.d/sqm stop
	/etc/init.d/sqm disable
}
exit 0
endef

$(eval $(call BuildPackage,sqm-scripts-ppe))



include $(TOPDIR)/rules.mk

PKG_NAME:=v2ray-geodata-singbox
PKG_RELEASE:=1

PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=xwcoco <xwcoco@gmail.com>

include $(INCLUDE_DIR)/package.mk

GEOIP_VER:=20221112
GEOIP_FILE:=geoip.db.$(GEOIP_VER)

define Download/geoip
  URL:=https://github.com/SagerNet/sing-geoip/releases/latest/download
  URL_FILE:=geoip.db
  FILE:=$(GEOIP_FILE)
  HASH:=skip
endef

GEOSITE_VER:=20221205040509
GEOSITE_FILE:=geosite.db.$(GEOSITE_VER)
define Download/geosite
  URL:=https://github.com/SagerNet/sing-geosite/releases/latest/download
  URL_FILE:=geosite.db
  FILE:=$(GEOSITE_FILE)
  HASH:=skip
endef

define Package/v2ray-geodata-singbox/template
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=IP Addresses and Names
  URL:=https://www.v2fly.org
  PKGARCH:=all
endef

define Package/v2ray-geoip-singbox
  $(call Package/v2ray-geodata-singbox/template)
  TITLE:=GeoIP List for Singbox
  VERSION:=$(GEOIP_VER)-$(PKG_RELEASE)
  LICENSE:=CC-BY-SA-4.0
endef

define Package/v2ray-geosite-singbox
  $(call Package/v2ray-geodata-singbox/template)
  TITLE:=Geosite List for Singbox
  VERSION:=$(GEOSITE_VER)-$(PKG_RELEASE)
  LICENSE:=MIT
endef

define Build/Prepare
  $(call Build/Prepare/Default)
ifneq ($(CONFIG_PACKAGE_v2ray-geoip-singbox),)
  $(call Download,geoip)
endif
ifneq ($(CONFIG_PACKAGE_v2ray-geosite-singbox),)
  $(call Download,geosite)
endif
endef

define Build/Compile
endef

define Package/v2ray-geoip-singbox/install
  $(INSTALL_DIR) $(1)/etc/singbox
  $(INSTALL_DATA) $(DL_DIR)/$(GEOIP_FILE) $(1)/etc/singbox/geoip.db
  echo "$(GEOIP_VER)" > $(1)/etc/singbox/geo_ip_version
endef

define Package/v2ray-geosite-singbox/install
  $(INSTALL_DIR) $(1)/etc/singbox
  $(INSTALL_DATA) $(DL_DIR)/$(GEOSITE_FILE) $(1)/etc/singbox/geosite.db
  echo "$(GEOSITE_VER)" > $(1)/etc/singbox/geo_site_version
endef
$(eval $(call BuildPackage,v2ray-geoip-singbox))
$(eval $(call BuildPackage,v2ray-geosite-singbox))
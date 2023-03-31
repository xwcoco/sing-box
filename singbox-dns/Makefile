#
# Copyright (C) 2016-2017 GitHub 
#
# This is free software, licensed under the GNU General Public License v3.
# See /LICENSE for more information.

include $(TOPDIR)/rules.mk

PKG_NAME:=xwcoco-singox-dns
PKG_VERSION:=1.2.1
PKG_RELEASE:=1
PKG_LICENSE:=GPLv3
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Web Servers/Proxies
  TITLE:=singbox dns fix.
  URL:=https://sing-box.sagernet.org
  DEPENDS:=$(GO_ARCH_DEPENDS) \
    +ca-bundle \
    +kmod-inet-diag \
    +kmod-netlink-diag \
    +kmod-tun
endef

define Package/x$(PKG_NAME)/description
	singbox add multi dns support.
endef


define Build/Configure
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) ./files/sing-box $(1)/etc/uci-defaults/sing-box
endef

$(eval $(call BuildPackage,$(PKG_NAME)))

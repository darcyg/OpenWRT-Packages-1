# 
# Copyright (C) 2006-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# Initial port of shellinabox to OpenWrt - Jan Jaeger 25-MAR-2010

include $(TOPDIR)/rules.mk

PKG_NAME:=shellinabox
PKG_VERSION:=2.10
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://shellinabox.googlecode.com/files
PKG_MD5SUM:=0e144910d85d92edc54702ab9c46f032

include $(INCLUDE_DIR)/package.mk

define Package/shellinabox
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Shell In A Box
	DEPENDS:= zlib
	URL:=http://shellinabox.googlecode.com
endef

define Package/shellinabox/description
Web based AJAX terminal emulator
endef

define Build/Configure
	$(call Build/Configure/Default)
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		$(TARGET_CONFIGURE_OPTS) \
		CFLAGS="$(TARGET_CFLAGS)" \
		BINDIR="/usr/sbin" \
		all
endef

define Package/shellinabox/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/shellinaboxd $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/$(PKG_NAME).init $(1)/etc/init.d/$(PKG_NAME)
endef

$(eval $(call BuildPackage,shellinabox))

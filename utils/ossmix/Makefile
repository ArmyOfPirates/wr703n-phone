#
# Copyright (C) 2010-2013 OpenWrt.org
# Copyright (C) 2010 Alfred E. Heggestad
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=ossmix
PKG_VERSION:=0.0.1
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/ossmix/Default
  SECTION:=utils
  CATEGORY:=Base system
  URL:=http://www.nope.gif/
endef

define Package/ossmix
$(call Package/ossmix/Default)
  TITLE:=OSS mixer
  DEPENDS:=+kmod-sound-core
endef

TARGET_CFLAGS += $(FPIC) -I$(LINUX_DIR)/include

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		CC="$(TARGET_CC)" \
		DESTDIR="$(PKG_INSTALL_DIR)" \
		EXTRA_CFLAGS="$(TARGET_CFLAGS) -DOPENWRT" \
		SYSROOT="$$$$($(FIND) $(TOOLCHAIN_DIR) -path '*/include/pthread.h' | sed -ne '1s#/include/pthread.h##p')" \
		SYSROOT_ALT="$(STAGING_DIR)/usr" \
		RELEASE=1 \
		CROSS_COMPILE="$(TARGET_CROSS)" \
		OS="linux" \
		all
endef

define Package/ossmix/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR) $(1)/usr/bin/ossmix
endef


$(eval $(call BuildPackage,ossmix))

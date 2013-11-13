#
# Copyright (C) 2006-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=amixer
PKG_VERSION:=1.0.24.2
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=ftp://ftp.alsa-project.org/pub/utils/ \
		http://alsa.cybermirror.org/utils/
PKG_MD5SUM:=8238cd57cb301d1c36bcf0ecb59ce6b2
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/amixer
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+alsa-lib +libpthread
# +libncurses
  TITLE:=ALSA (Advanced Linux Sound Architecture) mixer
  URL:=http://www.alsa-project.org/
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--disable-rpath \
		--disable-alsatest \
		--disable-xmlto \
		, \
		ac_cv_prog_ncurses5_config=no \
		ac_cv_prog_ncursesw5_config=no \
	)
endef

define Package/amixer/install
	$(INSTALL_DIR) $(1)/usr/{s,}bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/amixer $(1)/usr/bin/
#	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/alsamixer $(1)/usr/bin/
#	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/aplay $(1)/usr/bin/
#	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/arecord $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/alsactl $(1)/usr/sbin/

	$(INSTALL_DIR) $(1)/usr/share/alsa/init
	$(INSTALL_DATA) \
	    $(PKG_INSTALL_DIR)/usr/share/alsa/init/* \
	    $(1)/usr/share/alsa/init/
endef

$(eval $(call BuildPackage,amixer))

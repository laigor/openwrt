#
# Copyright (C) 2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=v4l-dvb
# PKG_REV:=e7d0ae06c74f55562c1589feb5a6802d77c14dbc
PKG_REV:=26b16ecad9e61c090b1492a6d5861870ac4d67cd
PKG_VERSION:=$(PKG_REV)
PKG_RELEASE:=3

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_REV).tar.bz2
PKG_SOURCE_URL:=git://linuxtv.org/media_build.git
PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=0

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define Package/v4l-dvb
  SECTION:=multimedia
  CATEGORY:=Multimedia
#  DEPENDS:=kmod-dvb-core +@KERNEL_KALLSYMS
  DEPENDS:=kmod-usb-core
  TITLE:=V4L-dvb
  URL:=http://www.linuxtv.org/
endef

define Package/v4l-dvb/description
  Live development version of V4L and DVB driver
endef

MAKE_VARS += \
	TOPDIR="" \
	KDIR=$(LINUX_DIR) \
	DIR=$(LINUX_DIR)\
	SRCDIR=$(LINUX_DIR)

define Build/Prepare
	$(call Build/Prepare/Default)
	if [ -d $(DL_DIR)/media_tree ] ; then (cd $(DL_DIR)/media_tree;git pull); else git clone --single-branch --depth 1 git://linuxtv.org/media_tree.git  $(DL_DIR)/media_tree;  fi
	( cd $(PKG_BUILD_DIR)/linux ; make tar DIR=$(DL_DIR)/media_tree )
	$(call Build/Compile/Default,untar)
#	$(call Build/Compile/Default,allmodconfig)
#	$(call Build/Compile/Default,xconfig)
#	$(call Build/Compile/Default,stagingconfig)
#	$(call Build/Compile/Default,allmodconfig)
	$(call Build/Compile/Default,menuconfig)
#	mv $(PKG_BUILD_DIR)/v4l/Makefile.media $(PKG_BUILD_DIR)/v4l/Makefile.media.old
#	cat $(PKG_BUILD_DIR)/v4l/Makefile.media.old | sed -r 's|\s+strip\s+| ${STRIP} |g' >$(PKG_BUILD_DIR)/v4l/Makefile.media
endef

#define Build/Configure
#	$(call Build/Compile/Default,tar DIR=$(DL_DIR)/media_tree)
#	$(CP) $(LINUX_DIR)/.config $(PKG_BUILD_DIR)/v4l/.config
#endef

define Build/Compile
#	$(call Build/Compile/Default,download)
#	$(call Build/Compile/Default,untar)
#	$(call Build/Compile/Default,allmodconfig)
#	$(call Build/Compile/Default,stagingconfig)
	$(call Build/Compile/Default)
#	$(call Build/Compile/Default,install)
endef


define Package/v4l-dvb/install
#	$(call Build/Compile/Default,install)
	$(INSTALL_DIR) $(1)/lib/modules/$(LINUX_VERSION)
#	$(FIND) $(PKG_INSTALL_DIR) -name *.$(LINUX_KMOD_SUFFIX) -type f | xargs cp -t $(1)/lib/modules/$(LINUX_VERSION)/
	$(FIND) $(PKG_INSTALL_DIR) -name *.$(LINUX_KMOD_SUFFIX) -type f -exec cp "{}" $(1)/lib/modules/$(LINUX_VERSION)/ \;
endef

$(eval $(call BuildPackage,v4l-dvb))

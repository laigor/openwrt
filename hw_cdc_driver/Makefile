# 
# Copyright (C) 2006-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=kmod-hw_cdc_driver
PKG_RELEASE:=1
#http://download-c.huawei.com/download/downloadCenter?downloadId=13971

include $(INCLUDE_DIR)/package.mk

define KernelPackage/hw_cdc_driver
  SUBMENU:=USB Support
  DEPENDS:=@USB_SUPPORT
  TITLE:=Huawei cdc driver
  FILES:= $(PKG_BUILD_DIR)/hw_cdc_driver.ko
  AUTOLOAD:=$(call AutoLoad,90,hw_cdc_driver)
endef

define KernelPackage/hw_cdc_driver/description
 Huawei cdc driver
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Compile
	$(MAKE) -C "$(LINUX_DIR)" \
		CROSS_COMPILE="$(TARGET_CROSS)" \
		ARCH="$(LINUX_KARCH)" \
		SUBDIRS="$(PKG_BUILD_DIR)" \
		EXTRA_CFLAGS="$(BUILDFLAGS)" \
		modules
endef

#define Build/InstallDev
#	mkdir -p $(1)/usr/include
#	$(CP) ./src/switch-core.h $(1)/usr/include/
#endef

#define Build/UninstallDev
#	rm -f $(1)/usr/include/switch-core.h
#endef

#define KernelPackage/switch/install
#	$(INSTALL_DIR) $(1)/lib/network/
#	$(INSTALL_BIN) ./files/switch.sh $(1)/lib/network/
#endef

$(eval $(call KernelPackage,hw_cdc_driver))

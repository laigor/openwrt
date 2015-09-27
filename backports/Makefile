#
# Copyright (C) 2009-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=backports
PKG_SUBVERSION:=3.10-rc1
PKG_VERSION:=$(PKG_SUBVERSION)-2
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_RELEASE:=1
PKG_SOURCE_URL:=https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v$(PKG_SUBVERSION)
#/$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SUBVERSION).tar.xz
#https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.10-rc1/backports-3.10-rc1-2.tar.xz
# PKG_MD5SUM:=bc107f9d8ff6bed4c2760a2817bbb029
TARGET_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl-stub/include
include $(INCLUDE_DIR)/package.mk

define KernelPackage/backports
  SUBMENU:=Kernel-Backports
  TITLE:=Linux kernel backports
  URL:=https://backports.wiki.kernel.org/index.php/Main_Page
  MAINTAINER:=Laigor
  FILES:=btsco.ko
  AUTOLOAD:=
#  FILES:=$(PKG_BUILD_DIR)/src/drv_ifxos.ko
#  AUTOLOAD:=$(call AutoLoad,10,drv_ifxos)
endef

#CONFIGURE_ARGS += \
#	ARCH=$(LINUX_KARCH) \
#	--enable-linux-26 \
#	--enable-kernelbuild="$(LINUX_DIR)" \
#	--enable-kernelincl="$(LINUX_DIR)/include" \
#	--enable-add_drv_cflags="-fno-pic -mno-abicalls -mlong-calls -G 0"

#define Build/Configure
#	(cd $(PKG_BUILD_DIR); make menuselect)
#	$(call Build/Configure/Default)
#	make menuselect
#	$(call Build/Compile/Default,menuconfig)
#	$(MAKE) -C "$(PKG_BUILD_DIR)" CROSS_COMPILE="$(KERNEL_CROSS)" ARCH="$(LINUX_KARCH)" EXTRA_CFLAGS="-I$(PKG_BUILD_DIR)/include" menuconfig
#endef

# TARGET_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl-stub/include

define Build/Compile
	$(MAKE) -C "$(PKG_BUILD_DIR)" CROSS_COMPILE="$(KERNEL_CROSS)" ARCH="$(LINUX_KARCH)" EXTRA_CFLAGS="-I$(PKG_BUILD_DIR)/include -Wno-undef" KLIB_BUILD="$(LINUX_DIR)" MODPROBE=true KLIB=$(TARGET_MODULES_DIR) KERNEL_SUBLEVEL=$(lastword $(subst ., ,$(KERNEL_PATCHVER))) KBUILD_LDFLAGS_MODULE_PREREQ= menuconfig modules
#	$(MAKE) -C "$(PKG_BUILD_DIR)" KLIB_BUILD="$(LINUX_DIR)" CROSS_COMPILE="$(TARGET_CROSS)" MODPROBE=true KLIB=$(TARGET_MODULES_DIR) EXTRA_CFLAGS="-I$(PKG_BUILD_DIR)/include" menuconfig modules
#	$(call Build/Compile/Default, KLIB_BUILD="$(LINUX_DIR)" CROSS_COMPILE="$(TARGET_CROSS)" MODPROBE=true KLIB=$(TARGET_MODULES_DIR) EXTRA_CFLAGS="-I$(PKG_BUILD_DIR)/include" modules)
#	$(MAKE) -C "$(PKG_BUILD_DIR)" CROSS_COMPILE="$(KERNEL_CROSS)" ARCH="$(LINUX_KARCH)" EXTRA_CFLAGS="-I$(PKG_BUILD_DIR)/include" modules
endef


$(eval $(call KernelPackage,backports))

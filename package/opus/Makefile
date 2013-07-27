# To build
# make oldconfig
# make package/opus/compile V=99
# To just run the packaging again
# make package/opus/compile V=99 CONFIG_AUTOREBUILD=

include $(TOPDIR)/rules.mk

PKG_NAME:=opus
PKG_VERSION:=1.0.3
PKG_RELEASE:=$(PKG_SOURCE_VERSION)

PKG_SOURCE:=opus-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://downloads.xiph.org/releases/opus/
PKG_MD5SUM:=86eedbd3c5a0171d2437850435e6edff

include $(INCLUDE_DIR)/package.mk

define Package/opus
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Opus codec
endef

# This uses the upstream install to put build products into $(PKG_INSTALL_DIR)
PKG_INSTALL:=1

# Now we pick what we really want to package from the build products
define Package/opus/install
  $(INSTALL_DIR) $(1)/usr/lib/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/libopus.s* $(1)/usr/lib/
endef

# Need to make the header available so that we can compile, e.g., parole later on
define Build/InstallDev
	$(INSTALL_DIR) $(STAGING_DIR)/usr/include/opus
	$(CP) $(PKG_BUILD_DIR)/include/* $(STAGING_DIR)/usr/include/opus/
	$(INSTALL_DIR) $(STAGING_DIR)/usr/lib/pkgconfig/
	$(CP) $(PKG_BUILD_DIR)/opus.pc $(STAGING_DIR)/usr/lib/pkgconfig/
	$(INSTALL_DIR) $(1)/usr/lib/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/libopus.so $(STAGING_DIR)/usr/lib/
endef

$(eval $(call BuildPackage,opus))

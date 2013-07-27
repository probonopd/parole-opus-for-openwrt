include $(TOPDIR)/rules.mk

PKG_NAME:=parole
PKG_VERSION:=010beta4
PKG_RELEASE:=$(PKG_SOURCE_VERSION)

PKG_SOURCE:=parole-$(PKG_VERSION).tgz
PKG_SOURCE_URL:=http://holdenc.altervista.org/parole/downloads/
PKG_MD5SUM:=755d7f40bd6b132340092e4f58995a3c

include $(INCLUDE_DIR)/package.mk

# Point to the headers
TARGET_CFLAGS += \
        -I$(STAGING_DIR)/usr/include \
        -I$(STAGING_DIR)/usr/include/opus

define Package/parole
  SECTION:=base
  CATEGORY:=Network
  DEPENDS:=+opus +alsa-lib +libogg +librt
  TITLE:=Simple voip program using the Opus codec
endef

define Package/parole/install
  $(INSTALL_DIR) $(1)/usr/bin/
	$(CP) $(PKG_BUILD_DIR)/parole $(1)/usr/bin/
endef

$(eval $(call BuildPackage,parole))

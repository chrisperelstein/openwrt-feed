include $(TOPDIR)/rules.mk

PKG_NAME:=goeap_proxy
PKG_VERSION:=0.1.2
PKG_RELEASE:=1
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/chrisperelstein/goeap_proxy.git
PKG_SOURCE_VERSION:=5e9e61e46ad9a9c6e9eb4efb6cbad966e2286aa0
PKG_SOURCE_DATE:=2020-06-27
PKG_MIRROR_HASH:=skip

GO_PKG:=github.com/pyther/goeap_proxy
GO_PKG_LDFLAGS_X:=main.Version=$(PKG_VERSION) main.BuildStamp=`date +%FT%T%z`

include $(INCLUDE_DIR)/package.mk
include ../../../../feeds/packages/lang/golang/golang-package.mk

define Package/goeap_proxy
	SECTION=:net
 	CATEGORY:=Network
	TITLE:=Proxy EAP packets between interfaces
  	URL:=https://github.com/pyther/goeap_proxy
	DEPENDS:=$(GO_ARCH_DEPENDS)
endef

define Package/goeap_proxy/description
Daemon written python to proxy EAP Authentication packets

endef

define Package/goeap_proxy/conffiles
/etc/config/goeap_proxy
endef

define Package/goeap_proxy/install
	$(call GoPackage/Package/Install/Bin,$(1))
	
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/etc/init.d/goeap_proxy $(1)/etc/init.d/goeap_proxy

	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/etc/config/goeap_proxy $(1)/etc/config/goeap_proxy
endef

$(eval $(call GoBinPackage,goeap_proxy))
$(eval $(call BuildPackage,goeap_proxy))


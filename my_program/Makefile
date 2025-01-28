include $(TOPDIR)/rules.mk

PKG_NAME:=my_program
PKG_VERSION:=1.0
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/my_program
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=My Custom Program
  DEPENDS:=
endef

define Package/my_program/description
  A simple C program for OpenWrt.
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Compile
	$(TARGET_CC) $(TARGET_CFLAGS) -o $(PKG_BUILD_DIR)/my_program $(PKG_BUILD_DIR)/my_program.c
endef

define Package/my_program/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/my_program $(1)/usr/bin/
endef

$(eval $(call BuildPackage,my_program))
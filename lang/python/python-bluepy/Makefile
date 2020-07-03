# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-bluepy
PKG_VERSION:=1.3.0
PKG_RELEASE:=1

PYPI_NAME:=bluepy
PKG_HASH:=2a71edafe103565fb990256ff3624c1653036a837dfc90e1e32b839f83971cec

PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=LICENSE

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python3-package.mk

define Package/python3-bluepy
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python interface to Bluetooth LE on Linux
  URL:=https://github.com/IanHarvey/bluepy
  DEPENDS:=+python3-light +python3-setuptools +glib2
endef

define Package/python3-bluepy/description
  This is a project to provide an API to allow access to Bluetooth Low Energy
  devices from Python. 
endef

MAKE_PATH:=bluepy/

define Build/Compile
	$(call Build/Compile/Default)
	$(call Py3Build/Compile)
endef

define Package/bluepy/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
	    $(1)$(PYTHON_PKG_DIR)
	$(RM) $(1)$(PYTHON_PKG_DIR)/usr/lib/python3*/site-packages/bluepy/{bluepy-helper.c,Makefile,bluez-src.tgz}
endef

$(eval $(call Py3Package,python3-bluepy))
$(eval $(call BuildPackage,python3-bluepy))
$(eval $(call BuildPackage,python3-bluepy-src))

#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=numpy
PKG_VERSION:=1.12.0
PKG_RELEASE:=1
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).zip
PKG_SOURCE_URL:=https://pypi.python.org/packages/b7/9d/8209e555ea5eb8209855b6c9e60ea80119dab5eff5564330b35aa5dc4b2c/
PKG_MD5SUM:=33e5a84579f31829bbbba084fe0a4300

include $(INCLUDE_DIR)/package.mk
-include $(if $(DUMP),,$(STAGING_DIR)/mk/python-package.mk)

define Package/numpy
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=numpy
  URL:=http://numpy.sf.net
  DEPENDS:=python-core @TARGET_x86||TARGET_olpc||TARGET_uml @BROKEN
endef

define Package/numpy/description
  API to GTK and glade library from python
endef

define Build/Compile
	cd $(PKG_BUILD_DIR) ; $(CONFIGURE_VARS) $(MAKE_VARS) python2.7 ./setup.py install --prefix="$(PKG_INSTALL_DIR)/usr"
endef

define Package/numpy/install
	mkdir -p $(1)
	cp -r $(PKG_INSTALL_DIR)/* $(1)
endef

$(eval $(call BuildPackage,numpy))

define Require/python27-dev
[ -e /usr/include/python2.7/pyconfig.h ]
endef

$(eval $(call Require,python27-dev, \
	Please install Python 2.7 (including development headers and libraries) \
))

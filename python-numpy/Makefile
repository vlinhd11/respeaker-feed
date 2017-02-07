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
PKG_SOURCE:=numpy-$(PKG_VERSION).zip
PKG_SOURCE_URL:=https://pypi.python.org/packages/b7/9d/8209e555ea5eb8209855b6c9e60ea80119dab5eff5564330b35aa5dc4b2c/
PKG_MD5SUM:=33e5a84579f31829bbbba084fe0a4300

include $(INCLUDE_DIR)/package.mk
-include $(if $(DUMP),,$(STAGING_DIR)/mk/python-package.mk)

define Package/numpy
  SECTION:=respeaker
  CATEGORY:=ReSpeaker
  TITLE:=numpy
  URL:=http://numpy.sf.net
  DEPENDS:=+python
endef

define Package/numpy/description
  API to GTK and glade library from python
endef

define Build/Compile
	$(call Build/Compile/PyMod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)" \
	)
endef

define Package/numpy/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,numpy))

include $(TOPDIR)/rules.mk

PKG_NAME:=psutil
PKG_VERSION:=5.1.0
PKG_RELEASE:=1

PKG_SOURCE:=psutil-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/ba/5f/87b151dd53f8790408adf5096fc81c3061313c36a089d9f7ec9e916da0c1/

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-psutil
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python-psutil
  URL:=https://pypi.python.org/pypi/psutil
  DEPENDS:=+python
endef

define Package/python-psutil/description
  psutil is a module providing an interface for retrieving information on all running processes and system utilization (CPU, memory, disks, network, users) in a portable way by using Python.
endef

define Build/Compile
	$(call Build/Compile/PyMod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)" \
	)
endef

define Package/python-psutil/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python-psutil))

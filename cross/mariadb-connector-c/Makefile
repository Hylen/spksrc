PKG_NAME = mariadb-connector-c
PKG_VERS = 3.1.7
PKG_EXT = tar.gz
DIST_NAME = v$(PKG_VERS)
PKG_DIST_NAME = $(DIST_NAME).$(PKG_EXT)
HOMEPAGE = https://github.com/mariadb-corporation/$(PKG_NAME)
PKG_DIST_SITE = $(HOMEPAGE)/archive
PKG_DIR = $(PKG_NAME)-$(PKG_VERS)

COMMENT  = Mariadb Connector/C, API for connecting from C
LICENSE  = LGPL

DEPENDS = cross/openssl

CONFIGURE_TARGET=mariadb_connector_c_configure

CMAKE_ARGS  = -DCMAKE_BUILD_TYPE=Release
CMAKE_ARGS += -DCMAKE_INSTALL_PREFIX=$(INSTALL_PREFIX)

CMAKE_ARGS  = -DCMAKE_BUILD_TYPE=Release
CMAKE_ARGS += -DCMAKE_INSTALL_PREFIX=$(INSTALL_PREFIX)
CMAKE_ARGS += -DCMAKE_CROSSCOMPILING=1
CMAKE_ARGS += -DCMAKE_SYSTEM_NAME=Linux
CMAKE_ARGS += -DCMAKE_C_COMPILER=$(TC_PATH)$(TC_PREFIX)gcc
CMAKE_ARGS += -DCMAKE_CXX_COMPILER=$(TC_PATH)$(TC_PREFIX)g++

CMAKE_ARGS +=  -DWITH_SSL=OPENSSL

POST_INSTALL_TARGET = mariadb_connector_c_post_install

.PHONY: mariadb_connector_c_configure

include ../../mk/spksrc.cross-cc.mk

mariadb_connector_c_configure:
	$(RUN) cmake $(CMAKE_ARGS)

mariadb_connector_c_post_install:
	cd $(STAGING_INSTALL_PREFIX)/lib/mariadb/ && \
		ln -s libmariadb.so libmysqlclient.so

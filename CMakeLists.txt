# Copyright (C) 2016 LuaDist.
# Created by Peter Kapec
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

project ( luasystem C )
cmake_minimum_required ( VERSION 2.8 )
include ( cmake/dist.cmake )
include ( lua )

set(SRC  src/core.c src/compat.c src/time.c )

if ( WIN32 )
  add_definitions ( "-DWINVER=0x0600" "-D_WIN32_WINNT=0x0600" )
endif ( )

if ( UNIX )
  set ( LIBS rt )
endif ( )

install_lua_module ( system.core ${SRC} LINK ${LIBS})
install_lua_module ( system.init system/init.lua )

install_doc ( README.md LICENSE )
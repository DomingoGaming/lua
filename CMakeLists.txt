cmake_minimum_required(VERSION 3.5)

project (lua)

file (
  GLOB SRCS
  lbaselib.c
  ldblib.c
  liolib.c
  lmathlib.c
  loslib.c
  ltablib.c
  lstrlib.c
  lutf8lib.c
  lbitlib.c
  loadlib.c
  lcorolib.c
  linit.c
)

set (
	CFLAGS
	-g
	-pedantic
	-Wextra
	-Wshadow
	-Wsign-compare
	-Wundef
	-Wwrite-strings
	-Wredundant-decls
	-Wdisabled-optimization
	-Wdeclaration-after-statement
	-Wmissing-prototypes
	-Wnested-externs
	-Wstrict-prototypes
	-Wc++-compat
	-Wold-style-definition

	-std=c99
	-DLUA_COMPAT_5_2
)

if (LINUX)
set (
	CFLAGS
	${CFLAGS} 
	-DLUA_USE_LINUX
	)
endif (LINUX)


set (
	LDFLAGS
	${CFLAGS}
)

set( CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} ${CFLAGS}" )
set( CMAKE_EXE_LINKER_FLAGS  "${CMAKE_EXE_LINKER_FLAGS} ${LDFLAGS}" )

add_library(lua STATIC ${SRCS})

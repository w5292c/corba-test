cmake_minimum_required (VERSION 2.6)

project (corba-test)

find_package ( Threads )
find_package ( Qt4       REQUIRED )
find_package ( PkgConfig REQUIRED )

set ( CODE_ROOT ${CMAKE_SOURCE_DIR}/src/ )

include_directories ( ${MCODE_TOP} )

INCLUDE ( ${QT_USE_FILE} )
ADD_DEFINITIONS ( ${QT_DEFINITIONS} )

set ( SRC_LIST
  ${CODE_ROOT}/main.cpp
)

add_executable( corba-test ${SRC_LIST} )
target_link_libraries ( corba-test ${CMAKE_THREAD_LIBS_INIT} )
target_link_libraries ( corba-test  ${QT_LIBRARIES} )

cmake_minimum_required (VERSION 2.6)

project (corba-test)

find_package ( Threads )
find_package ( Qt4       REQUIRED )
find_package ( PkgConfig REQUIRED )

pkg_check_modules ( OMNIORB4    omniORB4        REQUIRED )
link_directories ( ${OMNIORB4_LIBRARY_DIRS} )

set ( CODE_ROOT ${CMAKE_SOURCE_DIR}/src/ )

include_directories ( ${OMNIORB4_INCLUDE_DIRS} ${MCODE_TOP} )

INCLUDE ( ${QT_USE_FILE} )
ADD_DEFINITIONS ( ${QT_DEFINITIONS} )

set ( SRC_LIST
  ${CODE_ROOT}/main.cpp
)

set ( SERVER_SRC_LIST
  ${CODE_ROOT}/dataSK.cc
  ${CODE_ROOT}/server.cpp
  ${CODE_ROOT}/CServiceA.cpp
)

add_executable( corba-test ${SRC_LIST} )
target_link_libraries ( corba-test ${CMAKE_THREAD_LIBS_INIT} )
target_link_libraries ( corba-test  ${QT_LIBRARIES} )
target_link_libraries ( corba-test  ${OMNIORB4_LIBRARIES} )

add_executable( corba-server ${SERVER_SRC_LIST} )
target_link_libraries ( corba-server  ${OMNIORB4_LIBRARIES} )

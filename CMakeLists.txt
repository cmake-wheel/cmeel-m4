cmake_minimum_required(VERSION 3.20)

set(M4_VERSION 1.4.19)

project(cmeel-m4 VERSION ${M4_VERSION})

include(ExternalProject)
ExternalProject_Add(
  m4
  URL "https://ftpmirror.gnu.org/gnu/m4/m4-${M4_VERSION}.tar.xz"
  DOWNLOAD_EXTRACT_TIMESTAMP ON
  BUILD_IN_SOURCE ON
  CONFIGURE_COMMAND "./configure" "--prefix=${CMAKE_INSTALL_PREFIX}"
  BUILD_COMMAND "make"
  #TEST_COMMAND "make" "check"
  INSTALL_COMMAND "make" "install")

# dummy file for install target
install(FILES README.md DESTINATION share/cmeel-m4/)

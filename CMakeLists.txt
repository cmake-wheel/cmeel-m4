cmake_minimum_required(VERSION 3.30)

set(NAME m4)
set(VERSION 1.4.20)
set(EXT tar.xz)
set(SHA256 e236ea3a1ccf5f6c270b1c4bb60726f371fa49459a8eaaebc90b216b328daf2b)

project("cmeel-${NAME}" VERSION "${VERSION}")

include(ExternalProject)
ExternalProject_Add(
  ${NAME}
  URL "https://ftpmirror.gnu.org/gnu/${NAME}/${NAME}-${VERSION}.${EXT}"
  URL_HASH "SHA256=${SHA256}"
  DOWNLOAD_EXTRACT_TIMESTAMP ON
  BUILD_IN_SOURCE ON
  CONFIGURE_COMMAND "./configure" "--prefix=${CMAKE_INSTALL_PREFIX}"
  BUILD_COMMAND "make"
  # TEST_COMMAND "make" "check"
  INSTALL_COMMAND "make" "install")

# dummy file for install target
install(FILES "README.md" DESTINATION "share/cmeel-${NAME}/")

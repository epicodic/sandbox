project(sandbox)
cmake_minimum_required(VERSION 3.15)


add_executable(sandbox
    dummy.cpp
)

install(TARGETS	sandbox
        ARCHIVE DESTINATION "${CMAKE_INSTALL_LIBDIR}"
        LIBRARY DESTINATION "${CMAKE_INSTALL_LIBDIR}"
        RUNTIME DESTINATION "${CMAKE_INSTALL_BINDIR}"
)

set(CPACK_GENERATOR "DEB")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "epicodic@web.de")
set(CPACK_PACKAGING_INSTALL_PREFIX "/opt/sandbox")
set(CPACK_INSTALL_PREFIX "/opt/sandbox")
set(CPACK_PACKAGE_NAME "sandbox")
set(CPACK_PACKAGE_VERSION_MAJOR 1)
set(CPACK_PACKAGE_VERSION_MINOR 0)

set(CPACK_PACKAGE_VERSION_PATCH "$ENV{GITHUB_RUN_NUMBER}-$ENV{DISTRO_CODENAME}")

set(CPACK_DEBIAN_PACKAGE_NAME "${CPACK_PACKAGE_NAME}")
set(CPACK_DEBIAN_FILE_NAME "${CPACK_PACKAGE_NAME}-${CPACK_PACKAGE_VERSION_MAJOR}.${CPACK_PACKAGE_VERSION_MINOR}.${CPACK_PACKAGE_VERSION_PATCH}.deb")

set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "sandbox")
set(CPACK_PACKAGE_INSTALL_DIRECTORY "sandbox")
set(CPACK_PACKAGE_VENDOR "sandbox")
#set(CPACK_DEBIAN_PACKAGE_SHLIBDEPS ON)
set(CPACK_PACKAGE_CONTACT "epicodic@web.de")

include(CPack)


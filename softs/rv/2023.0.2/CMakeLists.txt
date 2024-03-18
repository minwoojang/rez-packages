CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

include(RezBuild)
include(RezRepository)
include(ExternalProject)

set(url_rv https://sg-software.ems.autodesk.com/deploy/rv/Previous_Release/Linux-release.tar.gz)

set(install_cmd ${CMAKE_CURRENT_SOURCE_DIR}/install.sh
    ${CMAKE_CURRENT_BINARY_DIR} ${CMAKE_INSTALL_PREFIX} ${RV_MAJOR_VERSION})


ExternalProject_add(
    rv
    URL ${url_rv}
    PREFIX rv
    UPDATE_COMMAND ""
    CONFIGURE_COMMAND ""
    INSTALL_COMMAND ${install_cmd}
    BUILD_COMMAND ""
    BUILD_IN_SOURCE 1
)

install(DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/rv/src/rv/ DESTINATION ${CMAKE_INSTALL_PREFIX})

project(gameclient.bnes)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(xbmc REQUIRED)

include(ExternalProject)

externalproject_add(bnes
                    GIT_REPOSITORY https://github.com/libretro/bnes-libretro
                    GIT_TAG ba52a8277
                    PREFIX bnes
                    CONFIGURE_COMMAND ""
                    INSTALL_COMMAND ""
                    BUILD_COMMAND make CXX=${CMAKE_CXX_COMPILER}
                    BUILD_IN_SOURCE 1)

set(BNES_CUSTOM_BINARY ${PROJECT_BINARY_DIR}/bnes/src/bnes/libretro${CMAKE_SHARED_LIBRARY_SUFFIX}
                        bnes_libretro${CMAKE_SHARED_LIBRARY_SUFFIX} bnes)

build_addon(gameclient.bnes BNES DEPLIBS)
add_dependencies(gameclient.bnes bnes)

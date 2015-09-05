project(game.libretro.bnes)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(kodi REQUIRED)
find_package(libretro-bnes REQUIRED)

set(DEPLIBS bnes)
set(BNES_CUSTOM_BINARY ${BNES_LIB}
                       game.libretro.bnes${CMAKE_SHARED_LIBRARY_SUFFIX} bnes)

build_addon(game.libretro.bnes BNES DEPLIBS)


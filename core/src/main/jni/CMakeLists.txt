cmake_minimum_required(VERSION 3.28)
project(core)

add_subdirectory(${EXTERNAL_ROOT} external)

aux_source_directory(src SRC_LIST)
aux_source_directory(src/jni SRC_LIST)

aux_source_directory(src/xzlib SRC_LIST)
#https://github.com/tukaani-project/xz-embedded

add_library(${PROJECT_NAME} STATIC ${SRC_LIST})

target_include_directories(${PROJECT_NAME} PUBLIC include)
target_include_directories(${PROJECT_NAME} PRIVATE src)

target_link_libraries(${PROJECT_NAME} PUBLIC dobby lsplant_static log fmt-header-only)
target_link_libraries(${PROJECT_NAME} PRIVATE dex_builder_static)

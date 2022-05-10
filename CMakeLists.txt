set(ROOT_DIR "${CMAKE_CURRENT_SOURCE_DIR}")

set(CMAKE_UNITY_BUILD true)
set(CMAKE_UNITY_BUILD_BATCH_SIZE 16)

include("${ROOT_DIR}/_Sources.cmake")

find_package(Qt6Core    CONFIG REQUIRED)
find_package(Qt6Widgets CONFIG REQUIRED)
find_package(Qt6Gui     CONFIG REQUIRED)

add_library(QHexEdit2 STATIC ${headers} ${sources})

target_link_libraries(QHexEdit2
    Qt6::Core
    Qt6::Widgets
    Qt6::Gui
)

target_include_directories(QHexEdit2 PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/src")

if(MSVC)
  target_compile_options(QHexEdit2 PRIVATE "/MP")
endif()


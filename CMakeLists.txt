cmake_minimum_required(VERSION 3.16)

project(WEXchat VERSION 1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)

# 找 Qt6 或 Qt5
find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Widgets Network)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Widgets Network)

# 收集当前目录下所有 cpp、h、ui、qrc
file(GLOB_RECURSE PROJECT_SOURCES
    "*.cpp"
    "*.h"
    "*.ui"
    "*.qrc"
)

# 生成可执行文件
qt_add_executable(WEXchat
    ${PROJECT_SOURCES}
)

target_link_libraries(WEXchat PRIVATE
    Qt${QT_VERSION_MAJOR}::Widgets
    Qt${QT_VERSION_MAJOR}::Network
)

install(TARGETS WEXchat
    RUNTIME DESTINATION bin
)

cmake_minimum_required(VERSION 3.16)

project(qml-module VERSION 0.1 LANGUAGES CXX)

set(CMAKE_AUTOMOC ON)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt6 6.2 COMPONENTS Quick REQUIRED)

qt_add_executable(appqml-module
    src/cpp/main.cpp
)

add_subdirectory(src/qml)

target_compile_definitions(appqml-module
    PRIVATE $<$<OR:$<CONFIG:Debug>,$<CONFIG:RelWithDebInfo>>:QT_QML_DEBUG>)
target_link_libraries(appqml-module
    PRIVATE Qt6::Quick)

cmake_minimum_required(VERSION 3.10)

project(QLoggerLib LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Core)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Core)

set(SRC_PREFIX "${CMAKE_CURRENT_SOURCE_DIR}/../qloggerlib")

set(HEADERS
    ${SRC_PREFIX}/configuration.h
    ${SRC_PREFIX}/consoleoutput.h
    ${SRC_PREFIX}/jsonoutput.h
    ${SRC_PREFIX}/output.h
    ${SRC_PREFIX}/qlogger.h
    ${SRC_PREFIX}/qloggerlib_global.h
    ${SRC_PREFIX}/signaloutput.h
    ${SRC_PREFIX}/textoutput.h
    ${SRC_PREFIX}/xmloutput.h)

set(SOURCES
    ${SRC_PREFIX}/configuration.cpp
    ${SRC_PREFIX}/consoleoutput.cpp
    ${SRC_PREFIX}/jsonoutput.cpp
    ${SRC_PREFIX}/output.cpp
    ${SRC_PREFIX}/qlogger.cpp
    ${SRC_PREFIX}/signaloutput.cpp
    ${SRC_PREFIX}/textoutput.cpp
    ${SRC_PREFIX}/xmloutput.cpp)

include_directories(${SRC_PREFIX})

add_library(QLoggerLib STATIC ${SOURCES} ${HEADERS})

target_link_libraries(QLoggerLib PRIVATE Qt${QT_VERSION_MAJOR}::Core)

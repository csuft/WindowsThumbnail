CMAKE_MINIMUM_REQUIRED(VERSION 3.6)
PROJECT(WindowsThumbnail CXX)

################################################################################
# Compiler and linker options
ADD_DEFINITIONS(-Wall -DWIN32_LEAN_AND_MEAN -DUNICODE -D_CRT_SECURE_NO_WARNINGS)

SET(CMAKE_AUTOMOC ON)
SET(CMAKE_AUTORCC ON) 
SET(CMAKE_CXX_STANDARD 11) 

################################################################################
# Sources and libraries
FILE(GLOB SOURCE_FILES "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp")
FILE(GLOB HEADER_FILES "${CMAKE_CURRENT_SOURCE_DIR}/src/*.h") 
 
SET(DEFS ${CMAKE_CURRENT_SOURCE_DIR}/src/ExportFunctions.def)   
################################################################################
# Compile target
ADD_LIBRARY(${PROJECT_NAME} SHARED ${SOURCE_FILES} ${HEADER_FILES} ${DEFS}) 
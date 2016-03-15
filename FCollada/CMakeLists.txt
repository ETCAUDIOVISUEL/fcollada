cmake_minimum_required(VERSION 3.0)

project(FCollada)

set(FCollada_SRC 
   DLLEntry.cpp
   FCollada.cpp
   FColladaPlugin.cpp
   StdAfx.cpp
)

set(FCollada_H
	FCollada.h
	FColladaPlugin.h
	StdAfx.h
)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}
                    ${CMAKE_CURRENT_BINARY_DIR}
)

include(FCDocument/FCDocument.cmake)
include(FMath/FMath.cmake)
include(FUtils/FUtils.cmake)
include(LibXML/LibXML.cmake)

add_definitions(-DUNICODE -D_UNICODE)

add_library(FCollada ${FCollada_SRC} ${FCollada_H}
    ${FUtils_SRC} ${FUtils_H}
    ${FMath_SRC} ${FMath_H}
    ${FCDocument_SRC} ${FCDocument_H}
    ${LibXML_SRC} ${LibXML_H}

target_include_directories(FCollada PUBLIC
	$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/LibXML/include>
	$<INSTALL_INTERFACE:include>
    $<INSTALL_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/LibXML/include>
)

set(FCOLLADA_INSTALL_PATH ${CMAKE_INSTALL_PREFIX}/Fcollada)

install(TARGETS FCollada DESTINATION lib)
install(FILES ${FCollada_H} DESTINATION include)
install(DIRECTORY FCDocument FMath FUtils LibXML DESTINATION include
    FILES_MATCHING PATTERN "*.h")

cmake_minimum_required(VERSION 3.0)

project(Fcollada)

set(FCollada_SRC 
   DLLEntry.cpp
   FCollada.cpp
   FCollada.h
   FColladaPlugin.cpp
   FColladaPlugin.h
   StdAfx.cpp
   StdAfx.h
   )

include_directories(${CMAKE_CURRENT_SOURCE_DIR}
                    ${CMAKE_CURRENT_BINARY_DIR}
)

add_subdirectory(FCDocument)
add_subdirectory(FMath)
add_subdirectory(FUtils)
add_subdirectory(LibXML)

add_library(Fcollada ${FCollada_SRC} ${FDocument_SRC} ${FMath_SRC} ${FUtils_SRC})
target_link_libraries(Fcollada ColladaXML)

set(FCOLLADA_INSTALL_PATH ${CMAKE_INSTALL_PREFIX}/Fcollada)

set_target_properties(ColladaXML PROPERTIES RUNTIME_OUTPUT_NAME ColladaXML)
install(TARGETS Fcollada DESTINATION lib)
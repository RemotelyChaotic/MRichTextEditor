cmake_minimum_required(VERSION 3.5)

project(MRichTextEditor CXX)

find_package(Qt5 REQUIRED
    Core
    Widgets)

add_library(${PROJECT_NAME} OBJECT
  ${CMAKE_CURRENT_LIST_DIR}/mrichtextedit.cpp
  ${CMAKE_CURRENT_LIST_DIR}/mtextedit.cpp
  ${CMAKE_CURRENT_LIST_DIR}/mrichtextedit.ui
  )

target_include_directories(${PROJECT_NAME} PUBLIC
    ${CMAKE_CURRENT_LIST_DIR}
    $<TARGET_PROPERTY:Qt5::Core,INTERFACE_INCLUDE_DIRECTORIES>
    $<TARGET_PROPERTY:Qt5::Widgets,INTERFACE_INCLUDE_DIRECTORIES>
)
if (UNIX AND NOT APPLE)
  target_compile_options(${PROJECT_NAME} PUBLIC -fPIC)
endif()

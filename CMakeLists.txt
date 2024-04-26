cmake_minimum_required(VERSION 3.5)

project(lingmo-alpine-fontpack)

set(FONT_PATH "sources/fonts")

file(GLOB FONT_FILES "${FONT_PATH}/*.ttf")

install(FILES ${FONT_FILES} DESTINATION "/usr/share/fonts")
cmake_minimum_required(VERSION 3.5)

project(lingmo-fontpkg)

set(font_list "${CMAKE_CURRENT_SOURCE_DIR}/fontURL.txt")
set(FONT_PATH "${CMAKE_CURRENT_SOURCE_DIR}/sources/fonts")

file(MAKE_DIRECTORY ${download_dir})

file(READ ${font_list} urls)
string(REPLACE "\n" ";" url_list ${urls})
foreach(url IN LISTS url_list)
    if(url)
        string(REGEX MATCH "([^/]+)$" filename ${url})
        message(STATUS "Downloading ${filename} from ${url}")
        file(DOWNLOAD ${url} ${download_dir}/${filename}
            TIMEOUT 60
            TLS_VERIFY ON
        )
    endif()
endforeach()

file(GLOB FONT_FILES "${FONT_PATH}/*.ttf")

install(FILES ${FONT_FILES} DESTINATION "/usr/share/fonts")
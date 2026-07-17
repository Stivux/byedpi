cmake_minimum_required(VERSION 3.16)
project(ciadpi VERSION 0.17.3 LANGUAGES C CXX)


add_executable("${PROJECT_NAME}")
set_target_properties("${PROJECT_NAME}"
        PROPERTIES
        CXX_STANDARD 20
        CXX_STANDARD_REQUIRED ON
        C_STANDARD 99
)

target_sources("${PROJECT_NAME}"
        PRIVATE
        packets.c main.c conev.c proxy.c desync.c mpool.c extend.c
)
if (WIN32)
    target_sources("${PROJECT_NAME}" PRIVATE win_service.c)
    target_link_libraries("${PROJECT_NAME}" ws2_32 mswsock)
endif ()
project(binarix C)
cmake_minimum_required(VERSION 2.8)

set(CMAKE_C_FLAGS "-Wall -Wextra -pedantic ${CMAKE_C_FLAGS}")

add_library(secure secure.c)

add_executable(binarix binarix.c)
target_link_libraries(binarix curses crypt secure)

install(TARGETS binarix
        RUNTIME DESTINATION bin
	PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE SETUID
	            GROUP_READ GROUP_EXECUTE
                    WORLD_READ WORLD_EXECUTE)


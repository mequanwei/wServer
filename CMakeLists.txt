cmake_minimum_required (VERSION 2.8)
project (Server)

include_directories(./)
LINK_DIRECTORIES(/usr/lib64/mysql/)

#modules
add_subdirectory(app)
add_subdirectory(server)
add_subdirectory(sem)
add_subdirectory(db)
add_subdirectory(pool)

set(MODULE_LIST server)
list(APPEND MODULE_LIST db)
list(APPEND MODULE_LIST sem)
list(APPEND MODULE_LIST pool)
list(APPEND MODULE_LIST app)


add_executable(client client/client.cpp)

add_executable(server_app main.cpp)
target_link_libraries(server_app ${MODULE_LIST})










    

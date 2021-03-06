project(libtorrent-examples)
cmake_minimum_required(VERSION 2.6)
# set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_CURRENT_SOURCE_DIR}/cmake/")

# Add extra include and library search directories so examples can optionally
# be built without a prior "make install" of libtorrent.
# list(INSERT CMAKE_INCLUDE_PATH 0 "${CMAKE_CURRENT_SOURCE_DIR}/../include")
# list(INSERT CMAKE_LIBRARY_PATH 0 "${CMAKE_CURRENT_BINARY_DIR}/..")

# Also use the generated pkg-config file prior to "make install".
# In an independent project, these lines would simply not exist.
# set(PKG_CONFIG_CHANGED_PATH "${CMAKE_CURRENT_BINARY_DIR}/..;$ENV{PKG_CONFIG_PATH}")
# if(UNIX)
    # string(REPLACE ";" ":" PKG_CONFIG_CHANGED_PATH "${PKG_CONFIG_CHANGED_PATH}")
# endif ()
# set(ENV{PKG_CONFIG_PATH} "${PKG_CONFIG_CHANGED_PATH}")

# find_package(LibtorrentRasterbar REQUIRED)
# find_package(Boost REQUIRED COMPONENTS system)

# include_directories(${LibtorrentRasterbar_INCLUDE_DIRS} ${Boost_INCLUDE_DIRS})
# add_definitions(${LibtorrentRasterbar_DEFINITIONS})

set(single_file_examples
    cat
    client1
    # client
    # make_torrent
    # connection_tester
    # upnp_test
    )

# foreach(example ${single_file_examples})
#     add_executable(${example} "${example}.cpp")
#     # target_link_libraries(${example} ${LibtorrentRasterbar_LIBRARIES} ${Boost_LIBRARIES})
# endforeach(example)

add_executable(client client.c)
add_executable(cat cat.cpp)
add_executable(client1 client1.cpp)
add_executable(client_test
    client_test.cpp
    print.cpp
    torrent_view.cpp
    session_view.cpp)
target_link_libraries(client_test torrent-rasterbar boost_system)

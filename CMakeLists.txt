cmake_minimum_required (VERSION 2.6)
project (lcurl)

file(GLOB lcurl_sources ./src/**.c)
SET(lcurl ${lcurl_sources})

ADD_LIBRARY (lcurl MODULE ${lcurl})

find_package(Lua REQUIRED)
find_package(CURL CONFIG REQUIRED)

target_include_directories(lcurl PRIVATE ${LUA_INCLUDE_DIR})
target_link_libraries(lcurl PRIVATE CURL::libcurl ${LUA_LIBRARIES})

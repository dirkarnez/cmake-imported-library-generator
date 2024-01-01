cmake-imported-library-generator
================================
### Documentation
- [find_package — CMake 3.28.0 Documentation](https://cmake.org/cmake/help/latest/command/find_package.html)

### Notes
```CMake
#
# LUA
#
IF(USE_LUA_STATIC)
  find_library(LUA_LIBRARIES NAMES liblua5.3.a)
ELSE(USE_LUA_STATIC)
  find_library(LUA_LIBRARIES NAMES liblua5.3.so)
ENDIF(USE_LUA_STATIC)
find_path(LUA_INCLUDE_DIRS NAMES lua5.3/lua.h)
IF(LUA_LIBRARIES AND LUA_INCLUDE_DIRS)
  MESSAGE(STATUS "LUA library found at: ${LUA_LIBRARIES}")
  INCLUDE_DIRECTORIES(${LUA_INCLUDE_DIRS}/lua5.3)
ELSE(LUA_LIBRARIES AND LUA_INCLUDE_DIRS)
  # try using find_package()
  find_package(Lua "5.3" REQUIRED)
  IF(LUA_FOUND)
    MESSAGE(STATUS "LUA library found at  : ${LUA_LIBRARIES}")
    MESSAGE(STATUS "LUA includes found at : ${LUA_INCLUDE_DIR}")
    INCLUDE_DIRECTORIES(${LUA_INCLUDE_DIR}) 
  ELSE(LUA_FOUND)
    MESSAGE(FATAL_ERROR "LUA 5.3 not found! use sudo apt-get install liblua5.3-dev")
  ENDIF(LUA_FOUND)
ENDIF(LUA_LIBRARIES AND LUA_INCLUDE_DIRS)
```

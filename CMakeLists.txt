cmake_minimum_required(VERSION 3.9)
project(cpp_arcade)

set(CMAKE_CXX_STANDARD 14)

include_directories("src/")

# Detect and add SFML
set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake_modules" ${CMAKE_MODULE_PATH})
#Find any version 2.X of SFML
#See the FindSFML.cmake file for additional details and instructions
find_package(SFML 2.4 REQUIRED network audio graphics window system)

find_package(SDL2 REQUIRED)
include_directories(${SDL2_INCLUDE_DIRS})

add_executable(cpp_arcade src/Main.cpp src/Core/Core.hpp
        src/Libraries/ILibrary.hpp src/Core/Core.cpp
        src/ArcadeApplication.cpp src/ArcadeApplication.hpp
        src/Games/IGame.hpp src/LibraryLoader.cpp src/LibraryLoader.hpp
        src/Games/Pacman/Pacman.cpp src/Games/Pacman/AIGhost.cpp
        src/Games/Pacman/AIGhost.hpp src/Core/Color.hpp
        src/Games/Snake/Snake.cpp src/Libraries/SFML.cpp
        src/Libraries/IMusic.hpp
        src/Core/HighScoreManager.cpp src/Core/HighScoreManager.hpp
        src/Libraries/Allegro.cpp src/Libraries/LibCaca.cpp
        src/Libraries/SDL.cpp src/Games/SolarFox/SolarFox.cpp
        src/Games/SolarFox/SolarFox.hpp)

target_link_libraries(cpp_arcade ${SFML_LIBRARIES} ${SFML_DEPENDENCIES})
target_link_libraries(cpp_arcade ${SDL2_LIBRARIES})

target_link_libraries(cpp_arcade ${CMAKE_DL_LIBS})

# Top-level CMakeLists.txt for wrtc-softphone
#
# Copyright 2014 Yegor Mazur <yegor.mazur@gmail.com>
#
# This file is part of Melange.
#
# Melange is free software: you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# Melange is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with Melange.  If not, see <http://www.gnu.org/licenses/>.

cmake_minimum_required (VERSION 2.8)
project (wrtc-softphone)

set(Application_HEADERS
	MainWindow.h
	)

set(Application_SOURCES
	main.cpp
	AudioAdaptor.cpp
	MainWindow.cpp
	)
	
find_package(Qt4 REQUIRED)

INCLUDE(${QT_USE_FILE})

include_directories(
	${PROJECT_SOURCE_DIR}/../../third-party/webrtc/webrtc/voice_engine/include
	${PROJECT_SOURCE_DIR}/../../third-party/webrtc
	)

QT4_WRAP_CPP(Application_HEADERS_MOC ${Application_HEADERS})
	
set(WebrtcBuild_ROOT ${PROJECT_SOURCE_DIR}/../webrtc-build)
add_subdirectory(${WebrtcBuild_ROOT} "${CMAKE_CURRENT_BINARY_DIR}/wrtcbuild")

add_executable(wrtc-softphone ${Application_SOURCES} ${Application_HEADERS_MOC})
target_link_libraries(wrtc-softphone ${QT_LIBRARIES} wrtcbuild rt pthread Xext X11 dl resolv)

add_dependencies(wrtc-softphone wrtcbuild)

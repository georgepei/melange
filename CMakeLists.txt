# Top-level CMakeLists.txt for Melange
#
# Copyright 2014 Fedor Lyakhov <fedor.lyakhov@gmail.com>
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

project(melange) # Use CMAKE_PROJECT_NAME to get this name

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_SOURCE_DIR}/src/cmake)

set(GST_DBUS_STUBS_ROOT ${PROJECT_SOURCE_DIR}/src/gst-dbus-stubs)
set(GST_AUDIOPLAYER_ROOT ${PROJECT_SOURCE_DIR}/src/gst-audioplayer)
set(GST_AUDIOPLAYER_LOCAL_ROOT ${PROJECT_SOURCE_DIR}/src/gst-audioplayer/local)
set(GST_AUDIOPLAYER_REMOTE_ROOT ${PROJECT_SOURCE_DIR}/src/gst-audioplayer/remote)
set(WRTC_SOFTPHONE_ROOT ${PROJECT_SOURCE_DIR}/src/wrtc-softphone)

set(GST_DBUS_STUBS_OUTPUT gst-dbus-stubs)

add_subdirectory(${GST_DBUS_STUBS_ROOT})
add_subdirectory(${GST_AUDIOPLAYER_LOCAL_ROOT})
add_subdirectory(${GST_AUDIOPLAYER_REMOTE_ROOT})
add_subdirectory(${WRTC_SOFTPHONE_ROOT})

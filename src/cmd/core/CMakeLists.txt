# synergy -- mouse and keyboard sharing utility
# Copyright (C) 2017 Symless Ltd.
# 
# This package is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# found in the file LICENSE that should have accompanied this file.
# 
# This package is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

add_executable(synergy-core main.cpp)
target_link_libraries(synergy-core
    arch base client common io mt net ipc platform server core ${libs} ${OPENSSL_LIBS})

if (SYNERGY_CORE_INSTALL)
    if (${CMAKE_SYSTEM_NAME} MATCHES "Darwin")
        install (TARGETS synergy-core DESTINATION ${SYNERGY_BUNDLE_BINARY_DIR})
    elseif (${CMAKE_SYSTEM_NAME} MATCHES "Linux")
        install (TARGETS synergy-core DESTINATION bin)
    endif()
endif()

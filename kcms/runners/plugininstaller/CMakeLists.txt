# SPDX-FileCopyrightText: 2022 Alexander Lohnau <alexander.lohnau@gmx.de>
# SPDX-License-Identifier: BSD-3-Clause

add_executable(krunner-plugininstaller
        main.cpp
        AbstractJob.cpp
        ScriptJob.cpp
        ZypperRPMJob.cpp)
if(HAVE_PACKAGEKIT)
    target_sources(krunner-plugininstaller PUBLIC PackageKitJob.cpp)
endif()

target_link_libraries(krunner-plugininstaller
  KF6::CoreAddons
  KF6::I18n
  Qt::Widgets
  KF6::Service
  KF6::KIOCore
  KF6::KIOWidgets
)
if(HAVE_PACKAGEKIT)
    target_link_libraries(krunner-plugininstaller PK::packagekitqt${QT_MAJOR_VERSION})
endif()

install(TARGETS krunner-plugininstaller DESTINATION ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})

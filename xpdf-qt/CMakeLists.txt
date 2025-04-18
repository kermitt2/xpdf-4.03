#========================================================================
#
# xpdf-qt/cmake-xpdf.txt
#
# CMake script for the xpdf application.
#
# Copyright 2015 Glyph & Cog, LLC
#
#========================================================================

#if ((QT4_FOUND OR Qt5Widgets_FOUND)
#    AND HAVE_SPLASH AND MULTITHREADED AND USE_EXCEPTIONS)
#  include_directories("${PROJECT_SOURCE_DIR}")
#  include_directories("${PROJECT_BINARY_DIR}")
#  include_directories("${PROJECT_SOURCE_DIR}/goo")
#  include_directories("${PROJECT_SOURCE_DIR}/fofi")
#  include_directories("${PROJECT_SOURCE_DIR}/splash")
#  include_directories("${PROJECT_SOURCE_DIR}/xpdf")
#  if (QT4_FOUND)
#    include(${QT_USE_FILE})
#  else ()
#    include_directories(SYSTEM "${QT_INCLUDES}")
#    add_definitions(${QT_DEFINITIONS})
#    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${QT_CFLAGS}")
#  endif ()
#  cmake_policy(SET CMP0020 NEW)
#
#  if (Qt5Widgets_FOUND AND NOT (Qt5Widgets_VERSION VERSION_LESS 5.7.0))
#    set(CMAKE_CXX_STANDARD 11)
#    set(CMAKE_CXX_STANDARD_REQUIRED ON)
#  endif ()
#
#  if (XPDFWIDGET_PRINTING)
#    if (WIN32)
#      if (EXISTS ${PROJECT_SOURCE_DIR}/xpdf/WinPDFPrinter.cc)
#        add_definitions(-DXPDFWIDGET_PRINTING=1)
#        add_definitions(-DXPDFWIDGET_WIN32_PRINTING=1)
#        set(XPDFWIDGET_PRINT_MODULES XpdfWidgetPrint.cc
#                                     ${PROJECT_SOURCE_DIR}/xpdf/GDIOutputDev.cc
#                                     ${PROJECT_SOURCE_DIR}/xpdf/WinPDFPrinter.cc)
#      endif ()
#    else ()
#      add_definitions(-DXPDFWIDGET_PRINTING=1)
#      set(XPDFWIDGET_PRINT_MODULES XpdfWidgetPrint.cc)
#    endif ()
#  else ()
#    set(XPDFWIDGET_PRINT_MODULES "")
#  endif ()
#
#  if (QT4_FOUND)
#    qt4_wrap_cpp(XPDFWIDGET_MOC XpdfWidget.h)
#    qt4_wrap_cpp(XPDFVIEWER_MOC XpdfViewer.h)
#    qt4_wrap_cpp(XPDFAPP_MOC XpdfApp.h)
#    qt4_add_resources(XPDF_ICONS icons.qrc)
#  else ()
#    qt5_wrap_cpp(XPDFWIDGET_MOC XpdfWidget.h)
#    qt5_wrap_cpp(XPDFVIEWER_MOC XpdfViewer.h)
#    qt5_wrap_cpp(XPDFAPP_MOC XpdfApp.h)
#    qt5_add_resources(XPDF_ICONS icons.qrc)
#  endif ()
#
#  # workaround for a conflict between the Qt5 QDateTime and windows.h
#  if (WIN32)
#    add_definitions(-DNOMINMAX)
#  endif ()
#
#  add_executable(xpdf
#    $<TARGET_OBJECTS:goo_objs>
#    $<TARGET_OBJECTS:fofi_objs>
#    $<TARGET_OBJECTS:splash_objs>
#    $<TARGET_OBJECTS:xpdf_objs>
#    $<TARGET_OBJECTS:xpdf_widget_objs>
#    ${XPDFWIDGET_PRINT_MODULES}
#    QtPDFCore.cc
#    XpdfApp.cc
#    XpdfViewer.cc
#    XpdfWidget.cc
#    xpdf.cc
#    xpdf.rc
#    ${XPDFAPP_MOC}
#    ${XPDFVIEWER_MOC}
#    ${XPDFWIDGET_MOC}
#    ${XPDF_ICONS}
#  )
#  target_link_libraries(xpdf ${QT_LIBRARIES} ${EXTRA_QT_LIBRARIES}
#                        ${PAPER_LIBRARY}
#                        ${FREETYPE_LIBRARY} ${FREETYPE_OTHER_LIBS}
#                        ${DTYPE_LIBRARY}
#                        ${LCMS_LIBRARY}
#                        ${FONTCONFIG_LIBRARY}
#                        ${CMAKE_THREAD_LIBS_INIT})
#  set_property(TARGET xpdf PROPERTY WIN32_EXECUTABLE 1)
#  if (QT4_FOUND)
#    set_property(TARGET xpdf PROPERTY QT4_NO_LINK_QTMAIN ON)
#  else ()
#    set_property(TARGET xpdf PROPERTY Qt5_NO_LINK_QTMAIN ON)
#  endif ()
#
#  install(TARGETS xpdf RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})
#  install(FILES ${PROJECT_SOURCE_DIR}/doc/xpdf.1 DESTINATION ${CMAKE_INSTALL_MANDIR}/man1)
#endif ()

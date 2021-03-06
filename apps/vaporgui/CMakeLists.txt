set (SRCS
	EventRouter.cpp
	RenderEventRouter.cpp
	RenderHolder.cpp
	ImageFrame.cpp
	ControlPointEditor.cpp
	DomainWidget.cpp
	GLWidget.cpp
	OpacityWidget.cpp
	ErrorReporter.cpp
	Histo.cpp
	ColorbarWidget.cpp
	SettingsEventRouter.cpp
	VizSelectCombo.cpp
	AnnotationEventRouter.cpp
	AnimationEventRouter.cpp
	MappingFrame.cpp
	HelloEventRouter.cpp
	NavigationEventRouter.cpp
	TwoDDataEventRouter.cpp
	WireFrameEventRouter.cpp
	RangeController.cpp
    PythonVariables.cpp
	Statistics.cpp
	Plot.cpp
	helloSubtabs.cpp
	TFWidget.cpp
	VariablesWidget.cpp
	GeometryWidget.cpp
	CopyRegionWidget.cpp
	RangeCombos.cpp
	BarbEventRouter.cpp
	BannerGUI.cpp
	AnimationParams.cpp
	GUIStateParams.cpp
	MouseModeParams.cpp
	SettingsParams.cpp
	main.cpp
	MainForm.cpp
	VizWin.cpp
	VizWinMgr.cpp
	TabManager.cpp
	TrackBall.cpp
	GLColorbarWidget.cpp
	ImageEventRouter.cpp
	ContourEventRouter.cpp
    SliceEventRouter.cpp
	DVREventRouter.cpp
	IsoSurfaceEventRouter.cpp
	IsoSurfaceSubtabs.cpp
	PlotParams.cpp
	StatisticsParams.cpp
	ContourSubtabs.cpp
    SliceSubtabs.cpp
	BarbSubtabs.cpp
	TransformTable.cpp
	VaporTable.cpp
	FidelityWidget.cpp
	QSliderEdit.cpp
	QRange.cpp
	QSinglePoint.cpp
	QIntValidatorWithFixup.cpp
	FileOperationChecker.cpp
	Combo.cpp
	windowsUtils.cpp
	Manip.cpp

	# Need to include all files that request .ui files
	TwoDSubtabs.h
	DVRSubtabs.h
	IsoSurfaceSubtabs.h
	WireFrameSubtabs.h
	Statistics.h
	Plot.h
    PythonVariables.h
	BarbSubtabs.h
	ColorbarWidget.h
	OrientationAngles.h
	TransformTable.h
	ImageSubtabs.h
	ContourSubtabs.h
    SliceSubtabs.h
	VaporTable.h
	FidelityWidget.h
	QSliderEdit.h
	QRange.h
	QSinglePoint.h

	MainForm.h
	VizWinMgr.h
	windowsUtils.h
	ErrorReporter.h
	Histo.h
	EventRouter.h
	GLWidget.h
	VizWin.h
	Core3_2_context.h
	TrackBall.h
	Manip.h
	NavigationEventRouter.h
	AnimationEventRouter.h
	AnimationParams.h
	AnnotationEventRouter.h
	BannerGUI.h
	BarbEventRouter.h
	BarbEventRouter.h
	Combo.h
	ContourEventRouter.h
	ControlPointEditor.h
	CopyRegionWidget.h
	DomainWidget.h
	FileOperationChecker.h
	GLColorbarWidget.h
	GUIStateParams.h
	GeometryWidget.h
	ImageEventRouter.h
	ImageEventRouter.h
	ImageFrame.h
	ImageFrame.h
	IsoSurfaceEventRouter.h
	MappingFrame.h
	MouseModeParams.h
	PlotParams.h
    PythonVariablesParams.h
	QIntValidatorWithFixup.h
	RangeCombos.h
	RangeController.h
	RenderEventRouter.h
	RenderHolder.h
	SettingsEventRouter.h
	SettingsParams.h
	StatisticsParams.h
	TFWidget.h
	TabManager.h
	VariablesWidget.h
	VizSelectCombo.h
	WireFrameEventRouter.h
)

set (UIS 
	LeftPanel.ui
	animationTab.ui
	NavigationTab.ui
	boxframe.ui
	startupTab.ui
	AnnotationGUI.ui
	SettingsGUI.ui
	appSettingsTab.ui
	NewRendererDialog.ui
	errMsg.ui
	DVRVariablesGUI.ui
	DVRAppearanceGUI.ui
	DVRGeometryGUI.ui
	DVRAnnotationGUI.ui
	IsoSurfaceVariablesGUI.ui
	IsoSurfaceAppearanceGUI.ui
	IsoSurfaceGeometryGUI.ui
	IsoSurfaceAnnotationGUI.ui
	helloLayoutSubtab.ui
	helloAppearanceSubtab.ui
	BarbAppearanceGUI.ui
	BarbVariablesGUI.ui
	BarbGeometryGUI.ui
	BarbAnnotationGUI.ui
	ImageAppearanceGUI.ui
	ImageGeometryGUI.ui
	ImageVariablesGUI.ui
	TwoDVariablesGUI.ui
	TwoDAppearanceGUI.ui
	TwoDGeometryGUI.ui
	TwoDAnnotationGUI.ui
	ContourVariablesGUI.ui
	ContourAppearanceGUI.ui
	ContourGeometryGUI.ui
	ContourAnnotationGUI.ui
	WireFrameVariablesGUI.ui
	WireFrameAppearanceGUI.ui
	WireFrameGeometryGUI.ui
	WireFrameAnnotationGUI.ui
    SliceVariablesGUI.ui
    SliceAppearanceGUI.ui
    SliceGeometryGUI.ui
    SliceAnnotationGUI.ui
	VariablesWidgetGUI.ui
	statsWindow.ui
	plotWindow.ui
	firstTimeUser.ui
    PythonVariablesGUI.ui
	TFWidgetGUI.ui
	GeometryWidgetGUI.ui
	ColorbarWidgetGUI.ui
	FidelityWidgetGUI.ui
	ControlPointEditorBase.ui
	StretchFactorTableGUI.ui
	OrientationAnglesGUI.ui
	CopyRegionWidgetGUI.ui
	
	QSliderEdit.ui
	QRange.ui
	QSinglePoint.ui
)

source_group (UIs FILES ${UIS})

find_package(Qt4 REQUIRED)
set (CMAKE_AUTOUIC ON) # This needs to appear before adding sources to work properly
set (CMAKE_AUTOMOC ON)
set (CMAKE_AUTORCC ON)
set (CMAKE_INCLUDE_CURRENT_DIR ON)

if (APPLE)
	set (SRCS ${SRCS} core_profile_attributes.mm)
	set (MACOSX_BUNDLE_ICON_FILE VAPOR.icns)
	set (MACOSX_BUNDLE_ICON_FILE_PATH ${CMAKE_SOURCE_DIR}/share/images/VAPOR.icns)
	set_source_files_properties(${MACOSX_BUNDLE_ICON_FILE_PATH} PROPERTIES MACOSX_PACKAGE_LOCATION "Resources")
	add_executable (vapor MACOSX_BUNDLE ${MACOSX_BUNDLE_ICON_FILE_PATH} ${SRCS} ${UIS})
	set (INSTALL_BIN_DIR ".")
elseif (WIN32)
	set (WINDOWS_ICON_PATH "${CMAKE_SOURCE_DIR}/share/images/vapor-win-icon.ico")
	configure_file (vapor.rc.in ${CMAKE_CURRENT_BINARY_DIR}/vaporgui.rc)
	add_executable (vapor WIN32 ${SRCS} ${UIS} ${CMAKE_CURRENT_BINARY_DIR}/vaporgui.rc)
else ()
	add_executable (vapor ${SRCS} ${UIS})
endif()

# target_link_libraries (vapor common vdc wasp render params m jpeg dl util GLEW tiff geotiff assimp Qt4::QtCore Qt4::QtGui Qt4::QtOpenGL)
target_link_libraries (vapor common vdc wasp render params jpeg ${GLEW} tiff geotiff assimp Qt4::QtCore Qt4::QtGui Qt4::QtOpenGL python${PYTHONVERSION})

if (APPLE)
	find_library (CORESERVICES CoreServices)
	find_library (FOUNDATION Foundation)
	find_library (COCOA Cocoa)
	# target_link_libraries (vapor "-framework CoreServices")
	target_link_libraries (vapor ${CORESERVICES} ${FOUNDATION} ${COCOA})
elseif (UNIX AND NOT APPLE)
	target_link_libraries (vapor quadmath)
endif ()

install (
	TARGETS vapor
	DESTINATION ${INSTALL_BIN_DIR}
	COMPONENT vaporgui
	)


ADD_LIBRARY ( PyIex ${LIB_TYPE}
	PyIex.cpp
)

TARGET_LINK_LIBRARIES ( PyIex
	${PYTHON_LIBRARIES}
	Iex${ILMBASE_LIBSUFFIX}
	${Boost_LIBRARIES}
)

INSTALL ( TARGETS PyIex
	DESTINATION ${LIB_INSTALL_DIR}
)

ADD_LIBRARY ( iexmodule ${LIB_TYPE}
	iexmodule.cpp
)

SET_TARGET_PROPERTIES ( iexmodule
	PROPERTIES PREFIX "" SUFFIX ${PYTHON_CEXTENSION} BUILD_WITH_INSTALL_RPATH ON
)

TARGET_LINK_LIBRARIES ( iexmodule
	PyIex
	Iex${ILMBASE_LIBSUFFIX}
	${Boost_LIBRARIES}
)

INSTALL ( TARGETS iexmodule
	DESTINATION ${PYTHON_INSTALL_DIR}
)


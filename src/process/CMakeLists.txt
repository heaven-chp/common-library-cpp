set(BUILD_TARGET "process")
set(ALIAS_NAME "lib::${BUILD_TARGET}")
set(TEST_BUILD_TARGET ${BUILD_TARGET}${POSTFIX_TEST_NAME})

set(HEADER
		Signal.h
		Process.h
		ChildProcess.h
		ParentProcess.h
		EnvironmentVariable.h
	)

set(SOURCE
		Signal.cpp
		Process.cpp
		ChildProcess.cpp
		ParentProcess.cpp
		EnvironmentVariable.cpp
	)

set(SOURCE_TEST
		test/main.cpp
		test/SignalTest.cpp
		test/ChildProcessTest.cpp
		test/ParentProcessTest.cpp
		test/EnvironmentVariableTest.cpp
	)

set(DEPENDENCIES
		lib::config
		lib::file
	)

set(CONFIGURE_FILE_TEST
		"test/test.h.in"
	)

func_build_library(${ALIAS_NAME} ${BUILD_TARGET} "${HEADER}" "${SOURCE}" "${DEPENDENCIES}")

func_build_unit_test(${TEST_BUILD_TARGET} "${SOURCE_TEST}" "${SOURCE}" "${DEPENDENCIES}" "${CONFIGURE_FILE_TEST}")

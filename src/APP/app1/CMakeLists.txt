#默认使用目录名作为项目名
GET_DIR_NAME(DIRNAME)

set(TARGET_NAME "${TARGET_PREFIX}${DIRNAME}")

#多个源文件用 [空格] 分隔
#如：set(STR_TARGET_SOURCES "main.cpp src_2.cpp")
file(GLOB ALL_SOURCES
	"${CMAKE_CURRENT_SOURCE_DIR}/*.cpp"
	"${CMAKE_CURRENT_SOURCE_DIR}/*.h"
	"${CMAKE_CURRENT_SOURCE_DIR}/*.fs"
)

set(STR_TARGET_SOURCES "")
foreach(SOURCE ${ALL_SOURCES})
	set(STR_TARGET_SOURCES "${STR_TARGET_SOURCES} ${SOURCE}")
endforeach(SOURCE ${ALL_SOURCES})

#set(STR_TARGET_SOURCES "${STR_TARGET_SOURCES} ${CMAKE_SOURCE_DIR}/config/config.in")
#set(STR_TARGET_SOURCES "${STR_TARGET_SOURCES} ${CMAKE_SOURCE_DIR}/include/CppUtil/OpenGL/CommonDefine.h")
#set(STR_TARGET_SOURCES "${STR_TARGET_SOURCES} ${CMAKE_SOURCE_DIR}/data/shaders/Common/basic_P2T2.vs")

#set(STR_TARGET_SOURCES "${DIRNAME}.cpp ${DIRNAME}.fs ${DIRNAME}.vs")
#多个库文件用 [空格] 分隔，如果为空，就输入[一个空格]
#如：set(STR_TARGET_LIBS "lib1.lib lib2.lib")
# 下面是寻找自己创建的那些库的，就是那些工具类创建的比如OpenGL
set(STR_TARGET_LIBS "OpenGL")

SETUP_PROJECT(${MODE} ${TARGET_NAME} ${STR_TARGET_SOURCES} ${STR_TARGET_LIBS})

INSTALL_SHADERS()

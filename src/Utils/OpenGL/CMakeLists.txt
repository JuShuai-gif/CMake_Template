#项目名，默认为目录名
GET_DIR_NAME(DIRNAME)
set(TARGET_NAME ${DIRNAME})
message("当前目录名： ${DIRNAME}")
#多个源文件用 [空格] 分隔
#如：set(STR_TARGET_SOURCES "main.cpp src_2.cpp")
file(GLOB ALL_SOURCES
	"${CMAKE_CURRENT_SOURCE_DIR}/*.cpp"
    "${CMAKE_SOURCE_DIR}/include/OpenGL/*.h"
)
set(STR_TARGET_SOURCES "")

foreach(SOURCE ${ALL_SOURCES})
	set(STR_TARGET_SOURCES "${STR_TARGET_SOURCES} ${SOURCE}")
endforeach(SOURCE ${ALL_SOURCES})

#set(STR_TARGET_SOURCES "${STR_TARGET_SOURCES} ${CMAKE_SOURCE_DIR}/include/CppUtil/OpenGL/Camera.h")

# 最后别忘了添加 glad.c 文件
set(STR_TARGET_SOURCES "${STR_TARGET_SOURCES} glad.c")

#多个库文件用 [空格] 分隔，如果为空，就输入[一个空格]
#如：set(STR_TARGET_LIBS "lib1.lib lib2.lib")
set(STR_TARGET_LIBS "libglfw3.a")

# 参数含义
# MODE 目标类型
# TARGET_NAME 目标名称
# STR_TARGET_SOURCES 目标源文件列表（多个文件以空格分隔）
# STR_TARGET_LIBS表示目标链接库列表
SETUP_PROJECT(${MODE} ${TARGET_NAME} ${STR_TARGET_SOURCES} ${STR_TARGET_LIBS})


# 因为这里可以当作库来看待，所以设置生成模式为lib
set(MODE "LIB")

GET_DIR_NAME(DIRNAME)

# 设置FOLDER_NAME为当前目录名
set(FOLDER_NAME ${DIRNAME})


ADD_ALL_SUBDIR()

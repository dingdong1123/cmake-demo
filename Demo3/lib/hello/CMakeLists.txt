# 查找当前目录下的所有源文件
# 并将名称保存到 DIR_LIB_SRCS 变量
cmake_minimum_required(VERSION 3.6)
project(hello)

aux_source_directory(. DIR_LIB_SRCS)

# 指定生成 Hello 链接库
add_library (${PROJECT_NAME} OBJECT ${DIR_LIB_SRCS})

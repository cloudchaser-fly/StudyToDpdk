# 定义工具链和编译选项
CC = gcc
CFLAGS = -Wall 
INCLUDES = -I./include 
#LDLIBS = -L./lib -lXDK

CFLAGS += $(INCLUDES)

# 定义目录
SRC_DIR := src
INC_DIR := include
LIB_DIR := lib
BIN_DIR := bin
OBJ_DIR := obj

# 自动获取所有源文件和对象文件路径
SOURCES := $(wildcard $(SRC_DIR)/*.c)
OBJECTS := $(patsubst $(SRC_DIR)/%.c, $(OBJ_DIR)/%.o, $(SOURCES))
#OBJECTS := $(SOURCES:$(SRC_DIR)/%.c=$(OBJ_DIR)/%.o)

# 最终目标
TARGET := $(BIN_DIR)/app

# 默认目标，构建二进制文件
all:$(TARGET)

# 连接：从.o生成可执行文件
$(TARGET):$(OBJECTS)
	@mkdir -p $(BIN_DIR)
	$(CC) -o $@ $^ $(CFLAGS)

# 编译：从.c文件生成.o文件
$(OBJ_DIR)/%.o:$(SRC_DIR)/%.c
	@mkdir -p $(OBJ_DIR)
	$(CC) -o $@ -c $< $(CFLAGS) -MMD -MP
#	$(CC) -o $@ -c $^ $(CFLAGS) 

# 包含自动生成的依赖文件(如.d文件)
-include $(OBJECTS:.o=.d)

# 清理生成的文件
clean:
	rm -fr $(OBJ_DIR) $(BIN_DIR)

help:
	@echo "Usage:"
	@echo "make			:编译项目"
	@echo "make clean	:清除所有生成的文件"
	@echo "make help	:帮助信息"

.PHONY: all clean help

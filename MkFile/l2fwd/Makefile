# 1.定义工具链和编译选项
GCC = gcc
PWD = $(shell pwd)

PKGCONF = pkg-config
CFLAGS += -Wall -O3 $(shell $(PKGCONF) --cflags libdpdk)
LDFLAGS += $(shell $(PKGCONF) --libs libdpdk)



# 2.定义目录
SRC_DIR := $(PWD)
INC_DIR := include
LIB_DIR := lib
BIN_DIR := bin
OBJ_DIR := obj

# 3.自动获取所有源文件和对象文件路径
SOURCES := $(wildcard $(SRC_DIR)/*.c)
OBJECTS := $(patsubst $(SRC_DIR)/%.c, $(OBJ_DIR)/%.o, $(SOURCES))

# 4.最终目标
TARGET := $(BIN_DIR)/app

# 默认目标，生存二进制文件
all:$(TARGET)

$(TARGET):$(OBJECTS)
	@mkdir -p $(BIN_DIR)
	$(GCC) -o $@ $^ $(LDFLAGS) $(CFLAGS)

#$(OBJ_DIR)/%.o:$(SRC_DIR)/%.c
$(OBJECTS):$(SOURCES)
	@mkdir -p $(OBJ_DIR)
	$(GCC) -o $@ -c $^ $(LDFLAGS) $(CFLAGS) 
	

# CFLAGS += -MMD -MP
# -include $(OBJECTS:.o=.d)

clean:
	rm -fr $(OBJ_DIR) $(BIN_DIR)

.PHONY: all clean

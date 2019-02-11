CC          := g++
CXXFLAGS    := -g -Wall
INCLUDE_DIR := -I../../src -I../../../inc/boost -I../../../inc/rabbitmq-c
SRC_DIR     := ../../src
OBJS        :=  $(notdir $(patsubst %.cpp,%.o,$(wildcard $(SRC_DIR)/*.cpp)))

LIB_DIR     := -L../../../../lib
LIB_BOOST   := -lboost_system -lboost_filesystem -lboost_chrono
LIB_AMQPC   := -lrabbitmq 
LIBS        := $(LIB_DIR) $(LIB_BOOST) $(LIB_AMQPC)

TARGET      := libSimpleAmqpClient.so

$(TARGET):$(OBJS)
	$(CC) -shared -o $(TARGET) $(OBJS) $(LIBS)

%.o : $(SRC_DIR)/%.cpp
	$(CC) $(CXXFLAGS) -fPIC -c -std=c++11 -DBOOST_ALL_DYN_LINK $(INCLUDE_DIR) $<
	
.PHONY:install
install:
	mv $(TARGET) ../../../../lib

.PHONY:clean
clean:
	rm -f $(OBJS) $(TARGET)
	
.PHONY:cleanobj
cleanobj:
	rm -f $(OBJS)

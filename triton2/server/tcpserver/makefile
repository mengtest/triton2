#################################################################
#	makefile for tcpserver
#################################################################

# include common makefile
COMM_DIR = ../servercommon/
COMM_OBJS = $(COMM_DIR)/src/*.o
CS_COMMON_DIR = ../../common/comm
CS_COMMON_OBJS = $(CS_COMMON_DIR)/*.o

# if the application need little file in comm, you can appoint .o here, such as

## !!!C_ARGS alse decides what the comm work!!!
## see the comm makefile
## 3 options for chose: SMALL_SIZE/MEDIUM_SIZE/LARGE_SIZE
C_ARGS:= -g  -D_DEBUG_  -DUSE_LOG4CPP -DENCODING_UTF8 -DMEDIUM_SIZE

##!!!CPP need export to comm!!!
##You might have to change this if your c++ compiler is not g++
export CPP:= g++

##generate object file
BINARY= ./bin/tcpsvrd

##tcpserver file path
TCPSVR_DIR = .
TCPSVR_INC = $(TCPSVR_DIR)/inc
TCPSVR_SRC = $(TCPSVR_DIR)/src
INCLUDE = -I$(COMM_DIR)/inc -I$(TCPSVR_INC) -I../../common/log4cpp/include -I../../common/comm
LIBS = -lpthread -L../../common/log4cpp/lib -llog4cpp
##source file .o
TCPSVR_OBJS = $(TCPSVR_SRC)/tcpctrl.o $(TCPSVR_SRC)/tcpsvrd.o $(CS_COMMON_DIR)/oi_tea.o $(COMM_DIR)/src/shm.o \
		$(COMM_DIR)/src/object.o  $(COMM_DIR)/src/charset.o \
		$(COMM_DIR)/src/base.o $(COMM_DIR)/src/config.o $(COMM_DIR)/src/log.o $(COMM_DIR)/src/code_queue.o



# You shouldn't need to make any more changes below this line.

all:$(BINARY)


$(BINARY): $(TCPSVR_OBJS) 
	rm -f $@
	$(CPP) $(C_ARGS) -o $@ $(TCPSVR_OBJS)  $(LIBS)

	
#common_obj:
#	( cd $(COMM_DIR); make -f makefile; )

.cpp.o:
	$(CPP) $(C_ARGS) $(INCLUDE) -o $@ -c $<

.c.o:
	$(CPP) $(C_ARGS) $(INCLUDE) -o $@ -c $<

.C.o:
	$(CPP) $(C_ARGS) $(INCLUDE) -o $@ -c $<
	
install:all
	cp $(BINARY) $(TRITON_BIN)
	
clean:
	rm -f $(TCPSVR_OBJS) $(BINARY) 



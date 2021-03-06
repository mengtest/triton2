
####### Compiler, tools and options
COMMONPATH	= ../../common# common file include path
CC		= gcc
CXX		= g++
LEX		= flex
YACC     	= yacc
CFLAGS   	= -g 
CXXFLAGS 	= -g -Wall -DLINUX -DWEST_SERVER -DENCODING_UTF8  -DOTHERSERVER -DUSE_LOG4CPP -DUSING_ERATING -D_DEBUG_ -D_GMDEBUG_ -DNDEBUG -D_USE_MESSAGE_BUFF_ -DUSE_LK_ASSERT #-D_TESTENV_ #-DYUENAN -D_TESTENV_#-D_ECHARGE_DEBUG_ #-DUSE_DECRYPTION_PROTOCAL
LEXFLAGS 	= 
YACCFLAGS	= -d
MYSQL_HOME = /usr/local/
INCPATH  	= -I./erating/EProtocol2/include -I./erating/EBase -I./erating/EAlgorithm -I./inc -I./$(COMMONPATH)/tiny -I./$(COMMONPATH)/comm -I./$(COMMONPATH)/comm/linux -I./$(COMMONPATH)/inc -I../servercommon/inc -I./$(COMMONPATH)/interface  -I./$(COMMONPATH)/protobuf/include  -I./$(COMMONPATH)/log4cpp/include -I./gm -I./$(COMMONPATH)/coredumper/include 

LINK     	= g++
LFLAGS   	= 
LIBS     	= -L../dataserver/lib/ -L./$(COMMONPATH)/protobuf/lib -lpthread -lprotobuf -L./$(COMMONPATH)/log4cpp/lib -llog4cpp -L./lib -lEProtocol2 -lEAlgorithm -lEBase -L./$(COMMONPATH)/coredumper/lib -lcoredumper #-static -lz
DEL_FILE 	= rm -f

PCH_X_H = inc/stdafx.hpp
PCH_X = inc/stdafx.hpp.gch

####### Files
MSG_OBJ = #../comm/msg ../comm/encoder ../src/coremessage

OBJECTS	= 	./debug/main.o ./debug/loginlogic.o ./debug/loginobj_manager.o \
			./debug/loginobj_manager_imp.o ./debug/message_dispatcher.o ./debug/clienthandle.o	\
			./debug/log.o ./debug/servertool.o ./debug/shm.o ./debug/code_queue.o \
			./debug/tinyxml.o ./debug/tinystr.o ./debug/tinyxmlerror.o ./debug/tinyxmlparser.o \
			./debug/coremessage_pb.hxx.pb.o ./debug/message_pb.hxx.pb.o ./debug/proxymessage_pb.hxx.pb.o \
			./debug/servermessage_pb.hxx.pb.o ./debug/log_msg_pb.hxx.pb.o \
			./debug/message_factory.o ./debug/servermessage_in.o ./debug/mailmessage_pb.hxx.pb.o \
			./debug/client_comm_engine.o ./debug/base.o ./debug/message_queue.o ./debug/sharemem.o \
			./debug/object.o ./debug/db_msg_pb.hxx.pb.o ./debug/oi_tea.o ./debug/gmmessage_pb.hxx.pb.o \
			./debug/gm_command.o debug/gm_service.o ./debug/property_pb.hxx.pb.o \
			./debug/template.o ./debug/charge_service.o ./debug/template_pb.hxx.pb.o ./debug/ibstore_pb.hxx.pb.o \
			./debug/rankmessage_pb.hxx.pb.o ./debug/charset.o ./debug/countrymessage_pb.hxx.pb.o \
			./debug/corpsinfo_pb.hxx.pb.o ./debug/familydbinfo_pb.hxx.pb.o ./debug/boursemessage_pb.hxx.pb.o \
			./debug/globalserver_pb.hxx.pb.o

MSG_OBJECTS = $(foreach OBJECT, $(MSG_OBJ), ../../common/src/$(OBJECT).o )
MSG_SRC	= $(foreach OBJECT, $(MSG_OBJ), ../../common/src/$(OBJECT).cpp )

TARGET          = ./bin/loginserver

first: all
####### Compile

./debug/boursemessage_pb.hxx.pb.o : $(COMMONPATH)/inc/boursemessage_pb.hxx.pb.cc
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/tinyxml.o : $(COMMONPATH)/tiny/tinyxml.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/tinystr.o : $(COMMONPATH)/tiny/tinystr.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/tinyxmlerror.o : $(COMMONPATH)/tiny/tinyxmlerror.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/tinyxmlparser.o : $(COMMONPATH)/tiny/tinyxmlparser.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<
	
./debug/loginlogic.o : src/loginlogic.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/main.o : src/main.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/template.o : $(COMMONPATH)/src/template.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/loginobj_manager.o : src/loginobj_manager.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/loginobj_manager_imp.o : src/loginobj_manager_imp.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/message_dispatcher.o : src/message_dispatcher.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/message_queue.o : src/message_queue.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/clienthandle.o : src/clienthandle.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/servertool.o : ../servercommon/src/servertool.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/message_pb.hxx.pb.o : $(COMMONPATH)/inc/message_pb.hxx.pb.cc
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/coremessage_pb.hxx.pb.o : $(COMMONPATH)/inc/coremessage_pb.hxx.pb.cc
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/log_msg_pb.hxx.pb.o : ../servercommon/inc/log_msg_pb.hxx.pb.cc
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/message_factory.o : $(COMMONPATH)/src/message_factory.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/proxymessage_pb.hxx.pb.o : ../servercommon/inc/proxymessage_pb.hxx.pb.cc
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/servermessage_pb.hxx.pb.o : ../servercommon/inc/servermessage_pb.hxx.pb.cc
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/client_comm_engine.o : $(COMMONPATH)/comm/client_comm_engine.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/log.o : ../servercommon/src/log.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/servermessage_in.o : ../servercommon/src/servermessage_in.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/shm.o : ../servercommon/src/shm.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/code_queue.o : ../servercommon/src/code_queue.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/base.o : ../servercommon/src/base.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/sharemem.o : ../servercommon/src/sharemem.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/object.o : ../servercommon/src/object.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/db_msg_pb.hxx.pb.o : ../servercommon/inc/db_msg_pb.hxx.pb.cc
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/property_pb.hxx.pb.o : $(COMMONPATH)/inc/property_pb.hxx.pb.cc
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<
	
./debug/countrymessage_pb.hxx.pb.o : $(COMMONPATH)/inc/countrymessage_pb.hxx.pb.cc
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/corpsinfo_pb.hxx.pb.o : $(COMMONPATH)/inc/corpsinfo_pb.hxx.pb.cc
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<
	
./debug/familydbinfo_pb.hxx.pb.o : $(COMMONPATH)/inc/familydbinfo_pb.hxx.pb.cc
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/oi_tea.o :  $(COMMONPATH)/comm/oi_tea.cpp
	$(CXX) -c -DWEST_SERVER $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/gm_command.o : gm/gm_command.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/gm_service.o : gm/gm_service.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/charge_service.o : gm/charge_service.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/gmmessage_pb.hxx.pb.o : ../servercommon/inc/gmmessage_pb.hxx.pb.cc
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/template_pb.hxx.pb.o : $(COMMONPATH)/inc/template_pb.hxx.pb.cc
	$(CXX) -c -DWEST_SERVER $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/ibstore_pb.hxx.pb.o : $(COMMONPATH)/inc/ibstore_pb.hxx.pb.cc
	$(CXX) -c -DWEST_SERVER $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/rankmessage_pb.hxx.pb.o : $(COMMONPATH)/inc/rankmessage_pb.hxx.pb.cc
	$(CXX) -c -DWEST_SERVER $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/charset.o : ../servercommon/src/charset.c
	$(CXX) -c -DWEST_SERVER $(CXXFLAGS) $(INCPATH) -o $@ $<

./debug/mailmessage_pb.hxx.pb.o : $(COMMONPATH)/inc/mailmessage_pb.hxx.pb.cc
	$(CXX) -c $(CXXFLAGS_3RD)  $(INCPATH) -o $@ $<

./debug/globalserver_pb.hxx.pb.o : ../servercommon/inc/globalserver_pb.hxx.pb.cc
	 $(CXX) -c $(CXXFLAGS_3RD)  $(INCPATH) -o $@ $<

####### Build rules
.cpp.o:; $(CXX) -c -DLINUX -DWEST_SERVER $(CXXFLAGS) $(INCPATH)  $< -o $@
.cc.o:; $(CXX) -c -DLINUX -DWEST_SERVER $(CXXFLAGS) $(INCPATH)  $< -o $@
.c.o:; $(CXX) -c -DLINUX -DWEST_SERVER $(CXXFLAGS) $(INCPATH)  $< -o $@

all: $(TARGET)

$(TARGET): $(OBJECTS) $(MSG_OBJECTS)
	$(LINK) $(LFLAGS) -o $(TARGET) $(OBJECTS) $(MSG_OBJECTS) $(LIBS)

$(OBJECTS): $(PCH_X)

$(MSG_OBJECTS): $(PCH_X)


$(PCH_X): $(PCH_X_H)
	$(CXX) $(CXXFLAGS) $(INCPATH) -x c++-header $> $^

clean:
	-$(DEL_FILE) $(OBJECTS) 
	-$(DEL_FILE) *~ core *.core
	rm -f $(TARGET) $(PCH_X)

install: all
	-cp $(TARGET) $(TRITON_BIN)







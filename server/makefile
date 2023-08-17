
CC=g++

CODEC_PATH=codec
LOG_PATH=log
SHM_PATH=shm
TCP_PATH=tcp
SERVEROP_PATH=serverOP
ORACLEOP_PATH=oracleOP

CPPLFAGS=-I $(CODEC_PATH)/include					\
		 -I $(LOG_PATH)/include		\
		 -I $(SHM_PATH)/include	\
		 -I $(TCP_PATH)/include  \
		 -I $(SERVEROP_PATH)/include	\
		 -I $(ORACLEOP_PATH)/include
		 


target=serMain
LIBS=-lstdc++ \
		-lssl \
		-lcrypto \
		-locci \
		-lclntsh \
		-lpthread
$(target):$(CODEC_PATH)/src/BaseASN1.o	\
		$(CODEC_PATH)/src/Codec.o	\
		$(CODEC_PATH)/src/CodecFactory.o	\
		$(CODEC_PATH)/src/RequestCodec.o	\
		$(CODEC_PATH)/src/RequestFactory.o	\
		$(CODEC_PATH)/src/RespondCodec.o	\
		$(CODEC_PATH)/src/RespondFactory.o	\
		$(CODEC_PATH)/src/SequenceASN1.o	\
		$(LOG_PATH)/src/ItcastLog.o		\
		$(SHM_PATH)/src/SecKeyShm.o		\
		$(SHM_PATH)/src/ShareMemory.o	\
		$(TCP_PATH)/src/TcpServer.o		\
		$(TCP_PATH)/src/TcpSocket.o		\
		$(SERVEROP_PATH)/src/ServerOperation.o	\
		$(ORACLEOP_PATH)/src/OCCIOP.o	\
		./main.o
	$(CC) -o $@ $^ $(LIBS) $(CPPLFAGS) 

%.o:%.cpp
	$(CC) -std=c++11 -c $< $(CPPLFAGS) -o $@

.PHONY:clean
clean:
	rm -rf *.o $(target) $(CODEC_PATH)/src/*.o $(LOG_PATH)/src/*.o $(SHM_PATH)/src/*.o $(TCP_PATH)/src/*.o  $(SERVEROP_PATH)/src/*.o $(ORACLEOP_PATH)/src/*.o
	rm -f core.*

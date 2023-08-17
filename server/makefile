src=$(wildcard *.cpp)
objs=$(patsubst %.cpp,%.o,$(src))
target=serMain
LIBS=-lstdc++ -lssl -lcrypto -locci -lclntsh -lpthread
$(target):$(objs)
	g++ -o $@ $^ $(LIBS) 

%.o:%.cpp
	g++ -std=c++11 -c -g $<

.PHONY:clean
clean:
	rm -f $(target) $(objs)

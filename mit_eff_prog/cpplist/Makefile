PROG := cpplist
SHELL := /bin/csh
CC := gcc
CXX := g++ 

COMPILER_OPTIONS := -m64 -Wall -Wextra -Wshadow -Werror -pedantic -Iinclude
CFLAGS := -std=c99 $(COMPILER_OPTIONS)
CXXFLAGS := -std=c++11 -Weffc++ $(COMPILER_OPTIONS)
LDFLAGS := -Wl,--no-as-needed -lm

DEBUGFLAGS := -g -O0 -D _DEBUG
RELEASEFLAGS := -O2 -D NDEBUG

TARGET  := $(PROG)-test.x
SOURCES := $(shell echo src/*.cpp)
HEADERS := $(shell echo include/*.h)
COMMON  :=
OBJECT_NAMES := $(SOURCE_NAMES:.cpp=.o)
OBJECTS := bin/apply.o bin/list_iterator.o bin/list_node.o bin/list.o bin/reduce.o bin/test.o

all: $(TARGET)

$(TARGET): $(OBJECTS) $(COMMON)
	$(CXX) $(FLAGS) $(CXXFLAGS) $(DEBUGFLAGS) -o $(TARGET) $(OBJECTS)

release: $(SOURCES) $(HEADERS) $(COMMON)
	$(CXX) $(FLAGS) $(CXXFLAGS) $(RELEASEFLAGS) -o $(TARGET) $(SOURCES)

zip:
	-zip $(PROG).zip $(HEADERS) $(SOURCES) Makefile GRADER_INFO.txt

clean:
	-rm -f $(TARGET) $(OBJECTS) $(PROG).zip

bin/%.o : src/%.cpp $(HEADERS) $(COMMON)
	$(CXX) $(CXXFLAGS) $(DEBUGFLAGS) -c -o $@ $<

.PHONY : all release

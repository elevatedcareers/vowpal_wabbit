ifeq ($(JAVA_HOME),)
  $(warning No JAVA_HOME found, JNI building will fail.  Please set JAVA_HOME when using JNI)
  exit 1
endif

BOOST_LDFLAGS = -L/lib/x86_64-linux-gnu -I/usr/include
VWLIBS := -L../vowpalwabbit/.libs -l vw -l allreduce
STDLIBS = $(BOOST_LDFLAGS) $(LIBS)
JAVA_INCLUDE = -I $(JAVA_HOME)/include -I $(JAVA_HOME)/include/linux
#FLAGS= -fPIC

ifeq ($(UNAME), Linux)
  JAVA_INCLUDE += -I $(JAVA_HOME)/include/linux
endif
ifeq ($(UNAME), FreeBSD)
  JAVA_INCLUDE += -I $(JAVA_HOME)/include/linux
endif
ifeq "CYGWIN" "$(findstring CYGWIN,$(UNAME))"
  JAVA_INCLUDE += -I $(JAVA_HOME)/include/linux
endif
ifeq ($(UNAME), Darwin)
  JAVA_INCLUDE += -I $(JAVA_HOME)/include/darwin
endif

all:
	cd ..; $(MAKE)

test:
	cd ..; $(MAKE) test
	
things: target/vw_jni.lib	

target/vw_jni.lib: src/main/c++/vw_VWScorer.cc ../vowpalwabbit/main.o ../vowpalwabbit/.libs/libvw.a ../vowpalwabbit/.libs/liballreduce.a
	mkdir -p target;
	$(CXX) -shared -fpic $(FLAGS) -o $@ $< $(VWLIBS) $(STDLIBS) $(JAVA_INCLUDE)

clean:
	rm -f target/vw_jni.lib

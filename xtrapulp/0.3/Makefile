MPICXX = mpicxx
CXXFLAGS = -fopenmp -O3 -std=c++11 -Wall -fPIC -O
#CXXFLAGS = -fopenmp -Ofast -Wall
LINKFLAGS = -fopenmp -O3 -std=c++11 -Wall -fPIC -O
#LINKFLAGS = -fopenmp -Ofast -Wall
TARGET = xtrapulp
LIBTARGET = libxtrapulp.a
TOCOMPILE = util.o generate.o pulp_util.o pulp_data.o fast_map.o dist_graph.o comms.o io_pp.o main.o
FORLIBPULP = util.o generate.o pulp_util.o pulp_data.o fast_map.o dist_graph.o comms.o io_pp.o pulp_init.o pulp_w.o pulp_v.o pulp_ve.o pulp_vec.o xtrapulp.o


all: libxtrapulp $(TOCOMPILE)
	$(MPICXX) $(LINKFLAGS) -o $(TARGET) $(TOCOMPILE) $(LIBTARGET)

libxtrapulp: $(FORLIBPULP)
	ar rvs $(LIBTARGET) *.o
	$(MPICXX) $(CXXFLAGS) -shared *.o -o libxtrapulp.so

.cpp.o:
	$(MPICXX) $(CXXFLAGS) -c $*.cpp

clean:
	rm -f *.o *.a $(TARGET)


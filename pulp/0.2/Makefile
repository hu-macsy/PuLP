CXX=mpicxx
CXXFLAGS= -fopenmp -O3 -Wall -fPIC -O

all: pulp libpulp

pulp.o:
	$(CXX) $(CXXFLAGS) -c pulp.cpp

libpulp: pulp.o
	#ar rvs libpulp.a pulp.o
	$(CXX) $(CXXFLAGS) -shared pulp.o -o libpulp.so

pulp: pulp.o
	$(CXX) $(CXXFLAGS) -o pulp pulp_main.cpp pulp.o

clean:
	rm -f pulp *.o *.a

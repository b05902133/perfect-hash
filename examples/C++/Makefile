CXX = g++ -Wall


lookup: main.o states-code.o
	$(CXX) -o $@ $^


main.o: main.cc states-code.hh
	$(CXX) -c $<


states-code.o: states-code.cc states-code.hh states.dat.h
	$(CXX) -c $<


states-code.cc: states.dat states-tmpl.cc states-code.hh
	python ../../perfect_hash.py --splitby '|' --keycol 2 states.dat \
                                     states-tmpl.cc


states.dat.h: states.dat
	python mk_header.py >$@


clean:
	rm -f lookup *.o states.dat.h states-code.cc


test: lookup
	./lookup 'NY'
	./lookup 'QW'

CC = gcc -Wall


a.out: main.c keys.code.h
	$(CC) $<


keys.code.h: keys.dat keys.tmpl.h
	python ../../perfect_hash.py -v $^


keys.dat:
	python ./mk_rnd_keys.py 1000 >keys.dat


clean:
	rm -f keys.dat keys.code.h a.out


test: a.out
	./a.out

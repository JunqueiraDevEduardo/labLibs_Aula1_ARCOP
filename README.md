# labLibs
### Lab workout on libraries

git@github.com:miguelleitao/lablibs.git

## Usage
    make clean

### Static exec, monolytic
    cat calc0.c
    make calc0
    ls -l calc0
    nm -W -g calc0
    ./calc0 11 + 55

### Static app, distributed
    cat calc.c
    cat sub.c
    cat sum.c
    make calc1
    ls -l calc1
    nm -W -g calc1
    ./calc1 11 + 55

### Using static library
    make calc2
    ls -l *.a calc2
    ar -t *.a
    nm *.a
    nm -W -g calc2
    ./calc2 11 + 55

### Full static app
    make calc3
    ls -l calc3
    nm -W -g calc3
    ./calc3 11 + 55

### Shared library
    make calc4
    ls -l calc4 *.so
    nm -D *.so
    export LD_LIBRARY_PATH=.
    ldd calc4
    nm -W -g calc4
    ./calc4 11 + 55

### Dynamic loading 
    cat calc_din.c
    make calc5
    ls -l calc5
    ldd calc5
    ./calc5 11 + 55
    
à medida que avanço de calc0 a calc5, o que o nm -W -g mostra muda porque mudos o modelo de ligação: tudo dentro de um único binário, depois objetos separados, depois biblioteca estática, binário totalmente estático, biblioteca partilhada e, por fim, carregamento dinâmico com dlopen/dlsym;

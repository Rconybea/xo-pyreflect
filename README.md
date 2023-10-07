# python bindings for c++ reflection library (xo-reflect)

## build + install
```
$ cd xo-pyreflect
$ mkdir build
$ cd build
$ INSTALL_PREFIX=/usr/local  # or wherever you prefer, e.g. ~/local
$ cmake \
    -DCMAKE_MODULE_PATH=${INSTALL_PREFIX}/share/cmake \
    -DCMAKE_PREFIX_PATH=${INSTALL_PREFIX} \
    -DCMAKE_INSTALL_PREFIX=${INSTALL_PREFIX} ..
$ make
$ make install
```

## build for unit test coverage
```
$ cd xo-pyreflect
$ mkdir build-ccov
$ cd build-ccov
$ cmake \
    -DCMAKE_MODULE_PATH=${INSTALL_PREFIX}/share/cmake \
    -DCMAKE_PREFIX_PATH=${INSTALL_PREFIX} \
    -DCODE_COVERAGE=ON \
    -DCMAKE_BUILD_TYPE=Debug ..
```

## LSP (language server) support

LSP looks for compile commands in the root of the source tree;
while Cmake creates them in the root of its build directory.

```
$ cd xo-pyreflect
$ ln -s build/compile_commands.json  # supply compile commands to LSP
```

## Examples

Assumes `xo-pyreflect` installed to `~/local2/lib`

```
PYTHONPATH=~/local2/lib python
>>> import pyreflect
>>> dir(pyreflect)
['SelfTagging', 'TaggedRcptr', 'TypeDescr', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__']
>>> pyreflect.TypeDescr.print_reflected_types()
<type_table_v[0]:>
```

Not _immediately_ interesting:  no reflected types in `pyreflect` itself

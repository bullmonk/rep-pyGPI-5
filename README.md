# pyGPI5 fork
~NOTE~ this is a fork from original [repo: pyGPI5](https://github.com/srkaeppler/pyGPI5)

## Necessary Changes Needed For Local Run

### 1. change 2 directories' values in `Models/MSIS.py`

at line 128, change from 
```
def __init__(self):
    self.geophys_dir = '/Users/srkaeppler/research/data/AFOSR_Eregion_Conductivity/Models/AP_KP'

    self.inLib = '/Users/srkaeppler/research/data/AFOSR_Eregion_Conductivity/Models/nrlmsise00/libnrlmsise-00.so'
```
to
```
def __init__(self):
    self.geophys_dir = '/***/Models/AP_KP'

    self.inLib = '/***/Models/nrlmsise00/libnrlmsise-00.so'
```

note replace the `***` with your local path, which you can get by go to this project root directory, and `pwd`.

### 2. change 1 direcotry value in `Models/IRI2016.py`
At line 10. change from
```
self.iridir = '/Users/srkaeppler/research/data/pyGPI5/Models/iri2016'
```
to 
```
self.iridir = '/***/Models/iri2016'
```
note replace the `***` with your local path, which you can get by go to this project root directory, and `pwd`.


### 3. rebuild lib files under `/Models/nrlmsise00`
go to `/Models/nrlmsise00`, then `make clean`, then `make`.
### 4. rebuild lib files under `/Models/iri2016`
1. changes in the makefile has to be done first. One need to set the `F2PY` value as his/her own app path.
    ```
    F2PY	= "/your own path/f2py"
    ```
    if this app is installed, one can find this path by run
    ```
    which f2py
    ```
2. rebuild with make command
    ```
    make clean
    make mkf2py
    ```
    then change the newly name `iri2016.cpython-311-x86_64-linux-gnu.so` (yours might look differently) into `iri2016.so`.

    rebuild `mkso` again
    ```
    make mkso
    ```
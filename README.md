# VSD Hardware Design Program

## OpenROAD installation guide

### `Steps to Install OpenROAD and Run GUI`

### 1. Clone the OpenROAD Repository

```bash
git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD.git
cd OpenROAD
```

### 2. Run the Setup Script

```bash
sudo ./etc/DependencyInstaller.sh
```


Installation of the dependencies is done here.


<img width="1358" height="652" alt="setup_sr" src="https://github.com/user-attachments/assets/2771f80c-5fa6-4212-807d-a1487bf4b12d" />
<img width="1339" height="452" alt="setup_sr2" src="https://github.com/user-attachments/assets/69da765c-286b-4328-94bc-28086cb8e950" />
<img width="1357" height="649" alt="setup_sr3" src="https://github.com/user-attachments/assets/e80d962b-09fb-45d3-84a8-bd3d13dcb579" />



I have encounter some errors like:

```
1ST :


tmp/DependencyInstaller-g83VNh/lemon-graph/lemon/arg_parser.cc: In member function ‘lemon::ArgParser& lemon::ArgParser::synonym(const string&, const string&)’:
/tmp/DependencyInstaller-g83VNh/lemon-graph/lemon/arg_parser.cc:224:20: warning: variable ‘s’ set but not used [-Wunused-but-set-variable]
  224 |     Opts::iterator s = _opts.find(syn);
      |                    ^
[ 21%] Building CXX object lemon/CMakeFiles/lemon.dir/lp_base.cc.o
[ 26%] Building CXX object lemon/CMakeFiles/lemon.dir/lp_skeleton.cc.o
[ 31%] Building CXX object lemon/CMakeFiles/lemon.dir/random.cc.o
[ 36%] Building CXX object lemon/CMakeFiles/lemon.dir/bits/windows.cc.o
[ 36%] Building CXX object lemon/CMakeFiles/lemon.dir/soplex.cc.o
In file included from /tmp/DependencyInstaller-g83VNh/lemon-graph/lemon/random.cc:22:
/tmp/DependencyInstaller-g83VNh/lemon-graph/lemon/random.h: In member function ‘void lemon::_random_bits::RandomCore<_Word>::fillState()’:
/tmp/DependencyInstaller-g83VNh/lemon-graph/lemon/random.h:252:24: warning: ISO C++17 does not allow ‘register’ storage class specifier [-Wregister]
  252 |         register Word *curr = state + length - 1;
      |                        ^~~~
/tmp/DependencyInstaller-g83VNh/lemon-graph/lemon/random.h:253:23: warning: ISO C++17 does not allow ‘register’ storage class specifier [-Wregister]
  253 |         register long num;
      |                       ^~~
/tmp/DependencyInstaller-g83VNh/lemon-graph/lemon/random.h: In instantiation of ‘void lemon::_random_bits::RandomCore<_Word>::fillState() [with _Word = long unsigned int]’:
/tmp/DependencyInstaller-g83VNh/lemon-graph/lemon/random.h:236:31:   required from ‘lemon::_random_bits::RandomCore<_Word>::Word lemon::_random_bits::RandomCore<_Word>::operator()() [with _Word = long unsigned int; lemon::_random_bits::RandomCore<_Word>::Word = long unsigned int]’
/tmp/DependencyInstaller-g83VNh/lemon-graph/lemon/random.h:456:23:   required from ‘bool lemon::_random_bits::BoolProducer<Word>::convert(lemon::_random_bits::RandomCore<Word>&) [with Word = long unsigned int]’
/tmp/DependencyInstaller-g83VNh/lemon-graph/lemon/random.h:760:35:   required from here
/tmp/DependencyInstaller-g83VNh/lemon-graph/lemon/random.h:252:24: warning: ISO C++17 does not allow ‘register’ storage class specifier [-Wregister]
  252 |         register Word *curr = state + length - 1;
      |                        ^~~~
/tmp/DependencyInstaller-g83VNh/lemon-graph/lemon/random.h:253:23: warning: ISO C++17 does not allow ‘register’ storage class specifier [-Wregister]
  253 |         register long num;
      |                       ^~~
/tmp/DependencyInstaller-g83VNh/lemon-graph/lemon/soplex.cc:23:10: fatal error: spxout.h: No such file or directory
   23 | #include <spxout.h>
      |          ^~~~~~~~~~
compilation terminated.
gmake[2]: *** [lemon/CMakeFiles/lemon.dir/build.make:177: lemon/CMakeFiles/lemon.dir/soplex.cc.o] Error 1
gmake[1]: *** [CMakeFiles/Makefile2:425: lemon/CMakeFiles/lemon.dir/all] Error 2
gmake: *** [Makefile:166: all] Error 2
[ERROR] Failed to execute: /home/openboxuser/.local/bin/cmake --build build -j 3 --target install


```

**FIX**

```

cd ~
git clone https://github.com/scipopt/soplex.git
cd soplex
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
make -j$(nproc)
sudo make install

```

```

2ND:

CMake Error at src/gpl/CMakeLists.txt:12 (find_package):
  Found package configuration file:

    /usr/local/lib/cmake/ortools/ortoolsConfig.cmake

  but it set ortools_FOUND to FALSE so package "ortools" is considered to be
  NOT FOUND.  Reason given by package:

  ortools could not be found because dependency Clp could not be found.


```

**FIX**


```

cd ~
git clone https://github.com/google/or-tools.git
cd or-tools
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release -DBUILD_DEPS=ON -DUSE_SCIP=OFF -DUSE_GLPK=OFF
make -j$(nproc)
sudo make install


```


### 3. Build OpenROAD


```

mkdir build && cd build
cmake ..
make
sudo make install


```

### 4. Verify Installation

```bash

source ./env.sh
yosys -help  
openroad -help

```
<img width="1357" height="649" alt="yosys_sr" src="https://github.com/user-attachments/assets/c0ed4558-4049-412a-a1ca-bad437b9c01f" />
<img width="1357" height="649" alt="source_sr" src="https://github.com/user-attachments/assets/eddd0103-b81b-46b5-a641-60057c2b6c63" />
<img width="1358" height="654" alt="openroad_sr" src="https://github.com/user-attachments/assets/1bf30098-0ccc-4bcb-8ba7-c0e07f7fe52d" />

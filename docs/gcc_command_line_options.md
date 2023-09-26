Compile with GCC
================

Consider, a binary/executable file `main` has generated from a C++ project. There is several gcc commands are available to get insightful information of binary file. Some of them are listed belows:

- Consider, in project folder `header.h, main.cpp` is present. If path of `header.h` is same as `main.cpp` and in terminal the following command run, binary will be generated
```cpp
g++ main.cpp -o main
```
- If the header file locates in any other directory then have to tell the compiler the path. Eg: in `include` folder header file is stored. Command will be
```cpp
g++ main.cpp -I include -o main
```
- Eg: Suppose in header file `pthread` library is included as like as `include<pthread>`. To compile now have to use:
```cpp
g++ main.cpp -I include -lpthread -o main
```
- If library has to be found from some other location then have to use `-Llib_search_path`
```cpp
g++ main.cpp -I include -lpthread -Llib_search_path -o main
```
- `file main` This one provides information of the file
- `objdump main`

# HPPC



Code from my terminal to generate these profiles 
(I had no pragmas yet)

```
jovyan@128460442ae1:~/erda_mount/HPPC/module2$ make clean
rm -fr seq vec
jovyan@128460442ae1:~/erda_mount/HPPC/module2$ make
g++ Water_sequential.cpp -O3 -ffast-math -pg -Wall -march=native -g -std=c++17 -o seq
g++ Water_vectorised.cpp -O3 -ffast-math -pg -Wall -march=native -g -std=c++17 -fopenmp-simd -o vec
jovyan@128460442ae1:~/erda_mount/HPPC/module2$ ./vec -steps 10000 -no_mol 100
Accumulated forces Bonds   : 3.1349e+08
Accumulated forces Angles  : 2.1046e+08
Accumulated forces Non-bond: 4.1355e+09
Elapsed total time:          1.0806
jovyan@128460442ae1:~/erda_mount/HPPC/module2$ gprof -p -b ./vec gmon.out > vec_100.txt
jovyan@128460442ae1:~/erda_mount/HPPC/module2$ ./vec -steps 10000 -no_mol 1000
Accumulated forces Bonds   : 3.0881e+09
Accumulated forces Angles  : 2.1028e+09
Accumulated forces Non-bond: 3.9918e+10
Elapsed total time:         10.7544
jovyan@128460442ae1:~/erda_mount/HPPC/module2$ gprof -p -b ./vec gmon.out > vec_1000.txt
jovyan@128460442ae1:~/erda_mount/HPPC/module2$ ./vec -steps 10000 -no_mol 10
Accumulated forces Bonds   : 3.119e+07
Accumulated forces Angles  : 1.8961e+07
Accumulated forces Non-bond: 2.9845e+08
Elapsed total time:          0.1007
jovyan@128460442ae1:~/erda_mount/HPPC/module2$ gprof -p -b ./vec gmon.out > vec_10.txt
```

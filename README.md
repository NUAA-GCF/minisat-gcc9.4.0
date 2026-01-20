# minisat-gcc9.4.0
a fixed minisat suitable for linux(gcc version is 9.4.0)
本项目基于minisat2.2.0版本进行更新目的为了适配gcc 9.4.0版本的linux系统
# 编译系统工具文件
cd /XXX/minisat
g++ -std=c++11 -Wno-literal-suffix -fpermissive -I. -Imtl -Iutils -c utils/System.cc -o System.o
g++ -std=c++11 -Wno-literal-suffix -fpermissive -I. -Imtl -Iutils -c utils/Options.cc -o Options.o

# 编译核心文件
cd core
g++ -std=c++11 -Wno-literal-suffix -fpermissive -I.. -I../mtl -I../utils -c Solver.cc -o Solver.o
g++ -std=c++11 -Wno-literal-suffix -fpermissive -I.. -I../mtl -I../utils -c Main.cc -o Main.o

# 链接生成可执行文件
g++ Solver.o Main.o ../System.o ../Options.o -o minisat -lz -lm

# 测试编译结果
./minisat --help

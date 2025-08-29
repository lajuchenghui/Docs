---
sidebar_position: 2
---
# DeepSeek-R1

## 1.编译可执行程序

1.进入源码目录

```
cd rknn-llm/examples/DeepSeek-R1-Distill-Qwen-1.5B_Demo/deploy/
```



2.修改交叉编译工具链

```
vi build-linux.sh
```

将原本的：

```
GCC_COMPILER_PATH=~/opts/gcc-arm-10.2-2020.11-x86_64-aarch64-none-linux-gnu/bin/aarch64-none-linux-gnu
```

修改为：

```
GCC_COMPILER_PATH=aarch64-linux-gnu
```

3.安装cmake

```
sudo apt install cmake -y
```



4.增加可执行权限并执行编译

```
chmod +x build-linux.sh
./build-linux.sh
```

运行效果：

```
baiwen@dshanpi-a1:~/rknn-llm/examples/DeepSeek-R1-Distill-Qwen-1.5B_Demo/deploy$ ./build-linux.sh
-- The C compiler identification is GNU 11.4.0
-- The CXX compiler identification is GNU 11.4.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/aarch64-linux-gnu-gcc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/aarch64-linux-gnu-g++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /home/baiwen/rknn-llm/examples/DeepSeek-R1-Distill-Qwen-1.5B_Demo/deploy/build/build_linux_aarch64_Release
[ 50%] Building CXX object CMakeFiles/llm_demo.dir/src/llm_demo.cpp.o
[100%] Linking CXX executable llm_demo
[100%] Built target llm_demo
Consolidate compiler generated dependencies of target llm_demo
[100%] Built target llm_demo
Install the project...
-- Install configuration: "Release"
-- Installing: /home/baiwen/rknn-llm/examples/DeepSeek-R1-Distill-Qwen-1.5B_Demo/deploy/install/demo_Linux_aarch64/./llm_demo
-- Set runtime path of "/home/baiwen/rknn-llm/examples/DeepSeek-R1-Distill-Qwen-1.5B_Demo/deploy/install/demo_Linux_aarch64/./llm_demo" to ""
-- Installing: /home/baiwen/rknn-llm/examples/DeepSeek-R1-Distill-Qwen-1.5B_Demo/deploy/install/demo_Linux_aarch64/lib/librkllmrt.so
```



5.进入可执行文件目录

```
cd install/demo_Linux_aarch64/
```



6.将预训练和转换完成的模型文件传输至开发板端中

```
baiwen@dshanpi-a1:~/rknn-llm/examples/DeepSeek-R1-Distill-Qwen-1.5B_Demo/deploy/install/demo_Linux_aarch64$  ls
DeepSeek-R1-Distill-Qwen-1.5B_W4A16_RK3576.rkllm  DeepSeek-R1-Distill-Qwen-7B_W4A16_G128_RK3576.rkllm  lib  llm_demo
```



## 2.模型推理

### 2.1 DeepSeek-R1 1.5B

1.导入依赖和环境变量

```
export LD_LIBRARY_PATH=./lib
export RKLLM_LOG_LEVEL=1
```

2.执行程序

```
./llm_demo ./DeepSeek-R1-Distill-Qwen-1.5B_W4A16_RK3576.rkllm 2048 4096
```

![image-20250822105053016](${images}/image-20250822105053016.png)

> 如果想退出可输入`Ctrl+C`。

### 2.2 DeepSeek-R1 7B

1.导入依赖和环境变量

```
export LD_LIBRARY_PATH=./lib
export RKLLM_LOG_LEVEL=1
```

2.执行程序

```
./llm_demo ./DeepSeek-R1-Distill-Qwen-7B_W4A16_G128_RK3576.rkllm 2048 4096
```

![image-20250822105538997](${images}/image-20250822105538997.png)

> 如果想退出可输入`Ctrl+C`。

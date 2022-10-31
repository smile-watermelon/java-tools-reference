## jmap (JVM memory map)
> 作用： 
> 获取dump文件(堆转储快照文件， 二进制文件)
> 获取目标进程内存信息，包括堆中各区域使用信息，堆中对象的统计信息，类加载等信息
> Heap dump 的时候会触发一次 Full GC，输出的是full gc 后留下的对象信息

### 基本使用
> 格式：jmap -option pid

- option 说明

| 选项             | 说明                                    |
|----------------|---------------------------------------|
| -dump          | 生成堆转储快照，即dump文件                       |
| -dump:live     | 只保存堆中存活的的对象                           |
| -heap          | 输出整个堆空间的详细信息，包括GC使用，堆配置信息，内存使用等信息     |
| -histo         | 输出堆中的统计信息，包括类，实例数量，合计容量               |
| -permstat      | 已ClassLoader为统计口径输出永久代的内存状态信息         |
|                | 仅linux/solaris平台有效                    |
| -finalizerinfo | 显示在F-Queue中等待Finalizer线程执行finale方法的对象 |
|                | 仅linux/solaris平台有效                    |
| -F             | 虚拟机没有响应时，强制打印                         |
|                | 仅linux/solaris平台有效                    |
| -J <flag>      | 传递给jmap启动时的参数                         |

- 手动执行，打印执行jmap这一刻堆中的信息
```shell
jmap -dump:format=b,file=./1.hprof 3089
```

- 手动执行，输出堆中存活的对象
```shell
jmap -dump:live,format=b,file=./1.hprof 3089 
```
- 在程序要OOM的时候自动打印对信息，jvm 配置参数
```
-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=./1.hprof
```

- 输出整个堆信息, 在mac M1 下这个命令可能不支持
```shell
jmap -heap 3089
```

- 输出堆中的统计信息，包括类，实例数量，合计容量
```shell
jmap -histo 3089
```
```shell
 num     #instances         #bytes  class name
----------------------------------------------
   1:          1440        9196144  [B
   2:           672        1041952  [I
   3:          6095         669848  [C
   4:          4867         116808  java.lang.String
   5:           697          79432  java.lang.Class
   6:          1303          58840  [Ljava.lang.Object;
   7:           621          24840  java.util.LinkedHashMap$Entry
   8:           325          16440  [Ljava.lang.String;

```

- 
```shell
jmap -permstat 3089
```

```shell
jmap -finalizerinfo
```
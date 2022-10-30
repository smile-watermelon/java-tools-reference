## jstat (JVM statistics monitoring tool) 见识虚拟机个钟运行状态信息，显示本地或远程类装载，内存，垃圾收集，JIT编译等运行数据

### 基本参数
- jstat -[option] [-t] [-h<lines>] <vmid> [<interval> [<count>]]

| 参数        | 说明             |
|-----------|----------------|
| -t        | 程序启动到当前的总运行时间  |
| -h<lines> | 每隔lines次答应一次表头 |
| vmid      | 进程id           |
| interval  | 每隔多就打印一次，单位毫秒  |
| count     | 总共打印次数         |

- 命令执行
```shell
jstat -class -t -h3 3089 1000 10
```
![img_1.png](img/img_1.png)

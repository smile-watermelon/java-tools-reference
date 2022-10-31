## jstack
> 用于生成虚拟机指定进程当前时刻的线程快照（虚拟机堆栈跟踪）
> 线程快照是当前虚拟机内指定进程的每一条线程正在执行的方法的堆栈集合

- 作用
1. 死锁 ⭐️
2. 等待资源 waiting on condition ⭐️ 
3. 等待获取监视器 waiting on monitor entry ⭐️
4. 阻塞 ⭐️
5. 执行中 Runnable 
6. 暂停 Suspended

- jstack <-option> <-pid>

| 选项  | 说明         |
|-----|------------|
| -l  | 打印锁的额外信息   |
| -e  | 打印线程的额外信息  |

```shell
jstack 3089
```

- 打印锁的额外信息
```shell
jstack -l 3089
```
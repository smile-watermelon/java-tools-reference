## jcmd java 工具类功能的整合

```shell
jcmd 3089 help
```
```
8565:
The following commands are available:
VM.unlock_commercial_features
JFR.configure
JFR.stop
JFR.start
JFR.dump
JFR.check
VM.native_memory
ManagementAgent.stop
ManagementAgent.start_local
ManagementAgent.start
VM.classloader_stats
GC.rotate_log
Thread.print
GC.class_stats
GC.class_histogram
GC.heap_dump
GC.finalizer_info
GC.heap_info
GC.run_finalization
GC.run
VM.uptime
VM.dynlibs
VM.flags
VM.system_properties
VM.command_line
VM.version
help
```

- jcmd = jps -l
- jcmd 3089 Thread.print = jstack 
- jcmd 3089 GC.class_histogram = jmap -histo 3089
- jcmd 3089 GC.heap_dump ./1.hprof = jmap -dump:format=b,file=./1.hprof 3089
- jcmd 3089 VM.system_properties = jinfo -sysprops 3089
- jcmd 3089 VM.uptime = jstat -class -t 3089 // 只显示时间 
- jcmd 3089 VM.flags // 打印进程虚拟机参数
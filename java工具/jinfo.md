## jinfo (Configuratition Info for java)

- 只有被管理的参数才可以被修改成功
```shell
java -XX:+PrintFlagsFinal -version | grep manageable
```
```shell
     intx CMSAbortablePrecleanWaitMillis           = 100                                    {manageable} {default}
     intx CMSTriggerInterval                       = -1                                     {manageable} {default}
     intx CMSWaitDuration                          = 2000                                   {manageable} {default}
     bool HeapDumpAfterFullGC                      = false                                  {manageable} {default}
     bool HeapDumpBeforeFullGC                     = false                                  {manageable} {default}
     bool HeapDumpOnOutOfMemoryError               = false                                  {manageable} {default}
    ccstr HeapDumpPath                             =                                        {manageable} {default}
    uintx MaxHeapFreeRatio                         = 70                                     {manageable} {default}
    uintx MinHeapFreeRatio                         = 40                                     {manageable} {default}
     bool PrintClassHistogram                      = false                                  {manageable} {default}
     bool PrintConcurrentLocks                     = false                                  {manageable} {default}
java version "11.0.17" 2022-10-18 LTS
Java(TM) SE Runtime Environment 18.9 (build 11.0.17+10-LTS-269)
Java HotSpot(TM) 64-Bit Server VM 18.9 (build 11.0.17+10-LTS-269, mixed mode)
```

```shell
jinfo <option> <pid>
```

- 执行此命令在Java中可以通过 System.getProperties();
```shell
jinfo -sysprops 3089
```

- 查看虚拟机参数设置
```shell
jinfo -flags 3089 
```
```
VM Flags:
-XX:CICompilerCount=4 -XX:InitialHeapSize=1073741824 -XX:MaxHeapSize=17179869184 -XX:MaxNewSize=5726273536 -XX:MinHeapDeltaBytes=524288 -XX:NewSize=357564416 -XX:OldSize=716177408 -XX:+UseCompressedClassPointers -XX:+UseCompressedOops -XX:+UseParallelGC
```

- 查看某个参数值
```shell
jinfo -flag  CICompilerCount 3089
```

- 查看jvm 启动所有参数初始值
```shell
java -XX+PrintFlagsInitial 
```

- 查看jvm 最终的参数值
```shell
java -XX+PrintFlagsFinal
```

- 查看被用户，jvm设置过的最终值
```shell
java -XX+PrintCommandLineFlags
```
### Circular Buffering
ETW supports recording into an in memory circular buffer. This will avoid
dropping events if the disk can't keep up. This is useful when profiling on low
performance machines under high load.
```
xperf -on  latency -stackwalk profile -Buffering -Buffersize 1024 -MinBuffers 50000 -MaxBuffers 50000
[do stuff you want to profile]
xperf -flush -f [output file]
xperf -stop
```

NOTE: converting circular buffer profiles is not yet supported.

### Unblocking stacks (Not yet suported)

```
xperf -on Latency+DISPATCHER -stackwalk Profile+CSwitch+ReadyThread
```


### Looking up providers/events

https://github.com/lallousx86/WinTools/tree/master/WEPExplorer is useful browser of this information

### Tracing vsync
`xperf -start "usersession" -on Microsoft-Windows-DxgKrnl:1:5`
`xperf -stop "usersession" -d out.etl`
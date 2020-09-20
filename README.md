# queue
```shell script
go get github.com/chenwbyx/queue
```
#### 实现了几种队列：
* 基于channel + slice的无锁队列
* 基于channel + ring-buffer queue的无锁队列
* 基于channel + slice的mutex-based queue
* 基于channel + ring-buffer queue的mutex-based queue
* 基于CAS的lock-free queue：三种通知方式优化

### Benchmark
```go
goos: windows
goarch: amd64
pkg: queue
BenchmarkChanQueue-12                         24          46990142 ns/op
BenchmarkChanRindBuf-12                       24          47742371 ns/op
BenchmarkLockQueue-12                         69          17018346 ns/op
BenchmarkLockRingBuf-12                       62          18197669 ns/op
BenchmarkLockFreeQueue-12                     85          12750016 ns/op
BenchmarkLockFreeQueueChan-12                 85          12768865 ns/op
BenchmarkLockFreeQueueSignal-12               85          12767584 ns/op
PASS
ok      queue   8.187s
```
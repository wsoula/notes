BPF Performance Analysis
---
* bpf allows you to view performance in linux
* `bpftrace __iwl_dbg`

Why BPF is changing linux
* bpf programs run to completion rather than blocking or sleeping

bpf allows applications to run in kernel-mode

bpf - berkeley packet filter - made to make tcpdump go faster
bpf -2019 - extended bpf
bpftrace for tracing

user defined bpf programs
* sdn config
* ddos migration
* intrusion detection
* container security
* observability
* firewalls
* devices drivers

bpf is opensource and in the linux kernel

bpf a new type of software

https://github.com/iovisor/bcc
https://github.com/iovisor/bpftrace
https://github.com/brendangregg/bpf-perf-tools-book
https://www.brendangregg/ebpf.html
https://www.brendangregg.com/bpf-performance-tools-book.html

`execsnoop.py -T` - better than top for really short running things you wont see
`runqlat.py 10 1` - queue latency - time spent waiting on cpu
`runqlewn.py 10 1` - run queue length -
`ffaults.bt` - filesystem faults
`biolatency.pt -mT 1 5` - disk i/o latency histograms, per second
`xfsslower.py 50` - xfs i/o slower than a threshold (variants for ext4, btrfs, zfs) - better indicator of file system pain than the one above which can include disk flushes that are normal
`xfsdist.py 60` - xfs (???)
`tcplife.py` - tcp session lifespans with connection details - see which service is connecting to another service
`tcpsynbl.bt` - tcp syn backlogs as histograms - too many syns can lead to a syn log attach
`funccount.py 'tcp_s*'` - count native function calls (C, C++, go, etc)
`mysqld_qslower.py $(pgrep mysqld)` - mysql queries slower than a threshold
`workq.bt` - work queue function execution times
`xenhyper.bt` - count hypercalls from Xen PV guests

above is 14 out of 150+ that are all open source

coping with all of them at netflix.  (I think he said it was better to make tools for what you want to see)

only one engineer at your company needs to learn tool development and then can turn everyone's ideas into tools

bpftrace - something or other - powerful one liners

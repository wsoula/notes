EC2 Performance Best Practices
---
* EC2 instance is a guest sitting on a hypervisor sitting on physical hardware
* Instance groups can get the nodes to spin up near each other
* hvm uses more of the underlying hardware and talks less to the hypervisor
* types
  * m - general
  * c - compute
  * d/i - storage and i/o
  * p/g - gpu
  * r/x - memory optimized
* a vCPU is typically a hyper-threaded physical core
  * divide vCPU by 2 to get the core count
  * core by EC2 & RDS DB - aws.amazon.com/ec2/virtualcores
* lstopo - gives physical representation of underlying server
* can turn hyper-threading off
  * useful for FPU heavy applications
  * use lscpu to validate layout
  * hot offline the "B" threads
  * for i in 'seq 64 127';do
    echo 0 > /sys/devices/system/cpu/cpu${i}/online
    done
      * might cause instability since you are doing it while its live and it is lost upon restart
  * set grub to only initialize the first half of the all threads
* instance sizing - c4.8xlarge = 2-c4.4xlarge = 4-c4.2xlarge = 8-c4.xlarge
* all resources are dedicated to your instance with no over commitment
* timekeeping
  * Xen clock source is default because all instances support it
  * TSC is handled by the physical server not the vm on it, causing calls to it to be significantly quicker
  * strace can tell how many calls are made and how long they take - strace -c ./test
  * cat /sys/devices/system/cl*/cl*/available_clocksource - to list them all
  * echo tsc > /sys/devices/system/cl*/cl*/current_clocksource - to change to tsc
* p-state and c-state control
  * c-state allow to set power saving feature of processor
  * can increase the latency of bringing up idle cores
  * "intel_idle.max_blah" in grub
  * change p-state to sudo sh -c "echo I" > to somewhere - dont turbo boost
* t2
  * cheapest and have cpu credits to boost instance
  * a cpu credit provides one core 100% for one minute
  * when idle adds credits and when busy takes credits
  * if using ASG then metric to key on is number of credits left
* x1.32XLarge
  * largest memory with 2TB of RAM
  * non-uniform memory access (numa)
  * each processor in a multi-CPU system has local memory
  * r3.8xlarge has two sockets with QPI in the middle
  * x1 has 4 sockets so even more complex - 488GB of ram per socket
  * 3.8+ kernel of linux uses numa automatically
  * set "numa=off" in grub or use nuactl to reduce numa paging if your application uses more memory than will fit on one socket
* operating systems impact performance
  * memory intensive web application
    * created many threads
    * rapidly allocated/deallocated memory
  * compare performance between rhel 6 and rhel 7
  * ebizzy -s 10 and perf stat ./ebizzy -s 10
  * flame graphs
* hugepages (mem)
  * disable transparent hugepages
  * use explicit huge pages
  * lwn.net/Articles/375096
* split driver model (io)
  * make sure to use latest kernel and os
  * persistent grants created in 3.8.0+ kernel
  * dmesg | egrep -i 'blkfront' - to validate you are using presistent grants
* device pass through - enhance networking (network)
  * sr-iov eliminates need for driver domain
  * physical network device exposes to virutal operating system
  * requires a specialized driver and to let EC2 know you are doing this
  * free and enabled by default in most omnis
* elastic network adapter (network)
  * next gen enhanced networking
    * hardware checksums
    * multi-queue support
    * receive side steering
  * 20 Gbps in a placement group
  * new open source amazon network driver
* network performance (network)
  * an traffic out of ec2 capped at 5Gbps
  * use iperf to test
  * instance size determines
* EBS Performance
  * instance size affects throughput
  * match volume size and type to your instance
  * use EBS optimized if EBS performance is important
* Conclusion
  * choose hvm ami
  * use tsc
  * c state and p state controls
  * monitor t2 cpu credits

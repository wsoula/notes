ContainerD
---
* containerd
  * fast, lightweight container supervisor
  * runc (OCI) multiplexer
  * Container lifecycle operations
This sits at the bottom of the docker stack, not meant to change much
Its faster to start 10 containers at a time than 100 at a time due to the system, so there is a lock free event look
Its daemonless - I want to upgrade my docker daemon but all my containers go down when I do
Container state - Managing state is easy when you dont have any.  Dont keep anything in memory.  /run is your friend (If you are writing system code and need to write something to the disk)
Daemonless problems - exit code and wait4(), tty/stdio, reparenting, facilitated by a shim
caontainerd launches a shim for every runc process, the shim starts runc and runc starts the container and then exits so the container process is owned by the shim
FIFO is a pipe
exit status - 
  * FIFO for blocking + file - fifo for exit event, file for exit status
  * O_CLOEXEC
  * RDONLY/WRONLY
stdio
  * FIFOs for data
  * fifos have a buffer - /proc/sys/fs/pipe-max-size - 64k - once that amount is reached then the process will block, this will happen if docker goes down and stops consuming from the pipe
re-parenting
  * shim launches runc
  * runc launches container and then exits
  * re-parenting full 
  * subreaper - prctl(PR_SET_CHILD_SUBREAPER, 1)
The OOM Problem
  * How do you connect to OOM notifications before the user process starts - see below
runtime workflow
  * create - initialize namespaces and config
  * start - exec the users process
  * delete - destroy the container
github.com/crosbymichael/dockercon-2016

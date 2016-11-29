unikernels - artifacts representing a set of software which runs in a single address space with no distinction between kernel and userpsace code
library operating system - a build system which can link a group of libraries representing traditional OS functions with an application to produce a unikernel
mirage has a github account with examples of unikernels (mirage.io?) mirageOS
halvm (?) haskell unikernel
https://github.com/search?utf8=✓&q=mirage+unikernel - several repos, qube might be the examples
can swap in your own libraries that cause edge cases always to test your app
* network interfaces that always have new packets waiting
* random number generator from a static list
* entropy sources that always block
* etc...
with ideas from project slirp they made VPNKkit
run a unikernel with docker tools - Martin Lucina unikernel-runner - given direct access to /dev/kvm on the host, which is a hypervisor - not really possible yet

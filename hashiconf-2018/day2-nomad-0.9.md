Extensible
* nvidia gpu plugin
* 0.9 supports devices and drivers but coming soon is storage volumes, networking, and logging
Advanced Scheduling
* prior to 0.8 you can end up with most allocations on one thing and one on the second.  This might be like when we add a node and theres just one alloc on it.
* solved with spread and target percentages
Placement Preference
* affinity - soft constraint, best effort to match preference
* can have multiple affinities with weights
* anti affinity with negative weight
* nomad alloc status -verbose <alloc-id> has metrics on how an allocation was scored for each node to see why nomad chose a particular node
Preemption
* chooses lower priority jobs to preempt
* to prevent cascades (where what you preempt then preempts something else over and over all the way down) jobs with priority delta < 10 of the job being placed will not be preempted
* starts at lowest priority and works up till it finds something to preempt
* preempted allocations are marked as DesiredStatus "evist"
* two new allocation API fields
  * PreemptedAllocs
  * PreemptedByAllocID
OSS will have just system jobs for preemption in 0.9

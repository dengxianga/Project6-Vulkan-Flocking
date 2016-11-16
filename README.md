Vulkan Flocking: compute and shading in one pipeline!
======================

**University of Pennsylvania, CIS 565: GPU Programming and Architecture, Project 6**

* Xiang Deng
* Tested on:  Windows 10-Home, i7-6700U @ 2.6GHz 16GB, GTX 1060 6GB (Personal Computer)

![](img/e.gif) 

* Analysis 

* Q: Why do you think Vulkan expects explicit descriptors for things like
generating pipelines and commands? HINT: this may relate to something in the
comments about some components using pre-allocated GPU memory.
* A: For efficiency, Vulkan uses pre-allocated command pool on GPU. Explicit descriptors is thus needed
for preallocation prior to the run time (to avoid the overhead).

* Q: Describe a situation besides flip-flop buffers in which you may need multiple
descriptor sets to fit one descriptor layout.
* A: When you need more descriptor set than two for the shader bindings, like normals, colors, etc. 
* Q: What are some problems to keep in mind when using multiple Vulkan queues?
  * take into consideration that different queues may be backed by different hardware
  * take into consideration that the same buffer may be used across multiple queues
* A: When diffrent queues are backed by different hardware, is some queue is only used by some hardware, it might sacrifice the performance of the hardware that
   does not need it.
     WHen multiple queues share the same buffer, we might run into racing problem.
* Q: What is one advantage of using compute commands that can share data with a
rendering pipeline?
* A: "no need to do state tracking", no need to transfer data between computing and rendering over and over again.
### Credits

* [Vulkan examples and demos](https://github.com/SaschaWillems/Vulkan) by [@SaschaWillems](https://github.com/SaschaWillems)

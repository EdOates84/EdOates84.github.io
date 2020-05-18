## Singularity & See Previous year codebase 

### Use of Singularity Container and GPU

### Sigularity on HPC
* One of the architecturally defined features in Singularity is that it can execute containers like native programs or scripts on a host computer. 
* As a result, integration with schedulers is simple and runs exactly as you would expect. 
* All standard input, output, error, pipes, IPC, and other communication pathways that are locally running programs employ are synchronized with the applications running locally within the container. 
* Users can run Singularity containers just as they run any other program on the HPC resource.

* To invoke a singularity, you need to load module singularity and Cuda, and if you need to use GPU, you also need to require the allocation of GPU before you shell the image.

This link contains some guidelines to set up the singularity container [here](https://github.com/singularityhub/singularityhub.github.io/wiki/Build-A-Container)

### Previous year codebase

I go through the last year's final usable code and read very precisely or understand all the functions and their working. I am also looking where my code well fitted in that codebase.

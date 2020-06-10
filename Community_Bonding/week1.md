## Community Bonding

![img](https://miro.medium.com/max/598/0*S6Es74nvRVxExEkL.png)

## Notes from the community bonding period

## Use of CRWU HPC

### Connection to HPC
* Red Hen Lab students are required to set up accounts on the Gallina HPC cluster at Case Western Reserve University since most projects must run on that server to pass.
* We have to use the HPC cluster instead of our local servers. 
* To connect to the CRWU, you firstly should download the Forticlient VPN(This step is crucial). 
* The website has already shown the details about how to use this VPN. Just notice that there are two passwords, the first one is the password you used to login in CASE, the second one is the DUO code.

This PDF contains some guidelines to access the HPC server.
[Set up your Account on the Gallina](https://drive.google.com/file/d/1Z_8akM36JkY-vICeLYqneHKOWqTN7wVA/view?usp=sharing)



### Use of Singularity Container and GPU

### Sigularity on HPC
* One of the architecturally defined features in Singularity is that it can execute containers like native programs or scripts on a host computer. 
* As a result, integration with schedulers is simple and runs correctly as you would expect. 
* All standard input, output, error, pipes, IPC, and other communication pathways that are locally running programs employ synchronized with the applications running locally within the container. 
* Users can run Singularity containers just as they run any other program on the HPC resource.

* To invoke a singularity, you need to load module singularity and Cuda, and if you need to use GPU, you also need to require the allocation of GPU before you shell the image.

This link contains some guidelines to set up the singularity container [here](https://github.com/singularityhub/singularityhub.github.io/wiki/Build-A-Container)

### Previous year codebase

I go through the last year's final usable code and read very precisely or understand all the functions and their working. I am also looking where my code well fitted in that codebase.

## Explore IMDB Dataset

### Objective-1
To find a channel by using multiple anchors from 8-hour long video

* By Face recognition we get anchors name by using anchors we can get channels, but we currently have big data there are so many constraints like multiple anchors with the same name, and an anchor worked in many shows.
* I convert this big dataset to relevant data by applying filters like we have most of the news shows and by using the profession of an anchor.
* We want to show name, but due to big data, we cannot get the correct show name. So we think we need one more thing which connects the show and anchor and we found channels.
* Currently we don't have any dataset that contains all news channels with their respective shows, So we are working on that.

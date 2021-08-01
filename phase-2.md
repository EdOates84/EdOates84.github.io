## Updated on 16 July 2021

Frankie and I met on 16 July and discussed how to proceed because we are currently more than halfway through, So we mutually decided:


1. Integrate the results from the past two year's algorithm.
2. Write the final script, which will process all the videos that are present in the red hen's database.
3. Run the final script

## Updated on 21 July 2021

I have Integrated the results from the past two year's algorithm.
I have made the required changes in code to get the final results which you can see below image.

![img](https://user-images.githubusercontent.com/46043645/126490333-ebb453eb-cab0-48e0-b405-8e78b17cef78.png)


This file is in the RedHenLab's Rosenthal dataset format:

filename: 2006-01-02_00001057_1-2_CNN_Newsroom_Rosemary_Church.txt

**2006-01-02** is the airing date

**1-2** means there are two shows segmented by algorithm, or this is the file of 1st show.

**CNN_Newsroom** is a show name.

**Rosemary_Church** is the anchor name of the whole show.

In the last second line, all the confident hosts are present.

In the last line, all the majority networks are present.

## Updated on 23 July 2021

I have made more changes in the final algorithm because I don't want to drop the primary information/prediction of anchors from the show's text file. I have pushed all the code to the [GSoC-2021](https://github.com/EdOates84/GSoC-2021) repository.

Here is the updated image:
![Screenshot from 2021-07-22 19-09-59](https://user-images.githubusercontent.com/46043645/126740409-c20dbf3f-71cd-4b36-a52d-5a5169fe54d3.png)

Now I'm going to work on the final script.


## Updated on 27 July 2021

Frankie and I met on 23 July and discussed about the final scripts. He suggested using slurm, which processes all the tv shows and returns the text files.

Here is the segment_tv.py file, which iterates all the shows:


``` python
"""
This file is made specifically to work on the tv dataset present
on the CWRU HPC Cluster.

Recursively works on all .mp4 files present in the CWRU tv dataset.
"""
import os
from segment_video import segment_video
from os.path import join as join

dataset = '/mnt/rds/redhen/gallina/tv/'
split   = '/mnt/rds/redhen/gallina/TvSplit/'

for y in os.listdir(dataset):
    for y_m in os.listdir(join(dataset, y)):
        for y_m_d in os.listdir(join(dataset, y, y_m)):
            for video in os.listdir(join(dataset, y, y_m, y_m_d)):
                vid_path    = join(dataset, y, y_m, y_m_d, video)
                output_path = join(split, y, y_m, y_m_d) # Exact same tree structure as tv/ is to be used in TvSplit/

                if not os.path.exists(output_path): 
                    os.makedirs(output_path) # os.makedirs creates all missing directories in the path recursively

                try:
                    segment_video(vid_path, output_path)
                except:
                    print("Error segmenting {}, possible problems: \n1. Video is too small (<20 minutes)\n2. Video file_name doesn\'t follow the tv naming convention\n3. Video .txt3 file doesn\'t follow the tv format\n4. Raise an issue on github if any other error exists".format(video))
```

## Updated on 2 August 2021

Now We have written all the final scripts:
1. final_script.py
2. final_script.slurm
3. segment_tv.py

### final_script.py

``` python
"""
This file is made specifically to work on the tv dataset present
on the CWRU HPC Cluster.

Recursively works on all .mp4 files present in the CWRU tv dataset.
"""
import os
from os.path import join as join
import subprocess

dataset = '/mnt/rds/redhen/gallina/tv/'
split   = '/mnt/rds/redhen/gallina/Singularity/TvSplit/'
slurm_path = '/mnt/rds/redhen/gallina/Singularity/Show-Segmentation-2021/final_usable_code/final_script.slurm'
verbose = '--verbose'
MP4 = 'mp4'

for y in os.listdir(dataset):
    for y_m in os.listdir(join(dataset, y)):
        for y_m_d in os.listdir(join(dataset, y, y_m)):
            for video in os.listdir(join(dataset, y, y_m, y_m_d)):
                if MP4 in str(video):
                    vid_path    = join(dataset, y, y_m, y_m_d, video)
                    output_path = join(split, y, y_m, y_m_d) # Exact same tree structure as tv/ is to be used in TvSplit/

                    if not os.path.exists(output_path): 
                        os.makedirs(output_path) # os.makedirs creates all missing directories in the path recursively
                    cmd = 'sbatch {slurm_path} {vid_path} {output_path} {verbose}'.format(slurm_path=slurm_path, vid_path=vid_path, output_path=output_path, verbose=verbose)
                    subprocess.run([cmd])
                else:
                    pass
```

### final_script.slurm

``` slurm
#!/bin/bash
#SBATCH -o test.o%j
#SBATCH --time=1-00:00:00
#SBATCH -mem=8gb     
#SBATCH -N 1                 
#SBATCH -n 1                 
module load singularity
singularity exec -B /mnt/rds/redhen/gallina/Singularity/Show-Segmentation-2021/show-segementation-2021_latest.sif python3 segment_tv.py $1 $2 $3
```

### segment_tv.py

``` python
import sys
from segment_video import segment_video

vid_path = sys.argv[1]
output_path = sys.argv[2]
verbose = sys.argv[3]

try:
    segment_video(vid_path, output_path, verbose)
except:
    print("Error segmenting {}, possible problems: \n1. Video is too small (<20 minutes)\n2. Video file_name doesn\'t follow the tv naming convention\n3. Video .txt3 file doesn\'t follow the tv format\n4. Raise an issue on github if any other error exists".format(vid_path))

```


The flow is, first of all, we need to take input so the **final_script.py** looping all the input videos and call **final_script.slurm** it will handle all the jobs and memory, then this slurm file call **segment_tv.py** file to execute the final function, which segments the video and stores it. 

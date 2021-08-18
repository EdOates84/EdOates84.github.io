# Final Submission

Majorly I worked on finding anchors, shows, channels probable and confident both or added in the final text file. Implemented the final production pipeline using python scripts and slurm to handle all the jobs submissions and output text files. I have tested my algorithm on HPC with extensive data of **7 months**. It took 5 continuous days/night to process **10k+ videos** and generate .txt file and .mp4(segmented video).
 
> **Path of Output files:** [/mnt..gallina/Singularity/Show-Segmentation-2021/TvSplit_2]()

> **Project Code:** [Show-Segmentation-2021](https://github.com/EdOates84/Show-Segmentation-2021)

> **Weekly Updated Blogs:** [Blogs](https://edoates84.github.io/)

## Here is the final production pipeline flow:

![Supervisor@2x](https://user-images.githubusercontent.com/46043645/129532906-cedbbc32-90cd-4982-8809-87f44da5799d.png)


## Results & Output

I spent a lot of time running algorithms and getting final .txt files at CaseHPC; this was very time-consuming. 
> The processing of a **single video** takes **40 to 50 min** on average.

> I spent **3 days/night** to achieve **4 months'** output.

> The **estimation** for the whole collection is **approx 180 days**.

### Examples of final .txt files:

#### Example 1 : 2015-12-05_France-2_2-2_unknown-anchor.txt

>TOP|20151205000000|2015-12-05_France-2_2-2_unknown-anchor<br>
COL|Communication Studies Archive, UCLA<br>
UID|11dc0427-f4b5-4997-816f-d8a01c729aa1<br>
SRC|Rosenthal Collection, UCLA<br>
TTL|<br>
PID|<br>
CMT|<br>
DUR|22:43:43<br>
VID|640x480<br>
LAN|ENG<br>
LBT|<br>
OVD|20151205000000|2015-12-05_0600_FR_France-2_Télématin_speciale_Telethon_2015<br>
OID|<br>
TMS|01:16:17-00:00:00<br>
INF|probable_host1:Grant-Tinker_Orson-Bean_Joe-E.-Tata_Al-Hunt_Pat-Boone<br>
Confident Anchors|Al-Hunt_<br>
Network|CBS_NBC_CNN_PBS_<br>
Probable Shows| <br>
{}<br>
Shows|Charlie_Rose<br>


#### Example 2 : 2015-12-05_KCET_1-1_Sue_Herera.txt

>TOP|20151205000000|2015-12-05_KCET_1-1_Sue_Herera<br>
COL|Communication Studies Archive, UCLA<br>
UID|a799196c-b03d-4162-8e4d-006b5be19583<br>
SRC|Rosenthal Collection, UCLA<br>
TTL|<br>
PID|<br>
CMT|<br>
DUR|00:00:00<br>
VID|640x426<br>
LAN|ENG<br>
LBT|<br>
OVD|20151205000000|2015-12-05_0130_US_KCET_Nightly_Business_Report<br>
OID|<br>
TMS|00:00:00-00:00:00<br>
INF|probable_host1:Sue-Herera_Elizabeth-Ashley_Crown-Prince-Dan_Emma-Cleasby_Christina-Strmer<br>
Confident Anchors|Sue-Herera_<br>
Network|CBS_NBC_<br>
Probable Shows| <br>
{}<br>
Shows|Nightly_Business_Report_with_Sue_Herera_and_Bill_Griffeth<br>


#### Example 3 : 2015-12-05_SIC_1-1_Cau_Reymond.txt

>TOP|20151205000000|2015-12-05_SIC_1-1_Cau_Reymond<br>
COL|Communication Studies Archive, UCLA<br>
UID|f39b2c74-1471-48fe-9e51-ffd0fd3cf1b2<br>
SRC|Rosenthal Collection, UCLA<br>
TTL|<br>
PID|<br>
CMT|<br>
DUR|23:55:45<br>
VID|640x512<br>
LAN|ENG<br>
LBT|<br>
OVD|20151205000000|2015-12-05_2300_BR_SIC_A_Regra_do_Jogo<br>
OID|<br>
TMS|00:04:15-00:00:00<br>
INF|probable_host1:Cau-Reymond_Seth-Tobias_Al-B.-Sure!_David-Guterson_Cha-Seung-won<br>
Confident Anchors|Al-B.-Sure!_<br>
Network|ABC_<br>
Probable Shows| <br>
{}<br>
Shows|Black_Men_Revealed<br>


### Examples of Show analytics for each 1 month data

These plots give an overall view of shows like No. of episodes of the show on the x-axis and the count of those episodes on the y-axis.

**Example:** This is the dictionary that contains show name and their occurrence.

{'Charlie_Rose': 6, 'Worldwide_Exchange': 2, 'The_Hot_List': 1, 'The_Ricki_Lake_Show': 1, 'Access_Daily': 2}

| x-axis      | y-axis(count) |
| ----------- | ----------- |
| 1           | 2           |
| 2           | 2           |
| 6           | 1           |

#### Example 1 : 2015-06

![2015-06](https://user-images.githubusercontent.com/46043645/129609108-0b875841-1b6a-4f19-993e-4ddf5efd7d77.png)


#### Example 2 : 2015-12

![2015-12](https://user-images.githubusercontent.com/46043645/129609090-d3a7d453-c662-493b-af79-cf4882c3490f.png)


#### Example 3 : 2015-01

![2015-05](https://user-images.githubusercontent.com/46043645/129609126-a701f910-9b81-42ce-9122-569a4e30c78e.png)


## Future work
> If possible, replace the current celeb detection method with Azure’s Computer Vision service.

> Currently the most time consuming process in the program is that of going frame by frame and extracting faces. This can be speed up using multi-threading or any other means possible.

> Explore the dataset that contains news shows with anchors and include it in the pipeline.


## Acknowledgments

I want to thank my mentors [Frankie Robertson](http://frankie.robertson.name/), [Francis Steen](https://comm.ucla.edu/person/francis-steen/), and [Anna Wilson](https://www.rees.ox.ac.uk/people/dr-anna-wilson). Special thanks to Frankie. He was very responsive and helpful all along. We talked through email and meet on zoom, google meet. He gave valuable insights whenever I was stuck or something that I could have done better.

Lastly, I would like to thank **Mark Turner and all other Red Hen Lab members** for their support.

And most importantly, I express my gratitude to the **people behind Google Summer of Code**. I had a delightful experience working in both GSoC 2020 and 2021. **I hope I keep contributing.**



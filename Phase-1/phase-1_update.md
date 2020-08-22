## Anchor Detection

By using face recognition, we are getting multiple persons with any profession, but we want only news anchors- 
* After exploring the whole IMDB dataset, we don't get professions of any anchors. 
* After a lengthy discussion and research, we got a Wikipedia API which will provide us all the necessary information.

Suppose we are getting five persons or prediction for a given show
* We have to check each person's professions, whether he/she is an anchor/host/journalist/presenter, etc.
* I wrote code for the check profession and got only one anchor from 5

<b>Code link - </b><a href="https://github.com/EdOates84/Show-Segmentation/blob/master/Phase-1/Get_Anchor.ipynb">Anchor Detection</a>

## Channel Detection
Next, we move on to finding a channel from the list of anchors-

In the process of finding the channel name-

There are two ways to get channels 
* By using subtitles- After the checking of whole Rosenthal dataset we don't have all subtitles files there are only 40-50% files which is useful for us, but we can't generalize it so we can choose next method to finding the channels.  

* By using Wikipedia content page - after research, we have a list of channels or networks. Then, the first check in this given channel is present in the anchors Wikipedia then store that channel or networks. Like this store all channels from each anchor of videos and then take commonly from these to finding the correct channel or network.

<b>Code link - </b><a href="https://github.com/EdOates84/Show-Segmentation/blob/master/Phase-1/Get_Channels.ipynb">Channel Detection</a>

Next, we move on to finding shows by using anchor name and IMDB-




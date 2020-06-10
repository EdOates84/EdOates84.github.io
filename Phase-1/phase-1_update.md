### Phase-1 Update

By using face recognition, we are getting multiple persons with any profession, but we want only news anchors- 
* After exploring the whole IMDB dataset, we don't get professions of any anchors. 
* After a lengthy discussion and research, we got a Wikipedia API which will provide us all the necessary information.

Suppose we are getting five persons or prediction for a given show
* We have to check each person's professions, whether he/she is an anchor/host/journalist/presenter, etc.
* I wrote code for the check profession and got only one anchor from 5

Next, we move on to finding a channel from the list of anchors

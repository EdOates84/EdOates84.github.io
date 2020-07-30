# Process of getting Networks

Now we are getting the show's exact network with the help of all probable hosts that is present in the whole video. We are using the voting method to find the correct network.


Example: We have seven shows in a particular video and get all anchors from that video. Using Wikipedia API, we get the wiki page of each anchor, and then we can easily search his/her networks.

let's say A, B, C, D, E are the different networks getting from each anchor  
{'A': 5, 'B': 4, 'C': 8, 'D': 4, 'E': 5}    
then C is the most voted network. C is the final network of that video.


Now we have correct anchors and correct networks of the video with us.


# Process of getting shows

We are using IMDb Dataset because it contains all information regarding a show. 
### Get_nconst
nconst (string) is a unique alphanumeric identifier of the name/person
In case of multiple nconst like dataset contains multiple anchors from the same name for this we are using filters
only consider those shows that aired during pull year
only take nconst who have news-related (Talk-shows and news genre) shows
at least one title must be of US region
Get_tconst
tconst (string) is a unique alphanumeric identifier of the title
take all titles for a particular nconst
Get_Shows
We are union all tconst associate with a particular nconst like by title_crew, known for the title.
If multiple shows like an anchor worked in many shows for this, we are using filters
only consider those shows that aired during pull year
only take nconst who have news-related (Talk-shows and news genre) shows
All shows from US region
only taking tv-series
end year of the show should be higher than pull year
starting year of the show should be less than pull year
checking title name in subtitle files
checking network of show
* By using these filters, we are getting the exact show in case of our probable host is correct 

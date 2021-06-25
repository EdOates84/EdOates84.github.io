In last week I mainly researched and explored the MediaWiki library. I have tried some different algorithms and getting the response. But I'm having trouble while using SPARQL, and I'm not able to use it. But most needed data I'm getting from the different implementation of MediaWiki.

This code will give us all information about the anchor which we provided in the input.

``` python
import requests

url = "https://www.wikidata.org/w/api.php"


while True:
    query = input("Enter name : ")
    if query == "quit":
        break
    else:
        params = {
        "action" : "wbsearchentities",
        "language" : "en",
        "format" : "json",
        "search" : query 
        }
        try:
            data = requests.get(url,params=params)
            print(data.json()["search"])
        except:
            print("Invalid Input try again !!!")
```

So, The main problem is in the current algorithm; we are getting 10 to 15 anchors of a single show. Generally, that is not possible because we have mostly News related show it may contain 2, 3 anchors maximum.

In this meeting, I also want to talk about the image(face) processing so that we can get relevant faces, not the bunch of other faces, because the MediaWiki and the anchor information is the second thing we need to focus on anchor detection. After all, it is the nerve of our project.

These are the result which we are getting from different approaches like from code and manually also.
![img](https://user-images.githubusercontent.com/46043645/123373639-53f6c980-d5a3-11eb-8108-52f6d6dd7650.png)

After Examine these results, I have noted some points:
* We are getting accurate anchors in 50 to 60% shows.
* In some shows, our code predicts wrong anchors, which are not even present in the whole video itself.
* Show name detection code works fine, but it is dependent on anchors.

So we decided to go through the Sasi Kiran(GSoCer'19) and find why we are getting the wrong anchors and its reason.

I have gone through his code; it took a lot of time because it's not that easy to debug someone's code and logic which he used at that time to achieve any goal. After debugging the code, I found some lead and a vision of where we should go, which we will discuss in the meeting.



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


After a lengthy discussion with Frankie in the last meeting (6th July), He suggested some broader alternatives. 
He offered to work parallelly on Sasi's code and prepare a dataset from the wiki data.


1. Sasi's code:


    Working on Sasi's code and logic is not that easy for me because last year, I was not working on his code, only adding more functionality to his code. So for more understanding, I have scheduled multiple calls with him and understand his code sothat I found some lead, and I figured it out, but the implementation was a bit lengthy and required some research from my side. That's what I'm doing.

    Sasi's code is lengthy. You can see it here: https://github.com/eonr/ShowSegmentation/blob/master/final_usable_code/Final_notebook.ipynb


2. Prepare dataset from the wiki data:

    I have successfully prepared a dataset from wiki data and downloaded it in json format, and the sample result is here:


``` json
[{
    "person": "http://www.wikidata.org/entity/Q3056623",
    "personLabel": "Erin Burnett",
    "birthDate": "1976-07-02T00:00:00Z",
    "workPeriod": "2003-01-01T00:00:00Z",
    "image": "http://commons.wikimedia.org/wiki/Special:FilePath/Erin%20Burnett%20-%20small.jpg"
}, {
    "person": "http://www.wikidata.org/entity/Q3106112",
    "personLabel": "Gilles Bouleau",
    "birthDate": "1962-05-25T00:00:00Z",
    "workPeriod": "1986-01-01T00:00:00Z",
    "image": "http://commons.wikimedia.org/wiki/Special:FilePath/Gilles%20Bouleau%20Cannes%202016.jpg"
}, {
    "person": "http://www.wikidata.org/entity/Q3124024",
    "personLabel": "Gérard Holtz",
    "birthDate": "1946-12-08T00:00:00Z",
    "workPeriod": "1972-01-01T00:00:00Z",
    "image": "http://commons.wikimedia.org/wiki/Special:FilePath/G%C3%A9rard%20Holtz.JPG"
}, {
    "person": "http://www.wikidata.org/entity/Q3131980",
    "personLabel": "Henri Sannier",
    "birthDate": "1947-09-07T00:00:00Z",
    "workPeriod": "1973-01-01T00:00:00Z",
    "image": "http://commons.wikimedia.org/wiki/Special:FilePath/Henri%20Sannier.jpg"
}, {
    "person": "http://www.wikidata.org/entity/Q3236790",
    "personLabel": "Lester Holt",
    "birthDate": "1959-03-08T00:00:00Z",
    "workPeriod": "1981-01-01T00:00:00Z",
    "image": "http://commons.wikimedia.org/wiki/Special:FilePath/Lester%20Holt%20by%20Gage%20Skidmore.jpg"
}, {
    "person": "http://www.wikidata.org/entity/Q3241332",
    "personLabel": "Linda Ellerbee",
    "birthDate": "1944-08-15T00:00:00Z",
    "workPeriod": "1964-01-01T00:00:00Z",
    "image": "http://commons.wikimedia.org/wiki/Special:FilePath/Linda%20Ellerbee.jpg"
}]
```

I have tested the code in hpc cluster with some of inputs and the code is perfectly working there without any issues.

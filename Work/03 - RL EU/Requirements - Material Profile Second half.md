Screen : 
Material Profile > User created 
Once we apply the filters 
We get a table called : Details table 

This is how it looks : 


Requirement : 
1. I want the same table below the details table , data with the same API 
2. That table name should be instead of Details Table it should be : IA Product Profile Edits
This is temporary , so this new table API is not yet done by the backend engineer , once that is given to me , so I have to change the API end point.

For now , 
- Check where the API endpoints are listed and mentioned 
- Please create the same end point with the different name similar to what we are doing take reference from the details table API name constant. 

Later once the API is given to me by the backend engineer , I will just change the end point , so that would be really helpful for me. 
Can you please plan it accordingly and help me do it , thanks 



![[../../attachments/Requirements - Material Profile Second half - user created UI.png]]

If we click on any product profile , it opens store contributions table for that product profile 
so the new table should also have the store contribution 

1. can you please check that it should be same for the store contribution table , only the payload should change and hence we can call and get the API data 
2. Please check how to make it some client specific , like some key if we can use from the API response and only to those it should show the new table and for other's it should not show the new table and it should be how it is , you can check , how old one was there 
3. Other clients should not be afffected with this change , only to some clients , how can we make this only for some clients we want , any key from the API or the configurations you can suggest 

Please go through the old code by checking the previous commits and then try to make it aligned , thanks 

payload -> new key -> 

`iaclone`
`userCreated`

kaha kaha call ho raha hai , us hisaab 
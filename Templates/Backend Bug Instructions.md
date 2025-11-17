
##### The issue description : 

##### The API which is causing the issue from the network browser , The CURL :
```

```

##### The Response in the network tab response / datadog or grafana 
```plain text

```


##### The logs after calling the API in the local : 
```plain text 

```

##### The Database findings : 
###### The SP which is getting called found from the local logs : 
```sql

```

###### The Database findings : 
```sql 

```

##### Repos to look at : 

###### core backend : 
```
/Users/rahulmishra/Desktop/mtp-core-backend/backend
```
- Backend code related core and to the API is written inside mtp-core-backend 
- There is one utils file which is being used to execute everything related to data like -> Executing a query , Executing a stored procedure and etc. 
- This utils file is installed from mtp-utils repo which is mentioned in the toml file so you can check this as well , if you would like or of any help : 
``` 
/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-zfxLRh0v-py3.12/lib/python3.12/site-packages/database/utils.py
```

###### mtp-database : 
```
/Users/rahulmishra/Desktop/mtp-database
```
- All the stored procedure which are being called in the API is stored here inside the folder of functions 
- Configurations are stored here in the form of csv. 
- The data for each client is seperated by the folder for example right now we are working with the `ralph_lauren_na` , so functions and the config for this client is stored in here 
- If some function is not present then it must be taking from the : `/Users/rahulmishra/Desktop/mtp-database/database/schemas/global/functions` -> common for everyone 
- So if we want to make something client specific we can take it from - `/Users/rahulmishra/Desktop/mtp-database/database/schemas/global/functions` and create the function inside the client or tenant folder

###### inventory backed : 
```
/Users/rahulmishra/Desktop/mtp-inventorysmart-backend/backend
```
- Inventory backend code and API is present in the repo 
- There is one utils file which is installed from the toml file : This utils file is for the execution and everything related to database query and formation , you can check this as well : 
	```path title:utils-path
	/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/database/utils.py
	```

##### Note : 
- So the backend is mtp (multi-tenant platform) which means single codebase is being used by multiple clients 
- So single change in the codebase can affect all the client in the bakcend 
- Hence , Most of the logic is handled with Store Procedure (SP) inside the mtp-database 
- Each client have their own folder where the configurations data in the form of `csv` is stored , SP in the form of `.sql` and in the SP function we mostly handle the client specific logic. One such example of configuration is : `tenant_attribute_master.csv` where tenant specific configurations are present. 
- Some SP are stored in the `global` schema which means are common for all the clients.
- I work with `signet` client. 
- Sometime the global SP we are using is not aligned with our client so we have to make that specific file in our folder and then make the changes and use , that will have the preference over the global outside schema. 


##### Request 
1. Please check the curl I have given , from that : 
	1. Please check the end point of the API 
	2. Payload by which we are calling and the filters in the payload
2. Please check the backend repo properly 
	1. check the entire flow of the API 
	2. And find out the logic as how things are working
	3. At what point it is breaking , check it from the logs as well. 
3. Please check the stored procedure involved and try to find out the logic or the error
4. If error logs are given please check those and try to find out the solid RCA
5. I want you to find out the problematic part of the code and the piece of code which is throwing error or causing the issue.
6. If you would like to debug more efficiently for some difficult bug , you can also suggest me the places to add the breakpoints in the backend codebase to stop the execution of the code and check the value , which I can provide you. 
7. Please go step by step and go deep and try to find out the root cause of the issue.





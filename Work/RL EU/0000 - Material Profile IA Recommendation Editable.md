---
feature: ../../attachments/00 - Material Profile IA Recommendation Editable - material Profile screen.png
---
#index 
****
The branch : 
```plain text
MTP-110375-Material-Profile-Editable
```

### The UI flow
There is a screen called Material Profile , I am attaching screenshot on the way , the screen looks like : 
![[../../attachments/00 - Material Profile IA Recommendation Editable - material Profile screen.png|700]]
Then next user can select filters which looks like this : 
![[../../attachments/00 - Material Profile IA Recommendation Editable - filters screen.png]]
Then a details table comes in the UI with the values which looks something like this : 
![[../../attachments/00 - Material Profile IA Recommendation Editable - details table.png]]
Now if we click on the material number , it opens a new table below 
So here If I click on the material number : 830903657001
It opens a new table below for that which is called as Store Contributions 
![[../../attachments/00 - Material Profile IA Recommendation Editable - store contribution.png|800]]
Overall table structure looks something like this , the columns in it : 
![[../../attachments/00 - Material Profile IA Recommendation Editable - store contribution table columns.png|300]]
### Logic High Level
There are two main things : 
1. Product Profile Pen % 
2. Overall Proportion %

###### Product Profile Pen % 
So if you check this : 
![[../../attachments/00 - Material Profile IA Recommendation Editable - product profile pen perc.png]]
- Each store has different size and then the product is distributed in the sizes like 
	- 1 - Size - 1 
	- 2 - Size - 2
	- 3 - Size - 3 
	- 11 - Size - 11 
	- 12 - Size - 12 
	- 13 - Size - 13 
- So in these sizes the product is distributed at each store level 
If we take example of one store : 
Store -> MADRID CHILDRENS
![[../../attachments/00 - Material Profile IA Recommendation Editable - single store example.png]]
So here : 
- 1 - Size - 1 = 0.62
- 2 - Size - 2 = 42.37
- 3 - Size - 3 = 49.7
- 11 - Size - 11 = 0
- 12 - Size - 12 = 7.3
- 13 - Size - 13 = 0.02
So now for the store MADRID CHILDRENS , if we add all the size values it should be always 100 (0.62 + 42.37 + 49.7 + 0 + 7.3 + 0.02) 

So this first column is at each store level and then we are distributing the sizes at each store and at the end the sum should be 100 % as this is percentage. 

###### Overall Proportion %
Now if you see the overall proportion % column 
You can see at the top it is 100% 
So the product profile which I clicked , how is that distributed at the stores 
Which stores has how much percentage , it denotes that. 
Which means , the material : 830903657001 is there in MADRID CHILDRENS -> 16.11% 
So this addition of percentage happens vertically. 
How much product is allocated to each store. 
![[../../attachments/00 - Material Profile IA Recommendation Editable - Overall proportion perc.png]]


- So now the requirement was , users want this IA recommended to be editable 
- And after the editing we should run some validation on the Product Profile Pen % and Overall Proportion % 
- Vertically and horizontally it should be 100% 
- and if that is perfect , we should move to the next step with a pop up for creation of the new material profile asking - name and description 
- These changes are already implemented , but I want you to -> 
	- Check the current percentage , how much decimal it is being rounded off 
	- According to that if our validation is in place or need some changes , because in some cases even without changing anything it should the sum is 99.99% and not passing the validation so make it aligned with the current handling of the decimal and all 
- And please check if our implementation is correct till now or not 

[[Changed Documentation - Material Profile]]
[[Complete Implementation Plan ]]
[[Rohan Handover]]

--- 
[[00 - Material Profile second half doc]]
[[changes done]]

---
[[Flags need for Material Profile]]

--- 

## Main things 
[[First Half - Validation + Save API]]
[[Second Half - Listing new table ]]
[[Configurations - Material Profile]]
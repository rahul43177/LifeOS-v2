The context : 
So basically I use obsidian for taking down the notes.
- Which creates the notes in the md format in my local.
- So as a software developer I thought of backing up my notes and entire vault in the github using `git init` command and then it will be safe there. 
- Then another problem arises -- how to sync it to my phone -- so I put the folder inside the iCloud , now my phone is also in sync with the laptop notes and then I downloaded the iCloud in windows PC as well. 
- So all my notes are now synced. 

The problem : 
1. So today I checked my iCloud drive which says notes folder / vault size is ~200mb 
2. I was wondering these md files are so huge ? 
3. Then something striked in my mind , maybe attachments are taking these spaces -- but attachment is also ~40 mb only 
4. Then I found that `.git` folder is taking 130 mb of my iCloud and entire folder -- which does not make any sense 

Why is this folder so big ? 
And is there any way to reduce the file size of this .git folder
I want to keep my workspace json changes and .obsidian changes pushed because if later in new device I clone this -- i will have all the configurations with me. 

Tell me : 
1. Why is it so big ? 
2. How to reduce this ?
3. For future what should I keep in mind ? To maintain it at less size! 
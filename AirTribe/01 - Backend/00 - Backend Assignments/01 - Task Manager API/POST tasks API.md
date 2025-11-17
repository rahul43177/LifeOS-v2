> Objective -- To create a new task with the required fields (title, description, completed).

#### Things need to be done
1. Postman will send the body according to the `model` 
2. We receive the body in a variable from - `req.body` called `newTaskData` or something like this
	1. We should also check weather the data is there or not -- as a validation 
	2. Also we should check all the details like title description and all are present or not 
	3. If **completed** is not there -- by default we should take it as false 
3. We add the new task data in the model or the in memory array we have created
4. And send the newly created data as well as the updated entire data -- or should we not ! 


#### Code 
```javascript 

const createNewTask = async (req, res) => {
  try {
    const { title, description, completed = false } = req.body; //by default completed is false 
    
    if(!title.trim() ||!description.trim()) { //validations 
        return res.status(400).json({
            status : false , 
            message : "Title and Description are required fields"
        }) 
    }
    
    //ensuring the completed is boolean 
    if(typeof completed != boolean) {
        return res.status(400).json({
            status : false , 
            message : "The completed can only be a boolean" 
        })
    }

    const newTask = {
        id : Date.now().round(2) , 
        title : title.trim() , 
        description : description.trim() , 
        completed
    }

    tasksData.push(newTask);
    return res.status(201).json({
        status : true , 
        newData : newTask , 
        entireData : tasksData  
    })
  } catch (error) {
    return res.status(500).json({
      status: false,
      error : error.message,
    });
  }
};
```

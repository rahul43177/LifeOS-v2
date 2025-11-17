#### Description : 
1. We just need the id from the **Path Parameter** 
2. We will find that id in the array -- we find the index using `indexOf` 
3. We remove that entry using [[../../04 - JavaScript Deep Dive/Splice Method|Splice Method]] 
4. Few validations as well we will put

#### Code 
```js title:deleteTaskAPI.js
const deleteTaskFromId = async (req,res) => {
  try { 
    let {id} = req.params; 
    if(!id) {
      return res.status(400).json({
        status : false , 
        message : "Please enter the ID" 
      })
    } else {
      id = Number(id) //converting it into the number 
    }
    // //my way -- old 
    // //finding that id and deleting/filtering it out 
    // //finding the id 
    // const taskId = tasksData.find((data) => {
    //   return data.id === id; 
    // })
    // if(!taskId) {
    //   return res.status(404).json({
    //     status : false , 
    //     message : "The ID not found" 
    //   })
    // }
    // let updatedData = tasksData.filter((singleTask) => {
    //   return singleTask.id !== id ; 
    // }) 
    // tasksData = updatedData;

    //new way -- 
      //we find the index
      //mutate the array manually using slice 

    const index = tasksData.findIndex(task => task.id == id);
    if(index == -1) {
      return res.status(404).json({
        status : false , 
        message : "The id not found" 
      })
    }
    if(!index) {
      return res.status(404).json({
        status : false , 
        message : "The ID not found"
      })
    }
    const removedTask = tasksData.splice(index , 1) ;
    


    return res.status(201).json({
      status : true , 
      message : `The task with ID - ${id} has been deleted successfully` , 
      totalTasks : tasksData.length ,
      deletedTaskData : tasksData , 
      removedTask
    })
    
  } catch(error) {
    return res.status(500).json({
      status : false , 
      error : error.message 
    })
  }
}
```

- Here I have done my part first using filter 
- But finding index and changing the original array done using splice , this is also nice. 
- Whenever we want to change something - use [[../../04 - JavaScript Deep Dive/Splice Method|Splice Method]]



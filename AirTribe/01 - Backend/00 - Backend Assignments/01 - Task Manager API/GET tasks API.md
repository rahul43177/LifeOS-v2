> Retrieve all tasks from the in memory database

```js 
const tasksData = require("../model/taskManagerDatabase");

const getAllTasks = async (req , res) => {
    try {
        //whatever the data is present in the tasksData -- entire data we need to send
        res.status(200).json({
            status : true , 
            message : "All tasks data fetched" , 
            data : tasksData
        })
    } catch(error) {
    }
}

module.exports = {
    getAllTasks , 
}
```

So basically , I just sent the entire `tasksData` into the response, that's it . simple and clean. 

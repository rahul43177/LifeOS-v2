> Retrieve a specific task by its ID.  

#### Description : 
User will put the id in the postman -- using the [[../../05 - NodeJS/Path Parameter|Path Parameter]]

#### Approach 
- We will destructure the value of the id from the params.
- Use the filter method of the arrays to filter the id user wants 
- Send it in the response 

Three things here : 
- [ ] Destructuring 
- [ ] Filter the task based on the ID from array 
- [ ] Send in the response 

#### Learning on the way : 
- `req.params` -> gives the data in the **key-value pair** - 
- API looks something like this : 
- `router.get("/:id", getTaskFromId);`
- And I called the API like : 
- `localhost:3000/tasks/3` 
- and then when I printed the `req.params`
- I got the in the console as : ->  `{ id: '3' }`

- So i can take the id with two ways  -> 
	- `const id = req.params.id`
	- `const {id} = req.params`
- One more observation , whatever we are passing in the `req.params` that is being passed in ***string***
- So anywhere if we want to use the number -- we would need to convert it.

#### Final  Code 
```js
const getTaskFromId  = async (req , res) => {
    try { 
        let {id} = req.params; 
        if(!id) {
            return res.status(400).json({
                status : false , 
                message : "Please enter the id" 
            }) 
        }
        id = Number(id);  //converting it into the number as -- path params are by default passed as strings -- and in our model we have int id 
        
        const taskById = tasksData.find((singleTask) => {
            return singleTask.id === id ; 
        })

        if (!taskById) {
            return res.status(404).json({
                status : false , 
                message : "Task not found" 
            })
        }

        return res.status(200).json(taskById)

    } catch(error) {
        return res.status(500).json({
            status : false ,
            error : error 
        })
    }
}
```



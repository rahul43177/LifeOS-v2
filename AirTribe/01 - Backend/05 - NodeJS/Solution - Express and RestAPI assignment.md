## index.js or app.js 
```js 
const express = require("express")
const app = express()
const courseRouter  = require("./routes/courseRouter")
const PORT = 3000; 
app.use(express.json())


//routes 
app.use("/course" , courseRouter);

app.listen(PORT , () => {
    console.log(`The server is running on the port : ${PORT}`)
})
```

## courseRouter.js 
```js
const express = require("express");
const router = express.Router();
const {
  getCoursesByCategory,
  getCourseById,
  addCourseInDB,
  updateCourses,
  deleteCourse
} = require("../controller/coursesController");

//courses based on category
router.get("/category-course", getCoursesByCategory);

//courses by id
router.get("/course-id/:id", getCourseById);

//add course in DB
router.post("/add-courses", addCourseInDB);

//update course by id
router.put("/update-course/:id", updateCourses);

//delete the course 
router.delete("/delete-course/:id" , deleteCourse);
module.exports = router;
```



## courseController.js 
```js 
const coursesDB = [
  {
    id: 1,
    courseName: "NodeJs Course",
    courseDescription: "Master the backend",
    category: "backend",
  },
  {
    id: 2,
    courseName: "ReactJs Course",
    courseDescription: "Master the frontend",
    category: "frontend",
  },
  {
    id: 3,
    courseName: "Database course",
    courseDescription: "Master the database",
    category: "backend",
  },
  {
    id: 4,
    courseName: "System Design Course",
    courseDescription: "Master the System Design",
    category: "Engineering",
  },
  {
    id: 5,
    courseName: "Data Structures and Algorithms Course",
    courseDescription: "Master the DSA",
    category: "Fundamentals",
  },
  {
    id: 6,
    courseName: "Mock Interview Course",
    courseDescription: "Master the technical interviews",
    category: "Fundamentals",
  },
  {
    id: 7,
    courseName: "High Level Design Course",
    courseDescription: "Master the HLD interviews",
    category: "Backend",
  },
  {
    id: 8,
    courseName: "Low Level Design Course",
    courseDescription: "Low Level Design Course",
    category: "Backend",
  },
  {
    id: 9,
    courseName: "CSS Mastery",
    courseDescription: "Master the CSS for best UI",
    category: "Frontend",
  },
  {
    id: 10,
    courseName: "Database Management System",
    courseDescription: "Master the DBMS as a DBA",
    category: "Backend",
  },
];

const getCoursesByCategory = async (req, res) => {
  try {
    const { category } = req.query;
    if (!category) {
      return res.json({
        status: true,
        courseData: coursesDB,
      });
    } else {
      const filteredData = coursesDB.filter(
        (singleCourse) =>
          singleCourse.category.toLowerCase() == category.toLowerCase()
      );
      res.json({
        status: true,
        courseData: filteredData,
      });
    }
  } catch (err) {
    res.json({
      status: false,
      erorr: err.message,
    });
  }
};

const getCourseById = async (req, res) => {
  try {
    const { id } = req.params; //path parameter -> single value -> telling which value we need. this is path parameter.
    if (!id)
      return res.status(400).json({
        status: false,
        message: "Id is not provided",
      });

    const filteredData = coursesDB.filter((singleCourse) => {
      return singleCourse.id == id;
    });
    if (filteredData.length == 0) {
      return res.status(404).json({
        status: false,
        message: "Id does not exist",
      });
    }

    return res.json({
      status: true,
      courseData: filteredData,
    });
  } catch (error) {
    return res.json({
      status: false,
      error: error,
    });
  }
};

const addCourseInDB = async (req, res) => {
  try {
    const courseDetails = req.body;
    if (!courseDetails || courseDetails.length == 0) {
      return res.status(400).json({
        status: false,
        message: "The course details are not provided",
      });
    }
    //finding the highest id
    let highestId = Math.max(...coursesDB.map((course) => course.id));

    const newCoursesData = [];
    courseDetails.forEach((course) => {
      highestId += 1;
      const newCourse = {
        id: highestId,
        name: course.name,
        courseDescription: course.courseDescription,
        category: course.category,
      };
      coursesDB.push(newCourse);
      newCoursesData.push(newCourse);
    });

    return res.status(201).json({
      status: true,
      message: "Course data added successfully",
      newCoursesData,
      entireCourseData: coursesDB,
    });
  } catch (error) {
    return res.json({
      status: false,
      error: error,
    });
  }
};

const updateCourses = async (req, res) => {
  try {
    const { courseName, courseDescription, category } = req.body;
    const { id } = req.params;

    coursesDB.forEach((course) => {
      if (course.id == id) {
        if (courseName) {
          course.courseName = courseName;
        } else if (courseDescription) {
          course.courseDescription = courseDescription;
        } else if (category) {
          course.category = category;
        }
      }
    });
    const updatedCourse = coursesDB.filter((course) => course.id == id);

    return res.status(200).json({
      status: true,
      message: "The course data is updated successfully",
      updatedCourse,
      allCourse: coursesDB,
    });
  } catch (error) {
    console.log(error);
    return res.status(500).json({
      status: false,
      errorMessage: error,
    });
  }
};

const deleteCourse = async (req, res) => {
  try {
    const {id} = req.params; 
    
    if(!id) return res.status(400).json({
        status : false , 
        message : "Id is not provided to delete the course"
    }) 

    const newData = coursesDB.filter((course) => {
        return course.id != id ; 
    })

    if(newData.length == coursesDB.length) {
        return res.status(400).json({
            status : false , 
            message : "The id you gave does not exist" 
        })
    }
    let OG =  coursesDB.length
    let newC = newData.length
    return res.status(200).json({
        status : true , 
        message : "The course has been deleted successfully" , 
        newData , 
        recordsDeleted : OG-newC
    })
    
  } catch (error) {
    console.log("error", error);
    return res.status(500).json({
      status: false,
      error: error,
    });
  }
};
module.exports = {
  getCoursesByCategory,
  getCourseById,
  addCourseInDB,
  updateCourses,
  deleteCourse
};

```


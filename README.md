# Contoso University
Tutorial: Get started with EF Core in an ASP.NET MVC web app

[Documentation](https://docs.microsoft.com/en-us/aspnet/core/data/ef-mvc/intro?view=aspnetcore-6.0)

## Static Files
[Jumbotron](https://getbootstrap.com/docs/4.0/components/jumbotron/) not working with default libraries.
- Install bootstrap-4.0.0 and extract to wwwroot folder
![image](https://user-images.githubusercontent.com/58488875/169333339-8b6ec171-f3d5-4bae-9b3b-3fc1b3615532.png)

## Data Models
A one-to-many relationship between Student and Enrollment entities. A student can be enrolled in any number of courses.
A one-to-many relationship between Course and Enrollment entities. A course can have any number of students enrolled in it.

![image](https://user-images.githubusercontent.com/58488875/169336135-50988fa6-98d7-4d07-98f4-1d9a5c7ed2be.png)

- Student
```
public class Student
    {
        public int ID { get; set; }
        public string LastName { get; set; }
        public string FirstMidName { get; set; }
        public DateTime EnrollmentDate { get; set; }

        public ICollection<Enrollment> Enrollments { get; set; }
    }
```
- Enrollment
```
public enum Grade
    {
        A, B, C, D, F
    }

    public class Enrollment
    {
        public int EnrollmentID { get; set; }
        public int CourseID { get; set; }
        public int StudentID { get; set; }
        public Grade? Grade { get; set; }

        public Course Course { get; set; }
        public Student Student { get; set; }
    }
```
- Course
```
public class Course
    {
        [DatabaseGenerated(DatabaseGeneratedOption.None)]
        public int CourseID { get; set; }
        public string Title { get; set; }
        public int Credits { get; set; }

        public ICollection<Enrollment> Enrollments { get; set; }
    }
```

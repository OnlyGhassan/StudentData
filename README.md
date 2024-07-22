# StudentData
StudentInfo, ScheduleInfo, AbsentInfo
# COOP Management System

This project is a COOP Management System built with ASP.NET Core using the Repository and Unit of Work patterns. It manages students, schedules, and absences, and provides an API for these operations.

## Project Structure

- **Controllers**: Handles API requests.
- **Models**: Contains data models.
- **Repository**: Contains repository interfaces and implementations.
- **Data**: Contains the DbContext for Entity Framework Core.

## Technologies Used

- ASP.NET Core
- Entity Framework Core
- SQL Server
- Swagger

## Getting Started

### Prerequisites

- .NET Core SDK 6.0 or later
- SQL Server

### Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/yourusername/coop-management-system.git
   cd coop-management-system

### Configure the database:

Update the connection string in appsettings.json:

   {
  "ConnectionStrings": {
    "DefaultConnection": "Server=your_server;Database=your_database;Trusted_Connection=True;MultipleActiveResultSets=true"
  }
}

### Run database migrations:
 
 dotnet ef database update

 ### Run the application:

 dotnet run
 
 ## API Endpoints

 ### Get Student Information:

 GET /student/{studentId}

 ### Get Schedule Information:

 GET /student/schedule/{studentId}

 ### Get Absence Information:

 GET /student/absent/{studentId}
 
Swagger
Swagger is used for API documentation and testing. After running the application, navigate to http://localhost:5000/swagger to view the API documentation.

Dependency Injection
The project uses Dependency Injection to manage dependencies. The following services are registered in Startup.cs:

IStudentData and StudentDataRepository
IAbsentData and AbsentDataRepository
IScheduleData and ScheduleDataRepository
IUnitOfWork and UnitOfWork
IStudentService and StudentService
Repository Pattern
Repositories are used to abstract the data access layer. Each entity (Student, Schedule, Absent) has its own repository interface and implementation.

Unit of Work Pattern
The Unit of Work pattern is used to group repository operations into a single transaction. The UnitOfWork class manages the repositories and ensures that all operations are committed together.

Contributing
Contributions are welcome! Please open an issue or submit a pull request.

License
This project is licensed under the MIT License.

Acknowledgements
ASP.NET Core Documentation
Entity Framework Core Documentation

Feel free to modify this README file according to your project's specifics and needs.

### Instructions for Adding the README to GitHub

1. **Place the `README.md` file in the root of your project directory.**

2. **Commit and push the changes to your GitHub repository:**

   ```bash
   git add README.md
   git commit -m "Add README file"
   git push origin main

# "The code is in private repository due to data sensitivity"


# COOP Project: KAU_OLR_API

## Overview

The KAU_OLR_API (King Abdulaziz University Online Registration API) is a comprehensive system designed to manage university data, including student information, schedules, absentee records, contracts, and sections. This system allows administrators and users to retrieve and manage various types of academic and administrative data effectively.

## System Architecture
![CodeFlow2](https://github.com/user-attachments/assets/781d838c-2928-4c52-bfb0-e6e1792886ea)

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Prerequisites](#prerequisites)
- [Database Setup](#database-setup)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Testing] (#Testing)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments] (#Acknowledgments)


## Features

- Retrieve student information by student ID and term date.
- Fetch schedule information for students based on their ID and term date.
- Obtain absentee records for students by student ID and term date.
- Retrieve section information using various parameters.
- Retrieve contract information using various parameters.
- Implement the Unit of Work pattern to manage database operations.
- Retrieve faculty and instructor details by ID and term.

## Technologies Used

- **ASP.NET Core**: Web API framework
- **Entity Framework Core**: ORM for database operations
- **SQL Server**: Database management system
- **Dependency Injection**: For managing dependencies and services
- **Logging**: Using Microsoft.Extensions.Logging
- **AutoMapper**: For object-to-object mapping

## Prerequisites

Before you begin, ensure you have met the following requirements:

- .NET Core SDK installed on your machine
- SQL Server or SQL Express installed
- Basic knowledge of C# and ASP.NET Core
- Basic knowledge of C#, ASP.NET Core, and SQL 
- Familiarity with RESTful APIs

## Database Setup

### 1. Create the Database

Create a new database in your SQL Server instance. You can do this using SQL Server Management Studio (SSMS) or any other database management tool.

### 2. Update Connection String

Update the connection string in `appsettings.json` with your SQL Server details. The `appsettings.json` file is located in the root of the project.

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=your_server_name;Database=your_database_name;User Id=your_username;Password=your_password;"
  }
}
```

### 3. Apply Migrations

Open a terminal or command prompt in the project directory and run the following command to apply migrations and create the necessary database schema:

dotnet ef database update


## Installation

### 1. Clone the Repository
```
git clone https://github.com/Auruka/KAU_OLR_API_Repository.git
cd KAU_OLR_API
```

### 2. Restore NuGet Packages

Restore the required NuGet packages by running the following command:
```
dotnet restore
```
### 3. Run the Application

Run the application using the following command:
```
dotnet run
```

## Usage

##Endpoints

###Get Student Data

  - URL: /student/StudentData
  - Method: GET
  - Parameters:
    - Date: The term date
    - studentId: The student ID
   
  - Example:
```
    curl -X GET "https://localhost:5274/api/NewApi/StudentData?Date=202401&studentId=1234567"
```
### Get Schedule Data

- URL: /student/ScheduleData
- Method: GET
- Parameters:
  - Date: The term date
  - studentId: The student ID
    
- Example:
```
curl -X GET "https://localhost:5274/api/NewApi/ScheduleData?Date=202401&studentId=1234567"
```
### Get Absent Data

- URL: /student/AbsentData
- Method: GET
- Parameters:
  - Date: The term date
  - studentId: The student ID

- Example:
```
curl -X GET "https://localhost:5274/api/NewApi/AbsentData?Date=202401&studentId=1234567"
```
### Get Section Data

- URL: /api/NewApi/teacher-data
- Method: GET
- Parameters:
  - term: The term date
  - crn: The CRN for the section
  - Gender: Gender of the teacher
  - atts: Acceptance type
  - id: The ID of the teacher
  - level: Level of study
  - type: Type of the contract (approved or not)
  - faculty: Faculty of the contract
  - courseCode: The code of the course (e.g., CPIT210)

- Example:
```
curl -X GET "https://localhost:5274/api/NewApi/teacher-data?term=202401&crn=13513&Gender=M&atts=DLRN&id=00052297&level=UG&type=approved&faculty=IT&courseCode=psy211"
```
### Get Contract Data

- URL: /api/NewApi/search-sections
- Method: GET
- Parameters:
  - Term: The term date
  - CRN: The CRN for the section
  - AcceptanceType: Acceptance type
  - InstructorID: The ID of the teacher
  - Level: Level of study
  - Campus: Campus of the contract
  - Course: The code of the course (e.g., CPIT210)

- Example:
```
curl -X GET "https://localhost:5274/api/NewApi/search-sections?CRN=13653&Campus=MCB&InstructorID=00016623&Course=CPCS381&Term=202401&AcceptanceType=REGL&Level=UG"
```

## Project Structure

```
appsettings.Development.json
appsettings.json
KAU_OLR_API.csproj
KAU_OLR_API.http
KAU_OLR_API.sln
Program.cs

├───Controllers
│       NewApiController.cs
│       StudentController.cs
├───Dtos
│       CourseContractDto.cs
│       SectionDataDto.cs
├───Models
│       AbsentInfo.cs
│       ScheduleInfo.cs
│       StudentDatum.cs
│       StudentInfo.cs
├───Repositories
│       DoctorContractRepo.cs
│       IDoctorContractData.cs
│       ISectionData.cs
│       IAbsentData.cs
│       IScheduleData.cs
│       IStudentData.cs
│       SectionRepo.cs
│       AbsentDataRepository.cs
│       ScheduleDataRepository.cs
│       StudentDataRepository.cs
├───Services
│       SearchContract.cs
│       SearchSection.cs
│       ISectionService.cs
│       SectionService.cs
├───UnitOfWork
│       IUnitOfWork.cs
│       UnitOfWork.cs
└───WebPage
    ├───css
    │       sheduleSheet.css
    │       styles.css
    ├───img
    │       icons8-user-circle-96.png
    │       logo.webp
    │       photo_2024-07-10_10-30-55.jpg
    └───js
            display.js
            main.js
            models.js
```
## Testing 
Unit Tests: Implement unit tests for critical components using xUnit or NUnit.
Integration Tests: Set up integration tests to ensure API endpoints work correctly with the database.

## Contributing

### Contributions are always welcome! Please follow these steps:

 1. Fork the repository.
 2. Create a new branch (git checkout -b feature-name).
 3. Make your changes and commit them (git commit -m 'Add some feature').
 4. Push to the branch (git push origin feature-name).
 5. Open a Pull Request.
 6. Engage in the review process.
 7. Keep your branch updated.

## License

### This project is licensed under the MIT License - see the LICENSE file for details.

### Acknowledgments 

## Special thanks to the development team and contributors who helped make this project a success.

### Instructions for Adding the README to GitHub

1. **Place the `README.md` file in the root of your project directory.**

2. **Commit and push the changes to your GitHub repository:**

   ```bash
   git add README.md
   git commit -m "Add README file"
   git push origin main

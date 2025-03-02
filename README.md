# Employee Management System

## Introduction
This project is a simple Employee Management System developed using ASP.NET Core MVC and Entity Framework Core. It enables users to manage employee records by performing CRUD (Create, Read, Update, Delete) operations efficiently.

## Key Features
- Add, view, update, and delete employee records.
- Data validation using annotations.
- Database operations powered by Entity Framework Core.
- User-friendly interface with structured views.


## Installation Guide
1. Clone this repository:
   ```sh
   git clone <repository-url>
   cd EmployeeManagementSystem
   ```

2. Install necessary dependencies:
   ```sh
   dotnet restore
   ```

3. Configure your database connection in `appsettings.json`:
   ```json
   "ConnectionStrings": {
     "DefaultConnection": "YourDatabaseConnectionStringHere"
   }
   ```

4. Set up the database:
   ```sh
   dotnet ef migrations add InitialCreate
   dotnet ef database update
   ```

5. Start the application:
   ```sh
   dotnet run
   ```


## License
This project is open-source and free to use.

## Author
- Ahmed Falah Alharbi


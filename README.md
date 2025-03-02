# Employee Management System

## Introduction
This project is a simple Employee Management System developed using ASP.NET Core MVC and Entity Framework Core. It enables users to manage employee records by performing CRUD (Create, Read, Update, Delete) operations efficiently.

## Key Features
- Add, view, update, and delete employee records.
- Data validation using annotations.
- Database operations powered by Entity Framework Core.
- User-friendly interface with structured views.

## Project Directory Structure
```
/EmployeeManagementSystem
│-- Controllers/
│   ├── EmployeeController.cs
│-- Models/
│   ├── Employee.cs
│-- Data/
│   ├── AppDbContext.cs
│-- Views/
│   ├── Employee/
│       ├── Index.cshtml
│       ├── Create.cshtml
│       ├── Edit.cshtml
│       ├── Delete.cshtml
│-- Program.cs
│-- Startup.cs (if applicable)
│-- appsettings.json
```

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

## Implementation Details
### 1. Employee Model (Employee.cs)
Defines an `Employee` class with properties:
```csharp
public class Employee
{
    [Key]
    public int Id { get; set; }
    
    [Required]
    [StringLength(100)]
    public string Name { get; set; }
    
    [Required]
    public string Position { get; set; }
    
    [Required]
    [Range(0, double.MaxValue)]
    public decimal Salary { get; set; }
}
```

### 2. Database Context (AppDbContext.cs)
Handles database interactions:
```csharp
public class AppDbContext : DbContext
{
    public AppDbContext(DbContextOptions<AppDbContext> options) : base(options) { }
    
    public DbSet<Employee> Employees { get; set; }
}
```

### 3. Employee Controller (EmployeeController.cs)
Manages CRUD actions using dependency injection:
```csharp
private readonly AppDbContext _context;
public EmployeeController(AppDbContext context)
{
    _context = context;
}
```

### 4. Views
- **Index.cshtml**: Displays employee list.
- **Create.cshtml**: Form to add employees.
- **Edit.cshtml**: Form to modify employee records.
- **Delete.cshtml**: Confirms before deleting an employee.

### 5. Routing Configuration (Program.cs)
Ensures proper route handling:
```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(
        name: "default",
        pattern: "{controller=Employee}/{action=Index}/{id?}");
});
```

## Running & Testing
- Open `http://localhost:5000/Employee` in your browser.
- Perform CRUD operations.
- Ensure form validation is working correctly.

## License
This project is open-source and free to use.

## Author
- Ahmed Falah Alharbi


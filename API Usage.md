# API Usage

## Clone the repo

To clone the repository, use the following command:

```bash
git clone <repository_url>
```

Replace <repository_url> with the URL of the repository.

## Restore packages

To ensure that all packages are restored before running the application, you can explicitly run the following command after cloning:

```bash
dotnet restore
```

## Updating appsettings.json

After cloning the repository, navigate to the project directory and update the appsettings.json file to include the following connection string under the "ConnectionStrings" section:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\MSSQLLocalDB;Database=roi_database;Trusted_Connection=True;"
  }
}
```

Replace "Database=roi_database with your desired database name.

## Creating the Database

Once the appsettings.json file is updated, run the following commands to create the database:

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

## Run the API

```bash
dotnet run
```

> After running the program, check the **IP address** of the server and update the `.http` file variable accordingly.

![image2](Images/JH_2024-05-12-21-07-52.png)

## Update the database in case of code changes

If you make changes to the code that affect the database schema, you may need to delete existing migrations and update the database. To do this, follow these steps:

```bash
dotnet ef database drop --force             # 1. Delete existing database
dotnet ef migrations remove                 # 2. Delete existing migrations
dotnet ef migrations add InitialCreate      # 3. Generate a new initial migration
dotnet ef database update                   # 4. Update the database with the new migration
```

These commands will remove existing migrations, generate a new initial migration based on the current state of the models, and apply the migration to update the database accordingly.

## Drop and Create new database

```bash
dotnet ef database drop --force
dotnet ef database update
```

## Create new project

```bash
dotnet new webapi  -minimal
```

## Add Packages

```bash
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Tools
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
```

## Installing REST Client Extension in VSCode

To install the REST Client extension in Visual Studio Code (VSCode), follow these steps:

1. Open VSCode.
2. Go to the Extensions view by clicking on the Extensions icon in the Sidebar or pressing `Ctrl+Shift+X`.
3. Search for "REST Client" in the Extensions Marketplace.
4. Click on the "Install" button next to the REST Client extension.

### Using .http file to Test the API

The `.http` file provides a convenient way to test the API endpoints using the REST Client extension in VSCode.

### Understanding Variables

The `.http` file may contain variables defined at the beginning of the file, such as:

```javascript
@HostAddress = http://localhost:5095
```

This variable `@HostAddress` represents the base URL of the ROI API. You can modify it to match the actual base URL of your API.

### Sending Requests

To send requests using the `.http` file, follow these steps:

1. Open the `.http` file in VSCode.
2. Ensure that the REST Client extension is installed.
3. Modify the base URL variable `@HostAddress` if needed.
4. Click on the "**Send Request**" button that appears over each request in the file to execute the request.

![image](Images/JH_2024-05-12-20-55-51.png)

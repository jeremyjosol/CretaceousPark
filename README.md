# Cretaceous Park

## Application Setup

1. Clone this repo.
2. Open the terminal and navigate to this project's production directory called "CretaceousPark".
3. Within the production directory "CretaceousPark", create two new files: `appsettings.json` and `appsettings.Development.json`.
4. Within `appsettings.json`, put in the following code. Make sure to replacing the `uid` and `pwd` values in the MySQL database connection string with your own username and password for MySQL. For the LearnHowToProgram.com lessons, we always assume the `uid` is `root` and the `pwd` is `epicodus`.

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*",
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Port=3306;database=cretaceous_api;uid=root;pwd=epicodus;"
  }
}
```

5. Within `appsettings.Development.json`, add the following code:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Trace",
      "Microsoft.AspNetCore": "Information",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  }
}
```

6. Create the database using the migrations in the Cretaceous Park API project. Open your shell (e.g., Terminal or GitBash) to the production directory "CretaceousPark", and run `dotnet ef database update`.
    > To optionally create a migration, run the command `dotnet ef migrations add MigrationName` where `MigrationName` is your custom name for the migration in UpperCamelCase. 
7. Within the production directory "CretaceousPark", run `dotnet watch run --launch-profile "CretaceousPark-Production"` in the command line to start the project in production mode with a watcher. 
8. To optionally further build out this project in development mode, start the project with `dotnet watch run` in the production directory "CretaceousPark".
9. Use your program of choice to make API calls. In your API calls, use the domain _http://localhost:5000_. Keep reading to learn about all of the available endpoints.

### Available Endpoints

```
GET http://localhost:5000/api/animals/
GET http://localhost:5000/api/animals/{id}
POST http://localhost:5000/api/animals/
PUT http://localhost:5000/api/animals/{id}
DELETE http://localhost:5000/api/animals/{id}
```

Note: `{id}` is a variable and it should be replaced with the id number of the animal you want to GET, PUT, or DELETE.

#### Optional Query String Parameters for GET Request

| Parameter   | Type        |  Required    | Description |
| ----------- | ----------- | -----------  | ----------- |
| species     | String      | not required | Returns animals with a matching species value |
| name        | String      | not required | Returns animals with a matching name value |
| minimumAge  | Number      | not required | Returns animals that have an age value that is greater than or equal to the specified minimumAge value |
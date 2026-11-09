# RaceDay — Combined Parts 1, 2 and 3

This repository contains the complete RaceDay coursework solution:

- **Part 1:** system planning, ERD, endpoint plan and SQL Server database schema (`Part1/` and `database/`).
- **Part 2:** ASP.NET Core 8 REST API with SQL Server/EF Core, JWT authentication, BCrypt password hashing, role policies, Swagger and API tests (`RaceDay.Api/`, `RaceDay.Api.Tests/`).
- **Part 3:** ASP.NET Core MVC web application consuming the REST API, Azure Blob Storage event banners, organiser and participant workflows, and Docker support (`RaceDay.Mvc/`).

## Start here

Follow [`README_PART3_INTEGRATION.md`](README_PART3_INTEGRATION.md) for database setup, secrets configuration, build/test commands, local run instructions, Docker and submission checks.

## Important

- Use .NET 8 and SQL Server.
- Register new users through the application; the Part 1 sample users have placeholder password hashes and cannot log in.
- The MVC application communicates with the API over HTTP(S). It does not connect directly to SQL Server.
- Azure banner upload requires a configured Azure Storage connection string.
- Replace the development JWT key with a long random secret before deployment.
- The source was statically reviewed and repaired in this environment, but a .NET SDK and SQL Server were unavailable here. Run `dotnet restore`, `dotnet build` and `dotnet test` on your machine before submission.


## Fixing NuGet restore / missing project.assets.json

If Visual Studio reports that `obj/project.assets.json` is missing, this is normally
because NuGet packages have not yet been restored. From the folder containing
`RaceDay.sln`, run:

```bash
dotnet clean RaceDay.sln
dotnet restore RaceDay.sln
dotnet build RaceDay.sln
dotnet test RaceDay.sln
```

In Visual Studio, you can also right-click the solution and select **Restore NuGet Packages**,
then use **Build > Rebuild Solution**. Do not delete or commit generated `obj` folders.

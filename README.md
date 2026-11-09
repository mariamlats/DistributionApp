# DistributionApp

**C# / .NET Framework 4.7.2 desktop application with DevExpress and SQL Server.**

This repository preserves a compiled Windows build of **LatzaDB**, a distribution-management desktop application. Its assemblies separate the domain layer, repository/data-access layer and desktop interface, with Entity Framework and DevExpress components included alongside the executable.

## Repository status

**This is currently a compiled-build archive.** The repository does not contain C# source files, a Visual Studio solution/project, a package manifest or a database schema/migrations. It cannot be rebuilt from the files here alone.

## Included components

| Files | Role |
| --- | --- |
| LatzaDB.exe | Windows desktop entry point |
| LatzaDB.Domain.dll | Domain assembly |
| LatzaDB.Repository.dll | Repository/data-access assembly |
| EntityFramework*.dll | Entity Framework 6 / SQL Server provider |
| DevExpress.*.v19.2.dll | DevExpress desktop UI, grid, reporting and related components |
| LatzaDB.exe.config | Runtime, UI and database configuration |
| *.config.example | Configuration examples for a server with certificate-verified SQL encryption |

The original debug-symbol files are excluded from the cleaned archive. Bundled third-party components retain their respective licences; their presence does not establish that every component is used by the application.

## Run the archived build

Use a Windows machine with:

- .NET Framework **4.7.2 or a compatible later 4.x runtime**.
- Access to a SQL Server database with the application's existing LatzaDB schema. That schema is not included here.
- The required application and dependency assemblies kept together.

Clone or download the repository:

~~~bash
git clone https://github.com/mariamlats/DistributionApp.git
~~~

Review the configuration and use a separate test database before launching the archived executable. The checked-in local configuration targets a local SQL Express instance and uses **Windows Integrated Security**, so database access follows the signed-in Windows account.

The executable normally reads **LatzaDB.exe.config**. The library-side configuration is retained for reference; .NET does not automatically merge it into the executable's configuration.

## Database configuration

The connection is named **LatzaDbContext**. The example files use placeholders for the server/database and specify:

~~~text
Integrated Security=True;Encrypt=True;TrustServerCertificate=False;Connect Timeout=15
~~~

Replace the placeholders with your environment's server and database. Certificate verification requires the SQL Server certificate to match the hostname and chain to a trusted certificate authority. The Windows account must have only the database permissions it needs.

Do not commit personalised connection settings, passwords, database backups or production data.

## What is needed to restore a source project

To make this a buildable portfolio project, add the original:

1. Visual Studio solution and C# projects for the application, domain and repository layers.
2. Database schema or migrations, with synthetic sample data.
3. Package/dependency declarations and the appropriate DevExpress development setup.
4. Build instructions and source-level regression tests.

Once those are available, the application logic and dependency versions can be reviewed and updated. The compiled application and its bundled libraries have not been runtime-tested or decompiled as part of this documentation cleanup. The XML configuration examples were parsed and checked locally.

## Attribution

Original project attribution from the previous README: [@bgkcsav4](https://github.com/bgkcsav4).

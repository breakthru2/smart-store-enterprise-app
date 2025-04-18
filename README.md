# Smart Store Enterprise App

## Project Overview

This project is a full-scale **Smart Store Enterprise Application** built with **ASP.NET Core Web API**, **Blazor WebAssembly**, **Entity Framework Core**, and **Docker**. The application aims to provide an e-commerce solution for managing products, orders, users, and more.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Project Setup](#project-setup)
3. [Database Setup](#database-setup)
4. [Running the Application](#running-the-application)
5. [Docker Setup](#docker-setup)
6. [API Endpoints](#api-endpoints)
7. [Testing](#testing)
8. [CI/CD Pipeline](#cicd-pipeline)
9. [License](#license)

---

## Prerequisites

Before running the project, ensure you have the following installed:

- **.NET 8 SDK** (for building and running the project)
- **Visual Studio 2022** (or any other .NET IDE)
- **SQL Server** or **SQL Server Express** (for the database)
- **Docker** (if you wish to run the app in containers)
- **Git** (for version control)

---

## Project Setup

To get started with the project:

1. Clone the repository:

    ```bash
    git clone https://github.com/yourusername/smart-store-enterprise-app.git
    ```

2. Open the **SmartStoreEnterpriseApp.sln** solution in **Visual Studio**.
3. Restore NuGet packages by right-clicking on the solution in Visual Studio and selecting **Restore NuGet Packages**.

---

## Database Setup

This project uses **SQL Server** to store data for the application. Follow these steps to set up the database:

1. Open **SQL Server Management Studio (SSMS)** and connect to your SQL Server instance.
2. In **SmartStoreEnterpriseApp.API**, modify the connection string in the `appsettings.json` to point to your SQL Server instance:

    ```json
    {
      "ConnectionStrings": {
        "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=SmartStoreDb;Trusted_Connection=True;MultipleActiveResultSets=true"
      }
    }
    ```

3. Run the following commands to apply database migrations:

    ```bash
    dotnet ef migrations add InitialCreate --project SmartStoreEnterpriseApp.Infrastructure --startup-project SmartStoreEnterpriseApp.API
    dotnet ef database update --project SmartStoreEnterpriseApp.Infrastructure --startup-project SmartStoreEnterpriseApp.API
    ```

---

## Running the Application

1. **Running the API Project**:
    - In Visual Studio, right-click the **SmartStoreEnterpriseApp.API** project and select **Set as Startup Project**.
    - Press **Ctrl + F5** to run the API.

2. **Running the Blazor WebAssembly Client**:
    - In Visual Studio, right-click the **SmartStoreEnterpriseApp.Client** project and select **Set as Startup Project**.
    - Press **Ctrl + F5** to run the Blazor WebAssembly app.

The Blazor app will automatically consume the API endpoints.

---

## Docker Setup

If you prefer to run the app in Docker containers:

1. In the root of your solution, ensure you have the `Dockerfile` (as described earlier) to containerize the application.
   
2. Build the Docker image:

    ```bash
    docker build -t smart-store-enterprise-app .
    ```

3. Run the Docker container:

    ```bash
    docker run -d -p 5000:80 --name smart-store-enterprise-app smart-store-enterprise-app
    ```

The app will be available at `http://localhost:5000`.

---

## API Endpoints

Here are some of the API endpoints you can use to interact with the application:

1. **Get Products**:
    - **GET** `/api/products`
    - Description: Fetch all products.

2. **Create Product**:
    - **POST** `/api/products`
    - Description: Create a new product.

3. **Get Orders**:
    - **GET** `/api/orders`
    - Description: Fetch all orders.

---

## Testing

Unit tests are implemented using **xUnit**. To run the tests:

1. Right-click on the **SmartStoreEnterpriseApp.Tests** project and select **Run Tests**.
2. Alternatively, use the following CLI command:

    ```bash
    dotnet test SmartStoreEnterpriseApp.Tests
    ```

---

## CI/CD Pipeline

The project comes with a **GitHub Actions** workflow that builds, tests, and deploys the application. To set up GitHub Actions for CI/CD:

1. Create a `.github/workflows/ci.yml` file.
2. Define the build, test, and deploy steps (the example I provided earlier).

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

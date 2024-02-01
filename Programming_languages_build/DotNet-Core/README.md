### dotnet core applciation build

* there is two terms
  * a. dotnet core
  * b. ASP Dontnet

* Dotnet core:  NET Core is a general-purpose development platform that allows building applications for various domains.
  * it is platform independency. we can __build and deploy__ application in any __operating system__

* ASP Dotnet: while ASP.NET Core is a web-specific framework built on top of . NET Core for developing web applications and APIs.
  * it is platform dependency. we can __build and deploy__ application in __windows__ only.


### hwo to generate sample dotnet core project

*  First install dotnet core in the workstation.
*  In the case windowws can use __visual studio__ code.

* we can simple run command __ dotnet new web__ . it will generate sample project.

### docker file for dotnet core application

```
# the code, is multi stage docker file
# Use the official .NET Core SDK image as the base image
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build-env

# Set the working directory inside the container
WORKDIR /app

# Copy the project files to the container
COPY . ./

# Restore dependencies and build the application
RUN dotnet restore
RUN dotnet publish -c Release -o out

# Create a runtime image
FROM mcr.microsoft.com/dotnet/aspnet:6.0

# Set the working directory inside the runtime container
WORKDIR /app

# Copy the published application from build-env to runtime container
COPY --from=build-env /app/out .

# Expose the port that the application will listen on
EXPOSE 80

# Set the entry point for the container
ENTRYPOINT ["dotnet", "YourAppName.dll"]
```

### starting docker container

* docker run -e ASPNETCORE_ENVIRONMENT=Development your_image_name

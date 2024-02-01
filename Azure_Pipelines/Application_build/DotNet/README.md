### dotnet core applciation build

```
# Use the official .NET Core SDK image as the base image
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build-env

# Set the working directory inside the container
WORKDIR /app

# Copy the project files to the container
COPY . ./

# Restore dependencies and build the application
RUN dotnet restore
RUN dotnet publish -c Release -o out

# Create a runtime image
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1

# Set the working directory inside the runtime container
WORKDIR /app

# Copy the published application from build-env to runtime container
COPY --from=build-env /app/out .

# Expose the port that the application will listen on
EXPOSE 80

# Set the entry point for the container
ENTRYPOINT ["dotnet", "YourAppName.dll"]
```

#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
WORKDIR /app
EXPOSE 84

FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY ["helloworld.razor.csproj", "."]
RUN dotnet restore "./helloworld.razor.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "helloworld.razor.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "helloworld.razor.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "helloworld.razor.dll"]
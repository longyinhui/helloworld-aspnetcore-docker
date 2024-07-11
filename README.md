# helloworld-aspnetcore-docker
This is a simple Helloworld solution including some ASP.NET Core web apps. The Razor web app is deployed in http://106.55.179.167:8084 by Docker

## Implementation Steps of Razor Web App
### _In Development environment_ (Windows + Visual Studio + .NET 7.0)
1. Create new ASP.NET Core Web App (Razor) project, enabling Docker
2. Update _Program.cs_ and _launchSetting.json_ (need to add port, e.g.:84)
3. Prepare Dockerfile (with `RUN dotnet build`)
4. Build in Visual Studio by Docker 

### _In Deployment environment_ (Linux-CentOS)
7. Copy solution or project folder to target server, and make sure Dockerfile is included
8. Run Docker 
```sh
cd <folder path>
docker build -t helloworldrazor:v1 .
docker run -it -d -p 8084:84 helloworldrazor:v1
```
> Note: `helloworldrazor:v1` is image's name
// 使用官方的 .NET 镜像作为基础镜像
FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS base
WORKDIR /app
EXPOSE 80

// 使用官方的 .NET SDK 镜像来构建应用
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src
COPY ShadowNetCore.WebAPI.csproj ./
RUN dotnet restore
COPY . .
WORKDIR "./"
RUN dotnet build -c Release -o /app/build

// 发布阶段
FROM build AS publish
RUN dotnet publish -c Release -o /app/publish

// 最终运行阶段
FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "ShadowNetCore.WebAPI.dll"]
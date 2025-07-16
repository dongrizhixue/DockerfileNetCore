# 使用官方 .NET 9.0 运行时基础镜像
FROM mcr.microsoft.com/dotnet/aspnet:9.0

# 设置工作目录为 /app
WORKDIR /app

# 复制当前目录所有文件到容器工作目录
COPY . .

# 设置环境变量（可选）
ENV ASPNETCORE_URLS=http://+:80
ENV ASPNETCORE_ENVIRONMENT=Production

# 暴露端口
EXPOSE 80

# 启动应用程序
ENTRYPOINT ["dotnet", "ShadowNetCore.WebAPI.dll"]
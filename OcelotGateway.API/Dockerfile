FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
WORKDIR /src
COPY ["OcelotGateway.API/OcelotGateway.API.csproj", "OcelotGateway.API/"]
RUN dotnet restore "OcelotGateway.API/OcelotGateway.API.csproj"
COPY . .
WORKDIR "/src/OcelotGateway.API"
RUN dotnet build "OcelotGateway.API.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "OcelotGateway.API.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
CMD ASPNETCORE_URLS=http://*:$PORT
ENTRYPOINT ["dotnet", "OcelotGateway.API.dll"]
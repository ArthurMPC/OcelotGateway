FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
WORKDIR /src
COPY ["ServiceOne.API/ServiceOne.API.csproj", "ServiceOne.API/"]
RUN dotnet restore "ServiceOne.API/ServiceOne.API.csproj"
COPY . .
WORKDIR "/src/ServiceOne.API"
RUN dotnet build "ServiceOne.API.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "ServiceOne.API.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "ServiceOne.API.dll"]
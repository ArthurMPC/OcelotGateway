FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
WORKDIR /src
COPY ["ServiceTwo.API/ServiceTwo.API.csproj", "ServiceTwo.API/"]
RUN dotnet restore "ServiceTwo.API/ServiceTwo.API.csproj"
COPY . .
WORKDIR "/src/ServiceTwo.API"
RUN dotnet build "ServiceTwo.API.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "ServiceTwo.API.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "ServiceTwo.API.dll"]
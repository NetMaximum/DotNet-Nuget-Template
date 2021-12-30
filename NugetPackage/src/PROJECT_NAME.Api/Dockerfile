FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY PROJECT_NAME.csproj /src/PROJECT_NAME.csproj
RUN dotnet restore
COPY . .
RUN dotnet publish -c Release -o /pub

FROM base AS final
WORKDIR /app
COPY --from=build /pub .
ENTRYPOINT ["dotnet", "PROJECT_NAME.dll"]
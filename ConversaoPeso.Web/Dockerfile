FROM mcr.microsoft.com/dotnet/sdk:5.0 as build
WORKDIR /app
COPY . ./
RUN dotnet restore
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:5.0 as final
WORKDIR /app
COPY --from=build /app/out . 
ENV ASPNETCORE_URLS=http://+:80
ENTRYPOINT [ "dotnet", "ConversaoPeso.Web.dll"]

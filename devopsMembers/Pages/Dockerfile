LABEL maintainer="zandler.oliveira@gmail.com"

FROM microsoft/dotnet:sdk AS build-env
WORKDIR /app

# Copy csproj e Faz o restore para dependencias
COPY *.csproj ./
RUN dotnet restore

# Copia o restore e faz o build
COPY . ./
RUN dotnet publish -c Release -o out

# Faz o build da imagem e cria o conteudo dentro dela
FROM microsoft/dotnet:aspnetcore-runtime
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "devopsMembers.dll"]
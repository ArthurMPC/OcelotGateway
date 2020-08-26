[![.Net Core 3.1](https://img.shields.io/badge/.NET%20Core-3.1-green)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

# OcelotGateway
This section showcases basic usage of Ocelot as API Gateway. [Ocelot Documentation](https://ocelot.readthedocs.io/en/latest/)

### Pre-requisites

- Docker
- Docker Compose

### Running Demo

Run the following shell command to boot up this demo

```sh
# Windows Users and Root Linux Users
docker-compose up -d

# Non-root Linux Users
sudo docker-compose up -d
```

### Testing Gateway

To access API One: http://localhost:57869/api1/weatherforecast

To access API Two: http://localhost:57869/api2/weatherforecast

### Using Swagger For Ocelot

Access: http://localhost:57869/swagger

### You can choose which API Swagger to use 
![Screenshot_1](https://user-images.githubusercontent.com/41999569/91312038-26c26a80-e78a-11ea-87de-9ec10c07a109.jpg)

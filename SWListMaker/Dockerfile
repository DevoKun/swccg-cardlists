
##
## docker build -t DiscordCardLinker -f Dockerfile .
##
## The dotnetcore images are based on Debian GNU/Linux 10 (buster)
##
## docker run -ti discordcardlinker:latest /bin/sh
##

##
## Build
##
FROM mcr.microsoft.com/dotnet/core/sdk AS build-env
WORKDIR /app

## Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

## Copy everything else and build
COPY ./* ./
RUN dotnet publish -c Debug -o out


##
## Build runtime image
##
FROM mcr.microsoft.com/dotnet/core/runtime

WORKDIR /app

COPY --from=build-env /app/out .

# bin/Debug/SWListMaker.exe
CMD ["bin", "Debug", "SWListMaker.exe"]




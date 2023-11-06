
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build-env
WORKDIR /app


COPY *.* ./
RUN dotnet publish -c Release -o out


FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build-env /app/out .


RUN apt update \
    && apt install -y --no-install-recommends \
        curl \
        wget \
        gnupg2 \
        software-properties-common

RUN curl -O https://packages.microsoft.com/debian/10/prod/pool/main/libm/libmsquic/libmsquic-1.5.0-amd64.deb
RUN dpkg -i libmsquic-1.5.0-amd64.deb

ENTRYPOINT ["dotnet", "dotnet-http3.dll"]

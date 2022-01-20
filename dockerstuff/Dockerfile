FROM debian:bullseye-slim
LABEL author="chirag350" maintainer="chirag350 <doge@chiragdev.xyz>"

COPY ./packages-microsoft-prod.deb /

RUN apt-get update -y && \
    dpkg -i /packages-microsoft-prod.deb && \
 	apt-get install -y curl ca-certificates openssl git tar fontconfig tzdata iproute2 apt-transport-https && \
    rm /packages-microsoft-prod.deb && \
    apt-get -y update && \
    apt-get install -y dotnet-sdk-6.0 aspnetcore-runtime-6.0 && \
 	useradd -d /home/container -m container && \
    rm -rf /usr/bin/fallocate && \
    apt-get clean -y

USER container
ENV user=container home=/home/container
WORKDIR /home/container
COPY ./entrypoint.sh /

CMD [ "/bin/bash", "/entrypoint.sh" ]
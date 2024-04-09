FROM mcr.microsoft.com/dotnet/runtime-deps:8.0

# https://github.com/nissl-lab/npoi/issues/981
# https://stackoverflow.com/questions/60934639/install-fonts-in-linux-container-for-asp-net-core/62888227#62888227
RUN echo "deb http://deb.debian.org/debian/ bookworm main contrib" > /etc/apt/sources.list && \
    echo "deb-src http://deb.debian.org/debian/ bookworm main contrib" >> /etc/apt/sources.list && \
    echo "deb http://security.debian.org/ bookworm-security main contrib" >> /etc/apt/sources.list && \
    echo "deb-src http://security.debian.org/ bookworm-security main contrib" >> /etc/apt/sources.list
RUN sed -i'.bak' 's/$/ contrib/' /etc/apt/sources.list
RUN apt-get update; apt-get install -y ttf-mscorefonts-installer fontconfig
# refresh system font cache
RUN fc-cache -f -v

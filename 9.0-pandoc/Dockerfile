FROM mcr.microsoft.com/dotnet/runtime-deps:9.0
ARG PANDOC_VERSION=3.8.2.1

RUN echo "deb http://deb.debian.org/debian/ bookworm main contrib" > /etc/apt/sources.list && \
    echo "deb-src http://deb.debian.org/debian/ bookworm main contrib" >> /etc/apt/sources.list && \
    echo "deb http://security.debian.org/ bookworm-security main contrib" >> /etc/apt/sources.list && \
    echo "deb-src http://security.debian.org/ bookworm-security main contrib" >> /etc/apt/sources.list && \
    sed -i'.bak' 's/$/ contrib/' /etc/apt/sources.list && \
    apt-get update && \
    apt-get install -y wget && \
    wget https://github.com/jgm/pandoc/releases/download/${PANDOC_VERSION}/pandoc-${PANDOC_VERSION}-1-amd64.deb && \
    dpkg -i pandoc-${PANDOC_VERSION}-1-amd64.deb && \
    rm pandoc-${PANDOC_VERSION}-1-amd64.deb && \
    # 清理临时文件
	apt-get clean &&\
	apt-get autoclean &&\
	rm -rf /tmp/* && rm -rf /var/lib/apt/lists/*

CMD ["bash"]


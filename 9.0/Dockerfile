FROM mcr.microsoft.com/dotnet/runtime-deps:9.0

# https://github.com/nissl-lab/npoi/issues/981
# https://stackoverflow.com/questions/60934639/install-fonts-in-linux-container-for-asp-net-core/62888227#62888227
RUN echo "deb http://deb.debian.org/debian/ bookworm main contrib" > /etc/apt/sources.list && \
    echo "deb-src http://deb.debian.org/debian/ bookworm main contrib" >> /etc/apt/sources.list && \
    echo "deb http://security.debian.org/ bookworm-security main contrib" >> /etc/apt/sources.list && \
    echo "deb-src http://security.debian.org/ bookworm-security main contrib" >> /etc/apt/sources.list && \
    sed -i'.bak' 's/$/ contrib/' /etc/apt/sources.list && \
    apt-get update && \
    apt-get install -y --no-install-recommends ttf-mscorefonts-installer fontconfig && \
    fc-cache -f -v && \
    # 清理临时文件
	apt-get clean &&\
	apt-get autoclean &&\
	rm -rf /tmp/* && rm -rf /var/lib/apt/lists/*

CMD ["bash"]
FROM mcr.microsoft.com/dotnet/runtime-deps:9.0

# Pandoc 版本（可通过 --build-arg 覆盖）
ARG PANDOC_VERSION=3.8.2.1
# 由 BuildKit/Buildx 提供，用于区分架构：amd64 / arm64 / ...
ARG TARGETARCH

RUN set -eux; \
    apt-get update; \
    apt-get install -y --no-install-recommends wget ca-certificates; \
    ARCH="${TARGETARCH}"; \
    if [ -z "$ARCH" ]; then ARCH="$(dpkg --print-architecture)"; fi; \
    echo "Target architecture: ${ARCH}"; \
    wget -q "https://github.com/jgm/pandoc/releases/download/${PANDOC_VERSION}/pandoc-${PANDOC_VERSION}-1-${ARCH}.deb"; \
    dpkg -i "pandoc-${PANDOC_VERSION}-1-${ARCH}.deb" || apt-get -y -f install; \
    rm -f "pandoc-${PANDOC_VERSION}-1-${ARCH}.deb"; \
    # 清理临时文件
	apt-get clean; \
	apt-get autoclean; \
	rm -rf /tmp/* /var/tmp/* /var/lib/apt/lists/*

CMD ["bash"]


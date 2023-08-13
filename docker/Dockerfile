FROM ubuntu as wasmbuild

# Install requirments
RUN DEBIAN_FRONTEND=noninteractive apt update && \
    DEBIAN_FRONTEND=noninteractive apt install make wget -y

# Install go
RUN wget https://go.dev/dl/go1.20.7.linux-amd64.tar.gz && \
    tar xzvf go1.20.7.linux-amd64.tar.gz && \
    ln -s /go/bin/go /usr/bin/go 
    
# Install tinygo
RUN wget https://github.com/tinygo-org/tinygo/releases/download/v0.28.1/tinygo_0.28.1_amd64.deb && \
    dpkg -i tinygo_0.28.1_amd64.deb

# Build filter 
COPY proxy-wasm-go-filter-template /opt/proxy-wasm-go-filter-template
RUN make -C /opt/proxy-wasm-go-filter-template

FROM kong:3.4.0

# Change user to 'root'
USER root

# Copy WASM filter 
COPY --from=wasmbuild /opt/proxy-wasm-go-filter-template/my-go-filter.wasm /usr/local/openresty/lualib/resty/my-go-filter.wasm
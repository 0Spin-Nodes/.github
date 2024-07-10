# 0SPIN. Blockchain Validation
![Screensshot_2](https://github.com/0Spin-Nodes/.github/assets/175016332/d57fb740-9ce5-4255-9b8a-847259b0155a)

## Usefull links

| Name  | Link |
| ------------- | ------------- |
| Mail  | amyallenaddgk@gmail.com |
| Discord  | zer0spin |
| Twitter  | https://x.com/zer0_spin |
| Medium  | https://medium.com/ |
| Keybase  | https://keybase.io/0spin |

# Our Contribution

| Project Name  | Status | Result |
| ------------- | ------------- | ------------- |
| OG LABS  | 🟢Working  | [Click fo more](https://github.com/0Spin-Nodes#0g-labs) |
| NUBIT  | 🟢Working  | [Click fo more](https://github.com/0Spin-Nodes#nubit) |
| VERSATUS  | 🟠in progress | - |
| KWIL  | 🟠in progress  | - |
| FRACTAL  | 🔴Stopped  | - |
| CLOVER  | 🔴Stopped  | - |
| BOUNCEBIT  | 🔴Stopped  | - |
| SEDA | 🔴Stopped  | - |
| KI  | 🔴Stopped  | - |
| CLOVER  | 🔴Stopped  | - |

# INFO

Our team comprises experts in blockchain technology, cryptography, and network management, all united by a common mission: to support the growth and security of blockchain networks worldwide. We pride ourselves on our deep industry knowledge and our commitment to maintaining the highest standards of reliability and performance.

In the rapidly evolving world of blockchain technology, security, transparency, and decentralization are paramount. At 0spin, we understand the critical role these elements play in the success and integrity of blockchain networks. As a dedicated team of professionals, we specialize in providing top-tier node validation services for leading cryptocurrency projects, ensuring the robustness and reliability of decentralized systems.

# Results

## 0G LABS

Full text om [Medium](https://medium.com/@0spin/work-by-0spin-in-the-0g-project-870519af6e72)

**Setting Up the 0G Node**

```
# Clone the repository
git clone https://github.com/0GNetwork/0G.git
cd 0G

# Build the node software
make install

# Initialize the node
ogd init "0SpinNode"

# Download the genesis file
wget -O $HOME/.ogd/config/genesis.json "https://raw.githubusercontent.com/0GNetwork/0G/main/genesis.json"

# Configure the node (example of configuring the persistent peers)
PEERS="node1@10.0.0.1:26656,node2@10.0.0.2:26656"
sed -i.bak -e "s/^persistent_peers *=.*/persistent_peers = \"$PEERS\"/" $HOME/.ogd/config/config.toml

# Start the node
ogd start
```

**Docker Configuration for 0G Node Deployment**

```
FROM golang:1.18-alpine

RUN apk add --no-cache git

WORKDIR /app

# Clone the repository
RUN git clone https://github.com/0GNetwork/0G.git . && \
    go build -o ogd ./cmd/ogd

EXPOSE 26656 26657

CMD ["./ogd", "start"]
```

**Docker Compose Setup**

```
version: '3.8'

services:
  0g-node:
    image: 0g-node
    ports:
      - "26656:26656"
      - "26657:26657"
    volumes:
      - ./data:/root/.ogd
```

**Configuration Files**

```
[node]
proxy_app = "tcp://127.0.0.1:26658"
rpc.laddr = "tcp://0.0.0.0:26657"
p2p.laddr = "tcp://0.0.0.0:26656"
persistent_peers = "node1@10.0.0.1:26656,node2@10.0.0.2:26656"
```

**Monitoring and Maintenance**

```
global:
  scrape_interval: 15s
scrape_configs:
  - job_name: '0G_node'
    static_configs:
      - targets: ['localhost:26660']
```

## NUBIT

Full text om [Medium](https://medium.com/@0spin/work-by-0spin-in-the-nubit-project-b05fc782de9e)

**Setting Up the Nubit Node**

```
# Clone the repository
git clone https://github.com/RiemaLabs/nubit-node.git
cd nubit-node

# Build the Docker image
docker build -t nubit-node .

# Run the node
docker run -d --name nubit-node -p 30303:30303 -v /nubit/data:/root/.nubit nubit-node
```

**Dockerfile for Building Nubit Node**

```
FROM golang:1.18-alpine

RUN apk add --no-cache git

WORKDIR /app

# Copy and build the application
COPY . .
RUN go build -o nubit-node ./cmd/nubit

EXPOSE 30303

CMD ["./nubit-node"]
```

**docker-compose.yml for Running Nubit Node Services**

```
version: '3'

services:
  nubit-node:
    image: nubit-node
    ports:
      - "30303:30303"
    volumes:
      - /nubit/data:/root/.nubit
```

**Advanced Configuration**

```
[Node]
Name = "NubitNode01"
NetworkId = 1
DataDir = "/root/.nubit"
```

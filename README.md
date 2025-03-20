# layeredge-cli
How to run layeredge light node on vps

Follow these steps to set up and run your LayerEdge CLI Light Node efficiently.

### Step 1: Install Required Dependencies

```
sudo apt update && sudo apt upgrade
sudo apt install nano 
```

### Install Go
```
sudo rm -rf /usr/local/go
curl -L https://go.dev/dl/go1.22.4.linux-amd64.tar.gz | sudo tar -xzf - -C /usr/local
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile
echo 'export PATH=$PATH:$(go env GOPATH)/bin' >> $HOME/.bash_profile
source .bash_profile
go version
```
### Install Rust
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Risc0 Toolchain: If not installed, run:

```
curl -L https://risczero.com/install | bash && rzup install
```

### Step 1: Clone the Light Node Repository

```
git clone https://github.com/Layer-Edge/light-node.git
cd light-node
```

### Step 3: Configure Environment Variables

Set up the required environment variables in your terminal session or add them to a .env file:

```
nano .env
```

```
GRPC_URL=34.31.74.109:9090
CONTRACT_ADDR=cosmos1ufs3tlq4umljk0qfe8k5ya0x6hpavn897u2cnf9k0en9jr7qarqqt56709
ZK_PROVER_URL=http://127.0.0.1:3001
API_REQUEST_TIMEOUT=100
POINTS_API=http://127.0.0.1:8080
PRIVATE_KEY='cli-node-private-key'
```

Replace with your privatkey

### Step 4: Start the Merkle Service

Before running the Light Node, start the Merkle service:

```
cd risc0-merkle-service
cargo build && cargo run
```

Wait until the Merkle service is fully initialized before proceeding.

### Step 5: Build and Run the LayerEdge Light Node

In a separate terminal window, navigate to the root directory and execute:

```
go build
./light-node
```
Ensure that the Light Node is running independently and correctly connected to the Merkle service.

### Configure Wallet to dashboard

- Connecting CLI Node with LayerEdge Dashboard
- To link your CLI node with the dashboard for analytics:

**Fetch Points via CLI**
``` 
https://light-node.layeredge.io/api/cli-node/points/{walletAddress}
```
Replace {walletAddress} with your actual CLI wallet address.

- Connect to Dashboard
- Navigate to dashboard.layeredge.io
- Connect your wallet
- Link your CLI node’s Public Key

---

**Follow** : https://x.com/cryptoconsol

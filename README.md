# Welcome to Hedera Local Node 👋
THe Hedera Local Node is a single node that replicates the Hedera network on a development environment/local machine offering a controlled environment for developing, testing, and experimenting with [decentralized applications (dApps)](https://docs.hedera.com/hedera/support-and-community/glossary#decentralized-application-dapp).

- ⚡ Rapid Initialization: Fast startup and synchronization, ensuring quick iterations during development.
- 💯 Comprehensive Hedera API Support: Full support for [Hedera APIs](https://docs.hedera.com/hedera/sdks-and-apis), enabling seamless interaction with the local network.
- 🔎 Low Latency: Minimal response times for RPC calls, ensuring efficient and smooth application performance.
- 🛠️ Controlled Environment: Provides a controlled and isolated environment for testing and debugging, reducing the risk of conflicts with other network resources.

### 🏃‍♂️ Getting started
Learn how to set up, configure and manage your Hedera Local Node using the following resources:

- [💻 Hardware Requirements](#-hardware-requirements)
- [🚀 Setting up Hedera Local Node](#-setting-up-hedera-local-node)
- [🛠️ Configuration Options](#%EF%B8%8F-configuration-options)
- [Ⓜ️ Operational Modes](#%E2%93%9C%EF%B8%8F-operational-modes)
- [🔀 Troubleshooting](#-troubleshooting)
- [🤼‍♂️ Interacting with Hedera Local Node](#%EF%B8%8F-interacting-with-hedera-local-node)

---

### 🆘 Community and Support

Join our community for support, discussions, and updates:

- [Discord](https://hedera.com/discord): Real-time connection with Hedera team and community.
- [X (Twitter)](https://x.com/hedera): Latest news and insights from Hedera.
- [Telegram](https://t.me/hederahashgraph): Share ideas and stay informed with Hedera users.
- [Meetups](https://docs.hedera.com/hedera/support-and-community/meetups): Learn and connect at community meetups.
- [Events](https://hedera.com/events): Engage in discussions and explore Hedera ecosystem.

### 🤝 Contributions and partnerships

We value community contributions and are eager to support your involvement. Here’s how you can contribute:

- ⭐ Give Hedera Local Node a [star on GitHub](https://github.com/hashgraph/hedera-local-node/stargazers).
- 📝 Share your thoughts on [X (Twitter)](https://x.com/hedera).
- 🐞 [Report bugs](https://github.com/hashgraph/hedera-local-node/issues/new?assignees=&labels=bug&projects=&template=bug.yml) or [suggest new features](https://github.com/hashgraph/hedera-local-node/issues/new?assignees=&labels=enhancement&projects=&template=enhancement.yml).
- 📣 Encourage others to explore and use Hedera Local Node.

> ### 💡 TIP
> If you're ready to make PRs but unsure where to start, join our [Discord](https://hedera.com/discord), and we'll guide you through some beginner-friendly issues.

## 💻 Hardware Requirements
The following specifications outline the minimal hardware requirements required to run the Hedera Local Node for different usage scenarios.

| Requirement                                        | Minimum Version       | Check Command             |
|----------------------------------------------------|-----------------------|---------------------------|
| [Node.js](https://nodejs.org/)                     | `>= v14.x`            | `node -v`                 |
| NPM                                                | `>= v6.14.17`         | `npm -v`                  |
| [Docker](https://www.docker.com/)                  | `>= v20.10.x`         | `docker -v`               |
| [Docker Compose](https://docs.docker.com/compose/) | `>= v2.12.2`          | `docker compose version`  |
| RAM                                                | Minimum 16GB          | N/A                       |


Ensure the following settings are set in your Docker Desktop app: 
- Ensure the following configurations are set at minimum in `Docker Settings -> Resources` and are available for use:
  | Resource              | Minimum Requirement    |
  |-----------------------|------------------------|
  | **CPUs**              | 6                      |
  | **Memory**            | 8GB                    |
  | **Swap**              | 1GB                    |
  | **Disk Image Size**   | 64GB                   |
  
   ![Hedera Local Node Img1](https://github.com/wolz-CODElife/docs-hedera-local-node/assets/55518764/f86813ef-f40a-43ef-9555-7e1c89965bc3)
- Enable `VirtioFS` file sharing in Docker settings.
  ![Hedera Local Node Img0](https://github.com/wolz-CODElife/docs-hedera-local-node/assets/55518764/7466b587-22b0-435e-b318-cbbacbcfecc6)
- Enable `Allow the default Docker sockets to be used (requires password)` in Docker settings.
  ![Hedera Local Node Img2](https://github.com/wolz-CODElife/docs-hedera-local-node/assets/55518764/122adb1e-782e-4937-8fc7-9285f83d9e73)


> ### 🚨 Note
> We intend the above specifications as a guideline. The minimal requirements support basic node operations, and may require increasing the parameters to ensure optimal performance and scalability for advanced needs.
> 
> The images may look different if you are on a different version

## 🚀 Setting up Hedera Local Node
You can run the Hedera Local Node in the following environments below:
- Docker container (We will walk through this in this guide)
- [Cloud Development Environment (CDE)](https://docs.hedera.com/hedera/tutorials/local-node/how-to-run-hedera-local-node-in-a-cloud-development-environment-cde)
- [Gitpod](https://docs.hedera.com/hedera/tutorials/local-node/how-to-run-hedera-local-node-in-a-cloud-development-environment-cde/gitpod)
- [GitHub Codespaces](https://docs.hedera.com/hedera/tutorials/local-node/how-to-run-hedera-local-node-in-a-cloud-development-environment-cde/codespaces)


### Installation
To set up Hedera Local Node, you need to install the following components:

1. Node.js and NPM: Install Node.js (version `>= v14.x`) and NPM (version `>= v6.14.17`) by following the [official installation guide](https://nodejs.org/).

2. Docker: Install Docker (version `>= v20.10.x`) and Docker Compose (version `>= v2.12.2`). Refer to the [Docker Setup Guide](https://docs.docker.com/get-docker/) for detailed instructions. Note that setup steps may vary based on your operating system.

3. CLI Tool: Use the following command to install the official release from the NPM repository:
   ```bash
   npm install @hashgraph/hedera-local -g
   ```
   This version includes a pre-configured Docker Compose setup and does not reflect any local changes made to the repository.

   For testing against the latest changes or specific branches/tags, install the `hedera-local` module as a symlink to your locally checked out copy of the repository:
   ```bash
   npm install && npm install -g
   ```
   
> ### 🚨 Note
> This version may not reflect the most recent changes to the main branch of this repository. It also uses a baked in version of the Docker Compose definitions and will not reflect any local changes made to the repository.

### Clone the Local Network

Open a new terminal and navigate to your preferred directory where your Hedera Local Node project will reside. Run the following commands to clone the repository and install dependencies on your local machine:

```bash
git clone https://github.com/hashgraph/hedera-local-node.git
cd hedera-local-node
npm install
```

> ### 🚨 Note
> For Windows users: You will need to update the file endings of `compose-network/mirror-node/init.sh` to enable compatibility with Unix-based systems by running this command in WSL:
>
> ```bash
> dos2unix compose-network/mirror-node/init.sh
> ```

### Start the Local Network

Before launching the network commands, ensure Docker is open on your machine. Note that the network will not start if Docker is not installed as per the above steps.

To start the local network, run the command below in the `/hedera-local-node` directory:
```bash
npm run start
```
> ### 💡 Tip
> You can pass the following CLI flags, this would be used later in the following sections:
> ```
> --d / --detached - Start the local node in detached mode.
> --h / --host - Override the default host.
> ```

To generate default accounts and start the local node in detached mode, use the command below:
```bash
// starts and generates the first 30 accounts
npm run start -- -d

or

// will start local node but will not generate the first 30 accounts
docker compose up -d
```

#### Stop the Local Network

To stop the local network:

```bash
npm run stop
```
```bash
docker compose down -v; git clean -xfd; git reset --hard
```

#### Restart the Local Network

To restart the local network:

```bash
npm run restart
```

#### Generate New Accounts

To generate new accounts for an already started network:

```bash
npm run generate-accounts
```

![image](https://github.com/wolz-CODElife/docs-hedera-local-node/assets/55518764/8a264e2b-7a37-4e13-a081-f0c9a5b95d91)

#### Using Generated Accounts with Hardhat
After generating accounts with the Hedera Local Node, you can use them in your Hardhat project by adding the following configuration to your `hardhat.config.js` file. This setup allows you to connect to your local Hedera network and use the generated accounts for development and testing.

```javascript
module.exports = {
  defaultNetwork: 'local',
  networks: {
    local: {
      url: 'http://localhost:7546',
      accounts: [
        '0x2e9771d364ba136b2297ffdccd93e2d017c117849bab82f33fb14eeace41d441',
        '0x41c8e78124f5aafdaa9a54bf4f855512babe666b1392be3dc465038d44a25cc5',
        '0xbf1ec97a9377e4121e03473bd8b272db65423028acf7f58acd8f8f7aca59d261',
        '0xcb2341159b97cb4c41f2a662d026fc9716c7bc4ede2b86b5dcff71fce4a68550',
        '0xee7472142c658abdee740a311ae04605ab1da4ced1115c9c38ebc1500644a05e',
        '0xfd9ab427ca33bbc161644b738b30b31194b6d241e3d4c5c136c44c679f3957dc',
        '0x47929231a2fd6373e1b04187bfb293098c1918c863e329820146a3294855376c',
        '0xe6575188817f863f7387790e03465a70acc7c346b2261c0c6165ed6c42910547',
        '0x621a90cdf84e7fdc350b16311818dfe4c841be13c1f18e55ebad56dd88f2482e',
        '0x5812380e2af0f3e10a958d468940b3e152d8a1bde5b0969073cd4d72dfab2491',
      ],
      chainId: 298,
    },
    testnet: {
      url: 'https://testnet.hashio.io/api',
      accounts: [],
      chainId: 296,
    },
  },
};
```
- **defaultNetwork:** Sets the default network to 'local', so Hardhat uses your local Hedera node by default.
- **networks.local:** Configuration for the local Hedera network.
  - **url:** Specifies the URL of the local Hedera network.
  - **accounts:** Lists the private keys of the generated accounts. These keys are used to sign transactions in your local network.
  - **chainId:** Sets the chain ID for the local network. For Hedera Local Node, use `298`.

> ### 🚨 Note
> Generated accounts are 3 types (ECDSA, Alias ECDSA and ED25519). All of them are usable via HederaSDK. Only Alias ECDSA accounts can be imported into wallet like Metamask or used in ethers.
> 
> Read more about [developer mode here](https://github.com/hashgraph/hedera-json-rpc-relay/blob/main/docs/dev-mode.md)

This configuration enables seamless interaction with your local Hedera network using the accounts you generated, facilitating development and testing within the Hardhat environment.

## 🛠️ Configuration Options

Running your initial prototype on a Single Local Node allows for quick iterations and debugging in a controlled environment. If your app needs to handle more complex scenarios, run the Multinode configuration. 

Single-node configuration simulates the network's functions on a smaller scale (on a single node), ideal for debugging, testing, and prototype development. Multi-node configuration distributes multiple instances of the Hedera network nodes across a single machine using Docker containers, intended for advanced testing and network emulation.

- [Single Node Configuration](https://docs.hedera.com/hedera/networks/localnet/single-node-configuration)  
- [Multinode Configuration](https://docs.hedera.com/hedera/networks/localnet/multinode-configuration)

### Available Commands

| Command | Flag | Default Value | Description |
|---------|------|---------------|-------------|
| `start` | --d or --detached | | Starts the local Hedera network in detached mode. |
| | --verbose | info | Sets the verbose level. Choices are "info" & "trace". |
| | --h or --host   | | Overrides the default host. |
| | --l or --limits | true | Enables/disables the JSON-RPC relay rate limits. |
| | --dev | | Enables/disables developer mode. |
| | --full | | Enables/disables full mode (Production local-node). |
| | --multinode | | Enables/disables multi-node mode. |
| | --balance | | Sets the starting hbar balance of the created accounts. |
| | --async | | Enables/disables asynchronous creation of accounts. |
| | --b or --blocklist| | Enables/disables account blocklisting, affecting generated startup accounts. |
| | --enable-debug | false | Enables/disables debugging of the local node. |
| | --network-tag | | Selects custom network node tag. |
| | --mirror-tag | | Selects custom mirror node tag. |
| | --relay-tag | | Selects custom hedera-json-rpc relay tag. |
| | --workdir | "[USER APP DATA]/hedera-local" | Path to the working directory for local node. |
| `stop` | | | Stops the local Hedera network and deletes all existing data. |
| `restart` | | | Restarts the local Hedera network. |
| `generate-accounts <n>`| --h or --host | | Generates N accounts (default 10). Overrides the default host. |
| | --balance | | Sets the starting hbar balance of the created accounts. |
| | --async | | Enables/disables asynchronous creation of accounts. |
| `debug [timestamp]` | | | Parses and prints the contents of the record file created during the selected timestamp. |
| | --enable-debug | false | Enables this feature. Local node must be started with the -g, --enable-debug flag. |

## Ⓜ️ Operational Modes
Hedera Local Node operates in two primary modes, Full Mode and Turbo Mode, each designed to cater to different development and testing needs.

- Full Mode: Designed for comprehensive data capture and storage, ideal for detailed testing and analysis:
  - **Data Upload:** Each node generates record stream files during operation. These files are systematically uploaded to their own directory within a MinIo bucket. MinIo is an object storage platform that provides tools for storing, retrieving, and searching blobs of data.
  - **Uploader Containers:** Specific uploader containers are assigned to each node to manage the data uploads. These include:
    - `record-streams-uploader-N`: Contains the record streams, which are sequences of transaction records grouped over specific intervals.
    - `account-balances-uploader-N`: Contains files detailing account balances.
    - `record-sidecar-uploader-N`: Contains lists of `TransactionSidecarRecords`, which are related to the same `RecordStreamFile` and provide additional context for transactions.

  This mode is useful for scenarios where detailed and persistent data storage is required for thorough analysis and debugging.

- Turbo Mode: Focuses on efficiency and speed, making it suitable for rapid development and scenarios where immediate data access is crucial:
  - **Local Data Access:** Instead of uploading data to an external storage, record stream files are read directly from their corresponding local directories on each node. This approach significantly reduces latency and resource consumption.
  - **Performance Optimization:** By eliminating the need to upload data, Turbo Mode minimizes the overhead and maximizes performance, providing faster feedback and quicker iterations during development.
  
  Turbo Mode is ideal for situations where the priority is on high performance and immediate data access, rather than long-term data storage.

## 🔀 Troubleshooting
Find below some common errors and how to troubleshoot them:

> ### Error: Node cannot start properly because necessary ports are in use!
>
> When attempting to start the Hedera Local Node, you might encounter an error indicating that certain ports are in use. This prevents the node from starting properly. Here is an example of the error message:
>
> ```plaintext
> hedera-local-node % npm run start -- -d
> > @hashgraph/hedera-local@2.26.2 start
> > npm run build && node ./build/index.js start -d
>
> > @hashgraph/hedera-local@2.26.2 build
> > rimraf ./build && tsc
>
> [Hedera-Local-Node] INFO (StateController) [✔︎] Starting start procedure!
> [Hedera-Local-Node] INFO (InitState) ⏳ Making sure that Docker is started and it is correct version...
> [Hedera-Local-Node] INFO (DockerService) ⏳ Checking docker compose version...
> [Hedera-Local-Node] INFO (DockerService) ⏳ Checking docker resources...
> [Hedera-Local-Node] ERROR (DockerService) [✘] [✘] Port 5551 is in use.
> [Hedera-Local-Node] ERROR (DockerService) [✘] [✘] Port 8545 is in use.
> [Hedera-Local-Node] ERROR (DockerService) [✘] [✘] Port 5600 is in use.
> [Hedera-Local-Node] ERROR (DockerService) [✘] [✘] Port 5433 is in use.
> [Hedera-Local-Node] ERROR (DockerService) [✘] [✘] Port 8082 is in use.
> [Hedera-Local-Node] ERROR (DockerService) [✘] [✘] Port 6379 is in use.
> [Hedera-Local-Node] WARNING (DockerService) [!] Port 7546 is in use.
> [Hedera-Local-Node] WARNING (DockerService) [!] Port 8080 is in use.
> [Hedera-Local-Node] WARNING (DockerService) [!] Port 3000 is in use.
> [Hedera-Local-Node] ERROR (DockerService) [✘] [✘] Node cannot start properly because necessary ports are in use!
> ```
>
> ### Suggested Fix
> 
> ##### Option 1: Generate New Accounts
>
>Instead of starting another instance of the network, use the command below to generate new accounts for an already running network:
>
> ```bash
> npm run generate-accounts
> ```
> 
> #### Option 2: Terminate Existing Processes
>
> If the above error occurs, ensure that you terminate any existing Docker processes for the local node and any other processes that are bound to these port numbers before running the `npm start` command. You can use the following commands to stop and clean up the Docker environment:
>
> ```bash
> docker compose down -v
> git clean -xfd
> git reset --hard
> ```

By stopping and cleaning up existing processes, you free up the necessary ports, allowing the Hedera Local Node to start properly.

## 🤼‍♂️ Interacting with Hedera Local Node
Interacting with Hedera Local Node involves various methods for submitting transactions, querying the network, and deploying smart contracts. Below are some essential references and explanations of key configurations.

### Network Variables

These are the local network variables to interact with the consensus and mirror nodes.

| Variable | Value | Description |
|----------|-------|-------------|
| Consensus Node Endpoint | `127.0.0.1:50211` | The IP address and port of the local consensus node. |
| Consensus Node Account ID | `0.0.3` | The node account ID to submit transactions and queries to. |
| Mirror Node GRPC Endpoint | `127.0.0.1:5600` | The mirror node network to use. |
| Mirror Node REST API Endpoint | `127.0.0.1:5551` | The endpoint to submit REST API requests to. |
| Account ID | `0.0.2` | The account ID to use to pay for transactions and queries. |
| Account Key | `302e0201003005...` | The private key to account 0.0.2 to sign transactions and queries with. |

### Folder Setup

The folder setup for Hedera Local Node includes various directories needed for configuration and operation.
```lua
hedera-local-node/
├── compose-network/
│   ├── grafana/
│   │   ├── dashboards/
│   │   └── datasources/
├── network-logs/
```

| Folder | Description |
|--------|-------------|
| `compose-network` | Contains static files needed for starting the local network. |
| `compose-network/grafana/dashboards` | Contains Grafana dashboard definitions in JSON format. Provisioned automatically at startup. |
| `compose-network/grafana/datasources` | Contains Grafana datasource definitions in YAML format. Provisioned automatically at startup. |
| `network-logs` | Created at runtime in the working directory, contains all log files generated after starting the local node. |

The local node writes its ephemeral data to a working directory, which can be set using the `--workdir` flag. The default directory depends on the OS:

| OS       | Default Working Directory                      |
|----------|------------------------------------------------|
| MacOS    | `~/Library/Application Support/hedera-local`   |
| Linux    | `~/.local/share/hedera-local`                  |
| Windows  | `%USERPROFILE%\AppData\Local\hedera-local`     |

### Environment Variables

To modify memory limits, properties, and other configurations, update the `.env` file:

| Component        | Environment Variable            |
|------------------|---------------------------------|
| Platform         | `PLATFORM_JAVA_HEAP_MIN`, `PLATFORM_JAVA_HEAP_MAX` |
| Consensus Node   | `NETWORK_NODE_MEM_LIMIT`        |
| Mirror Node      | `MIRROR_GRPC_MEM_LIMIT`, `MIRROR_IMPORTER_MEM_LIMIT`, `MIRROR_REST_MEM_LIMIT`, `MIRROR_WEB3_MEM_LIMIT` |

To change properties in `application.properties`, `api-permission.properties`, or `bootstrap.properties`, update the `APPLICATION_CONFIG_PATH` to the location of the updated config folder in the `.env` file.

> ### 🚨 Note
> Ensure to run `docker compose down -v`, `git clean -xfd`, and `git reset --hard` before `docker compose up -d` for the changes to take effect.

### Exposed Endpoints

| Type                              | Endpoint                           |
|-----------------------------------|------------------------------------|
| Consensus Node Endpoint           | `http://localhost:50211`           |
| Mirror Node GRPC Endpoint         | `http://localhost:5600`            |
| Mirror Node REST API Endpoint     | `http://localhost:5551`            |
| JSON RPC Relay Endpoint           | `http://localhost:7546`            |
| JSON RPC Relay Websocket Endpoint | `http://localhost:8546`            |
| Mirror Node Explorer              | `http://localhost:8080`            |
| Grafana UI                        | `http://localhost:3000`            |
| Prometheus UI                     | `http://localhost:9090`            |

### Grafana & Prometheus

- **Accessing Prometheus:** Access the deployed Prometheus instance at [http://localhost:9090](http://localhost:9090). No credentials are required.
- **Accessing Grafana:** Access the deployed Grafana instance at [http://localhost:3000](http://localhost:3000). Use the default credentials:
  - User Name: `admin`
  - Password: `admin`
- **Adding New Dashboards:** Export dashboards as JSON definitions and place them in the `compose-network/grafana/dashboards` folder to ensure automatic restoration after `docker compose down -v`.

### Verifying Running Node

There are different ways to verify that a node is running:

1. **Check Block Number using Hashscan Block Explorer:**
   - Visit the local mirror node explorer endpoint at [http://localhost:8080/devnet/dashboard](http://localhost:8080/devnet/dashboard).
   - Ensure that `LOCALNET` is selected from the dropdown at the top right corner in the Node Explorer Dashboard to view the Hedera network running within your local network.
     ![image](https://github.com/wolz-CODElife/docs-hedera-local-node/assets/55518764/9084ae27-03c9-4674-b9e1-8dce78b56ec1)
   - Select any listed block to view details such as Consensus, Block, Transaction Hash, etc.
     ![image](https://github.com/wolz-CODElife/docs-hedera-local-node/assets/55518764/78bfd29b-68b9-453a-9256-f6598b516560)
2. **Send cURL request to getBlockNumber:**
   Verify interaction with Hedera Testnet using JSON-RPC by issuing an `eth_getBlockByNumber` JSON-RPC request:

   ```bash
   curl http://localhost:7546/ \
   -X POST \
   -H "Content-Type: application/json" \
   --data '{"method":"eth_getBlockByNumber","params":["latest",false],"id":1,"jsonrpc":"2.0"}'
   ```

   You should receive a response with the block details.

### Other Methods

For more detailed information on interacting with your local network, refer to the following documentation:

- **Set up a local network:**  You can interact with the consensus node in the following ways:
  - Create and submit transactions and queries to a consensus node
  - Interact with the mirror node via REST APIs
  
  For detailed instructions, refer to the [Hedera SDK documentation](https://docs.hedera.com/hedera/sdks-and-apis/sdks/set-up-your-local-network).
- **Interact with the Mirror Node via REST APIs:** Access historical data and transaction records using the mirror node's REST APIs.

  More information can be found in the [Hedera REST API documentation](https://docs.hedera.com/hedera/sdks-and-apis/apis/rest-api).
- **Deploy Smart Contracts:** You can deploy and interact with smart contracts on Hedera.

  For a step-by-step guide, visit the [Hedera Smart Contracts tutorial](https://docs.hedera.com/hedera/tutorials/smart-contracts).

These references provide comprehensive guides on creating and submitting transactions, interacting with the mirror node via REST APIs, and deploying smart contracts on the Hedera network.

## 📄 License

[Apache License 2.0](https://github.com/hashgraph/hedera-json-rpc-relay/blob/main/LICENSE)

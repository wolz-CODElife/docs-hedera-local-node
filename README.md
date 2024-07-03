# Welcome to Hedera Local Node 👋
THe Hedera Local Node is a single node that replicates the Hedera network on a development environment/local machine offering a controlled environment for developing, testing, and experimenting with [decentralized applications (dApps)](https://docs.hedera.com/hedera/support-and-community/glossary#decentralized-application-dapp).

- ⚡ Rapid Initialization: Fast startup and synchronization, ensuring quick iterations during development.
- 💯 Comprehensive Hedera API Support: Full support for [Hedera APIs](https://docs.hedera.com/hedera/sdks-and-apis), enabling seamless interaction with the local network.
- 🔎 Low Latency: Minimal response times for RPC calls, ensuring efficient and smooth application performance.
- 🛠️ Controlled Environment: Provides a controlled and isolated environment for testing and debugging, reducing the risk of conflicts with other network resources.

### 🏃‍♂️ Getting started
Learn how to set up, configure and manage your Hedera Local Node using the following resources:

- 💻 Hardware Requirements
- 🚀 Setting up Hedera Local Node
- Configuration Options
- Operational Modes
- Interacting with Hedera Local Node
- Download a Snapshot

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
> The image may look different if you are on a different version

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

> ### 🤷🏼‍♂️ Optional
> For Windows users: You will need to update the file endings of `compose-network/mirror-node/init.sh` by running this command in WSL:
>
> ```bash
> dos2unix compose-network/mirror-node/init.sh
> ```

### Start the Local Network



## Setup and Configuration

### Single-Node Configuration

Single-node configuration simulates a Hedera network with a single node on your local machine. This setup is ideal for initial development, debugging, and testing.

### Multi-Node Configuration

Multi-node configuration allows you to distribute multiple instances of Hedera network nodes across a single machine using Docker containers. This setup is intended for advanced testing and network emulation.


## Operational Modes

### Full Mode

In Full Mode, the system captures and stores comprehensive data:

- **Data Upload:** Each node generates record stream files during operation. These files are uploaded to their own directory within the MinIo bucket.
- **Uploader Containers:** Managed by specific uploader containers assigned to each node, including:
  - `record-streams-uploader-N` (contains record streams)
  - `account-balances-uploader-N` (contains account balances files)
  - `record-sidecar-uploader-N` (contains a list of `TransactionSidecarRecords`)

### Turbo Mode

Turbo Mode prioritizes efficiency and speed:

- **Local Data Access:** Record stream files are read directly from their corresponding local directories on each node. This method reduces latency and resource consumption, making it ideal for scenarios where immediate data access and high performance are prioritized.


## CLI Tool

The CLI tool (`@hashgraph/hedera-local`) provides commands for interacting with the local Hedera network.

### Installation

#### Official NPM Release

Install the official release from the NPM repository:

```bash
npm install @hashgraph/hedera-local -g
```

#### Local Development Installation

Install the `hedera-local` module as a symlink against your locally checked out copy of this repository:

```bash
npm install && npm install -g
```

### Usage

- Start the network: `npm run start`
- Restart the network: `npm run restart`
- Stop the network: `npm run stop`
- Generate new accounts: `npm run generate-accounts`

### CLI Commands

```
$ hedera

Local Hedera Package - Runs consensus and mirror nodes on localhost:
- consensus node URL: 127.0.0.1:50211
- node ID: 0.0.3
- mirror node URL: http://127.0.0.1:5551

Available commands:
    start - Starts the local Hedera network.
        options:
            --d or --detached
            --verbose
            --h or --host
            --l or --limits
            --dev
            --full
            --multinode
            --balance
            --async
            --b or --blocklist
            --enable-debug
            --network-tag
            --mirror-tag
            --relay-tag
            --workdir
    stop - Stops the local Hedera network and deletes all existing data.
    restart - Restart the local Hedera network.
    generate-accounts <n> - Generates N accounts, default 10.
        options:
            --h or --host
            --balance
            --async
    debug [timestamp] - Parses and prints the contents of the record file that has been created during the selected timestamp.
```


## Docker

### Setup

1. Clone the `hedera-local-node` repository:

```bash
git clone https://github.com/hashgraph/hedera-local-node.git
```

2. Navigate to the `hedera-local-node` directory:

```bash
cd hedera-local-node
```

3. For Windows users: Update file endings of `compose-network/mirror-node/init.sh`:

```bash
dos2unix compose-network/mirror-node/init.sh
```

4. Start the network:

```bash
docker compose up -d
```

### Managing the Network

- **Stop the Network:**

```bash
docker compose down -v; git clean -xfd; git reset --hard
```


## Network Variables

- **Consensus Node Endpoint:** `127.0.0.1:50211`
- **Consensus Node Account ID:** `0.0.3`
- **Mirror Node GRPC Endpoint:** `127.0.0.1:5600`
- **Mirror Node REST API Endpoint:** `127.0.0.1:5551`
- **Account ID:** `0.0.2`
- **Account Key:** `302e020100300506032b65700422042091132178e72057a1d7528025956fe39b0b847f200ab59b2fdd367017f3087137`

---

## Folder Setup

1. `compose-network`: Contains static files needed for starting the local network.
2. `compose-network/grafana/dashboards`: Contains Grafana dashboard definitions in JSON format.
3. `compose-network/grafana/datasources`: Contains Grafana datasource definitions in YAML format.
4. `network-logs`: Created at runtime, containing log files generated after starting the local node.


## Grafana & Prometheus

### Accessing Prometheus

- URL: [http://localhost:9090](http://localhost:9090)
- No credentials required.

### Accessing Grafana

- URL: [http://localhost:3000](http://localhost:3000)
- Default credentials: `admin` / `admin`

### Adding New Dashboards

Dashboards can be exported as JSON definitions and placed in the `compose-network/grafana/dashboards` folder to ensure they are automatically restored after a `docker compose down -v` or equivalent operation.


## 📄 License

[Apache License 2.0](https://github.com/hashgraph/hedera-json-rpc-relay/blob/main/LICENSE)

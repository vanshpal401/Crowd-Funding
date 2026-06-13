# 🌟 Genesis - Decentralized Web3 Crowdfunding Platform

Genesis is a premium, feature-rich Web3 crowdfunding application built with **Solidity**, **Hardhat**, **React (v17)**, **Tailwind CSS**, and **Ethers.js**. It enables creators to initiate crowdfunding campaigns directly on the blockchain and allows contributors to back projects with ether safely.

Features include automated payouts, transaction fees (tax) directed to the platform owner, real-time stats tracking, and a dynamic frontend UI with toast notifications.

---

## ✨ Key Features

- **MetaMask Wallet Integration**: Smooth connection flow to read user balances and accounts.
- **Campaign Management**: Creators can create, update, or delete campaign details (such as target goal, deadline, description, and image URL).
- **Safe & Transparent Funding**: Backers can pledge ether to any open project. Contributions are locked in the smart contract.
- **Automated Payouts**: Once a campaign reaches 100% of its funding goal, funds are immediately disbursed (less a 5% platform tax sent to the contract owner).
- **Automatic Refunds**: If a campaign is deleted by the creator, all contributions are automatically returned to the backers.
- **Global Platform Stats**: Real-time tracking of total campaigns launched, total backings, and cumulative ether donated.
- **Activity & Logs**: Displays a contribution ledger containing detailed logs of backers and their pledges for each campaign.

---

## 🛠️ Tech Stack & Libraries

- **Smart Contract Layer**:
  - [Solidity v0.8.11](https://soliditylang.org/) — Smart contract language.
  - [Hardhat](https://hardhat.org/) — Ethereum development environment for compiling, deploying, and testing contracts.
  - [Ethers.js v5](https://docs.ethers.org/v5/) — Library to interact with the Ethereum Blockchain and smart contract.
- **Frontend Layer**:
  - [React JS (v17)](https://react.dev/) — User interface framework.
  - [Tailwind CSS v3](https://tailwindcss.com/) — Modern utility-first CSS styling.
  - [React Hooks Global State](https://github.com/n1ru4l/react-hooks-global-state) — Lightweight global state management.
  - [React Router DOM v6](https://reactrouter.com/) — Client-side routing.
  - [React Toastify](https://github.com/fkhadra/react-toastify) — Smooth browser notifications.
  - [Moment.js](https://momentjs.com/) — Date and time parsing.
- **Hosting & Deployment**:
  - [Firebase Hosting](https://firebase.google.com/) — Fast and secure static hosting.

---

## 📁 Project Structure

```text
crowd-funding/
├── .firebase/             # Firebase build cache
├── build/                 # Compiled production frontend files
├── hardhat.config.js      # Hardhat configuration file
├── package.json           # Project dependencies & scripts
├── postcss.config.js      # PostCSS configuration for Tailwind
├── tailwind.config.js     # Tailwind CSS theme customization
├── config-overrides.js    # Custom Webpack re-wiring for React
├── scripts/
│   └── deploy.js          # Hardhat deployment script for Genesis contract
└── src/
    ├── App.jsx            # Main App entry containing route mapping
    ├── index.css          # Core CSS stylesheet importing Tailwind
    ├── index.jsx          # React app startup script
    ├── abis/              # Compiled contract ABIs and deployed address json
    ├── components/        # Reusable React UI components
    │   ├── Header.jsx         # Navigation bar & Wallet connector
    │   ├── Hero.jsx           # Welcome section displaying platform stats
    │   ├── Projects.jsx       # Grid lists showing all active projects
    │   ├── ProjectDetails.jsx # Detailed single-project viewer
    │   ├── CreateProject.jsx  # Popup modal to launch a campaign
    │   ├── UpdateProject.jsx  # Popup modal to edit campaign info
    │   ├── DeleteProject.jsx  # Popup modal to delete project (refunds backers)
    │   ├── BackProject.jsx    # Popup modal to pledge ether contributions
    │   └── ProjectBackers.jsx # Table layout for campaign backers
    ├── contracts/         # Solidity smart contracts
    │   └── Genesis.sol        # Core crowdfunding Solidity contract
    ├── services/          # Blockchain helper services
    │   └── blockchain.jsx     # Functions mapping React to contract methods
    ├── store/             # Global variables state registry
    └── views/             # App views/pages
        ├── Home.jsx           # Main home page
        └── Project.jsx        # Project details view page
```

---

## 🚀 Getting Started

### 📋 Prerequisites
Make sure you have the following installed on your machine:
- [Node.js](https://nodejs.org/) (v14+ recommended)
- [Yarn](https://yarnpkg.com/) or NPM
- [MetaMask Wallet Extension](https://metamask.io/) in your browser.

---

### ⚙️ Local Development Setup

Follow these steps to set up and run the project locally:

#### 1. Install Dependencies
Run the following command in the root folder to install all packages:
```bash
yarn install
```

#### 2. Start Local Ethereum Blockchain Node
Launch the local blockchain emulator provided by Hardhat:
```bash
yarn hardhat node
```
*Keep this terminal running. It will output a list of 20 accounts with their corresponding private keys, loaded with 10,000 mock ETH each.*

#### 3. Deploy the Smart Contract
Open a new terminal window and run the deployment script to compile and deploy the Genesis contract onto the local network:
```bash
yarn hardhat run scripts/deploy.js --network localhost
```
*This script will compile the contract, deploy it to localhost, and write the address and ABI configurations directly to `src/abis/` for the frontend to consume.*

#### 4. Configure MetaMask for Localhost
To connect MetaMask to your local node:
1. Open the **MetaMask** browser extension.
2. Click the Network dropdown at the top and select **Add network** -> **Add a network manually**.
3. Set the configurations:
   - **Network Name**: `Hardhat Localhost`
   - **New RPC URL**: `http://127.0.0.1:8545`
   - **Chain ID**: `31337`
   - **Currency Symbol**: `ETH`
4. Save the network and switch to it.
5. Import an account using one of the **Private Keys** printed by `yarn hardhat node` to get access to test ETH.

#### 5. Start the React Frontend App
Start the development server:
```bash
yarn start
```
Your browser should open automatically to `http://localhost:3000`. You can now connect your wallet and interact with the platform!

---

## 🧪 Running Tests
To run the automated test suite for the crowdfunding smart contract, run:
```bash
yarn hardhat test
```

---

## 🌐 Deployment to Firebase Hosting

To build the React application and deploy it to Firebase Hosting, run:

```bash
# 1. Build the optimized production distribution files
yarn build

# 2. Deploy to the configured Firebase project (genesis-45443)
firebase deploy
```

---

## 🛡️ License
Distributed under the MIT License. See `LICENSE` or contact developers for more details.

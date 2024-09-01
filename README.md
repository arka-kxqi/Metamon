
# Metamon

## Overview

**Metamon** is a pioneering project that I developed, building on the innovative Metagraph framework of the Constellation Network. This application-specific blockchain harnesses the power of NFTs, token distribution mechanisms, and social credit systems to create a dynamic, user-centric ecosystem. Metamon is designed to incentivize positive community engagement and foster a thriving decentralized environment by seamlessly integrating functionalities such as NFT management, token faucets, and social credit tracking.

## Disclaimer

This project, **Metamon**, is applicable to both the Metagraph Projects and On-Chain Tooling tracks in the hackathon. It leverages the Euclid SDK to create innovative metagraph functionalities while also developing tools that enhance interaction with Constellation's network components, making it relevant for both categories.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
  - [NFT Metagraph](#nft-metagraph)
  - [Token Faucet](#token-faucet-based-on-api-data)
  - [Elpaca Metagraph](#elpaca-metagraph)
- [Architecture](#architecture)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Sample UI](#sample-ui)
- [Contribution](#contribution)
- [Resources and Support](#resources-and-support)
- [License](#license)

## Introduction

Welcome to **Metamon**, a unique project that I've created for the Constellation Metagraph Hackathon. Metamon serves as a showcase for the versatility and scalability of the Constellation Network, demonstrating how application-specific blockchains can be leveraged to integrate multiple functionalities effectively. With features ranging from NFT management to dynamic token distribution and social credit tracking, Metamon illustrates the potential of the Constellation ecosystem in redefining user interaction and incentivization within the blockchain space.

## Features

### NFT Metagraph

At the core of Metamon is a comprehensive NFT management system, based on the ERC-721 standard but optimized for the Constellation Network's architecture. The system allows users to:

- **Mint NFT Collections**: Create and organize NFTs into distinct collections.
- **Mint NFTs**: Generate unique NFTs within a specific collection.
- **Transfer NFT Collections**: Easily transfer ownership of entire NFT collections.
- **Transfer NFTs**: Enable the transfer of individual NFTs between wallets.

**Data Access via Metagraph REST APIs:**

- Retrieve all NFT collections.
- Retrieve a specific collection by ID.
- Retrieve all NFTs within a collection.
- Retrieve a specific NFT within a collection by ID.
- Find all collections owned by a specific address.
- Find all NFTs owned by a specific address.

### Token Faucet Based on API Data

Metamon includes a custom token faucet that facilitates fair and dynamic token distribution to eligible addresses, retrieved from a custom API endpoint.

- **Fixed Distribution**: Initially set to distribute 100 tokens, with the flexibility to adjust as needed.
- **API Integration**: Dynamically fetches addresses from the `/addresses` endpoint and distributes tokens accordingly.
- **Scalable Rewards**: Supports multiple wallets, ensuring proportional token distribution among eligible addresses.

### Elpaca Metagraph

The Elpaca Metagraph introduces an innovative social credit system that tracks and rewards positive community behaviors within the Metamon ecosystem.

- **Social Credit Tracking**: Monitors and incentivizes user engagement through a transparent credit system.
- **Data Sources and Workers**: Leverages automated data collection and processing to update social credits hourly.
- **Token Minting Rates**: Implements a reward structure for activities such as transactions, wallet creation, and social media engagement.

## Architecture

Metamon is architected as a series of interconnected modules, fully leveraging the capabilities of the Constellation Network's Metagraph framework:

- **Layer 0 (L0)**: The foundational layer handling core network operations.
- **Layer 1 (L1)**: Manages application-specific logic and state transitions.
- **Data Layer**: Manages data storage and retrieval via a dedicated Data API.
- **Shared Data**: Provides utility functions and common services across modules.

### Application Lifecycle

The application lifecycle of Metamon is managed through various methods, ensuring smooth operation and integration with the Constellation Network:

- **Validation Methods**: `validateUpdate`, `validateData`
- **State Management**: `combine`, `setCalculatedState`, `getCalculatedState`, `hashCalculatedState`
- **Serialization Methods**: `serializeBlock`, `deserializeBlock`, `serializeState`, `deserializeState`, `serializeUpdate`, `deserializeUpdate`
- **API Routes**: Custom endpoints facilitate interaction with the metagraph state.

For further details, refer to the [Constellation Network Documentation](https://docs.constellationnetwork.io/sdk/metagraph-framework/data/overview).

## Getting Started

### Prerequisites

- **Node.js** (v14 or later)
- **npm** (v6 or later)
- **Scala** (v2.13.x)
- **Docker** (optional, for containerization)
- **Conda SDK**: Ensure you have the Euclid SDK installed and configured.

### Installation

1. **Clone the Repository**

   ```bash
   git clone https://github.com/yourusername/metamon.git
   cd metamon
   ```

2. **Install Backend Dependencies**

   ```bash
   cd backend
   npm install
   ```

3. **Install Frontend Dependencies**

   ```bash
   cd ../sample-ui
   npm install
   ```

### Running the Application

1. **Start the Backend API**

   ```bash
   cd backend
   npm run dev
   ```

   The API will be accessible at `http://localhost:8000/addresses`.

2. **Start the Frontend UI**

   ```bash
   cd ../sample-ui
   npm start
   ```

   The UI will be accessible at `http://localhost:3000`.

3. **Deploy the Metagraph**

   Ensure that the metagraph is properly configured and connected to the Constellation Network. Refer to the [Metagraph Deployment Guide](https://docs.constellationnetwork.io/sdk/metagraph-framework/deployment) for detailed instructions.

## API Endpoints

Metamon offers a set of RESTful APIs for interacting with the NFT and token systems:

### NFT Endpoints

- `GET /data-application/collections`: Retrieve all NFT collections.
- `GET /data-application/collections/:collection_id`: Retrieve a specific collection by ID.
- `GET /data-application/collections/:collection_id/nfts`: Retrieve all NFTs within a collection.
- `GET /data-application/collections/:collection_id/nfts/:nft_id`: Retrieve a specific NFT by ID.
- `GET /data-application/addresses/:address/collections`: Retrieve all collections owned by an address.
- `GET /data-application/addresses/:address/nfts`: Retrieve all NFTs owned by an address.

### Token Faucet Endpoints

- `GET /addresses`: Retrieve the latest 20 stored addresses.
- `POST /addresses`: Store a new address.

  **Request Body:**

  ```json
  {
    "address": "DAG..."
  }
  ```

  **Responses:**

  - `201 Created`: Successfully stored the address.
  - `400 Bad Request`: Invalid DAG wallet address.

## Sample UI

Metamon includes a React-based frontend that interfaces with the metagraph and displays real-time data from the API endpoints. The UI provides an intuitive interface for users to:

- View and manage NFT collections and individual NFTs.
- Monitor token distributions and wallet balances.
- Track social credit scores and community engagement metrics.

**Features:**

- **Dashboard**: Overview of all collections and NFTs.
- **Minting Interface**: Create and manage NFT collections.
- **Token Faucet Dashboard**: View token distribution status and recent transactions.
- **Social Credit Tracker**: Monitor and display community engagement metrics.

Refer to the [sample-ui/README.md](./sample-ui/README.md) for additional details on the frontend setup and functionalities.

## Contribution

Contributions are welcome! If you're interested in enhancing Metamon, whether by fixing bugs, adding new features, or improving documentation, your efforts are greatly appreciated.

**Steps to Contribute:**

1. **Fork the Repository**
2. **Create a Feature Branch**

   ```bash
   git checkout -b feature/YourFeature
   ```

3. **Commit Your Changes**

   ```bash
   git commit -m "Add your feature"
   ```

4. **Push to the Branch**

   ```bash
   git push origin feature/YourFeature
   ```

5. **Open a Pull Request**

## Resources and Support

- **Constellation Network Documentation**: [https://docs.constellationnetwork.io](https://docs.constellationnetwork.io)
- **Euclid SDK Overview**: [Euclid SDK Documentation](https://docs.constellationnetwork.io/sdk/euclid/overview)
- **Metagraph Framework**: [Metagraph Documentation](https://docs.constellationnetwork.io/sdk/metagraph-framework/overview)
- **Support Email**: [support@metamonproject.com](mailto:support@metamonproject.com)

## Inspiration
The inspiration behind Metamon stems from the desire to create a dynamic blockchain ecosystem that integrates NFTs, token distribution, and social credit mechanisms to foster positive community engagement. We wanted to showcase the potential of the Constellation Network by building an application-specific blockchain that pushes the boundaries of decentralized interactions.

## What it does
Metamon is a blockchain platform built on the Constellation Network's Metagraph framework. It offers a robust NFT management system, a token faucet for dynamic distribution, and a social credit system that rewards positive user engagement. These features combine to create a comprehensive ecosystem that incentivizes and tracks community participation.

## How we built it
We built Metamon using the Euclid SDK, leveraging Scala to develop the metagraph functionalities. The platform's architecture integrates multiple modules that interact with the Constellation Network, including a Layer 1 metagraph for application logic, a data layer for storage and retrieval, and a shared data layer for common utilities. The front-end UI was developed using React, providing an intuitive interface for users.

## Challenges we ran into
One of the major challenges was integrating multiple functionalities into a single, cohesive platform while ensuring scalability and seamless interaction with the Constellation Network. We also faced difficulties in optimizing token distribution based on real-time API data and managing the social credit system across diverse data sources.

## Accomplishments that we're proud of
We're proud of successfully building a versatile and scalable blockchain platform that integrates various innovative features. The development of a robust NFT management system and a dynamic token distribution model that adapts to real-time data are significant achievements. Additionally, creating a social credit system that fosters positive community engagement is a major milestone.

## What we learned
Through this project, we gained deeper insights into the Constellation Network's Metagraph framework and the Euclid SDK. We learned how to effectively integrate NFTs, token distribution, and social credit mechanisms into a blockchain platform. Additionally, we enhanced our skills in managing and optimizing blockchain-based data systems and user engagement tracking.

## What's next for Metamon
In the future, we plan to expand Metamon's capabilities by integrating additional social credit features and enhancing the scalability of the platform. We aim to explore further opportunities within the Constellation ecosystem, including potential collaborations and expanding the metagraph functionalities to support new use cases. Additionally, we plan to refine the user interface and improve the overall user experience to attract a broader audience.
# Merkle Proof Verification of Blockchain Transactions

## Project Overview

- This application designed to interact with and verify Bitcoin blockchain Transaction data in real-time.
- It focuses on demonstrating the crucial concept of Merkle trees in blockchain technology, providing users with tools to verify transactions and understand how blockchain data integrity is maintained.
- Allowing users to select a transaction hash and Merkle proof to verify inclusion on-chain.
- Verifying Transaction Inclusion: accepts a transaction hash as inputs and verifies whether the transaction is part of the stored Merkle tree. It returns true if the proof is valid and false otherwise.

## Index

- [Core Functionality](#core-functionality)
  - [Block Information Display](#1-block-information-display)
  - [Merkle Root Verification System](#2-merkle-root-verification-system)
  - [Transaction Verification Module](#3-transaction-verification-module)
- [Technical Implementation](#technical-implementation)
  - [Frontend Architecture](#frontend-architecture)
  - [Backend Architecture](#backend-architecture)
  - [Security and Reliability Features](#security-and-reliability-features)
  - [External APIs](#external-apis)
- [API Endpoints](#api-endpoints)
- [Error Handling](#error-handling)
- [Component Structure](#component-structure)
- [Technical Challenges Addressed](#technical-challenges-addressed)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Environment Setup](#environment-setup)
- [Running the Application](#running-the-application)

## Core Functionality

### 1. Block Information Display

- **Real-time Data**: Fetches the latest Bitcoin block information from multiple reliable sources
- **Block Details**: Shows essential block information including:
  - Block hash
  - Block height
  - Number of transactions
  - Merkle root
- **Resilient Design**: Implements fallback mechanisms using multiple block explorer APIs to ensure reliable data access

### 2. Merkle Root Verification System

- **Dynamic Calculation**: Independently calculates the Merkle root from block transactions
- **Visual Comparison**: Provides a clear visual interface comparing:
  - The blockchain's stated Merkle root
  - The locally calculated Merkle root
- **Verification Process**:
  - Constructs a Merkle tree from transaction data
  - Performs hash calculations using the SHA-256 algorithm
  - Validates the integrity of the block's transaction data

### 3. Transaction Verification Module

- **Transaction Selection**: Allows users to choose specific transactions from the current block
- **Proof Generation**: Creates Merkle proofs demonstrating transaction inclusion
- **Visual Verification**: Shows step-by-step proof validation with:
  - Direction indicators (left/right hashing)
  - Intermediate hash values
  - Final verification result

## Technical Implementation

### Frontend Architecture

- **React Components**:
  1. `BlockInfo`: Manages and displays block data
  2. `MerkleRootVerification`: Handles Merkle root comparison
  3. `TransactionVerification`: Processes transaction verification
- **User Interface**:
  - Clean, intuitive design using Tailwind CSS
  - Responsive layout adapting to different screen sizes
  - Dark mode support for better user experience
  - Interactive elements with clear visual feedback

### Backend Architecture

- **API Integration**:
  - Multiple blockchain data sources for reliability
  - Fallback mechanism with exponential backoff
  - Error handling and data validation
- **Merkle Tree Implementation**:

  - Custom hash pair calculation
  - Buffer manipulation for correct byte ordering
  - Efficient proof generation algorithm

### Security and Reliability Features

1. **Data Integrity**:

   - Double SHA-256 hashing following Bitcoin protocol
   - Verification of all calculated values
   - Multiple data source validation

2. **Error Handling**:

   - Comprehensive error catching and reporting
   - User-friendly error messages
   - Automatic retry mechanisms

3. **Performance**:
   - Efficient data processing
   - Optimized API calls
   - Caching where appropriate

### External APIs

- Blockchain.info
- Blockstream.info
- BlockCypher

## API Endpoints

### GET /latest-block

Fetches the latest Bitcoin block data including:

- Block hash
- Block height
- Merkle root
- Transaction count

### GET /merkle-proof/:txHash

Generates a Merkle proof for a specific transaction:

- Proof steps with direction (left/right)
- Sibling hashes
- Verification result

## Error Handling

### Backend

- Implements retry logic with exponential backoff
- Multiple block explorer API fallbacks
- Comprehensive error messages
- Request timeout handling

### Frontend

- Loading states for all operations
- User-friendly error messages
- Graceful degradation
- Responsive error handling

## Component Structure

### BlockInfo

- Displays basic block information
- Real-time data fetching
- Responsive layout

### MerkleRootVerification

- Visual comparison of Merkle roots
- Interactive verification display
- Color-coded validation results

### TransactionVerification

- Fetches the latest block information and transactions from two APIs when the component mounts. It limits the displayed transactions to the first 10.
- I used 10 transactions because the number of transactions in a block is large. To make the process more robust, I selected 10 transactions as a sample.
- Transaction selection interface
- Proof generation and display
- Step-by-step verification process

## Technical Challenges Addressed

1. **Data Reliability**:

   - Multiple API fallback system
   - Robust error handling
   - Data validation and verification

2. **Cryptographic Implementation**:

   - Correct byte ordering
   - Hash function implementation
   - Proof generation algorithms

3. **User Experience**:
   - Real-time data updates
   - Clear visual feedback
   - Intuitive interface design

## Getting Started

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- Git

### Installation

1. Clone the repository

```bash
git clone [your-repository-url]
cd [project-name]
```

2. Install Backend Dependencies

```bash
cd server
npm install
```

3. Install Frontend Dependencies

```bash
cd client
npm install
```

### Environment Setup

Create `.env` files in both frontend and backend directories:

Backend `.env`:

```
PORT=5000
```

Frontend `.env`:

```
REACT_APP_API_URL=http://localhost:5000
```

## Running the Application

1. Start the Backend Server

```bash
cd server
npm run start
```

The server will start on `http://localhost:5000`

2. Start the Frontend Application

```bash
cd client
npm run start
```

The application will open in your browser at `http://localhost:3000`

---

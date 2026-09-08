# How to Connect MetaMask Wallet to a Website

## Introduction

This guide shows you how to connect a user's MetaMask wallet to a website using JavaScript. After following this guide, users will be able to connect their wallet and you will be able to read their wallet address.

**Who this is for:** Developers building simple Web3 websites or dApps.

## Prerequisites

- Basic knowledge of HTML and JavaScript
- MetaMask browser extension installed
- A modern browser (Chrome, Brave, or Firefox)

## Step 1: Check if MetaMask is Installed

First, check whether the user has MetaMask installed.

if (typeof window.ethereum !== "undefined") {
  console.log("MetaMask is installed!");
} else {
  console.log("Please install MetaMask");
}

## Step 2: Request Wallet Connection

Ask the user to connect their wallet using the following code:

async function connectWallet() {
  try {
    const accounts = await window.ethereum.request({ 
      method: "eth_requestAccounts" 
    });
    
    const walletAddress = accounts[0];
    console.log("Connected wallet:", walletAddress);
    
    return walletAddress;
  } catch (error) {
    console.error("User rejected the connection", error);
  }
}

## Step 3: Display the Wallet Address

Once connected, you can show the wallet address on your website.

Example:

const address = await connectWallet();
document.getElementById("wallet-address").innerText = address;

## Step 4: Listen for Account Changes

Users can switch accounts in MetaMask. You should listen for this event:

window.ethereum.on("accountsChanged", (accounts) => {
  if (accounts.length > 0) {
    console.log("Switched to:", accounts[0]);
  } else {
    console.log("Wallet disconnected");
  }
});

## Full Example

button onclick="connectWallet()">Connect Wallet</button>
p id="wallet-address"></p>

script
  async function connectWallet() {
    if (typeof window.ethereum === "undefined") {
      alert("Please install MetaMask");
      return;
    }

    try {
      const accounts = await window.ethereum.request({ 
        method: "eth_requestAccounts" 
      });
      
      document.getElementById("wallet-address").innerText = accounts[0];
    } catch (error) {
      console.error(error);
    }
  }
/script

## Common Errors

- User rejects the connection request
- MetaMask is not installed
- Website is not running on HTTPS (required in production)

## Next Steps

- Detect the current network (Ethereum, Polygon, etc.)
- Add support for switching networks
- Sign a message for authentication
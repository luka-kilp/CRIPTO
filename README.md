<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>White Powder Bear Cryptocurrency</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: black;
            color: white;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
        }

        header {
            text-align: center;
            margin-bottom: 20px;
        }

        header h1 {
            font-size: 3rem;
            margin: 0;
        }

        header p {
            font-size: 1.2rem;
            color: #aaa;
        }

        .crypto-image {
            margin: 20px 0;
            width: 150px;
            height: 150px;
            border-radius: 50%;
            overflow: hidden;
            border: 2px solid #ff6b6b;
            display: flex;
            align-items: center;
            justify-content: center;
            background: black;
        }

        .crypto-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .price, .balance {
            font-size: 1.5rem;
            margin: 20px 0;
        }

        button {
            background-color: #ff6b6b;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            color: white;
            font-size: 1rem;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: #ff4c4c;
        }

        footer {
            margin-top: 50px;
            font-size: 0.9rem;
            color: #777;
        }

    </style>
</head>
<body>
    <header>
        <h1>White Powder Bear Cryptocurrency</h1>
        <p>The Future of Digital Assets</p>
    </header>

    <div class="crypto-image">
        <img src="bear.jpg" alt="White Powder Bear Logo">
    </div>

    <div class="balance">Wallet Balance: <span id="balance">0</span> WPB</div>

    <button id="connectWallet">Connect Wallet</button>

    <footer>
        &copy; 2024 White Powder Bear Crypto. All Rights Reserved.
    </footer>

    <script src="https://cdn.jsdelivr.net/npm/web3/dist/web3.min.js"></script>
    <script>
        const contractAddress = "YOUR_CONTRACT_ADDRESS_HERE";
        const abi = [
            // Replace with your contract's ABI
        ];

        let web3;
        let contract;

        document.getElementById('connectWallet').onclick = async () => {
            if (window.ethereum) {
                web3 = new Web3(window.ethereum);
                await ethereum.request({ method: 'eth_requestAccounts' });
                const accounts = await web3.eth.getAccounts();
                const account = accounts[0];

                contract = new web3.eth.Contract(abi, contractAddress);
                const balance = await contract.methods.balanceOf(account).call();
                document.getElementById('balance').textContent = web3.utils.fromWei(balance, 'ether');
            } else {
                alert('MetaMask not detected!');
            }
        };
    </script>
</body>
</html>

// Solidity Contract Code (WhitePowderBearToken.sol)
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract WhitePowderBearToken is ERC20 {
    address public owner;

    constructor(uint256 initialSupply) ERC20("White Powder Bear Token", "WPB") {
        owner = msg.sender;
        _mint(msg.sender, initialSupply * (10 ** decimals()));
    }

    function mint(address to, uint256 amount) external {
        require(msg.sender == owner, "Only the owner can mint tokens");
        _mint(to, amount);
    }
}

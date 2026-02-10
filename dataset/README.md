


##  Data Sourcing

1. Go to [Etherscan](https://etherscan.io/contractsverified)
2.Select a contract to view its source code.

> **Why this source?**
> * **Real-world data:** Actual contracts deployed on Mainnet.
> * **Transparency:** Source code is verified and public.
> * **Safety:** Sandbox-ready for static analysis.


## Recommended Domains
The following sectors represent the core focus areas for high-security smart contract development:

* **DeFi Contracts**: The backbone of decentralized finance.
* **Tokens (ERC20)**: Standardized asset implementations.
* **Staking**: Mechanisms for locking assets to earn rewards.
* **Yield Farming**: Strategies for optimizing asset returns.
* **Liquidity Pools**: Automated market maker (AMM) foundations.

---

## Token Contract Functions
These specific functions require the most rigorous testing and validation:

| Action | Description |
| :--- | :--- |
| **Transfer** | Moving assets between external or contract addresses. |
| **Withdraw** | Removing assets from a protocol or vault. |
| **Mint / Burn** | Creating or destroying supply, impacting total valuation. |

---

**# Contract Verification Guidelines

When auditing or browsing **Verified Contracts**, use the following keywords and constraints to filter for high-value targets.

###  Priority Keywords
Search for contracts whose names or source code explicitly include:

* **Financial Logic**: `Vault`, `Pool`, `Liquidity`, `Reward`
* **Asset Management**: `Token`, `Staking`
* **State Changes**: `Withdraw`

---

## Elements to Avoid
To save time and focus on unique logic, filter out the following:

### 1. Boilerplate & Utilities
* **Libraries**: Standard implementations like `SafeMath` or `Ownable`.
* **Interfaces**: Abstract definitions without executable logic.

### 2. Low-Value Targets
* **Test Contracts**: Deployment scripts or mock contracts used for staging.
* **Small Footprints**: Any contract with **fewer than 100 lines of code**, as these rarely contain complex DeFi mechanisms.**

---

###  Extraction Components

### 1. Solidity Source Code
Copy the full `.sol` code and save it using a consistent naming convention.
* **Save as:** `code.sol`

### 2. Comments (Text)
Extract standard comments to identify developer explanations.
* `// comment`
* `/* comment */`
* **Save as:** `comments.txt`
  
### 3. NatSpec Documentation
NatSpec provides high-value semantic meaning for intent-behavior detection.

`solidity
/// @notice Allows users to withdraw funds safely
/// @dev Only user funds are transferred`
* **Save as:** `natspec.txt`
  
### 4. Function Names

Function signatures carry significant semantic weight regarding the contract's intended purpose. By analyzing these names, we can establish a baseline for "intended behavior" before auditing the underlying logic.

| Function Name | Implied Intent |
| :--- | :--- |
| `withdraw()` | Standard fund retrieval |
| `safeTransfer()` | Checked token movement |
| `emergencyWithdraw()` | Admin-level recovery |
* **Save as:** `functions.txt`
```
dataset/
 ├── contract_1/
 │   ├── code.sol       # Full source code
 │   ├── comments.txt   # Inline comments
 │   ├── natspec.txt    # NatSpec tags
 │   └── functions.txt  # Function signatures
 ├── contract_2/
 └── contract_3/

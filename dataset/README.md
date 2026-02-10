
##  Data Sourcing

1. Go to [Etherscan](https://etherscan.io/)
2. Navigate to **"More"** → **"Verified Contracts"**
3. Select a contract to view its source code.

> **Why this source?**
> * **Real-world data:** Actual contracts deployed on Mainnet.
> * **Transparency:** Source code is verified and public.
> * **Safety:** Sandbox-ready for static analysis.

---

##  Extraction Components

### 1. Solidity Source Code
Copy the full `.sol` code and save it using a consistent naming convention.
* **Save as:** `contract_name.sol`

### 2. Comments (Text)
Extract standard comments to identify developer explanations.
* `// comment`
* `/* comment */`

### 3. NatSpec Documentation
NatSpec provides high-value semantic meaning for intent-behavior detection.

`solidity
/// @notice Allows users to withdraw funds safely
/// @dev Only user funds are transferred`

### 4. Function Names

Function signatures carry significant semantic weight regarding the contract's intended purpose. By analyzing these names, we can establish a baseline for "intended behavior" before auditing the underlying logic.

| Function Name | Implied Intent |
| :--- | :--- |
| `withdraw()` | Standard fund retrieval |
| `safeTransfer()` | Checked token movement |
| `emergencyWithdraw()` | Admin-level recovery |

```
dataset/
 ├── contract_1/
 │   ├── code.sol       # Full source code
 │   ├── comments.txt   # Inline comments
 │   ├── natspec.txt    # NatSpec tags
 │   └── functions.txt  # Function signatures
 ├── contract_2/
 └── contract_3/

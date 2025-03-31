# trustfi: Progressive Trust Microfinance System

TrustFi is a decentralized microfinance platform built on the Stacks blockchain that implements a progressive trust system for lending. The platform allows borrowers to access loans with decreasing collateral requirements as they build their reputation through successful repayments.

## Core Features

### Progressive Trust System
- **Dynamic Loan Limits**: Loan amounts increase as borrowers successfully repay
- **Algorithmic Credit Limits**: Maximum loan amounts calculated based on reputation score and repayment history
- **Decreasing Collateral Requirements**: Collateral percentage decreases with each successful repayment
- **Community Endorsements**: Allows community members to vouch for borrowers, improving their standing

## Smart Contract Architecture

The TrustFi platform is built around a primary Clarity smart contract that handles:

1. **Borrower Management**: Tracks reputation scores, loan history, and collateral requirements
2. **Loan Lifecycle**: Handles loan requests, repayments, and defaults
3. **Reputation Scoring**: Adjusts reputation based on repayment behavior
4. **Collateral Management**: Calculates and manages collateral requirements
5. **Community Endorsements**: Allows community members to endorse borrowers

## Technical Implementation

### Key Parameters

- **Loan Amounts**: Minimum 0.1 STX, maximum 100 STX (adjustable based on reputation)
- **Collateral Requirements**: Starting at 80%, can decrease to as low as 20%
- **Reputation System**: Gain 10 points per repayment, lose 25 points per default
- **Loan Duration**: 30 days standard with 5 days grace period

### Functions

| Function | Description |
|----------|-------------|
| `initialize-borrower` | Register a new borrower in the system |
| `request-loan` | Request a loan with the required collateral |
| `repay-loan` | Repay an active loan and retrieve collateral |
| `process-default` | Process a defaulted loan (after grace period) |
| `endorse-borrower` | Add community endorsement for a borrower |
| `calculate-max-loan-amount` | Calculate maximum loan amount based on reputation |
| `calculate-collateral-percentage` | Calculate required collateral percentage |
| `get-borrower-data` | Retrieve all data for a specific borrower |
| `get-loan-status` | Check the status of a borrower's loan |
| `is-loan-defaulted` | Check if a loan is in default status |

## Getting Started

### Prerequisites

- [Clarinet](https://github.com/hirosystems/clarinet) for local development and testing
- [Stacks Wallet](https://www.hiro.so/wallet) for interacting with the deployed contract

### Local Development

1. Clone the repository:

git clone [https://github.com/yourusername/trustfi-progressive-lending.git](https://github.com/yourusername/trustfi-progressive-lending.git)
cd trustfi-progressive-lending

```plaintext

2. Install Clarinet:
```

curl -sS [https://get.clarinet.com](https://get.clarinet.com) | sh

```plaintext

3. Initialize a new Clarinet project:
```

clarinet new

```plaintext

4. Copy the contract to the contracts directory:
```

cp trust-lending.clar contracts/

```plaintext

5. Run tests:
```

clarinet test

```plaintext

### Deployment

1. Deploy to the Stacks testnet:
```

clarinet deploy --testnet

```plaintext

2. Deploy to the Stacks mainnet (requires STX for transaction fees):
```

clarinet deploy --mainnet

```plaintext

## Interacting with the Contract

### As a Borrower

1. Initialize yourself as a borrower:
```

stx call initialize-borrower

```plaintext

2. Request a loan:
```

stx call request-loan amount=1000000 // 1 STX

```plaintext

3. Repay a loan:
```

stx call repay-loan

```plaintext

### As a Community Member

1. Endorse a borrower:
```

stx call endorse-borrower borrower=ST1PQHQKV0RJXZFY1DGX8MNSNYVE3VGZJSRTPGZGM weight=5

```plaintext

## Future Roadmap

1. **Phase 1**: Basic reputation scoring and small loans with higher collateral (current implementation)
2. **Phase 2**: 
- Add interest rate calculations based on reputation
- Implement community governance for parameter adjustments
- Add loan purpose tracking and verification

3. **Phase 3**: 
- Integrate with real-world identity verification systems
- Add multi-asset collateral support
- Implement cross-chain reputation importing

4. **Phase 4**: 
- Develop a DAO for community-based loan approvals
- Implement zero-knowledge proofs for privacy-preserving reputation
- Create a secondary market for loan trading

## Security Considerations

- The contract includes safeguards against common vulnerabilities
- Collateral is held in the contract until loan repayment or default
- Grace periods prevent immediate defaults due to minor delays
- Reputation penalties for defaults discourage malicious behavior

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Stacks Foundation for blockchain infrastructure
- Clarity language documentation and community
- Microfinance research and best practices from traditional finance
```

## Key Implementation Details

1. **Progressive Trust Mechanism**:

1. The contract tracks reputation scores that increase with each successful repayment
2. Loan amounts are calculated based on reputation score using `calculate-max-loan-amount`
3. Collateral requirements decrease with each successful repayment, calculated by `calculate-collateral-percentage`



2. **Reputation System**:

1. Borrowers gain reputation points for successful repayments
2. Borrowers lose reputation points for defaults
3. Community endorsements can boost a borrower's standing



3. **Collateral Management**:

1. Collateral is held in the contract until loan repayment
2. Collateral percentage decreases by 5% per successful repayment
3. Minimum collateral requirement is 20% regardless of reputation



4. **Default Handling**:

1. Grace period of 5 days after loan due date
2. Default processing can be triggered by anyone after grace period
3. Defaulted loans result in collateral forfeiture and reputation damage

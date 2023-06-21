# Ballot_Test_Gnosis_Contracts

## WhitelistSoulbound1155NFT.sol
ERC1155 Soulbound NFT implementation to serve as whitelist and KYC mechanism for participants.
- **Contract:** https://gnosisscan.io/address/0x77f6A5f1B7a2b6D6C322Af8581317D6Bb0a52689

| Function | Visibility | Restricted | Description |
| ------------- | :-------------: | :-----: | :----- |
| burn | public | yes | Used to burn tokens from members. |
| mint | public | yes | Used to mint tokens to members. |
| setSoulbound | public | yes | Used to restrict token ID transfers. |
| totalSupply | public | no | Used to track token ID supply and overall supply. |

## BallotContract.sol
Voting contract with a custom whitelist and KYC criteria determined by holdgin NFTs.
- **Contract:** https://gnosisscan.io/address/0x84Da107541eCda5B1dd16B322938A9629162512E


## Whitelist & KYC Mechanism

The NFT ID 0 from the ERC1155 implementation should be a representation of the user's KYC completition, meaning that, if user holds this NFT, platforms and business logic inside contracts should understand that the user have a valid and active KYC.

The subsecuent NFTs represents if the user is whitelisted for the voting contracts or not, as requested, every new voting initiative is a new contract, which means that, if users want to vote on the current deployed voting initiative, they must hold NFT ID 0 for KYC along with NFT ID 1 for the voting contract, but if a new voting contract is deployed, users should hold NFT ID 0 and NFT ID 2 for the respective voring contract, and so on (only if needed, by design whitelisted NFTs can be reused on more than 1 voting contract).

- NFT ID 0 represents the user KYC compliance.
- NFT ID 1~N represents the user whitelist for the voting contracts.

## Improvements

- The **safeBatchTransferFrom** function from the ERC1155 contract is not soulbound enabled, users could transfer their NFTs using this method.

# Governance rules

For governance purposes, Pyth uses an instance of [spl-realms](https://realms.today/). 

Governance is structured in proposals. 

There are two types of proposals :
- An advisory plain text proposal
- A binding onchain transaction

The following are the current rules of Pyth governance :

- Only staked tokens can vote.
- Any participant in the Pyth DAO may submit a proposal to the governance program to be subject to a vote by the Pyth DAO if such proposal is supported by at least the `Minimum Proposal Quantity` of Staked Tokens.
- A proposal will succeed if :
    -  The proposal is supported by a majority of votes cast; and
    -  The `Minimum Voting percentage` of all staked tokens must have voted in favor of the proposal 
- A proposal will fail if the condition above hasn't been met after 7 days.

`Minimum Proposal Quantity` and `Minimum Voting percentage` are two parameters that can be modified at the discretion of the DAO.
For different governance tasks, the DAO might decide to have different parameters.
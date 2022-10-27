# The governance contract

For governance purposes, Pyth uses an instance of [spl-realms](https://realms.today/). This is binding onchain governance, please make sure you understand the contents of the transaction before you approve.
It can be interacted with [here](https://app.realms.today/dao/PYTH)
The address of the governance program is [`GovFUVGZWWwyoLq8rhnoVWknRFkhDSbQiSoREJ5LiZCV`](https://explorer.solana.com/address/GovFUVGZWWwyoLq8rhnoVWknRFkhDSbQiSoREJ5LiZCV)

Governance follows the following rules :

- Only staked tokens can vote.
- Anyone can create a proposal as long as they have `x`% of staked tokens
- For a proposal to succeed `y`% of the staked tokens at the time the proposal was created need to vote yes AND there more yesses than noes need have been cast
- If the above condition hasn't been met after 7 days the proposal fails

`x` and `y` are two parameters chosen by governance and might vary depending on the governance task.
# Solana Price Feeds

Solana Price Feeds continuously stream price updates to the Solana blockchain.
Each price feed is stored in a separate Solana account.
Application developers can simply pass the relevant account to their solana program, then deserialize the data in the accounts to read the current value of the feed.
Pyth provides a [Solana SDK](solana.md) to assist with this process.

Before getting started with the SDK, please read [_Using Price Feeds_](best-practices.md) to understand how Pyth price feeds are represented, and to learn best practices to use Pyth prices safely and correctly.

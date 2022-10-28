# Staking rules

These are the current rules of Pyth staking :

1. Pyth staking is organized in one-week epochs. Each Thursday at 00:00am UTC (midnight between Wednesday and Thursday), a new epoch starts. 
2. When user stakes their Pyth tokens, their stake will only become active at the start of the next epoch.   
3. When a user requests to unlock their Pyth tokens, the tokens will go into cooldown at the end of the current epoch and will be withdrawable after one full cooldown epoch.

Examples : 
- Daniel requests to lock his tokens in epoch 1, his tokens will become `Locked` on epoch 2.
- Alice requests to unlock her tokens during epoch 1. Her tokens will become `Unlocked` at the start of epoch 3 and only then will she be able to withdraw them.


# The staking program

The staking program is the program that custodies all staked Pyth tokens. 

It can be interacted with [here](https://staking.pyth.network/staking).

The address of the staking program is [`sta99txADjRfwHQQMNckb8vUN4jcAAhN2HBMTR2Ah6d`](https://explorer.solana.com/address/sta99txADjRfwHQQMNckb8vUN4jcAAhN2HBMTR2Ah6d).

Pyth staking follows the following rules : 

1. Pyth staking is organized in one-week epochs. Each Thursday at 00:00am (midnight between Wednesday and Thursday), a new epoch starts. 
2. When user stakes their Pyth tokens, their stake will only become active at the start of the next epoch.   
Example : If Daniel requests to lock their tokens in epoch 1, his tokens will be active on epoch 2.
3. When a user requests to unlock their Pyth tokens, the tokens will go into cooldown at the end of the current epoch and will be withdrawable after one cooldown epoch.
Example : This means if Alice requests to unlock her tokens during epoch 1 she'll be able to withdraw at the start of epoch 3. 

There are 3 types of tokens in the staking contract:
- Locked tokens : these are tokens that are staked, they can be unlocked by going to the unlock tab
- Unlocked tokens : these tokens are free to be withdrawn
- Unvested tokens : these tokens are subject to a vesting schedule, they can only be withdrawn once they vest. A user can see when is the next vesting event by clicking on `Unvested`. Additionally the owner of unvested tokens can choose to stake them, making them eligible to vote.

# The staking UI

{% hint style="info" %}
Staked tokens can't be withdrawn immediately, make sure you understand the [rules](staking-rules.md) before staking your tokens.
{% endhint %}

First, go to the [staking frontend](https://staking.pyth.network/) and connect your wallet

Once you connect your wallet, you'll be presented with the state of your current stake account.

The tokens in the current connected wallet can be seen next to `Balance`.

A user can have 3 types of tokens in the staking program:
- Locked : these are tokens that are staked, they can be unlocked by going to the `Unlock` tab
- Unlocked : these tokens are free to be withdrawn in the `Withdraw` tab
- Unvested : these tokens are subject to a vesting schedule, they can only be withdrawn once they vest. A user can see when is the next vesting event by clicking on `Unvested`. Additionally any owner of unvested tokens can choose to stake them, making them eligible to vote.

Additionally some tokens are in warmup or cooldown:
- Warmup tokens are represented in gray in the locked area, they'll become locked once enough time passes
- Cooldown tokens are represented in gray in the unlocked area, they'll become unlocked once enough time passes

![](<../.gitbook/assets/Screen Shot 2022-10-28 at 10.56.59 AM.png>)

As an example, the user in the image above has :
- 0.5 locked tokens
- 0.5 tokens in cooldown
- No unlocked tokens nor unvested tokens
- No tokens in his current wallet

# How to lock tokens

- Go to the `Lock` tab
- Enter the amount
- Click the big `Lock` button

# How to unlock tokens

- Go to the `Unlock` tab
- Enter the amount
- Click the big `Unlock` button
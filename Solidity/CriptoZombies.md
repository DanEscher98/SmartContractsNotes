# Cripto Zombies


## Basics

### Modifiers

#### Visibility modifiers
- `private`: It's only callable from other functions inside the
    contract.
- `internal`: Like `private`, but can also be called by contracts that
    inherit from this one.
- `external`: Can only be called outside the contract.
- `public`: Can be called anywhere, both internally and externally.

#### State modifiers
These don't cost any gas to call if called outside the contract. But
they do cost gas if called internally by another function.
- `view`: Tells that by running the function, no data will be
    saved/changed at the blockchain.
- `pure`: Tells that not only is like `view`, but also doesn't read
    any data from the blockchain.

#### Custom modifiers
For these we can define custom logic to determine how the affect a
function. They even may have arguments.

#### The `payable` modifier
They are a special type of function that can receive `Ether`. If a
function is not marked `payable` and you try to send `Ether` to it,
the function will reject your transaction. 
```solidity
contract OnlineStore {
  function buySomething() external payable {
    // Check to make sure 0.001 ether was sent to the function call:
    require(msg.value == 0.001 ether);
    // If so, some logic to transfer the digital item to the caller of the function:
    transferThing(msg.sender);
  }
}
```

## General tips

### Ch4
- Inside `structs` we want to use the smallest `uint`s we can get away
    with it, in order to pay less gas.

### Ch5
- `require` is similar to `assert`. The difference is that `require`
    will refund the user the rest of their gas when a function fails,
    whereas `assert` will not. `assert` is typically used when
    something has gone horribly wrong with the code.

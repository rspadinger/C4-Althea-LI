# Winning bot race submission
This is the top-ranked automated findings report, from TragedyOTCommons bot. All findings in this report will be considered known issues for the purposes of your C4 audit.

## Summary

| |Issue|Instances| Gas Savings
|-|:-|:-:|:-:|
| [[M-01](#m-01)] | `_safeMint()` should be used rather than `_mint()` wherever possible | 2| 0|
| [[M-02](#m-02)] | Burning is missing access control | 1| 0|
| [[M-03](#m-03)] | Unsafe use of `transfer()`/`transferFrom()` with `IERC20` | 1| 0|
| [[L-01](#l-01)] | Code does not follow the best practice of check-effects-interaction | 13| 0|
| [[L-02](#l-02)] | Division by zero not prevented | 1| 0|
| [[L-03](#l-03)] | Events may be emitted out of order due to reentrancy | 16| 0|
| [[L-04](#l-04)] | External calls in an un-bounded `for-`loop may result in a DOS | 11| 0|
| [[L-05](#l-05)] | Functions calling tokens with transfer hooks are missing reentrancy guards | 2| 0|
| [[L-06](#l-06)] | Local variable shadows state variable | 2| 0|
| [[L-07](#l-07)] | Loss of precision | 1| 0|
| [[L-08](#l-08)] | Some tokens may revert when large transfers are made | 1| 0|
| [[L-09](#l-09)] | State variables not capped at reasonable values | 1| 0|
| [[L-10](#l-10)] | Tokens may be minted to `address(0x0)` | 2| 0|
| [[L-11](#l-11)] | Use `Ownable2Step` rather than `Ownable` | 1| 0|
| [[G-01](#g-01)] | `do`-`while` is cheaper than `for`-loops when the initial check can be skipped | 7| 0|
| [[G-02](#g-02)] | Consider using `ERC721A` over `ERC721` | 3| 0|
| [[G-03](#g-03)] | Use `uint256(1)`/`uint256(2)` instead of `true`/`false` to save gas for changes | 2| 17100|
| [[G-04](#g-04)] | Use `Array.unsafeAccess()` to avoid repeated array length checks | 24| 50400|
| [[G-05](#g-05)] | Mappings are cheaper to use than storage arrays | 6| 12600|
| [[G-06](#g-06)] | State variables only set in the constructor should be declared `immutable` | 1| 2097|
| [[G-07](#g-07)] | State variables can be packed into fewer storage slots by truncating timestamp bytes | 1| 2000|
| [[G-08](#g-08)] | Avoid updating storage when the value hasn't changed | 1| 800|
| [[G-09](#g-09)] | Events should be emitted outside of loops | 3| 1125|
| [[G-10](#g-10)] | Assembly: Use scratch space for building calldata | 4| 880|
| [[G-11](#g-11)] | Using `this` to access functions results in an external call, wasting gas | 5| 500|
| [[G-12](#g-12)] | Using `bool`s for storage incurs overhead | 2| 200|
| [[G-13](#g-13)] | Avoid transferring amounts of zero in order to save gas | 1| 100|
| [[G-14](#g-14)] | State variables should be cached in stack variables rather than re-reading them from storage | 10| 970|
| [[G-15](#g-15)] | Use the inputs/results of assignments rather than re-reading state variables | 2| 194|
| [[G-16](#g-16)] | `++i`/`i++` should be `unchecked{++i}`/`unchecked{i++}` when it is not possible for them to overflow, as is the case when used in `for`- and `while`-loops | 9| 540|
| [[G-17](#g-17)] | Consider pre-calculating the address of `address(this)` to save gas | 5| 0|
| [[G-18](#g-18)] | Consider using `solady`'s token contracts to save gas | 5| 0|
| [[G-19](#g-19)] | State variable read in a loop | 8| 776|
| [[G-20](#g-20)] | Use local variables for emitting | 1| 96|
| [[G-21](#g-21)] | Multiple accesses of a storage array should use a local variable cache | 1| 42|
| [[G-22](#g-22)] | Functions guaranteed to revert when called by normal users can be marked `payable` | 10| 210|
| [[G-23](#g-23)] | Constructors can be marked `payable` | 2| 42|
| [[G-24](#g-24)] | `internal` functions only called once can be inlined to save gas | 3| 60|
| [[G-25](#g-25)] | `unchecked {}`  can be used on the division of two `uint`s in order to save gas | 1| 20|
| [[G-26](#g-26)] | Assembly: Checks for `address(0x0)` are more efficient in assembly | 3| 54|
| [[G-27](#g-27)] | Don't use `_msgSender()` if not supporting EIP-2771 | 4| 64|
| [[G-28](#g-28)] | Assembly: Use scratch space when building emitted events with two data arguments | 1| 15|
| [[G-29](#g-29)] | Counting down when iterating, saves gas | 9| 108|
| [[G-30](#g-30)] | Duplicated `require()`/`revert()` checks should be refactored to a modifier or function to save deployment gas | 2| 0|
| [[G-31](#g-31)] | Optimize names to save gas | 1| 0|
| [[G-32](#g-32)] | Reduce gas usage by moving to Solidity 0.8.19 or later | 3| 0|
| [[G-33](#g-33)] | Use custom errors rather than `revert()`/`require()` strings to save gas | 18| 0|
| [[G-34](#g-34)] | Using `> 0` costs more gas than `!= 0` when used on a `uint` in a `require()` statement | 1| 6|
| [[G-35](#g-35)] | `++i` costs less gas than `i++`, especially when it's used in `for`-loops (`--i`/`i--` too) | 9| 45|
| [[G-36](#g-36)] | `require()`/`revert()` strings longer than 32 bytes cost extra gas | 13| 39|
| [[G-37](#g-37)] | `>=` costs less gas than `>` | 13| 39|
| [[G-38](#g-38)] | Reduce deployment costs by tweaking contracts' metadata | 2| 0|
| [[G-39](#g-39)] | Stack variable is only used once | 5| 15|
| [[G-40](#g-40)] | A `memory` array's `length` should not be looked up in every iteration of a `for`/`while`-loop | 1| 3|
| [[G-41](#g-41)] | Enable IR-based code generation | -| 0|
| [[G-42](#g-42)] | Using `private` rather than `public`, saves gas | 8| 0|
| [[N-01](#n-01)] | `constant`s/`immutable`s redefined elsewhere | 2| 0|
| [[N-02](#n-02)] | `public` functions not called by the contract should be declared `external` instead | 14| 0|
| [[N-03](#n-03)] | Array is `push()`ed but not `pop()`ed | 3| 0|
| [[N-04](#n-04)] | Avoid external calls in modifiers | 1| 0|
| [[N-05](#n-05)] | Avoid the use of sensitive terms | 1| 0|
| [[N-06](#n-06)] | Consider adding emergency-stop functionality | 2| 0|
| [[N-07](#n-07)] | Consider adding formal verification proofs | -| 0|
| [[N-08](#n-08)] | Consider adding validation of user inputs | 7| 0|
| [[N-09](#n-09)] | Consider bounding input array length | 1| 0|
| [[N-10](#n-10)] | Consider defining system-wide constants in a single file | 3| 0|
| [[N-11](#n-11)] | Consider disabling `renounceOwnership()` | 1| 0|
| [[N-12](#n-12)] | Consider emitting an event at the end of the constructor | 1| 0|
| [[N-13](#n-13)] | Consider making contracts `Upgradeable` | 2| 0|
| [[N-14](#n-14)] | Consider moving duplicated strings to constants | 2| 0|
| [[N-15](#n-15)] | Consider providing a ranged getter for array state variables | 1| 0|
| [[N-16](#n-16)] | Consider using `delete` rather than assigning zero/false to clear values | 4| 0|
| [[N-17](#n-17)] | Consider using named function arguments | 1| 0|
| [[N-18](#n-18)] | Consider using named mappings | 1| 0|
| [[N-19](#n-19)] | Consider using named returns | 2| 0|
| [[N-20](#n-20)] | Consider using the `using`-`for` syntax | 2| 0|
| [[N-21](#n-21)] | Constants in comparisons should appear on the left side | 9| 0|
| [[N-22](#n-22)] | Contracts should have all `public`/`external` functions exposed by `interface`s | 2| 0|
| [[N-23](#n-23)] | Contracts should have full test coverage | -| 0|
| [[N-24](#n-24)] | Critical system parameter changes should be behind a timelock | 1| 0|
| [[N-25](#n-25)] | Custom errors should be used rather than `revert()`/`require()` | 18| 0|
| [[N-26](#n-26)] | Duplicated `require()`/`revert()` checks should be refactored to a modifier or function | 2| 0|
| [[N-27](#n-27)] | Error messages should descriptive, rather that cryptic | 1| 0|
| [[N-28](#n-28)] | Event is not properly `indexed` | 5| 0|
| [[N-29](#n-29)] | Events are missing sender information | 12| 0|
| [[N-30](#n-30)] | Events should use parameters to convey information | 6| 0|
| [[N-31](#n-31)] | High cyclomatic complexity | 1| 0|
| [[N-32](#n-32)] | Import declarations should import specific identifiers, rather than the whole file | 13| 0|
| [[N-33](#n-33)] | Imports could be organized more systematically | 1| 0|
| [[N-34](#n-34)] | Large or complicated code bases should implement invariant tests | -| 0|
| [[N-35](#n-35)] | Missing checks for empty parameters in the constructor | 4| 0|
| [[N-36](#n-36)] | Missing checks for uint state variable assignments | 1| 0|
| [[N-37](#n-37)] | Missing checks for uint state variable constructor assignments | 1| 0|
| [[N-38](#n-38)] | Missing event for critical parameter change | 1| 0|
| [[N-39](#n-39)] | Mixed usage of `int`/`uint` with `int256`/`uint256` | 8| 0|
| [[N-40](#n-40)] | Named imports of parent contracts are missing | 9| 0|
| [[N-41](#n-41)] | NatSpec: Contract declarations should have `@author` tags | 1| 0|
| [[N-42](#n-42)] | NatSpec: Contract declarations should have `@title` tags | 1| 0|
| [[N-43](#n-43)] | NatSpec: Event `@param` tag is missing | 14| 0|
| [[N-44](#n-44)] | NatSpec: Event declarations should have `@dev` tags | 13| 0|
| [[N-45](#n-45)] | NatSpec: Event declarations should have `@notice` tags | 13| 0|
| [[N-46](#n-46)] | NatSpec: Event declarations should have descriptions | 13| 0|
| [[N-47](#n-47)] | NatSpec: Function `@param` tag is missing | 8| 0|
| [[N-48](#n-48)] | NatSpec: Function `@return` tag is missing | 2| 0|
| [[N-49](#n-49)] | NatSpec: Function declarations should have `@dev` tags | 22| 0|
| [[N-50](#n-50)] | NatSpec: Function declarations should have `@notice` tags | 1| 0|
| [[N-51](#n-51)] | NatSpec: Function declarations should have descriptions | 1| 0|
| [[N-52](#n-52)] | NatSpec: Modifier `@param` tag is missing | 2| 0|
| [[N-53](#n-53)] | NatSpec: Non-public state variable declarations should use `@dev` tags | 5| 0|
| [[N-54](#n-54)] | NatSpec: State variable declarations should have descriptions | 5| 0|
| [[N-55](#n-55)] | Setters should prevent re-setting of the same value | 1| 0|
| [[N-56](#n-56)] | Style guide: Contract does not follow the Solidity style guide's suggested layout ordering | 2| 0|
| [[N-57](#n-57)] | Style guide: Extraneous whitespace | 1| 0|
| [[N-58](#n-58)] | Style guide: Function ordering does not follow the Solidity style guide | 4| 0|
| [[N-59](#n-59)] | Style guide: Initialisms should be capitalized | 4| 0|
| [[N-60](#n-60)] | Style guide: Lines are too long | 26| 0|
| [[N-61](#n-61)] | Style guide: Non-`external`/`public` variable names should begin with an underscore | 7| 0|
| [[N-62](#n-62)] | Style guide: Variable names for `constant`s are improperly named | 3| 0|
| [[N-63](#n-63)] | The `nonReentrant` `modifier` should occur before all other modifiers | 2| 0|
| [[N-64](#n-64)] | The `nonReentrant` `modifier` should occur before all other modifiers | 2| 0|
| [[N-65](#n-65)] | Typos | 3| 0|
| [[N-66](#n-66)] | Unused `event` definition | 1| 0|
| [[N-67](#n-67)] | Unused `public` contract variable | 2| 0|
| [[N-68](#n-68)] | Unused function parameter | 3| 0|
| [[N-69](#n-69)] | Use of `override` is unnecessary | 2| 0|
| [[N-70](#n-70)] | Use the latest solidity (prior to 0.8.20 if on L2s) for deployment | 3| 0|
| [[N-71](#n-71)] | Variables need not be initialized to zero | 7| 0|
| [[N-72](#n-72)] | Vulnerable versions of packages are being used | -| 0|

### Medium Risk Issues

### [M-01]<a name="m-01"></a> `_safeMint()` should be used rather than `_mint()` wherever possible

`_mint()` is [discouraged](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/d4d8d2ed9798cc3383912a23b5e8d5cb602f7d4b/contracts/token/ERC721/ERC721.sol#L271) in favor of `_safeMint()` which ensures that the recipient is either an EOA or implements `IERC721Receiver`. Both [OpenZeppelin](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/d4d8d2ed9798cc3383912a23b5e8d5cb602f7d4b/contracts/token/ERC721/ERC721.sol#L238-L250) and [solmate](https://github.com/Rari-Capital/solmate/blob/4eaf6b68202e36f67cab379768ac6be304c8ebde/src/tokens/ERC721.sol#L180) have versions of this function. In the cases below, `_mint()` does not call `ERC721TokenReceiver.onERC721Received()` on the recipient.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

322:         _mint(account, amount);

```


*GitHub* : [322](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L322-L322)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

73:          _mint(msg.sender, AccountId);

```


*GitHub* : [73](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L73-L73)

### [M-02]<a name="m-02"></a> Burning is missing access control

The function allows any user to arbitrarily burn tokens from a passed in address. If someone approves the contract (e.g. for `type(uint256).max`), any other user can trigger a burn

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

344      function burnFromAndDistribute(address account, uint256 amount) public {
345          if (_isPastMinDistributionPeriod()) {
346              distributeToAllHolders();
347          }
348          burnFrom(account, amount);
349:     }

```


*GitHub* : [344](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L344-L349)

### [M-03]<a name="m-03"></a> Unsafe use of `transfer()`/`transferFrom()` with `IERC20`

Some tokens do not implement the ERC20 standard properly but are still accepted by most code that accepts ERC20 tokens.  For example Tether (USDT)'s `transfer()` and `transferFrom()` functions on L1 do not return booleans as the specification requires, and instead have no return value. When these sorts of tokens are cast to `IERC20`, their [function signatures](https://medium.com/coinmonks/missing-return-value-bug-at-least-130-tokens-affected-d67bf08521ca) do not match and therefore the calls made, revert (see [this](https://gist.github.com/IllIllI000/2b00a32e8f0559e8f386ea4f1800abc5) link for a test case). The number of affected tokens is higher than one would expect, due to the fact that at one point OpenZeppelin was using the incorrect signatures in its published interface. Use OpenZeppelin's `SafeERC20`'s `safeTransfer()`/`safeTransferFrom()` instead

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureNFT.sol

179:                 bool result = IERC20(erc20).transfer(destination, balance);

```


*GitHub* : [179](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L179-L179)

### Low Risk Issues

### [L-01]<a name="l-01"></a> Code does not follow the best practice of check-effects-interaction

Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

*There are 13 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit balanceOf() called prior to this assignment in _afterTokenTransfer(), via: _afterTokenTransfer()
174:                     holders[i] = holders[holders.length - 1];

/// @audit transfer() called prior to this assignment in distribute(), via: distribute()
/// @audit balanceOf() called prior to this assignment in distribute(), via: distribute()
/// @audit totalSupply() called prior to this assignment in distribute(), via: distribute(), _beginDistribution()
/// @audit balanceOf() called prior to this assignment in distribute(), via: distribute(), _beginDistribution()
232:         nextDistributionRecipient = i;

/// @audit balanceOf() called prior to this assignment in _beginDistribution(), via: _beginDistribution()
/// @audit totalSupply() called prior to this assignment in _beginDistribution(), via: _beginDistribution()
279:         nextDistributionRecipient = 0;

/// @audit getThresholds() called prior to this assignment in withdrawFromManagedNFTs(), via: withdrawFromManagedNFTs()
/// @audit withdrawBalancesTo() called prior to this assignment in withdrawFromManagedNFTs(), via: withdrawFromManagedNFTs()
380:         nextWithdrawal = i;

/// @audit getThresholds() called prior to this assignment in withdrawFromManagedNFTs(), via: withdrawFromManagedNFTs()
/// @audit withdrawBalancesTo() called prior to this assignment in withdrawFromManagedNFTs(), via: withdrawFromManagedNFTs()
383:             nextWithdrawal = 0;

/// @audit transferFrom() called prior to this assignment in releaseManagedNFT(), via: releaseManagedNFT()
/// @audit AccountId() called prior to this assignment in releaseManagedNFT(), via: releaseManagedNFT()
425:                 ManagedNFTs[i] = ManagedNFTs[ManagedNFTs.length - 1];

```


*GitHub* : [232](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L232-L232), [232](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L232-L232), [232](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L232-L232), [174](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L174-L174), [232](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L232-L232), [279](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L279-L279), [279](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L279-L279), [380](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L380-L380), [380](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L380-L380), [383](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L383-L383), [383](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L383-L383), [425](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L425-L425), [425](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L425-L425)

### [L-02]<a name="l-02"></a> Division by zero not prevented

The divisions below take an input parameter or state variable which does not have any zero-value checks, which may lead to the functions reverting with a panic when zero is passed. Note that according to the Ethereum documentation, well-functioning functions should never panic

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit supply
275:             uint256 entitlement = balance / supply;

```


*GitHub* : [275](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L275-L275)

### [L-03]<a name="l-03"></a> Events may be emitted out of order due to reentrancy

Ensure that events follow the best practice of check-effects-interaction, and are emitted before external calls

*There are 16 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit transfer() called prior to this emission in distribute(), via: distribute()
/// @audit balanceOf() called prior to this emission in distribute(), via: distribute()
/// @audit totalSupply() called prior to this emission in distribute(), via: distribute(), _beginDistribution()
/// @audit balanceOf() called prior to this emission in distribute(), via: distribute(), _beginDistribution()
229:                 emit Distribution(recipient, distributableERC20s, receipts);

/// @audit balanceOf() called prior to this emission in _beginDistribution(), via: _beginDistribution()
/// @audit totalSupply() called prior to this emission in _beginDistribution(), via: _beginDistribution()
280:         emit DistributionStarted();

/// @audit withdrawBalancesTo() called prior to this emission in withdrawFromManagedNFTs(), via: withdrawFromManagedNFTs()
/// @audit getThresholds() called prior to this emission in withdrawFromManagedNFTs(), via: withdrawFromManagedNFTs()
378:             emit Withdrawal(address(withdrawFrom));

/// @audit getThresholds() called prior to this emission in withdrawFromManagedNFTs(), via: withdrawFromManagedNFTs()
/// @audit withdrawBalancesTo() called prior to this emission in withdrawFromManagedNFTs(), via: withdrawFromManagedNFTs()
384:             emit WithdrawalFinished();

/// @audit ownerOf() called prior to this emission in addManagedNFT(), via: addManagedNFT()
/// @audit AccountId() called prior to this emission in addManagedNFT(), via: addManagedNFT()
402:         emit AddManagedNFT(nftContract);

/// @audit transferFrom() called prior to this emission in releaseManagedNFT(), via: releaseManagedNFT()
/// @audit AccountId() called prior to this emission in releaseManagedNFT(), via: releaseManagedNFT()
433:         emit ReleaseManagedNFT(nftContract, to);

```


*GitHub* : [229](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L229-L229), [229](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L229-L229), [229](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L229-L229), [229](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L229-L229), [280](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L280-L280), [280](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L280-L280), [378](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L378-L378), [378](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L378-L378), [384](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L384-L384), [384](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L384-L384), [402](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L402-L402), [402](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L402-L402), [433](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L433-L433), [433](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L433-L433)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit balanceOf() called prior to this emission in _withdrawBalancesTo(), via: _withdrawBalancesTo()
/// @audit transfer() called prior to this emission in _withdrawBalancesTo(), via: _withdrawBalancesTo()
184:         emit SuccessfulWithdrawal(destination, erc20s, amounts);

```


*GitHub* : [184](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L184-L184), [184](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L184-L184)

### [L-04]<a name="l-04"></a> External calls in an un-bounded `for-`loop may result in a DOS

Consider limiting the number of iterations in `for-`loops that make external calls

*There are 11 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit balanceOf() : 
/// @audit transfer() : 
/// @audit balanceOf() :  _afterTokenTransfer(), _transfer(), transfer()
/// @audit balanceOf() :  _beforeTokenTransfer(), _transfer(), transfer()
220                  for (uint j = 0; j < distributableERC20s.length; j++) {
221                      IERC20 toDistribute = IERC20(distributableERC20s[j]);
222                      uint256 entitlement = erc20EntitlementPerUnit[j] *
223                          this.balanceOf(recipient);
224                      if (toDistribute.transfer(recipient, entitlement)) {
225                          receipts[j] = entitlement;
226                      }
227:                 }

/// @audit balanceOf() : 
271          for (uint i = 0; i < distributableERC20s.length; i++) {
272              uint256 balance = IERC20(distributableERC20s[i]).balanceOf(
273                  address(this)
274              );
275              uint256 entitlement = balance / supply;
276              erc20EntitlementPerUnit.push(entitlement);
277:         }

/// @audit withdrawBalancesTo() : 
/// @audit getThresholds() : 
371          for (i = nextWithdrawal; i < limit; i++) {
372              LiquidInfrastructureNFT withdrawFrom = LiquidInfrastructureNFT(
373                  ManagedNFTs[i]
374              );
375  
376              (address[] memory withdrawERC20s, ) = withdrawFrom.getThresholds();
377              withdrawFrom.withdrawBalancesTo(withdrawERC20s, address(this));
378              emit Withdrawal(address(withdrawFrom));
379:         }

```


*GitHub* : [220](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L220-L227), [220](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L220-L227), [220](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L220-L227), [220](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L220-L227), [271](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L271-L277), [371](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L371-L379), [371](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L371-L379)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit transfer() : 
/// @audit balanceOf() :  _afterTokenTransfer(), _transfer(), transfer()
/// @audit balanceOf() :  _beforeTokenTransfer(), _transfer(), transfer()
/// @audit balanceOf() : 
175          for (uint i = 0; i < erc20s.length; i++) {
176              address erc20 = erc20s[i];
177              uint256 balance = IERC20(erc20).balanceOf(address(this));
178              if (balance > 0) {
179                  bool result = IERC20(erc20).transfer(destination, balance);
180                  require(result, "unsuccessful withdrawal");
181                  amounts[i] = balance;
182              }
183:         }

```


*GitHub* : [175](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L175-L183), [175](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L175-L183), [175](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L175-L183), [175](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L175-L183)

### [L-05]<a name="l-05"></a> Functions calling tokens with transfer hooks are missing reentrancy guards

Even if the function follows the best practice of check-effects-interaction, not using a reentrancy guard when there may be transfer hooks will open the users of this protocol up to [read-only reentrancies](https://chainsecurity.com/curve-lp-oracle-manipulation-post-mortem/) with no way to protect against it, except by block-listing the whole protocol.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit transfer() :  _withdrawBalancesTo(), withdrawBalances()
135:     function withdrawBalances(address[] calldata erc20s) public virtual {

/// @audit transfer() :  _withdrawBalancesTo(), withdrawBalancesTo()
153      function withdrawBalancesTo(
154          address[] calldata erc20s,
155          address destination
156:     ) public virtual {

```


*GitHub* : [135](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L135-L135), [153](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L153-L156)

### [L-06]<a name="l-06"></a> Local variable shadows state variable



*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit ERC20._name is an existing state variable
457:         string memory _name,

/// @audit ERC20._symbol is an existing state variable
458:         string memory _symbol,

```


*GitHub* : [457](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L457-L457), [458](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L458-L458)

### [L-07]<a name="l-07"></a> Loss of precision

Division by large numbers may result in the result being zero, due to solidity not supporting fractions. Consider requiring a minimum amount for the numerator to ensure that it is always larger than the denominator

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit division by supply
275:             uint256 entitlement = balance / supply;

```


*GitHub* : [275](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L275-L275)

### [L-08]<a name="l-08"></a> Some tokens may revert when large transfers are made

Tokens such as COMP or UNI will revert when an address' balance reaches [`type(uint96).max`](https://github.com/compound-finance/compound-protocol/blob/a3214f67b73310d547e00fc578e8355911c9d376/contracts/Governance/Comp.sol#L238). Ensure that the calls below can be broken up into smaller batches if necessary.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureNFT.sol

169       */
170      function _withdrawBalancesTo(
171          address[] calldata erc20s,
172          address destination
173      ) internal {
174          uint256[] memory amounts = new uint256[](erc20s.length);
175          for (uint i = 0; i < erc20s.length; i++) {
176              address erc20 = erc20s[i];
177              uint256 balance = IERC20(erc20).balanceOf(address(this));
178              if (balance > 0) {
179:                 bool result = IERC20(erc20).transfer(destination, balance);

```


*GitHub* : [169](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L169-L179)

### [L-09]<a name="l-09"></a> State variables not capped at reasonable values

Consider adding minimum/maximum value checks to ensure that the state variables below can never be used to excessively harm users, including via griefing

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit _minDistributionPeriod
471:         MinDistributionPeriod = _minDistributionPeriod;

```


*GitHub* : [471](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L461-L461)

### [L-10]<a name="l-10"></a> Tokens may be minted to `address(0x0)`

Neither the listed functions, nor `_mint()` prevent minting to `address(0x0)`

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit  _mint(), mint()
318      function mint(
319          address account,
320          uint256 amount
321:     ) public onlyOwner nonReentrant {

```


*GitHub* : [318](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L318-L321)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit  _mint(), ()
62       constructor(
63           string memory accountName
64       )
65           ERC721(
66               string.concat(
67                   "althea://liquid-infrastructure-account/",
68                   accountName
69               ),
70               string.concat("LIA:", accountName)
71           )
72:      {

```


*GitHub* : [62](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L62-L72)

### [L-11]<a name="l-11"></a> Use `Ownable2Step` rather than `Ownable`

[`Ownable2Step`](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/3d7a93876a2e5e1d7fe29b5a0e96e222afdc4cfa/contracts/access/Ownable2Step.sol#L31-L56) and [`Ownable2StepUpgradeable`](https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/blob/25aabd286e002a1526c345c8db259d57bdf0ad28/contracts/access/Ownable2StepUpgradeable.sol#L47-L63) prevent the contract ownership from mistakenly being transferred to an address that cannot handle it (e.g. due to a typo in the address), by requiring that the recipient of the owner permissions actively accept via a contract call of its own.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

29    contract LiquidInfrastructureERC20 is
30        ERC20,
31        ERC20Burnable,
32        Ownable,
33        ERC721Holder,
34        ReentrancyGuard
35:   {

```


*GitHub* : [29](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L29-L35)

### Gas Risk Issues

### [G-01]<a name="g-01"></a> `do`-`while` is cheaper than `for`-loops when the initial check can be skipped

`for (uint256 i; i < len; ++i){ ... }` -> `do { ...; ++i } while (i < len);`

*There are 7 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

171:             for (uint i = 0; i < holders.length; i++) {

220:                 for (uint j = 0; j < distributableERC20s.length; j++) {

271:         for (uint i = 0; i < distributableERC20s.length; i++) {

421:         for (uint i = 0; i < ManagedNFTs.length; i++) {

467:         for (uint i = 0; i < _approvedHolders.length; i++) {

```


*GitHub* : [467](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L467-L467), [171](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L171-L171), [220](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L220-L220), [271](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L271-L271), [421](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L421-L421)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

120:         for (uint i = 0; i < newErc20s.length; i++) {

175:         for (uint i = 0; i < erc20s.length; i++) {

```


*GitHub* : [175](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L175-L175), [120](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L120-L120)

### [G-02]<a name="g-02"></a> Consider using `ERC721A` over `ERC721`

[ERC721A](https://www.azuki.com/erc721a) is much more gas-efficient for minting multiple NFTs in the same transaction

*There are 3 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

29   contract LiquidInfrastructureERC20 is
30       ERC20,
31       ERC20Burnable,
32       Ownable,
33       ERC721Holder,
34       ReentrancyGuard
35:  {

```


*GitHub* : [29](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L29-L35)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

33:  contract LiquidInfrastructureNFT is ERC721, OwnableApprovableERC721 {

```


*GitHub* : [33](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L33-L33)

```solidity
File: contracts/OwnableApprovableERC721.sol

20   abstract contract OwnableApprovableERC721 is Context, ERC721 {
21       /**
22        * @dev Throws if called by any account other than the owner.
23:       */

```


*GitHub* : [20](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L20-L23)

### [G-03]<a name="g-03"></a> Use `uint256(1)`/`uint256(2)` instead of `true`/`false` to save gas for changes

Avoids a Gsset (**20000 gas**) when changing from `false` to `true`, after having been `true` in the past. Since most of the bools aren't changed twice in one transaction, I've counted the amount of gas as half of the full amount, for each variable. Note that public state variables can be re-written to be `private` and use `uint256`, but have public getters returning `bool`s.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit reset in: disapproveHolder()
65:      mapping(address => bool) public HolderAllowlist;

/// @audit reset in: _endDistribution()
80:      bool public LockedForDistribution;

```


*GitHub* : [80](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L80-L80), [65](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L65-L65)

### [G-04]<a name="g-04"></a> Use `Array.unsafeAccess()` to avoid repeated array length checks

When using storage arrays, solidity adds an internal lookup of the array's length (a Gcoldsload **2100 gas**) to ensure you don't read past the array's end. You can avoid this lookup by using [`Array.unsafeAccess()`](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/94697be8a3f0dfcd95dfb13ffbd39b5973f5c65d/contracts/utils/Arrays.sol#L57) in cases where the length has already been checked, as is the case with the instances below

*There are 24 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

171:             for (uint i = 0; i < holders.length; i++) {

172:                 if (holders[i] == from) {

174:                     holders[i] = holders[holders.length - 1];

174:                     holders[i] = holders[holders.length - 1];

174:                     holders[i] = holders[holders.length - 1];

175:                     holders.pop();

215:             address recipient = holders[i];

218:                     distributableERC20s.length

220:                 for (uint j = 0; j < distributableERC20s.length; j++) {

221:                     IERC20 toDistribute = IERC20(distributableERC20s[j]);

222:                     uint256 entitlement = erc20EntitlementPerUnit[j] *

229:                 emit Distribution(recipient, distributableERC20s, receipts);

271:         for (uint i = 0; i < distributableERC20s.length; i++) {

272:             uint256 balance = IERC20(distributableERC20s[i]).balanceOf(

276:             erc20EntitlementPerUnit.push(entitlement);

373:                 ManagedNFTs[i]

421:         for (uint i = 0; i < ManagedNFTs.length; i++) {

422:             address managed = ManagedNFTs[i];

425:                 ManagedNFTs[i] = ManagedNFTs[ManagedNFTs.length - 1];

425:                 ManagedNFTs[i] = ManagedNFTs[ManagedNFTs.length - 1];

425:                 ManagedNFTs[i] = ManagedNFTs[ManagedNFTs.length - 1];

426:                 ManagedNFTs.pop();

```


*GitHub* : [174](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L174-L174), [175](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L175-L175), [215](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L215-L215), [218](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L218-L218), [220](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L220-L220), [221](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L221-L221), [222](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L222-L222), [229](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L229-L229), [271](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L271-L271), [272](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L272-L272), [276](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L276-L276), [373](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L373-L373), [421](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L421-L421), [422](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L422-L422), [425](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L425-L425), [425](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L425-L425), [425](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L425-L425), [426](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L426-L426), [171](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L171-L171), [174](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L174-L174), [174](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L174-L174), [172](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L172-L172)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

121:             thresholdErc20s.push(newErc20s[i]);

122:             thresholdAmounts.push(newAmounts[i]);

```


*GitHub* : [121](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L121-L121), [122](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L122-L122)

### [G-05]<a name="g-05"></a> Mappings are cheaper to use than storage arrays

When using storage arrays, solidity adds an internal lookup of the array's length (a Gcoldsload **2100 gas**) to ensure you don't read past the array's end. You can avoid this lookup by using a `mapping` and storing the number of entries in a separate storage variable. In cases where you have sentinel values (e.g. 'zero' means invalid), you can avoid length checks

*There are 6 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

46:      address[] private distributableERC20s;

47:      uint256[] private erc20EntitlementPerUnit;

48:      address[] private holders;

60:      address[] public ManagedNFTs;

```


*GitHub* : [48](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L48-L48), [46](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L46-L46), [47](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L47-L47), [60](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L60-L60)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

39:      address[] private thresholdErc20s;

40:      uint256[] private thresholdAmounts;

```


*GitHub* : [39](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L39-L39), [40](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L40-L40)

### [G-06]<a name="g-06"></a> State variables only set in the constructor should be declared `immutable`

Avoids a Gsset (**20000 gas**) in the constructor, and replaces the first access in each transaction (Gcoldsload - **2100 gas**) and each access thereafter (Gwarmacces - **100 gas**) with a `PUSH32` (**3 gas**). 

While `string`s are not value types, and therefore cannot be `immutable`/`constant` if not hard-coded outside of the constructor, the same behavior can be achieved by making the current contract `abstract` with `virtual` functions for the `string` accessors, and having a child contract override the functions with the hard-coded implementation-specific values.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

75:      uint256 public MinDistributionPeriod;

```


*GitHub* : [75](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L75-L75)

### [G-07]<a name="g-07"></a> State variables can be packed into fewer storage slots by truncating timestamp bytes

By using a `uint32` rather than a larger type for variables that track timestamps, one can save gas by using fewer storage slots per struct, at the expense of the protocol breaking after the year 2106 (when `uint32` wraps). If this is an acceptable tradeoff, if variables occupying the same slot are both written the same function or by the constructor, avoids a separate Gsset (**20000 gas**). Reads of the variables can also be cheaper

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit Variable ordering with 9 slots instead of the current 10:
///           address[](32):distributableERC20s, uint256[](32):erc20EntitlementPerUnit, address[](32):holders, address[](32):ManagedNFTs, mapping(32):HolderAllowlist, uint256(32):LastDistribution, uint256(32):nextDistributionRecipient, uint256(32):nextWithdrawal, uint64(8):MinDistributionPeriod, bool(1):LockedForDistribution
29:   contract LiquidInfrastructureERC20 is

```


*GitHub* : [29](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L29)

### [G-08]<a name="g-08"></a> Avoid updating storage when the value hasn't changed

If the old value is equal to the new value, not re-storing the value will avoid a Gsreset (**2900 gas**), potentially at the expense of a Gcoldsload (**2100 gas**) or a Gwarmaccess (**100 gas**)

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit distributableERC20s:  setDistributableERC20s()
441      function setDistributableERC20s(
442          address[] memory _distributableERC20s
443      ) public onlyOwner {
444          distributableERC20s = _distributableERC20s;
445:     }

```


*GitHub* : [441](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L441-L445)

### [G-09]<a name="g-09"></a> Events should be emitted outside of loops

Emitting an event has an overhead of **375 gas**, which will be incurred on every iteration of the loop. It is cheaper to `emit` only [once](https://github.com/ethereum/EIPs/blob/adad5968fd6de29902174e0cb51c8fc3dceb9ab5/EIPS/eip-1155.md?plain=1#L68) after the loop has finished.

*There are 3 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit  distribute()
229:                 emit Distribution(recipient, distributableERC20s, receipts);

/// @audit  withdrawFromManagedNFTs()
378:             emit Withdrawal(address(withdrawFrom));

```


*GitHub* : [229](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L229-L229), [378](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L378-L378)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit  _withdrawBalancesTo(), withdrawBalancesTo(), withdrawFromManagedNFTs()
184:         emit SuccessfulWithdrawal(destination, erc20s, amounts);

```


*GitHub* : [184](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L184-L184)

### [G-10]<a name="g-10"></a> Assembly: Use scratch space for building calldata

If an external call's calldata can fit into two or fewer words, use the scratch space to build the calldata, rather than allowing Solidity to do a memory expansion.

*There are 4 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

224                      if (toDistribute.transfer(recipient, entitlement)) {
225                          receipts[j] = entitlement;
226:                     }

396:         address nftOwner = nft.ownerOf(nft.AccountId());

```


*GitHub* : [396](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L396-L396), [224](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L224-L226)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

177:             uint256 balance = IERC20(erc20).balanceOf(address(this));

179:                 bool result = IERC20(erc20).transfer(destination, balance);

```


*GitHub* : [179](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L179-L179), [177](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L177-L177)

### [G-11]<a name="g-11"></a> Using `this` to access functions results in an external call, wasting gas

External calls have an overhead of **100 gas**, which can be avoided by not referencing the function using `this`. Contracts [are allowed](https://docs.soliditylang.org/en/latest/contracts.html#function-overriding) to override their parents' functions and change the visibility from `external` to `public`, so make this change if it's required in order to call the function internally.

*There are 5 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

142:         bool exists = (this.balanceOf(to) != 0);

169:         bool stillHolding = (this.balanceOf(from) != 0);

223:                         this.balanceOf(recipient);

270:         uint256 supply = this.totalSupply();

```


*GitHub* : [223](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L223-L223), [270](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L270-L270), [142](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L142-L142), [169](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L169-L169)

```solidity
File: contracts/OwnableApprovableERC721.sol

26:              ERC721(this).ownerOf(tokenId) == _msgSender(),

```


*GitHub* : [26](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L26-L26)

### [G-12]<a name="g-12"></a> Using `bool`s for storage incurs overhead

```solidity
    // Booleans are more expensive than uint256 or any type that takes up a full
    // word because each write operation emits an extra SLOAD to first read the
    // slot's contents, replace the bits taken up by the boolean, and then write
    // back. This is the compiler's defense against contract upgrades and
    // pointer aliasing, and it cannot be disabled.
```
https://github.com/OpenZeppelin/openzeppelin-contracts/blob/58f635312aa21f947cae5f8578638a85aa2519f5/contracts/security/ReentrancyGuard.sol#L23-L27
Use `uint256(0)` and `uint256(1)` for true/false to avoid a Gwarmaccess (**[100 gas](https://gist.github.com/IllIllI000/1b70014db712f8572a72378321250058)**) for the extra SLOAD

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

65:      mapping(address => bool) public HolderAllowlist;

80:      bool public LockedForDistribution;

```


*GitHub* : [65](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L65-L65), [80](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L80-L80)

### [G-13]<a name="g-13"></a> Avoid transferring amounts of zero in order to save gas

Skipping the external call when nothing will be transferred, will save at least **100 gas**

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

224:                     if (toDistribute.transfer(recipient, entitlement)) {

```


*GitHub* : [224](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L224-L224)

### [G-14]<a name="g-14"></a> State variables should be cached in stack variables rather than re-reading them from storage

The instances below point to the second+ access of a state variable within a function. Caching of a state variable replaces each Gwarmaccess (**100 gas**) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses.

*There are 10 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit distributableERC20s on line 218
220:                  for (uint j = 0; j < distributableERC20s.length; j++) {

/// @audit distributableERC20s on line 220
221:                      IERC20 toDistribute = IERC20(distributableERC20s[j]);

/// @audit distributableERC20s on line 221
229:                  emit Distribution(recipient, distributableERC20s, receipts);

/// @audit distributableERC20s on line 271
272:              uint256 balance = IERC20(distributableERC20s[i]).balanceOf(

/// @audit holders on line 185
187:              distribute(holders.length);

/// @audit nextDistributionRecipient on line 209
214:          for (i = nextDistributionRecipient; i < limit; i++) {

/// @audit nextDistributionRecipient on line 232
234:          if (nextDistributionRecipient == holders.length) {

/// @audit nextWithdrawal on line 362
367:              numWithdrawals + nextWithdrawal,

/// @audit nextWithdrawal on line 367
371:          for (i = nextWithdrawal; i < limit; i++) {

/// @audit nextWithdrawal on line 380
382:          if (nextWithdrawal == ManagedNFTs.length) {

```


*GitHub* : [187](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L187), [214](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L214), [234](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L234), [220](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L220), [371](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L371), [382](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L382), [367](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L367), [221](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L221), [229](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L229), [272](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L272)

### [G-15]<a name="g-15"></a> Use the inputs/results of assignments rather than re-reading state variables

When a state variable is assigned, it saves gas to use the value being assigned, later in the function, rather than re-reading the state variable itself. If needed, it can also be stored to a local variable, and be used in that way. Both options avoid a Gwarmaccess (**100 gas**). Note that if the operation is, say `+=`, the assignment also results in a value which can be used. The instances below point to the first reference after the assignment, since later references are already covered by issues describing the caching of state variable values.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit use result of assignment of nextDistributionRecipient, here
234:         if (nextDistributionRecipient == holders.length) {

/// @audit use result of assignment of nextWithdrawal, here
382:         if (nextWithdrawal == ManagedNFTs.length) {

```


*GitHub* : [234](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L234-L234), [382](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L382-L382)

### [G-16]<a name="g-16"></a> `++i`/`i++` should be `unchecked{++i}`/`unchecked{i++}` when it is not possible for them to overflow, as is the case when used in `for`- and `while`-loops

The `unchecked` keyword is new in solidity version 0.8.0, so this only applies to that version or higher, which these instances are. This saves **30-40 gas [per loop](https://gist.github.com/hrkrshnn/ee8fabd532058307229d65dcd5836ddc#the-increment-in-for-loop-post-condition-can-be-made-unchecked)**

*There are 9 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

171:              for (uint i = 0; i < holders.length; i++) {

214:          for (i = nextDistributionRecipient; i < limit; i++) {

220:                  for (uint j = 0; j < distributableERC20s.length; j++) {

271:          for (uint i = 0; i < distributableERC20s.length; i++) {

371:          for (i = nextWithdrawal; i < limit; i++) {

421:          for (uint i = 0; i < ManagedNFTs.length; i++) {

467:          for (uint i = 0; i < _approvedHolders.length; i++) {

```


*GitHub* : [171](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L171), [467](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L467), [421](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L421), [371](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L371), [271](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L271), [220](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L220), [214](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L214)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

120:          for (uint i = 0; i < newErc20s.length; i++) {

175:          for (uint i = 0; i < erc20s.length; i++) {

```


*GitHub* : [120](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L120), [175](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L175)

### [G-17]<a name="g-17"></a> Consider pre-calculating the address of `address(this)` to save gas

Use `foundry`'s [`script.sol`](https://book.getfoundry.sh/reference/forge-std/compute-create-address) or `solady`'s [`LibRlp.sol`](https://github.com/Vectorized/solady/blob/main/src/utils/LibRLP.sol) to save the value in a constant, which will avoid having to spend gas to push the value on the stack every time it's used.

*There are 5 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

273:                 address(this)

377:             withdrawFrom.withdrawBalancesTo(withdrawERC20s, address(this));

398:             nftOwner == address(this),

418:         nft.transferFrom(address(this), to, nft.AccountId());

```


*GitHub* : [377](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L377-L377), [398](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L398-L398), [418](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L418-L418), [273](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L273-L273)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

177:             uint256 balance = IERC20(erc20).balanceOf(address(this));

```


*GitHub* : [177](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L177-L177)

### [G-18]<a name="g-18"></a> Consider using `solady`'s token contracts to save gas

They're written using heavily-optimized assembly, and will your users a lot of gas

*There are 5 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit ERC721Holder
/// @audit ERC20Burnable
/// @audit ERC20
29   contract LiquidInfrastructureERC20 is
30       ERC20,
31       ERC20Burnable,
32       Ownable,
33       ERC721Holder,
34       ReentrancyGuard
35:  {

```


*GitHub* : [29](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L29-L35), [29](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L29-L35), [29](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L29-L35)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit ERC721
33:  contract LiquidInfrastructureNFT is ERC721, OwnableApprovableERC721 {

```


*GitHub* : [33](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L33-L33)

```solidity
File: contracts/OwnableApprovableERC721.sol

/// @audit ERC721
20   abstract contract OwnableApprovableERC721 is Context, ERC721 {
21       /**
22        * @dev Throws if called by any account other than the owner.
23:       */

```


*GitHub* : [20](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L20-L23)

### [G-19]<a name="g-19"></a> State variable read in a loop

The state variable should be cached in and read from a local variable, or accumulated in a local variable then written to storage once outside of the loop, rather than reading/updating it on every iteration of the loop, which will replace each Gwarmaccess (**100 gas**) with a much cheaper stack read.

*There are 8 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit holders
171              for (uint i = 0; i < holders.length; i++) {
172                  if (holders[i] == from) {
173                      // Remove the element at i by copying the last one into its place and removing the last element
174                      holders[i] = holders[holders.length - 1];
175                      holders.pop();
176                  }
177:             }

/// @audit distributableERC20s
/// @audit distributableERC20s
/// @audit distributableERC20s
214          for (i = nextDistributionRecipient; i < limit; i++) {
215              address recipient = holders[i];
216              if (isApprovedHolder(recipient)) {
217                  uint256[] memory receipts = new uint256[](
218                      distributableERC20s.length
219                  );
220                  for (uint j = 0; j < distributableERC20s.length; j++) {
221                      IERC20 toDistribute = IERC20(distributableERC20s[j]);
222                      uint256 entitlement = erc20EntitlementPerUnit[j] *
223                          this.balanceOf(recipient);
224                      if (toDistribute.transfer(recipient, entitlement)) {
225                          receipts[j] = entitlement;
226                      }
227                  }
228  
229                  emit Distribution(recipient, distributableERC20s, receipts);
230              }
231:         }

/// @audit erc20EntitlementPerUnit
271          for (uint i = 0; i < distributableERC20s.length; i++) {
272              uint256 balance = IERC20(distributableERC20s[i]).balanceOf(
273                  address(this)
274              );
275              uint256 entitlement = balance / supply;
276              erc20EntitlementPerUnit.push(entitlement);
277:         }

/// @audit ManagedNFTs
421          for (uint i = 0; i < ManagedNFTs.length; i++) {
422              address managed = ManagedNFTs[i];
423              if (managed == nftContract) {
424                  // Delete by copying in the last element and then pop the end
425                  ManagedNFTs[i] = ManagedNFTs[ManagedNFTs.length - 1];
426                  ManagedNFTs.pop();
427                  break;
428              }
429:         }

```


*GitHub* : [271](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L276-L276), [421](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L426-L426), [214](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L220-L220), [214](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L229-L229), [171](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L175-L175), [214](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L218-L218)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit thresholdErc20s
/// @audit thresholdAmounts
120          for (uint i = 0; i < newErc20s.length; i++) {
121              thresholdErc20s.push(newErc20s[i]);
122              thresholdAmounts.push(newAmounts[i]);
123:         }

```


*GitHub* : [120](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L121-L121), [120](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L122-L122)

### [G-20]<a name="g-20"></a> Use local variables for emitting

Use the function/modifier's local copy of the non-simple state variable, rather than incurring an extra Gwarmaccess (**100 [gas](https://gist.github.com/IllIllI000/4a138405b8834bc9dc66b5bdf94715f9)**). In the unlikely event that the state variable hasn't already been used by the function/modifier, consider whether it is really necessary to include it in the event, given the fact that it incurs a Gcoldsload (**2100 gas**), or whether it can be passed in to or back out of the functions that _do_ use it, or whether it should be removed from the event, and instead be emitted separately when its value actually changes.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit distributableERC20s
226                      }
227                  }
228  
229                  emit Distribution(recipient, distributableERC20s, receipts);
230              }
231:         }

```


*GitHub* : [226](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L226-L231)

### [G-21]<a name="g-21"></a> Multiple accesses of a storage array should use a local variable cache

The instances below point to the second+ access of a value inside a storage array, within a function. Caching an array index value in a local `storage` or `calldata` variable when the value is accessed [multiple times](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0), saves **~42 gas per access** due to not having to recalculate the array's keccak256 hash (`Gkeccak256` - **30 gas**) and that calculation's associated stack operations.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit ManagedNFTs...[]
425:                 ManagedNFTs[i] = ManagedNFTs[ManagedNFTs.length - 1];

```


*GitHub* : [425](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L425-L425)

### [G-22]<a name="g-22"></a> Functions guaranteed to revert when called by normal users can be marked `payable`

If a function modifier such as `onlyOwner` is used, or a function checks `msg.sender` some other way, the function will revert if a normal user tries to pay the function. Marking the function as `payable` will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided. The extra opcodes avoided are `CALLVALUE`(2),`DUP1`(3),`ISZERO`(3),`PUSH2`(3),`JUMPI`(10),`PUSH1`(3),`DUP1`(3),`REVERT`(0),`JUMPDEST`(1),`POP`(2), which costs an average of about **21 gas per call** to the function, in addition to the extra deployment cost

*There are 10 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

106:     function approveHolder(address holder) public onlyOwner {

116:     function disapproveHolder(address holder) public onlyOwner {

303      function mintAndDistribute(
304          address account,
305          uint256 amount
306:     ) public onlyOwner {

318      function mint(
319          address account,
320          uint256 amount
321:     ) public onlyOwner nonReentrant {

394:     function addManagedNFT(address nftContract) public onlyOwner {

413      function releaseManagedNFT(
414          address nftContract,
415          address to
416:     ) public onlyOwner nonReentrant {

441      function setDistributableERC20s(
442          address[] memory _distributableERC20s
443:     ) public onlyOwner {

```


*GitHub* : [394](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L394-L394), [106](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L106-L106), [441](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L441-L443), [413](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L413-L416), [116](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L116-L116), [303](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L303-L306), [318](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L318-L321)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

135:     function withdrawBalances(address[] calldata erc20s) public virtual {

153      function withdrawBalancesTo(
154          address[] calldata erc20s,
155          address destination
156:     ) public virtual {

203:     function recoverAccount() public virtual onlyOwner(AccountId) {

```


*GitHub* : [203](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L203-L203), [135](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L135-L135), [153](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L153-L156)

### [G-23]<a name="g-23"></a> Constructors can be marked `payable`

Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided. A constructor can safely be marked as payable, since only the deployer would be able to pass funds, and the project itself would not pass any funds.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

456       constructor(
457           string memory _name,
458           string memory _symbol,
459           address[] memory _managedNFTs,
460           address[] memory _approvedHolders,
461           uint256 _minDistributionPeriod,
462           address[] memory _distributableErc20s
463:      ) ERC20(_name, _symbol) Ownable() {

```


*GitHub* : [456](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L456-L463)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

62        constructor(
63            string memory accountName
64        )
65            ERC721(
66                string.concat(
67                    "althea://liquid-infrastructure-account/",
68                    accountName
69                ),
70                string.concat("LIA:", accountName)
71:           )

```


*GitHub* : [62](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L62-L71)

### [G-24]<a name="g-24"></a> `internal` functions only called once can be inlined to save gas

Not inlining costs **20 to 40 gas** because of two extra `JUMP` instructions and additional stack operations needed for function calls. The inliner can do it only for 'simple' cases:
> Now to get back to the point why we require the routine to be simple: As soon as you do more complicated things like for example branching, calling external contracts, the Common Subexpression Eliminator cannot re-construct the code anymore or does not do full symbolic evaluation of the expressions. 

https://soliditylang.org/blog/2021/03/02/saving-gas-with-simple-inliner/

Therefore, the instances below contain branching or use op-codes with side-effects

*There are 3 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

151:     function _beforeMintOrBurn() internal view {

257:     function _beginDistribution() internal {

286:     function _endDistribution() internal {

```


*GitHub* : [286](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L286-L286), [257](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L257-L257), [151](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L151-L151)

### [G-25]<a name="g-25"></a> `unchecked {}`  can be used on the division of two `uint`s in order to save gas

The division cannot overflow, since both the numerator and the denominator are non-negative

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

275:             uint256 entitlement = balance / supply;

```


*GitHub* : [275](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L275-L275)

### [G-26]<a name="g-26"></a> Assembly: Checks for `address(0x0)` are more efficient in assembly

Using assembly allows you to [skip](https://gist.github.com/IllIllI000/d6b4b26af2fcd19827093a121e7e3f78) the clearing of the higher-order bits before performing the check for equality.

*There are 3 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

133:         if (!(to == address(0))) {

139:         if (from == address(0) || to == address(0)) {

139:         if (from == address(0) || to == address(0)) {

```


*GitHub* : [133](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L133-L133), [139](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L139-L139), [139](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L139-L139)

### [G-27]<a name="g-27"></a> Don't use `_msgSender()` if not supporting EIP-2771

Use `msg.sender` if the code does not implement [EIP-2771 trusted forwarder](https://eips.ethereum.org/EIPS/eip-2771) support

*There are 4 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureNFT.sol

137:              _isApprovedOrOwner(_msgSender(), AccountId),

158:              _isApprovedOrOwner(_msgSender(), AccountId),

```


*GitHub* : [137](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L137), [158](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L158)

```solidity
File: contracts/OwnableApprovableERC721.sol

26:               ERC721(this).ownerOf(tokenId) == _msgSender(),

37:           if (_isApprovedOrOwner(_msgSender(), tokenId)) {

```


*GitHub* : [26](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L26), [37](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L37)

### [G-28]<a name="g-28"></a> Assembly: Use scratch space when building emitted events with two data arguments

Using the [scratch space](https://gist.github.com/IllIllI000/87c4f03139fa03780fa548b8e4b02b5b) for more than one, but at most two words worth of data (non-indexed arguments) will save gas over needing Solidity's abi memory expansion used for emitting normally.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

433:         emit ReleaseManagedNFT(nftContract, to);

```


*GitHub* : [433](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L433-L433)

### [G-29]<a name="g-29"></a> Counting down when iterating, saves gas

Counting down saves **6 [gas](https://gist.github.com/IllIllI000/764476152f228f8a25a41f1ca14003f5)** _per loop_, since checks for zero are more efficient than checks against any other value

*There are 9 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

171:             for (uint i = 0; i < holders.length; i++) {

214:         for (i = nextDistributionRecipient; i < limit; i++) {

220:                 for (uint j = 0; j < distributableERC20s.length; j++) {

271:         for (uint i = 0; i < distributableERC20s.length; i++) {

371:         for (i = nextWithdrawal; i < limit; i++) {

421:         for (uint i = 0; i < ManagedNFTs.length; i++) {

467:         for (uint i = 0; i < _approvedHolders.length; i++) {

```


*GitHub* : [371](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L371-L371), [421](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L421-L421), [467](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L467-L467), [214](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L214-L214), [220](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L220-L220), [271](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L271-L271), [171](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L171-L171)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

120:         for (uint i = 0; i < newErc20s.length; i++) {

175:         for (uint i = 0; i < erc20s.length; i++) {

```


*GitHub* : [120](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L120-L120), [175](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L175-L175)

### [G-30]<a name="g-30"></a> Duplicated `require()`/`revert()` checks should be refactored to a modifier or function to save deployment gas

This will cost more runtime gas, but will reduce deployment gas when the function is (optionally called via a modifier) called more than once as is the case for the examples below. Most projects do not make this trade-off, but it's available nonetheless.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureNFT.sol

136          require(
137              _isApprovedOrOwner(_msgSender(), AccountId),
138              "caller is not the owner of the Account token and is not approved either"
139:         );

157          require(
158              _isApprovedOrOwner(_msgSender(), AccountId),
159              "caller is not the owner of the Account token and is not approved either"
160:         );

```


*GitHub* : [157](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L157-L160), [136](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L136-L139)

### [G-31]<a name="g-31"></a> Optimize names to save gas

`public`/`external` function names and `public` member variable names can be optimized to save gas. See [this](https://gist.github.com/IllIllI000/a5d8b486a8259f9f77891a919febd1a9) link for an example of how it works. Below are the interfaces/abstract contracts that can be optimized so that the most frequently-called functions use the least amount of gas possible during method lookup. Method IDs that have two leading zero bytes can save **128 gas** each during deployment, and renaming functions to have lower method IDs will save **22 gas** per call, [per sorted position shifted](https://medium.com/joyso/solidity-how-does-function-name-affect-gas-consumption-in-smart-contract-47d270d8ac92)

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit  getThresholds(), setThresholds(), withdrawBalances(), withdrawBalancesTo(), recoverAccount()
33:  contract LiquidInfrastructureNFT is ERC721, OwnableApprovableERC721 {

```


*GitHub* : [33](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L33-L33)

### [G-32]<a name="g-32"></a> Reduce gas usage by moving to Solidity 0.8.19 or later

See [this](https://blog.soliditylang.org/2023/02/22/solidity-0.8.19-release-announcement/#preventing-dead-code-in-runtime-bytecode) link for the full details. Additionally, every new release has new optimizations, which will save gas.

*There are 3 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

2:   pragma solidity 0.8.12; // Force solidity compliance

```


*GitHub* : [2](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L2-L2)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

2:   pragma solidity 0.8.12; // Force solidity compliance

```


*GitHub* : [2](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L2-L2)

```solidity
File: contracts/OwnableApprovableERC721.sol

2:   pragma solidity 0.8.12; // Force solidity compliance

```


*GitHub* : [2](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L2-L2)

### [G-33]<a name="g-33"></a> Use custom errors rather than `revert()`/`require()` strings to save gas

Custom errors are available from solidity version 0.8.4. Custom errors save [**~50 gas**](https://gist.github.com/IllIllI000/ad1bd0d29a0101b25e57c293b4b0c746) each time they're hit by [avoiding having to allocate and store the revert string](https://blog.soliditylang.org/2021/04/21/custom-errors/#errors-in-depth). Not defining the strings also save deployment gas

*There are 18 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

107:         require(!isApprovedHolder(holder), "holder already approved");

117:         require(isApprovedHolder(holder), "holder not approved");

132:         require(!LockedForDistribution, "distribution in progress");

134              require(
135                  isApprovedHolder(to),
136                  "receiver not approved to hold the token"
137:             );

152          require(
153              !_isPastMinDistributionPeriod(),
154              "must distribute before minting or burning"
155:         );

199:         require(numDistributions > 0, "must process at least 1 distribution");

201              require(
202                  _isPastMinDistributionPeriod(),
203                  "MinDistributionPeriod not met"
204:             );

258          require(
259              !LockedForDistribution,
260              "cannot begin distribution when already locked"
261:         );

287          require(
288              LockedForDistribution,
289              "cannot end distribution when not locked"
290:         );

360:         require(!LockedForDistribution, "cannot withdraw during distribution");

397          require(
398              nftOwner == address(this),
399              "this contract does not own the new ManagedNFT"
400:         );

431:         require(true, "unable to find released NFT in ManagedNFTs");

```


*GitHub* : [199](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L199-L199), [107](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L107-L107), [117](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L117-L117), [132](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L132-L132), [134](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L134-L137), [152](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L152-L155), [201](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L201-L204), [258](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L258-L261), [287](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L287-L290), [360](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L360-L360), [397](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L397-L400), [431](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L431-L431)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

112          require(
113              newErc20s.length == newAmounts.length,
114              "threshold values must have the same length"
115:         );

136          require(
137              _isApprovedOrOwner(_msgSender(), AccountId),
138              "caller is not the owner of the Account token and is not approved either"
139:         );

157          require(
158              _isApprovedOrOwner(_msgSender(), AccountId),
159              "caller is not the owner of the Account token and is not approved either"
160:         );

180:                 require(result, "unsuccessful withdrawal");

```


*GitHub* : [112](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L112-L115), [157](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L157-L160), [180](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L180-L180), [136](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L136-L139)

```solidity
File: contracts/OwnableApprovableERC721.sol

25           require(
26               ERC721(this).ownerOf(tokenId) == _msgSender(),
27               "OwnableApprovable: caller is not the owner"
28:          );

40:              revert("OwnableApprovable: caller is not owner nor approved");

```


*GitHub* : [25](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L25-L28), [40](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L40-L40)

### [G-34]<a name="g-34"></a> Using `> 0` costs more gas than `!= 0` when used on a `uint` in a `require()` statement

This change saves **[6 gas](https://aws1.discourse-cdn.com/business6/uploads/zeppelin/original/2X/3/363a367d6d68851f27d2679d10706cd16d788b96.png)** per instance. The optimization works until solidity version [0.8.13](https://gist.github.com/IllIllI000/bf2c3120f24a69e489f12b3213c06c94) where there is a regression in gas costs.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

199:          require(numDistributions > 0, "must process at least 1 distribution");

```


*GitHub* : [199](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L199)

### [G-35]<a name="g-35"></a> `++i` costs less gas than `i++`, especially when it's used in `for`-loops (`--i`/`i--` too)

Saves **5 gas per loop**

*There are 9 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

171:              for (uint i = 0; i < holders.length; i++) {

214:          for (i = nextDistributionRecipient; i < limit; i++) {

220:                  for (uint j = 0; j < distributableERC20s.length; j++) {

271:          for (uint i = 0; i < distributableERC20s.length; i++) {

371:          for (i = nextWithdrawal; i < limit; i++) {

421:          for (uint i = 0; i < ManagedNFTs.length; i++) {

467:          for (uint i = 0; i < _approvedHolders.length; i++) {

```


*GitHub* : [214](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L214), [220](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L220), [271](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L271), [371](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L371), [421](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L421), [467](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L467), [171](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L171)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

120:          for (uint i = 0; i < newErc20s.length; i++) {

175:          for (uint i = 0; i < erc20s.length; i++) {

```


*GitHub* : [120](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L120), [175](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L175)

### [G-36]<a name="g-36"></a> `require()`/`revert()` strings longer than 32 bytes cost extra gas

Each extra memory word of bytes past the original 32 [incurs an MSTORE](https://gist.github.com/hrkrshnn/ee8fabd532058307229d65dcd5836ddc#consider-having-short-revert-strings) which costs **3 gas**

*There are 13 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

134               require(
135                   isApprovedHolder(to),
136                   "receiver not approved to hold the token"
137:              );

152           require(
153               !_isPastMinDistributionPeriod(),
154               "must distribute before minting or burning"
155:          );

199:          require(numDistributions > 0, "must process at least 1 distribution");

258           require(
259               !LockedForDistribution,
260               "cannot begin distribution when already locked"
261:          );

287           require(
288               LockedForDistribution,
289               "cannot end distribution when not locked"
290:          );

360:          require(!LockedForDistribution, "cannot withdraw during distribution");

397           require(
398               nftOwner == address(this),
399               "this contract does not own the new ManagedNFT"
400:          );

431:          require(true, "unable to find released NFT in ManagedNFTs");

```


*GitHub* : [287](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L287-L290), [360](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L360), [397](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L397-L400), [431](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L431), [199](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L199), [258](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L258-L261), [134](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L134-L137), [152](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L152-L155)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

112           require(
113               newErc20s.length == newAmounts.length,
114               "threshold values must have the same length"
115:          );

136           require(
137               _isApprovedOrOwner(_msgSender(), AccountId),
138               "caller is not the owner of the Account token and is not approved either"
139:          );

157           require(
158               _isApprovedOrOwner(_msgSender(), AccountId),
159               "caller is not the owner of the Account token and is not approved either"
160:          );

```


*GitHub* : [112](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L112-L115), [136](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L136-L139), [157](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L157-L160)

```solidity
File: contracts/OwnableApprovableERC721.sol

25            require(
26                ERC721(this).ownerOf(tokenId) == _msgSender(),
27                "OwnableApprovable: caller is not the owner"
28:           );

40:               revert("OwnableApprovable: caller is not owner nor approved");

```


*GitHub* : [40](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L40), [25](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L25-L28)

### [G-37]<a name="g-37"></a> `>=` costs less gas than `>`

The compiler uses opcodes `GT` and `ISZERO` for solidity code that uses `>`, but only requires `LT` for `>=`, [which saves **3 gas**](https://gist.github.com/IllIllI000/3dc79d25acccfa16dee4e83ffdc6ffde). If `<` is being used, the condition can be inverted. In cases where a for-loop is being used, one can count down rather than up, in order to use the optimal operator

*There are 13 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

171:             for (uint i = 0; i < holders.length; i++) {

186:         if (num > 0) {

199:         require(numDistributions > 0, "must process at least 1 distribution");

214:         for (i = nextDistributionRecipient; i < limit; i++) {

220:                 for (uint j = 0; j < distributableERC20s.length; j++) {

265:         if (erc20EntitlementPerUnit.length > 0) {

271:         for (uint i = 0; i < distributableERC20s.length; i++) {

371:         for (i = nextWithdrawal; i < limit; i++) {

421:         for (uint i = 0; i < ManagedNFTs.length; i++) {

467:         for (uint i = 0; i < _approvedHolders.length; i++) {

```


*GitHub* : [220](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L220-L220), [171](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L171-L171), [186](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L186-L186), [199](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L199-L199), [214](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L214-L214), [265](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L265-L265), [271](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L271-L271), [371](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L371-L371), [421](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L421-L421), [467](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L467-L467)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

120:         for (uint i = 0; i < newErc20s.length; i++) {

175:         for (uint i = 0; i < erc20s.length; i++) {

178:             if (balance > 0) {

```


*GitHub* : [120](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L120-L120), [175](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L175-L175), [178](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L178-L178)

### [G-38]<a name="g-38"></a> Reduce deployment costs by tweaking contracts' metadata

See [this](https://www.rareskills.io/post/solidity-metadata) link, at its bottom, for full details

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

29   contract LiquidInfrastructureERC20 is
30       ERC20,
31       ERC20Burnable,
32       Ownable,
33       ERC721Holder,
34       ReentrancyGuard
35:  {

```


*GitHub* : [29](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L29-L35)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

33:  contract LiquidInfrastructureNFT is ERC721, OwnableApprovableERC721 {

```


*GitHub* : [33](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L33-L33)

### [G-39]<a name="g-39"></a> Stack variable is only used once

If the variable is only accessed once, it's cheaper to use the assigned value directly that one time, and save the **3 gas** the extra stack assignment would spend

*There are 5 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

142:         bool exists = (this.balanceOf(to) != 0);

169:         bool stillHolding = (this.balanceOf(from) != 0);

185:         uint256 num = holders.length;

396:         address nftOwner = nft.ownerOf(nft.AccountId());

```


*GitHub* : [396](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L396-L396), [142](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L142-L142), [169](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L169-L169), [185](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L185-L185)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

140:         address destination = ownerOf(AccountId);

```


*GitHub* : [140](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L140-L140)

### [G-40]<a name="g-40"></a> A `memory` array's `length` should not be looked up in every iteration of a `for`/`while`-loop

Caching the length of `memory` arrays changes each length lookup (i.e. on every iteration) from an `MLOAD` to a `DUP<N>` (**3 gas**), and gets rid of the extra `DUP<N>` needed to store the stack offset, saving **3 [gas](https://gist.github.com/IllIllI000/6f2891c6393fbbbd7dd83d62d839dc5e)**.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

467:         for (uint i = 0; i < _approvedHolders.length; i++) {

```


*GitHub* : [467](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L467-L467)

### [G-41]<a name="g-41"></a> Enable IR-based code generation

By using `--via-ir` or `{"viaIR": true}`, the compiler is able to use more advanced [multi-function optimizations](https://docs.soliditylang.org/en/v0.8.17/ir-breaking-changes.html#solidity-ir-based-codegen-changes), for extra gas savings.

*There are 0 instance(s) of this issue:*

```solidity
File: Various Files
```


### [G-42]<a name="g-42"></a> Using `private` rather than `public`, saves gas

For constants, the values can be read from the verified contract source code, or if there are multiple values there can be a single getter function that [returns a tuple](https://github.com/code-423n4/2022-08-frax/blob/90f55a9ce4e25bceed3a74290b854341d8de6afa/src/contracts/FraxlendPair.sol#L156-L178) of the values of all currently-public constants. Saves **3406-3606 gas** in deployment gas due to the compiler not having to create non-payable getter functions for deployment calldata, not having to store the bytes of the value outside of where it's used, and not adding another entry to the method ID table

*There are 8 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

54:      uint256 public constant Version = 1;

60:      address[] public ManagedNFTs;

65:      mapping(address => bool) public HolderAllowlist;

70:      uint256 public LastDistribution;

75:      uint256 public MinDistributionPeriod;

80:      bool public LockedForDistribution;

```


*GitHub* : [80](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L80-L80), [70](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L70-L70), [65](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L65-L65), [75](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L75-L75), [60](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L60-L60), [54](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L54-L54)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

46:      uint256 public constant Version = 1;

53:      uint256 public constant AccountId = 1;

```


*GitHub* : [53](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L53-L53), [46](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L46-L46)

### NonCritical Risk Issues

### [N-01]<a name="n-01"></a> `constant`s/`immutable`s redefined elsewhere

Consider defining each of these in only one contract so that values cannot become out of sync when only one location is updated (i.e. having `ContA.X`,`ContB.Y` is fine since they're different constant names in different files, but `ContA.X`, `ContB.X` is not since it's the same constant defined in multiple files with the same value). Even things like `decimals` and `VERSION` can employ file-level constants such as `PREFERRED_DECIMALS = 18` and `INITIAL_VERSION = "1.0.0"`

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit Seen in LiquidInfrastructureNFT
54:      uint256 public constant Version = 1;

```


*GitHub* : [54](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L54-L54)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit Seen in LiquidInfrastructureERC20
46:      uint256 public constant Version = 1;

```


*GitHub* : [46](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L46-L46)

### [N-02]<a name="n-02"></a> `public` functions not called by the contract should be declared `external` instead

Contracts [are allowed](https://docs.soliditylang.org/en/latest/contracts.html#function-overriding) to override their parents' functions and change the visibility from `external` to `public`.

*There are 14 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

106:      function approveHolder(address holder) public onlyOwner {

116:      function disapproveHolder(address holder) public onlyOwner {

303       function mintAndDistribute(
304           address account,
305           uint256 amount
306:      ) public onlyOwner {

331:      function burnAndDistribute(uint256 amount) public {

344:      function burnFromAndDistribute(address account, uint256 amount) public {

351       function withdrawFromAllManagedNFTs() public {
352:          withdrawFromManagedNFTs(ManagedNFTs.length);

394:      function addManagedNFT(address nftContract) public onlyOwner {

413       function releaseManagedNFT(
414           address nftContract,
415           address to
416:      ) public onlyOwner nonReentrant {

441       function setDistributableERC20s(
442           address[] memory _distributableERC20s
443:      ) public onlyOwner {

```


*GitHub* : [106](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L106), [116](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L116), [303](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L303-L306), [331](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L331), [344](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L344), [351](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L351-L352), [394](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L394), [413](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L413-L416), [441](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L441-L443)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

84        function getThresholds()
85            public
86            view
87            virtual
88:           returns (address[] memory, uint256[] memory)

108       function setThresholds(
109           address[] calldata newErc20s,
110           uint256[] calldata newAmounts
111:      ) public virtual onlyOwnerOrApproved(AccountId) {

135:      function withdrawBalances(address[] calldata erc20s) public virtual {

153       function withdrawBalancesTo(
154           address[] calldata erc20s,
155:          address destination

203:      function recoverAccount() public virtual onlyOwner(AccountId) {

```


*GitHub* : [84](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L84-L88), [108](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L108-L111), [135](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L135), [153](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L153-L155), [203](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L203)

### [N-03]<a name="n-03"></a> Array is `push()`ed but not `pop()`ed

Array entries are added but are never removed. Consider whether this should be the case, or whether there should be a maximum, or whether old entries should be removed. Cases where there are specific potential problems will be flagged separately under a different issue.

*There are 3 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

276:             erc20EntitlementPerUnit.push(entitlement);

```


*GitHub* : [276](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L276-L276)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

121:             thresholdErc20s.push(newErc20s[i]);

122:             thresholdAmounts.push(newAmounts[i]);

```


*GitHub* : [122](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L122-L122), [121](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L121-L121)

### [N-04]<a name="n-04"></a> Avoid external calls in modifiers

It is unusual to have external calls in modifiers, and doing so will make reviewers more likely to miss important external interactions. Consider moving the external call to an internal function, and calling that function from the modifier.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/OwnableApprovableERC721.sol

/// @audit ownerOf()
24       modifier onlyOwner(uint256 tokenId) {
25           require(
26               ERC721(this).ownerOf(tokenId) == _msgSender(),
27               "OwnableApprovable: caller is not the owner"
28           );
29           _;
30:      }

```


*GitHub* : [24](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L26-L26)

### [N-05]<a name="n-05"></a> Avoid the use of sensitive terms

Use [alternative variants](https://www.zdnet.com/article/mysql-drops-master-slave-and-blacklist-whitelist-terminology/), e.g. allowlist/denylist instead of whitelist/blacklist

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

63:        * @notice This collection holds the whitelist for accounts approved to hold the LiquidInfrastructureERC20

```


*GitHub* : [63](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L63)

### [N-06]<a name="n-06"></a> Consider adding emergency-stop functionality

Adding a way to quickly halt protocol functionality in an emergency, rather than having to pause individual contracts one-by-one, will make in-progress hack mitigation faster and much less stressful.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

29   contract LiquidInfrastructureERC20 is
30       ERC20,
31       ERC20Burnable,
32       Ownable,
33       ERC721Holder,
34       ReentrancyGuard
35:  {

```


*GitHub* : [29](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L29-L35)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

33:  contract LiquidInfrastructureNFT is ERC721, OwnableApprovableERC721 {

```


*GitHub* : [33](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L33-L33)

### [N-07]<a name="n-07"></a> Consider adding formal verification proofs

Consider using formal verification to mathematically prove that your code does what is intended, and does not have any edge cases with unexpected behavior. The solidity compiler itself has this functionality [built in](https://docs.soliditylang.org/en/latest/smtchecker.html#smtchecker-and-formal-verification)

*There are 0 instance(s) of this issue:*

```solidity
File: Various Files
```


### [N-08]<a name="n-08"></a> Consider adding validation of user inputs

There are no validations done on the arguments below. Consider that the Solidity [documentation](https://docs.soliditylang.org/en/latest/control-structures.html#panic-via-assert-and-error-via-require) states that `Properly functioning code should never create a Panic, not even on invalid external input. If this happens, then there is a bug in your contract which you should fix`. This means that there should be explicit checks for expected ranges of inputs. Underflows/overflows result in panics should not be used as range checks, and allowing funds to be sent to  `0x0`, which is the default value of address variables and has many gotchas, should be avoided.

*There are 7 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit account
303      function mintAndDistribute(
304          address account,
305          uint256 amount
306      ) public onlyOwner {
307          if (_isPastMinDistributionPeriod()) {
308              distributeToAllHolders();
309          }
310          mint(account, amount);
311:     }

/// @audit account
318      function mint(
319          address account,
320          uint256 amount
321      ) public onlyOwner nonReentrant {
322          _mint(account, amount);
323:     }

/// @audit account
344      function burnFromAndDistribute(address account, uint256 amount) public {
345          if (_isPastMinDistributionPeriod()) {
346              distributeToAllHolders();
347          }
348          burnFrom(account, amount);
349:     }

/// @audit nftContract
394      function addManagedNFT(address nftContract) public onlyOwner {
395          LiquidInfrastructureNFT nft = LiquidInfrastructureNFT(nftContract);
396          address nftOwner = nft.ownerOf(nft.AccountId());
397          require(
398              nftOwner == address(this),
399              "this contract does not own the new ManagedNFT"
400          );
401          ManagedNFTs.push(nftContract);
402          emit AddManagedNFT(nftContract);
403:     }

/// @audit nftContract
/// @audit to
413      function releaseManagedNFT(
414          address nftContract,
415          address to
416      ) public onlyOwner nonReentrant {
417          LiquidInfrastructureNFT nft = LiquidInfrastructureNFT(nftContract);
418          nft.transferFrom(address(this), to, nft.AccountId());
419  
420          // Remove the released NFT from the collection
421          for (uint i = 0; i < ManagedNFTs.length; i++) {
422              address managed = ManagedNFTs[i];
423              if (managed == nftContract) {
424                  // Delete by copying in the last element and then pop the end
425                  ManagedNFTs[i] = ManagedNFTs[ManagedNFTs.length - 1];
426                  ManagedNFTs.pop();
427                  break;
428              }
429          }
430          // By this point the NFT should have been found and removed from ManagedNFTs
431          require(true, "unable to find released NFT in ManagedNFTs");
432  
433          emit ReleaseManagedNFT(nftContract, to);
434:     }

```


*GitHub* : [344](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L344-L349), [394](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L394-L403), [413](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L413-L434), [413](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L413-L434), [303](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L303-L311), [318](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L318-L323)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit destination
153      function withdrawBalancesTo(
154          address[] calldata erc20s,
155          address destination
156      ) public virtual {
157          require(
158              _isApprovedOrOwner(_msgSender(), AccountId),
159              "caller is not the owner of the Account token and is not approved either"
160          );
161          _withdrawBalancesTo(erc20s, destination);
162:     }

```


*GitHub* : [153](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L153-L162)

### [N-09]<a name="n-09"></a> Consider bounding input array length

The functions below take in an unbounded array, and make function calls for entries in the array. While the function will revert if it eventually runs out of gas, it may be a nicer user experience to `require()` that the length of the array is below some reasonable maximum, so that the user doesn't have to use up a full transaction's gas only to see that the transaction reverts.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

214          for (i = nextDistributionRecipient; i < limit; i++) {
215              address recipient = holders[i];
216              if (isApprovedHolder(recipient)) {
217                  uint256[] memory receipts = new uint256[](
218                      distributableERC20s.length
219                  );
220                  for (uint j = 0; j < distributableERC20s.length; j++) {
221                      IERC20 toDistribute = IERC20(distributableERC20s[j]);
222                      uint256 entitlement = erc20EntitlementPerUnit[j] *
223                          this.balanceOf(recipient);
224                      if (toDistribute.transfer(recipient, entitlement)) {
225                          receipts[j] = entitlement;
226                      }
227                  }
228  
229                  emit Distribution(recipient, distributableERC20s, receipts);
230              }
231:         }

```


*GitHub* : [214](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L214-L231)

### [N-10]<a name="n-10"></a> Consider defining system-wide constants in a single file

`ContA.X = 0`, `ContB.Y = 1`, `ContC.Z = 2` -> `ContConstants.X = 0`, `ContConstants.Y = 1`, `ContConstants.Z = 2`; `ContA.X = X`, `ContB.Y = Y`, `ContC.Z = Z`,

*There are 3 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

54:      uint256 public constant Version = 1;

```


*GitHub* : [54](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L54-L54)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

46:      uint256 public constant Version = 1;

53:      uint256 public constant AccountId = 1;

```


*GitHub* : [53](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L53-L53), [46](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L46-L46)

### [N-11]<a name="n-11"></a> Consider disabling `renounceOwnership()`

If the plan for your project does not include eventually giving up all ownership control, consider overwriting OpenZeppelin's `Ownable`'s `renounceOwnership()` function in order to disable it.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit Ownable.renounceOwnership()
29   contract LiquidInfrastructureERC20 is
30       ERC20,
31       ERC20Burnable,
32       Ownable,
33       ERC721Holder,
34       ReentrancyGuard
35:  {

```


*GitHub* : [29](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L29-L35)

### [N-12]<a name="n-12"></a> Consider emitting an event at the end of the constructor

This will allow users to easily exactly pinpoint when and by whom a contract was constructed

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureNFT.sol

62       constructor(
63           string memory accountName
64       )
65           ERC721(
66               string.concat(
67                   "althea://liquid-infrastructure-account/",
68                   accountName
69               ),
70               string.concat("LIA:", accountName)
71           )
72:      {

```


*GitHub* : [62](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L62-L72)

### [N-13]<a name="n-13"></a> Consider making contracts `Upgradeable`

This allows for bugs to be fixed in production, at the expense of _significantly_ increasing centralization.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

29   contract LiquidInfrastructureERC20 is
30       ERC20,
31       ERC20Burnable,
32       Ownable,
33       ERC721Holder,
34       ReentrancyGuard
35:  {

```


*GitHub* : [29](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L29-L35)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

33:  contract LiquidInfrastructureNFT is ERC721, OwnableApprovableERC721 {

```


*GitHub* : [33](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L33-L33)

### [N-14]<a name="n-14"></a> Consider moving duplicated strings to constants



*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureNFT.sol

138:             "caller is not the owner of the Account token and is not approved either"

159:             "caller is not the owner of the Account token and is not approved either"

```


*GitHub* : [159](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L159-L159), [138](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L138-L138)

### [N-15]<a name="n-15"></a> Consider providing a ranged getter for array state variables

While the compiler automatically provides a getter for accessing single elements within a public state variable array, it doesn't provide a way to fetch the whole array, or subsets thereof. Consider adding a function to allow the fetching of slices of the array, especially if the contract doesn't already have multicall functionality.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

60:      address[] public ManagedNFTs;

```


*GitHub* : [60](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L60-L60)

### [N-16]<a name="n-16"></a> Consider using `delete` rather than assigning zero/false to clear values

The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic

*There are 4 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

118:         HolderAllowlist[holder] = false;

279:         nextDistributionRecipient = 0;

292:         LockedForDistribution = false;

383:             nextWithdrawal = 0;

```


*GitHub* : [279](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L279-L279), [292](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L292-L292), [383](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L383-L383), [118](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L118-L118)

### [N-17]<a name="n-17"></a> Consider using named function arguments

When calling functions in external contracts with multiple arguments, consider using [named](https://docs.soliditylang.org/en/latest/control-structures.html#function-calls-with-named-parameters) function parameters, rather than positional ones.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

377:             withdrawFrom.withdrawBalancesTo(withdrawERC20s, address(this));

```


*GitHub* : [377](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L377-L377)

### [N-18]<a name="n-18"></a> Consider using named mappings

Consider moving to solidity version 0.8.18 or later, and using [named mappings](https://ethereum.stackexchange.com/a/145555) to make it easier to understand the purpose of each mapping

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

65:      mapping(address => bool) public HolderAllowlist;

```


*GitHub* : [65](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L65-L65)

### [N-19]<a name="n-19"></a> Consider using named returns

Using named returns makes the code more self-documenting, makes it easier to fill out NatSpec, and in some cases can save gas. The cases below are where there currently is at most one return statement, which is ideal for named returns.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

96:      function isApprovedHolder(address account) public view returns (bool) {

```


*GitHub* : [96](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L96-L96)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

84       function getThresholds()
85           public
86           view
87           virtual
88           returns (address[] memory, uint256[] memory)
89:      {

```


*GitHub* : [84](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L84-L89)

### [N-20]<a name="n-20"></a> Consider using the `using`-`for` syntax

The `using`-`for` [syntax](https://docs.soliditylang.org/en/latest/contracts.html#using-for) is the more common way of calling library functions.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

208          uint256 limit = Math.min(
209              nextDistributionRecipient + numDistributions,
210              holders.length
211:         );

366          uint256 limit = Math.min(
367              numWithdrawals + nextWithdrawal,
368              ManagedNFTs.length
369:         );

```


*GitHub* : [208](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L208-L211), [366](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L366-L369)

### [N-21]<a name="n-21"></a> Constants in comparisons should appear on the left side

Doing so will prevent [typo bugs](https://www.moserware.com/2008/01/constants-on-left-are-better-but-this.html) where the first '!', '>', '<', or '=' at the beginning of the operator is missing.

*There are 9 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

142:         bool exists = (this.balanceOf(to) != 0);

169:         bool stillHolding = (this.balanceOf(from) != 0);

186:         if (num > 0) {

199:         require(numDistributions > 0, "must process at least 1 distribution");

245:         if (totalSupply() == 0 || holders.length == 0) {

245:         if (totalSupply() == 0 || holders.length == 0) {

265:         if (erc20EntitlementPerUnit.length > 0) {

362:         if (nextWithdrawal == 0) {

```


*GitHub* : [245](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L245-L245), [142](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L142-L142), [169](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L169-L169), [186](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L186-L186), [199](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L199-L199), [245](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L245-L245), [265](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L265-L265), [362](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L362-L362)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

178:             if (balance > 0) {

```


*GitHub* : [178](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L178-L178)

### [N-22]<a name="n-22"></a> Contracts should have all `public`/`external` functions exposed by `interface`s

The `contract`s should expose an `interface` so that other projects can more easily integrate with it, without having to develop their own non-standard variants.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit  Version(), ManagedNFTs(), HolderAllowlist(), LastDistribution(), MinDistributionPeriod(), LockedForDistribution(), isApprovedHolder(), approveHolder(), disapproveHolder(), distributeToAllHolders(), distribute(), mintAndDistribute(), mint(), burnAndDistribute(), burnFromAndDistribute(), withdrawFromAllManagedNFTs(), withdrawFromManagedNFTs(), addManagedNFT(), releaseManagedNFT(), setDistributableERC20s()
29   contract LiquidInfrastructureERC20 is
30       ERC20,
31       ERC20Burnable,
32       Ownable,
33       ERC721Holder,
34       ReentrancyGuard
35:  {

```


*GitHub* : [29](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L29-L35)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit  Version(), AccountId(), getThresholds(), setThresholds(), withdrawBalances(), withdrawBalancesTo(), recoverAccount()
33:  contract LiquidInfrastructureNFT is ERC721, OwnableApprovableERC721 {

```


*GitHub* : [33](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L33-L33)

### [N-23]<a name="n-23"></a> Contracts should have full test coverage

While 100% code coverage does not guarantee that there are no bugs, it often will catch easy-to-find bugs, and will ensure that there are fewer regressions when the code invariably has to be modified. Furthermore, in order to get full coverage, code authors will often have to re-organize their code so that it is more modular, so that each component can be tested separately, which reduces interdependencies between modules and layers, and makes for code that is easier to reason about and audit.

*There are 0 instance(s) of this issue:*

```solidity
File: Various Files
```


### [N-24]<a name="n-24"></a> Critical system parameter changes should be behind a timelock

From the point of view of a user, the changing of the owner of a contract is a high risk operation that may have outcomes ranging from an attacker gaining control over the protocol, to the function no longer functioning due to a typo in the destination address. To give users plenty of warning so that they can validate any ownership or other critical parameter changes, these changes should be behind a timelock.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureNFT.sol

108      function setThresholds(
109          address[] calldata newErc20s,
110          uint256[] calldata newAmounts
111      ) public virtual onlyOwnerOrApproved(AccountId) {
112          require(
113              newErc20s.length == newAmounts.length,
114              "threshold values must have the same length"
115          );
116          // Clear the thresholds before overwriting
117          delete thresholdErc20s;
118          delete thresholdAmounts;
119  
120          for (uint i = 0; i < newErc20s.length; i++) {
121              thresholdErc20s.push(newErc20s[i]);
122              thresholdAmounts.push(newAmounts[i]);
123          }
124          emit ThresholdsChanged(newErc20s, newAmounts);
125:     }

```


*GitHub* : [108](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L108-L125)

### [N-25]<a name="n-25"></a> Custom errors should be used rather than `revert()`/`require()`

Custom errors are available from solidity version 0.8.4. Custom errors are more easily processed in `try`-`catch` blocks, and are easier to re-use and maintain.

*There are 18 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

107:         require(!isApprovedHolder(holder), "holder already approved");

117:         require(isApprovedHolder(holder), "holder not approved");

132:         require(!LockedForDistribution, "distribution in progress");

134              require(
135                  isApprovedHolder(to),
136                  "receiver not approved to hold the token"
137:             );

152          require(
153              !_isPastMinDistributionPeriod(),
154              "must distribute before minting or burning"
155:         );

199:         require(numDistributions > 0, "must process at least 1 distribution");

201              require(
202                  _isPastMinDistributionPeriod(),
203                  "MinDistributionPeriod not met"
204:             );

258          require(
259              !LockedForDistribution,
260              "cannot begin distribution when already locked"
261:         );

287          require(
288              LockedForDistribution,
289              "cannot end distribution when not locked"
290:         );

360:         require(!LockedForDistribution, "cannot withdraw during distribution");

397          require(
398              nftOwner == address(this),
399              "this contract does not own the new ManagedNFT"
400:         );

431:         require(true, "unable to find released NFT in ManagedNFTs");

```


*GitHub* : [132](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L132-L132), [134](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L134-L137), [152](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L152-L155), [199](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L199-L199), [201](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L201-L204), [258](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L258-L261), [287](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L287-L290), [360](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L360-L360), [397](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L397-L400), [431](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L431-L431), [117](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L117-L117), [107](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L107-L107)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

112          require(
113              newErc20s.length == newAmounts.length,
114              "threshold values must have the same length"
115:         );

136          require(
137              _isApprovedOrOwner(_msgSender(), AccountId),
138              "caller is not the owner of the Account token and is not approved either"
139:         );

157          require(
158              _isApprovedOrOwner(_msgSender(), AccountId),
159              "caller is not the owner of the Account token and is not approved either"
160:         );

180:                 require(result, "unsuccessful withdrawal");

```


*GitHub* : [157](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L157-L160), [180](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L180-L180), [112](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L112-L115), [136](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L136-L139)

```solidity
File: contracts/OwnableApprovableERC721.sol

25           require(
26               ERC721(this).ownerOf(tokenId) == _msgSender(),
27               "OwnableApprovable: caller is not the owner"
28:          );

40:              revert("OwnableApprovable: caller is not owner nor approved");

```


*GitHub* : [40](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L40-L40), [25](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L25-L28)

### [N-26]<a name="n-26"></a> Duplicated `require()`/`revert()` checks should be refactored to a modifier or function



*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureNFT.sol

136          require(
137              _isApprovedOrOwner(_msgSender(), AccountId),
138              "caller is not the owner of the Account token and is not approved either"
139:         );

157          require(
158              _isApprovedOrOwner(_msgSender(), AccountId),
159              "caller is not the owner of the Account token and is not approved either"
160:         );

```


*GitHub* : [136](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L136-L139), [157](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L157-L160)

### [N-27]<a name="n-27"></a> Error messages should descriptive, rather that cryptic

The error message should clearly state _how_/_why_ something is an error, not just that a specific error state was reached; someone shouldn't have to read the code in order to see how to resolve the problem

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureNFT.sol

179                  bool result = IERC20(erc20).transfer(destination, balance);
180:                 require(result, "unsuccessful withdrawal");

```


*GitHub* : [179](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L179-L180)

### [N-28]<a name="n-28"></a> Event is not properly `indexed`

Index event fields make the field more quickly accessible [to off-chain tools](https://ethereum.stackexchange.com/questions/40396/can-somebody-please-explain-the-concept-of-event-indexing) that parse events. This is especially useful when it comes to filtering based on an address. However, note that each index field costs extra gas during emission, so it's not necessarily best to index the maximum allowed per event (three fields). Where applicable, each `event` should use three `indexed` fields if there are three or more fields, and gas usage is not particularly of concern for the events in question. If there are fewer than three applicable fields, all of the applicable fields should be indexed.

*There are 5 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

38:       event Distribution(address recipient, address[] tokens, uint256[] amounts);

41:       event Withdrawal(address source);

43:       event AddManagedNFT(address nft);

44:       event ReleaseManagedNFT(address nft, address to);

```


*GitHub* : [41](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L41), [43](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L43), [44](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L44), [38](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L38)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

34:       event SuccessfulWithdrawal(address to, address[] erc20s, uint256[] amounts);

```


*GitHub* : [34](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L34)

### [N-29]<a name="n-29"></a> Events are missing sender information

When an action is triggered based on a user's action, not being able to filter based on who triggered the action makes event processing a lot more cumbersome. Including the `msg.sender` the events of these types of action will make events much more useful to end users, especially when `msg.sender` is not `tx.origin`.

*There are 12 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

229:                 emit Distribution(recipient, distributableERC20s, receipts);

280:         emit DistributionStarted();

294:         emit DistributionFinished();

363:             emit WithdrawalStarted();

378:             emit Withdrawal(address(withdrawFrom));

384:             emit WithdrawalFinished();

402:         emit AddManagedNFT(nftContract);

433:         emit ReleaseManagedNFT(nftContract, to);

475:         emit Deployed();

```


*GitHub* : [384](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L384-L384), [229](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L229-L229), [280](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L280-L280), [294](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L294-L294), [363](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L363-L363), [378](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L378-L378), [402](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L402-L402), [433](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L433-L433), [475](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L475-L475)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

124:         emit ThresholdsChanged(newErc20s, newAmounts);

184:         emit SuccessfulWithdrawal(destination, erc20s, amounts);

204:         emit TryRecover();

```


*GitHub* : [184](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L184-L184), [204](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L204-L204), [124](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L124-L124)

### [N-30]<a name="n-30"></a> Events should use parameters to convey information

For example, rather than using `event Paused()` and `event Unpaused()`, use `event PauseState(address indexed whoChangedIt, bool wasPaused, bool isNowPaused)`

*There are 6 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

36:      event Deployed();

37:      event DistributionStarted();

39:      event DistributionFinished();

40:      event WithdrawalStarted();

42:      event WithdrawalFinished();

```


*GitHub* : [36](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L36-L36), [42](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L42-L42), [39](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L39-L39), [40](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L40-L40), [37](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L37-L37)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

35:      event TryRecover();

```


*GitHub* : [35](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L35-L35)

### [N-31]<a name="n-31"></a> High cyclomatic complexity

Consider breaking down these blocks into more manageable units, by splitting things into utility functions, by reducing nesting, and by using early returns

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

198      function distribute(uint256 numDistributions) public nonReentrant {
199          require(numDistributions > 0, "must process at least 1 distribution");
200          if (!LockedForDistribution) {
201              require(
202                  _isPastMinDistributionPeriod(),
203                  "MinDistributionPeriod not met"
204              );
205              _beginDistribution();
206          }
207  
208          uint256 limit = Math.min(
209              nextDistributionRecipient + numDistributions,
210              holders.length
211          );
212  
213          uint i;
214          for (i = nextDistributionRecipient; i < limit; i++) {
215              address recipient = holders[i];
216              if (isApprovedHolder(recipient)) {
217                  uint256[] memory receipts = new uint256[](
218                      distributableERC20s.length
219                  );
220                  for (uint j = 0; j < distributableERC20s.length; j++) {
221                      IERC20 toDistribute = IERC20(distributableERC20s[j]);
222                      uint256 entitlement = erc20EntitlementPerUnit[j] *
223                          this.balanceOf(recipient);
224                      if (toDistribute.transfer(recipient, entitlement)) {
225                          receipts[j] = entitlement;
226                      }
227                  }
228  
229                  emit Distribution(recipient, distributableERC20s, receipts);
230              }
231          }
232          nextDistributionRecipient = i;
233  
234          if (nextDistributionRecipient == holders.length) {
235              _endDistribution();
236          }
237:     }

```


*GitHub* : [198](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L198-L237)

### [N-32]<a name="n-32"></a> Import declarations should import specific identifiers, rather than the whole file

Using import declarations of the form `import {<identifier_name>} from "some/file.sol"` avoids polluting the symbol namespace making flattened files smaller, and speeds up compilation (but does not save any gas)

*There are 13 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

4:    import "@openzeppelin/contracts/utils/math/Math.sol";

5:    import "@openzeppelin/contracts/access/Ownable.sol";

6:    import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

7:    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

8:    import "@openzeppelin/contracts/token/ERC721/utils/ERC721Holder.sol";

9:    import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";

10:   import "@openzeppelin/contracts/security/ReentrancyGuard.sol";

11:   import "./LiquidInfrastructureNFT.sol";

```


*GitHub* : [6](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L6), [7](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L7), [8](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L8), [9](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L9), [10](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L10), [11](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L11), [4](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L4), [5](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L5)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

4:    import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5:    import "@openzeppelin/contracts/token/ERC721/ERC721.sol";

6:    import "./OwnableApprovableERC721.sol";

```


*GitHub* : [6](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L6), [5](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L5), [4](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L4)

```solidity
File: contracts/OwnableApprovableERC721.sol

4:    import "@openzeppelin/contracts/utils/Context.sol";

5:    import "@openzeppelin/contracts/token/ERC721/ERC721.sol";

```


*GitHub* : [4](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L4), [5](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L5)

### [N-33]<a name="n-33"></a> Imports could be organized more systematically

The contract's interface should be imported first, followed by each of the interfaces it uses, followed by all other files. The examples below do not follow this layout.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

6:   import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

```


*GitHub* : [6](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L6-L6)

### [N-34]<a name="n-34"></a> Large or complicated code bases should implement invariant tests

Large code bases, or code with lots of inline-assembly, complicated math, or complicated interactions between multiple contracts, should implement [invariant fuzzing tests](https://medium.com/coinmonks/smart-contract-fuzzing-d9b88e0b0a05). Invariant fuzzers such as Echidna require the test writer to come up with invariants which should not be violated under any circumstances, and the fuzzer tests various inputs and function calls to ensure that the invariants always hold. Even code with 100% code coverage can still have bugs due to the order of the operations a user performs, and invariant fuzzers, with properly and extensively-written invariants, can close this testing gap significantly.

*There are 0 instance(s) of this issue:*

```solidity
File: Various Files
```


### [N-35]<a name="n-35"></a> Missing checks for empty parameters in the constructor



*There are 4 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit _managedNFTs
/// @audit _approvedHolders
/// @audit _distributableErc20s
456      constructor(
457          string memory _name,
458          string memory _symbol,
459          address[] memory _managedNFTs,
460          address[] memory _approvedHolders,
461          uint256 _minDistributionPeriod,
462          address[] memory _distributableErc20s
463:     ) ERC20(_name, _symbol) Ownable() {

```


*GitHub* : [456](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L462-L462), [456](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L460-L460), [456](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L459-L459)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit accountName
62       constructor(
63           string memory accountName
64       )
65           ERC721(
66               string.concat(
67                   "althea://liquid-infrastructure-account/",
68                   accountName
69               ),
70               string.concat("LIA:", accountName)
71           )
72:      {

```


*GitHub* : [62](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L63-L63)

### [N-36]<a name="n-36"></a> Missing checks for uint state variable assignments

Consider whether reasonable bounds checks for variables would be useful

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit 0(_minDistributionPeriod)
471:         MinDistributionPeriod = _minDistributionPeriod;

```


*GitHub* : [471](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L461-L461)

### [N-37]<a name="n-37"></a> Missing checks for uint state variable constructor assignments

Consider whether reasonable bounds checks for variables would be useful

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit _minDistributionPeriod
456      constructor(
457          string memory _name,
458          string memory _symbol,
459          address[] memory _managedNFTs,
460          address[] memory _approvedHolders,
461          uint256 _minDistributionPeriod,
462          address[] memory _distributableErc20s
463:     ) ERC20(_name, _symbol) Ownable() {

```


*GitHub* : [456](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L461-L461)

### [N-38]<a name="n-38"></a> Missing event for critical parameter change

Events help non-contract tools to track changes

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit distributableERC20s:  setDistributableERC20s()
441      function setDistributableERC20s(
442          address[] memory _distributableERC20s
443:     ) public onlyOwner {

```


*GitHub* : [441](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L441-L443)

### [N-39]<a name="n-39"></a> Mixed usage of `int`/`uint` with `int256`/`uint256`

`int256`/`uint256` are the preferred type names (they're what are used for function signatures), so they should be used consistently

*There are 8 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

171:             for (uint i = 0; i < holders.length; i++) {

213:         uint i;

220:                 for (uint j = 0; j < distributableERC20s.length; j++) {

271:         for (uint i = 0; i < distributableERC20s.length; i++) {

421:         for (uint i = 0; i < ManagedNFTs.length; i++) {

467:         for (uint i = 0; i < _approvedHolders.length; i++) {

```


*GitHub* : [171](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L171-L171), [421](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L421-L421), [467](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L467-L467), [213](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L213-L213), [271](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L271-L271), [220](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L220-L220)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

120:         for (uint i = 0; i < newErc20s.length; i++) {

175:         for (uint i = 0; i < erc20s.length; i++) {

```


*GitHub* : [120](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L120-L120), [175](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L175-L175)

### [N-40]<a name="n-40"></a> Named imports of parent contracts are missing



*There are 9 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit ERC20
30:      ERC20,

/// @audit ERC20Burnable
31:      ERC20Burnable,

/// @audit Ownable
32:      Ownable,

/// @audit ERC721Holder
33:      ERC721Holder,

/// @audit ReentrancyGuard
34:      ReentrancyGuard

```


*GitHub* : [30](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L30-L30), [31](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L31-L31), [32](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L32-L32), [33](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L33-L33), [34](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L34-L34)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit ERC721
/// @audit OwnableApprovableERC721
33:  contract LiquidInfrastructureNFT is ERC721, OwnableApprovableERC721 {

```


*GitHub* : [33](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L33-L33), [33](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L33-L33)

```solidity
File: contracts/OwnableApprovableERC721.sol

/// @audit Context
/// @audit ERC721
20:  abstract contract OwnableApprovableERC721 is Context, ERC721 {

```


*GitHub* : [20](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L20-L20), [20](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L20-L20)

### [N-41]<a name="n-41"></a> NatSpec: Contract declarations should have `@author` tags



*There are 1 instance(s) of this issue:*

```solidity
File: contracts/OwnableApprovableERC721.sol

20   abstract contract OwnableApprovableERC721 is Context, ERC721 {
21       /**
22        * @dev Throws if called by any account other than the owner.
23:       */

```


*GitHub* : [20](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L20-L23)

### [N-42]<a name="n-42"></a> NatSpec: Contract declarations should have `@title` tags



*There are 1 instance(s) of this issue:*

```solidity
File: contracts/OwnableApprovableERC721.sol

20   abstract contract OwnableApprovableERC721 is Context, ERC721 {
21       /**
22        * @dev Throws if called by any account other than the owner.
23:       */

```


*GitHub* : [20](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L20-L23)

### [N-43]<a name="n-43"></a> NatSpec: Event `@param` tag is missing



*There are 14 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit Missing '@param recipient'
/// @audit Missing '@param tokens'
/// @audit Missing '@param amounts'
33       ERC721Holder,
34       ReentrancyGuard
35   {
36       event Deployed();
37       event DistributionStarted();
38:      event Distribution(address recipient, address[] tokens, uint256[] amounts);

/// @audit Missing '@param source'
36       event Deployed();
37       event DistributionStarted();
38       event Distribution(address recipient, address[] tokens, uint256[] amounts);
39       event DistributionFinished();
40       event WithdrawalStarted();
41:      event Withdrawal(address source);

/// @audit Missing '@param nft'
38       event Distribution(address recipient, address[] tokens, uint256[] amounts);
39       event DistributionFinished();
40       event WithdrawalStarted();
41       event Withdrawal(address source);
42       event WithdrawalFinished();
43:      event AddManagedNFT(address nft);

/// @audit Missing '@param nft'
/// @audit Missing '@param to'
39       event DistributionFinished();
40       event WithdrawalStarted();
41       event Withdrawal(address source);
42       event WithdrawalFinished();
43       event AddManagedNFT(address nft);
44:      event ReleaseManagedNFT(address nft, address to);

```


*GitHub* : [36](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L36-L41), [38](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L38-L43), [39](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L39-L44), [39](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L39-L44), [33](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L33-L38), [33](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L33-L38), [33](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L33-L38)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit Missing '@param to'
/// @audit Missing '@param erc20s'
/// @audit Missing '@param amounts'
29    * to begin a recovery process which will finish after the transaction completes. Asynchronously the x/microtx module
30    * will ignore thresholds and transfer all of the Liquid Account's balances to this NFT, which may be withdrawn
31    * normally with withdrawBalances().
32    */
33   contract LiquidInfrastructureNFT is ERC721, OwnableApprovableERC721 {
34:      event SuccessfulWithdrawal(address to, address[] erc20s, uint256[] amounts);

/// @audit Missing '@param erc20s'
/// @audit Missing '@param amounts'
31    * normally with withdrawBalances().
32    */
33   contract LiquidInfrastructureNFT is ERC721, OwnableApprovableERC721 {
34       event SuccessfulWithdrawal(address to, address[] erc20s, uint256[] amounts);
35       event TryRecover();
36:      event SuccessfulRecovery(address[] erc20s, uint256[] amounts);

/// @audit Missing '@param newErc20s'
/// @audit Missing '@param newAmounts'
32    */
33   contract LiquidInfrastructureNFT is ERC721, OwnableApprovableERC721 {
34       event SuccessfulWithdrawal(address to, address[] erc20s, uint256[] amounts);
35       event TryRecover();
36       event SuccessfulRecovery(address[] erc20s, uint256[] amounts);
37:      event ThresholdsChanged(address[] newErc20s, uint256[] newAmounts);

```


*GitHub* : [31](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L31-L36), [31](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L31-L36), [32](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L32-L37), [32](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L32-L37), [29](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L29-L34), [29](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L29-L34), [29](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L29-L34)

### [N-44]<a name="n-44"></a> NatSpec: Event declarations should have `@dev` tags

`@dev` is used to explain extra details to developers

*There are 13 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

36:      event Deployed();

37:      event DistributionStarted();

38:      event Distribution(address recipient, address[] tokens, uint256[] amounts);

39:      event DistributionFinished();

40:      event WithdrawalStarted();

41:      event Withdrawal(address source);

42:      event WithdrawalFinished();

43:      event AddManagedNFT(address nft);

44:      event ReleaseManagedNFT(address nft, address to);

```


*GitHub* : [39](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L39-L39), [40](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L40-L40), [41](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L41-L41), [42](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L42-L42), [43](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L43-L43), [44](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L44-L44), [36](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L36-L36), [37](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L37-L37), [38](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L38-L38)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

34:      event SuccessfulWithdrawal(address to, address[] erc20s, uint256[] amounts);

35:      event TryRecover();

36:      event SuccessfulRecovery(address[] erc20s, uint256[] amounts);

37:      event ThresholdsChanged(address[] newErc20s, uint256[] newAmounts);

```


*GitHub* : [34](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L34-L34), [35](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L35-L35), [36](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L36-L36), [37](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L37-L37)

### [N-45]<a name="n-45"></a> NatSpec: Event declarations should have `@notice` tags

`@notice` is used to explain to end users what the event does, and the compiler interprets `///` or `/**` comments (but not `//` or `/*`) as this tag if one wasn't explicitly provided

*There are 13 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

36:      event Deployed();

37:      event DistributionStarted();

38:      event Distribution(address recipient, address[] tokens, uint256[] amounts);

39:      event DistributionFinished();

40:      event WithdrawalStarted();

41:      event Withdrawal(address source);

42:      event WithdrawalFinished();

43:      event AddManagedNFT(address nft);

44:      event ReleaseManagedNFT(address nft, address to);

```


*GitHub* : [37](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L37-L37), [38](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L38-L38), [41](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L41-L41), [42](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L42-L42), [43](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L43-L43), [44](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L44-L44), [40](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L40-L40), [39](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L39-L39), [36](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L36-L36)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

34:      event SuccessfulWithdrawal(address to, address[] erc20s, uint256[] amounts);

35:      event TryRecover();

36:      event SuccessfulRecovery(address[] erc20s, uint256[] amounts);

37:      event ThresholdsChanged(address[] newErc20s, uint256[] newAmounts);

```


*GitHub* : [37](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L37-L37), [34](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L34-L34), [35](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L35-L35), [36](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L36-L36)

### [N-46]<a name="n-46"></a> NatSpec: Event declarations should have descriptions



*There are 13 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

36:      event Deployed();

37:      event DistributionStarted();

38:      event Distribution(address recipient, address[] tokens, uint256[] amounts);

39:      event DistributionFinished();

40:      event WithdrawalStarted();

41:      event Withdrawal(address source);

42:      event WithdrawalFinished();

43:      event AddManagedNFT(address nft);

44:      event ReleaseManagedNFT(address nft, address to);

```


*GitHub* : [39](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L39-L39), [40](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L40-L40), [41](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L41-L41), [42](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L42-L42), [43](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L43-L43), [44](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L44-L44), [36](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L36-L36), [37](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L37-L37), [38](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L38-L38)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

34:      event SuccessfulWithdrawal(address to, address[] erc20s, uint256[] amounts);

35:      event TryRecover();

36:      event SuccessfulRecovery(address[] erc20s, uint256[] amounts);

37:      event ThresholdsChanged(address[] newErc20s, uint256[] newAmounts);

```


*GitHub* : [37](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L37-L37), [34](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L34-L34), [35](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L35-L35), [36](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L36-L36)

### [N-47]<a name="n-47"></a> NatSpec: Function `@param` tag is missing



*There are 8 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit Missing '@param account'
299       *
300       * @notice attempts to distribute to every holder in this block, which may exceed the block gas limit
301       * if this fails then first call distribute
302       */
303      function mintAndDistribute(
304:         address account,

/// @audit Missing '@param amount'
300       * @notice attempts to distribute to every holder in this block, which may exceed the block gas limit
301       * if this fails then first call distribute
302       */
303      function mintAndDistribute(
304          address account,
305:         uint256 amount

/// @audit Missing '@param account'
314       * Allows the contract owner to mint tokens for an address
315       *
316       * @notice minting may only occur when a distribution has happened within MinDistributionPeriod blocks
317       */
318      function mint(
319:         address account,

/// @audit Missing '@param amount'
315       *
316       * @notice minting may only occur when a distribution has happened within MinDistributionPeriod blocks
317       */
318      function mint(
319          address account,
320:         uint256 amount

/// @audit Missing '@param amount'
326       * Convenience function that allows a token holder to distribute when necessary and then burn their tokens right after
327       *
328       * @notice attempts to distribute to every holder in this block, which may exceed the block gas limit
329       * if this fails then first call distribute() enough times to finish a distribution and then call burn()
330       */
331:     function burnAndDistribute(uint256 amount) public {

/// @audit Missing '@param account'
/// @audit Missing '@param amount'
339       * Convenience function that allows an approved sender to distribute when necessary and then burn the approved tokens right after
340       *
341       * @notice attempts to distribute to every holder in this block, which may exceed the block gas limit
342       * if this fails then first call distribute() enough times to finish a distribution and then call burnFrom()
343       */
344:     function burnFromAndDistribute(address account, uint256 amount) public {

/// @audit Missing '@param _minDistributionPeriod'
456      constructor(
457          string memory _name,
458          string memory _symbol,
459          address[] memory _managedNFTs,
460          address[] memory _approvedHolders,
461:         uint256 _minDistributionPeriod,

```


*GitHub* : [315](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L315-L320), [326](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L326-L331), [339](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L339-L344), [339](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L339-L344), [456](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L456-L461), [299](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L299-L304), [300](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L300-L305), [314](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L314-L319)

### [N-48]<a name="n-48"></a> NatSpec: Function `@return` tag is missing



*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit Missing '@return  '
92       /**
93        * Indicates if the account is approved to hold the ERC20 token or not
94        * @param account the potential holder of the token
95        */
96:      function isApprovedHolder(address account) public view returns (bool) {

/// @audit Missing '@return  '
239      /**
240       * Determines if the minimum distribution period has elapsed, which is used for restricting
241       * minting and burning operations
242       */
243:     function _isPastMinDistributionPeriod() internal view returns (bool) {

```


*GitHub* : [239](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L239-L243), [92](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L92-L96)

### [N-49]<a name="n-49"></a> NatSpec: Function declarations should have `@dev` tags

`@dev` is used to explain to developers what the potential integration issues/foot-guns are

*There are 22 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

96:      function isApprovedHolder(address account) public view returns (bool) {

106:     function approveHolder(address holder) public onlyOwner {

116:     function disapproveHolder(address holder) public onlyOwner {

127      function _beforeTokenTransfer(
128          address from,
129          address to,
130          uint256 amount
131:     ) internal virtual override {

151:     function _beforeMintOrBurn() internal view {

164      function _afterTokenTransfer(
165          address from,
166          address to,
167          uint256 amount
168:     ) internal virtual override {

184:     function distributeToAllHolders() public {

198:     function distribute(uint256 numDistributions) public nonReentrant {

243:     function _isPastMinDistributionPeriod() internal view returns (bool) {

257:     function _beginDistribution() internal {

286:     function _endDistribution() internal {

303      function mintAndDistribute(
304          address account,
305          uint256 amount
306:     ) public onlyOwner {

318      function mint(
319          address account,
320          uint256 amount
321:     ) public onlyOwner nonReentrant {

331:     function burnAndDistribute(uint256 amount) public {

344:     function burnFromAndDistribute(address account, uint256 amount) public {

351:     function withdrawFromAllManagedNFTs() public {

359:     function withdrawFromManagedNFTs(uint256 numWithdrawals) public {

394:     function addManagedNFT(address nftContract) public onlyOwner {

413      function releaseManagedNFT(
414          address nftContract,
415          address to
416:     ) public onlyOwner nonReentrant {

441      function setDistributableERC20s(
442          address[] memory _distributableERC20s
443:     ) public onlyOwner {

456      constructor(
457          string memory _name,
458          string memory _symbol,
459          address[] memory _managedNFTs,
460          address[] memory _approvedHolders,
461          uint256 _minDistributionPeriod,
462          address[] memory _distributableErc20s
463:     ) ERC20(_name, _symbol) Ownable() {

```


*GitHub* : [96](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L96-L96), [151](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L151-L151), [164](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L164-L168), [184](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L184-L184), [198](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L198-L198), [243](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L243-L243), [257](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L257-L257), [286](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L286-L286), [303](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L303-L306), [318](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L318-L321), [331](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L331-L331), [344](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L344-L344), [351](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L351-L351), [359](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L359-L359), [394](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L394-L394), [413](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L413-L416), [441](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L441-L443), [456](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L456-L463), [116](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L116-L116), [106](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L106-L106), [127](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L127-L131)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

62       constructor(
63           string memory accountName
64       )
65           ERC721(
66               string.concat(
67                   "althea://liquid-infrastructure-account/",
68                   accountName
69               ),
70               string.concat("LIA:", accountName)
71           )
72:      {

```


*GitHub* : [62](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L62-L72)

### [N-50]<a name="n-50"></a> NatSpec: Function declarations should have `@notice` tags

`@notice` is used to explain to end users what the function does, and the compiler interprets `///` or `/**` comments (but not `//` or `/*`) as this tag if one wasn't explicitly provided

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

351:     function withdrawFromAllManagedNFTs() public {

```


*GitHub* : [351](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L351-L351)

### [N-51]<a name="n-51"></a> NatSpec: Function declarations should have descriptions



*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

351:     function withdrawFromAllManagedNFTs() public {

```


*GitHub* : [351](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L351-L351)

### [N-52]<a name="n-52"></a> NatSpec: Modifier `@param` tag is missing



*There are 2 instance(s) of this issue:*

```solidity
File: contracts/OwnableApprovableERC721.sol

/// @audit Missing '@param tokenId'
19    */
20   abstract contract OwnableApprovableERC721 is Context, ERC721 {
21       /**
22        * @dev Throws if called by any account other than the owner.
23        */
24:      modifier onlyOwner(uint256 tokenId) {

/// @audit Missing '@param tokenId'
30       }
31   
32       /**
33        * @dev Throws if called by any account other than the owner or someone approved by the owner
34        */
35:      modifier onlyOwnerOrApproved(uint256 tokenId) {

```


*GitHub* : [19](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L19-L24), [30](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L30-L35)

### [N-53]<a name="n-53"></a> NatSpec: Non-public state variable declarations should use `@dev` tags

i.e. `@dev` [tags](https://docs.soliditylang.org/en/latest/natspec-format.html#tags). Note that since they're non-public, `@notice` is not the right tag to use.

*There are 5 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

46:      address[] private distributableERC20s;

47:      uint256[] private erc20EntitlementPerUnit;

48:      address[] private holders;

```


*GitHub* : [48](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L48-L48), [47](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L47-L47), [46](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L46-L46)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

39:      address[] private thresholdErc20s;

40:      uint256[] private thresholdAmounts;

```


*GitHub* : [39](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L39-L39), [40](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L40-L40)

### [N-54]<a name="n-54"></a> NatSpec: State variable declarations should have descriptions

e.g. `@notice` [tags](https://docs.soliditylang.org/en/latest/natspec-format.html#tags)

*There are 5 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

46:      address[] private distributableERC20s;

47:      uint256[] private erc20EntitlementPerUnit;

48:      address[] private holders;

```


*GitHub* : [47](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L47-L47), [46](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L46-L46), [48](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L48-L48)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

39:      address[] private thresholdErc20s;

40:      uint256[] private thresholdAmounts;

```


*GitHub* : [40](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L40-L40), [39](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L39-L39)

### [N-55]<a name="n-55"></a> Setters should prevent re-setting of the same value

This especially problematic when the setter also emits the same value, which may be confusing to offline parsers

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit distributableERC20s:  setDistributableERC20s()
441      function setDistributableERC20s(
442          address[] memory _distributableERC20s
443      ) public onlyOwner {
444          distributableERC20s = _distributableERC20s;
445:     }

```


*GitHub* : [441](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L441-L445)

### [N-56]<a name="n-56"></a> Style guide: Contract does not follow the Solidity style guide's suggested layout ordering

The [style guide](https://docs.soliditylang.org/en/v0.8.16/style-guide.html#order-of-layout) says that, within a contract, the ordering should be 1) Type declarations, 2) State variables, 3) Events, 4) Modifiers, and 5) Functions, but the contract(s) below do not follow this ordering

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit event ReleaseManagedNFT came earlier
46:       address[] private distributableERC20s;

```


*GitHub* : [46](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L46)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit event ThresholdsChanged came earlier
39:       address[] private thresholdErc20s;

```


*GitHub* : [39](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L39)

### [N-57]<a name="n-57"></a> Style guide: Extraneous whitespace

See the [whitespace](https://docs.soliditylang.org/en/v0.8.16/style-guide.html#whitespace-in-expressions) section of the Solidity Style Guide

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

376:              (address[] memory withdrawERC20s, ) = withdrawFrom.getThresholds();

```


*GitHub* : [376](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L376)

### [N-58]<a name="n-58"></a> Style guide: Function ordering does not follow the Solidity style guide

According to the [Solidity style guide](https://docs.soliditylang.org/en/v0.8.17/style-guide.html#order-of-functions), functions should be laid out in the following order :`constructor()`, `receive()`, `fallback()`, `external`, `public`, `internal`, `private`, but the cases below do not follow this pattern

*There are 4 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit _afterTokenTransfer() came earlier
184       function distributeToAllHolders() public {
185:          uint256 num = holders.length;

/// @audit _endDistribution() came earlier
303       function mintAndDistribute(
304           address account,
305           uint256 amount
306:      ) public onlyOwner {

/// @audit setDistributableERC20s() came earlier
456       constructor(
457           string memory _name,
458           string memory _symbol,
459           address[] memory _managedNFTs,
460           address[] memory _approvedHolders,
461           uint256 _minDistributionPeriod,
462           address[] memory _distributableErc20s
463:      ) ERC20(_name, _symbol) Ownable() {

```


*GitHub* : [456](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L456-L463), [303](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L303-L306), [184](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L184-L185)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit _withdrawBalancesTo() came earlier
203:      function recoverAccount() public virtual onlyOwner(AccountId) {

```


*GitHub* : [203](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L203)

### [N-59]<a name="n-59"></a> Style guide: Initialisms should be capitalized

According to the Solidity [style guide](https://docs.soliditylang.org/en/latest/style-guide.html#naming-styles) initialisms such as "NFT" should be capitalized

*There are 4 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

462:         address[] memory _distributableErc20s

```


*GitHub* : [462](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L462-L462)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

37:      event ThresholdsChanged(address[] newErc20s, uint256[] newAmounts);

39:      address[] private thresholdErc20s;

109:         address[] calldata newErc20s,

```


*GitHub* : [37](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L37-L37), [39](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L39-L39), [109](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L109-L109)

### [N-60]<a name="n-60"></a> Style guide: Lines are too long

Usually lines in source code are limited to [80](https://softwareengineering.stackexchange.com/questions/148677/why-is-80-characters-the-standard-limit-for-code-width) characters. Today's screens are much larger so it's reasonable to stretch this in some cases. The solidity style guide recommends a maximumum line length of [120 characters](https://docs.soliditylang.org/en/v0.8.17/style-guide.html#maximum-line-length), so the lines below should be split when they reach that length.

*There are 26 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

19:    * A LiquidInfrastructureNFT typically represents some form of infrastructure involved in an Althea pay-per-forward network

20:    * which frequently receives payments from peers on the network for performing an automated service (e.g. providing internet).

21:    * This LiquidInfrastructureERC20 acts as a convenient aggregation layer to enable dead-simple investment in real-world assets

22:    * with automatic revenue accrual. Simply by holding this ERC20 owners are entitled to revenue from the network represented by the token.

24:    * Revenue is gathered from managed LiquidInfrastructureNFTs by the protocol and distributed to token holders on a semi-regular basis,

27:    * Minting and burning of this ERC20 is restricted if the minimum distribution period has elapsed, and it is reenabled once a new distribution is complete.

57:        * @notice This collection holds the managed LiquidInfrastructureNFTs which periodically generate revenue and deliver

101:       * Adds `holder` to the list of approved token holders. This is necessary before `holder` may receive any of the underlying ERC20.

112:       * Marks `holder` as NOT approved to hold the token, preventing them from receiving any more of the underlying ERC20.

149:       * Implements an additional lock on minting and burning, ensuring that supply changes happen after any potential distributions

182:       * Performs a distribution to all of the current holders, which may trigger out of gas errors if there are too many holders

192:       * Begins or continues a distribution, preventing transfers, mints, and burns of the token until all rewards have been paid out

326:       * Convenience function that allows a token holder to distribute when necessary and then burn their tokens right after

339:       * Convenience function that allows an approved sender to distribute when necessary and then burn the approved tokens right after

356:       * Performs withdrawals from the ManagedNFTs collection, depositing all token balances into the custody of this contract

```


*GitHub* : [192](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L192), [19](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L19), [20](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L20), [21](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L21), [22](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L22), [24](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L24), [27](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L27), [57](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L57), [101](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L101), [112](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L112), [149](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L149), [182](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L182), [326](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L326), [339](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L339), [356](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L356)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

12:    * @dev An NFT contract used to control a Liquid Infrastructure Account - a Cosmos Bank module account intrinsically connected to the EVM

13:    * through Althea's x/microtx module. On chains which are not Althea-L1 this is a standalone ERC721 which should receive revenue periodically,

16:    * A Liquid Infrastructure Account typically represents some form of infrastructure involved in an Althea pay-per-forward network

17:    * which frequently receives payments from peers on the network for performing an automated service (e.g. providing internet).

18:    * Each instance of this LiquidInfrastructureNFT contract represents one x/bank module account, the address of which is a part of

21:    * As the x/microtx module is used to conduct microtransactions (the payment layer for Althea networks), receiving accounts

22:    * will accrue Cosmos Coins and likely spend these same tokens to pay their upstream costs. If any such account is a Liquid

23:    * account (see x/microtx documentation), the x/microtx module will query this LiquidInfrastructureNFT's BalanceThresholds

198:       * the entire transaction is resolved. It will not be possible to recoverAccount() and immediately withdrawBalances()

```


*GitHub* : [17](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L17), [18](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L18), [21](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L21), [22](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L22), [23](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L23), [198](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L198), [16](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L16), [13](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L13), [12](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L12)

```solidity
File: contracts/OwnableApprovableERC721.sol

11:    * @dev For contracts with manually enumerated tokens (e.g. RockId = 1, PaperId = 2, ScissorsId = 3) use the modifiers like so:

16:    *      // Either the owner, a sender approved for all the tokens the owner of PaperId, or a sender approved for specifically PaperId gets to call this

```


*GitHub* : [11](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L11), [16](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L16)

### [N-61]<a name="n-61"></a> Style guide: Non-`external`/`public` variable names should begin with an underscore

According to the Solidity Style Guide, non-`external`/`public` variable names should begin with an [underscore](https://docs.soliditylang.org/en/latest/style-guide.html#underscore-prefix-for-non-external-functions-and-variables)

*There are 7 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

46:      address[] private distributableERC20s;

47:      uint256[] private erc20EntitlementPerUnit;

48:      address[] private holders;

85:      uint256 internal nextDistributionRecipient;

90:      uint256 private nextWithdrawal;

```


*GitHub* : [85](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L85-L85), [90](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L90-L90), [48](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L48-L48), [47](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L47-L47), [46](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L46-L46)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

39:      address[] private thresholdErc20s;

40:      uint256[] private thresholdAmounts;

```


*GitHub* : [40](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L40-L40), [39](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L39-L39)

### [N-62]<a name="n-62"></a> Style guide: Variable names for `constant`s are improperly named

According to the [Style guide](https://docs.soliditylang.org/en/latest/style-guide.html#constants), for `constant` variable names, each word should use all capital letters, with underscores separating each word (CONSTANT_CASE)

*There are 3 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

54:      uint256 public constant Version = 1;

```


*GitHub* : [54](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L54-L54)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

46:      uint256 public constant Version = 1;

53:      uint256 public constant AccountId = 1;

```


*GitHub* : [46](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L46-L46), [53](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L53-L53)

### [N-63]<a name="n-63"></a> The `nonReentrant` `modifier` should occur before all other modifiers

This is a best-practice to protect against reentrancy in other modifiers

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

321:      ) public onlyOwner nonReentrant {

416:      ) public onlyOwner nonReentrant {

```


*GitHub* : [416](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L416), [321](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L321)

### [N-64]<a name="n-64"></a> The `nonReentrant` `modifier` should occur before all other modifiers

This is a best-practice to protect against reentrancy in other modifiers

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

318      function mint(
319          address account,
320          uint256 amount
321:     ) public onlyOwner nonReentrant {

413      function releaseManagedNFT(
414          address nftContract,
415          address to
416:     ) public onlyOwner nonReentrant {

```


*GitHub* : [413](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L413-L416), [318](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L318-L321)

### [N-65]<a name="n-65"></a> Typos



*There are 3 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureNFT.sol

/// @audit Occassionally
28:    * Occassionally devices and wallets can be lost, in which case the owner of this contract can call recoverAccount()

/// @audit addressses
100:       * The ERC20s specified here have EVM addressses, querying the x/erc20 module will reveal their

```


*GitHub* : [28](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L28), [100](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L100)

```solidity
File: contracts/OwnableApprovableERC721.sol

/// @audit onwerOf
9:     * onwerOf, getApproved, and isApprovedForAll functions

```


*GitHub* : [9](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L9)

### [N-66]<a name="n-66"></a> Unused `event` definition

Note that there may be cases where an event superficially appears to be used, but this is only because there are multiple definitions of the event in different files. In such cases, the event definition should be moved into a separate file. The instances below are the unused definitions.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureNFT.sol

36:      event SuccessfulRecovery(address[] erc20s, uint256[] amounts);

```


*GitHub* : [36](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L36-L36)

### [N-67]<a name="n-67"></a> Unused `public` contract variable

Note that there may be cases where a variable superficially appears to be used, but this is only because there are multiple definitions of the variable in different files. In such cases, the variable definition should be moved into a separate file. The instances below are the unused variables.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

54:      uint256 public constant Version = 1;

```


*GitHub* : [54](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L54-L54)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

46:      uint256 public constant Version = 1;

```


*GitHub* : [46](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L46-L46)

### [N-68]<a name="n-68"></a> Unused function parameter

Comment out the variable name to suppress compiler warnings

*There are 3 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

/// @audit amount
127      function _beforeTokenTransfer(
128          address from,
129          address to,
130          uint256 amount
131:     ) internal virtual override {

/// @audit to
/// @audit amount
164      function _afterTokenTransfer(
165          address from,
166          address to,
167          uint256 amount
168:     ) internal virtual override {

```


*GitHub* : [164](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L164-L168), [164](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L164-L168), [127](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L127-L131)

### [N-69]<a name="n-69"></a> Use of `override` is unnecessary

Starting with Solidity version [0.8.8](https://docs.soliditylang.org/en/v0.8.20/contracts.html#function-overriding), using the `override` keyword when the function solely overrides an interface function, and the function doesn't exist in multiple base contracts, is unnecessary.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

127      function _beforeTokenTransfer(
128          address from,
129          address to,
130          uint256 amount
131:     ) internal virtual override {

164      function _afterTokenTransfer(
165          address from,
166          address to,
167          uint256 amount
168:     ) internal virtual override {

```


*GitHub* : [127](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L127-L131), [164](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L164-L168)

### [N-70]<a name="n-70"></a> Use the latest solidity (prior to 0.8.20 if on L2s) for deployment

```
When deploying contracts, you should use the latest released version of Solidity. Apart from exceptional cases, only the latest version receives security fixes.
```
https://docs.soliditylang.org/en/v0.8.20/

Since deployed contracts should not use floating pragmas, I've flagged all instances where a version prior to 0.8.19 is allowed by the version pragma

*There are 3 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

2:   pragma solidity 0.8.12; // Force solidity compliance

```


*GitHub* : [2](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L2-L2)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

2:   pragma solidity 0.8.12; // Force solidity compliance

```


*GitHub* : [2](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L2-L2)

```solidity
File: contracts/OwnableApprovableERC721.sol

2:   pragma solidity 0.8.12; // Force solidity compliance

```


*GitHub* : [2](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/OwnableApprovableERC721.sol#L2-L2)

### [N-71]<a name="n-71"></a> Variables need not be initialized to zero

The default value for variables is zero, so initializing them to zero is superfluous.

*There are 7 instance(s) of this issue:*

```solidity
File: contracts/LiquidInfrastructureERC20.sol

171:             for (uint i = 0; i < holders.length; i++) {

220:                 for (uint j = 0; j < distributableERC20s.length; j++) {

271:         for (uint i = 0; i < distributableERC20s.length; i++) {

421:         for (uint i = 0; i < ManagedNFTs.length; i++) {

467:         for (uint i = 0; i < _approvedHolders.length; i++) {

```


*GitHub* : [271](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L271-L271), [421](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L421-L421), [467](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L467-L467), [220](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L220-L220), [171](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureERC20.sol#L171-L171)

```solidity
File: contracts/LiquidInfrastructureNFT.sol

120:         for (uint i = 0; i < newErc20s.length; i++) {

175:         for (uint i = 0; i < erc20s.length; i++) {

```


*GitHub* : [175](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L175-L175), [120](https://github.com/code-423n4/2024-02-althea-liquid-infrastructure/blob/2b26c04f0448505635210416bef9d3ce96391b16/liquid-infrastructure/contracts/LiquidInfrastructureNFT.sol#L120-L120)

### [N-72]<a name="n-72"></a> Vulnerable versions of packages are being used

This project's specific package versions are vulnerable to the specific CVEs listed below. While the CVEs may involve code not in use by your project, consider switching to more recent versions of these packages that don't have these vulnerabilities, to avoid reviewers wasting time trying to determine whether there is vulnerable code from these packages in use.

*There are 0 instance(s) of this issue:*

```solidity
File: Various Files/// @audit Vulnerabilities:
///          
```



- [CVE-2021-41264](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-41264) - **CRITICAL** -  (`@openzeppelin/contracts >=4.1.0 <4.3.2`): OpenZeppelin Contracts is a library for smart contract development. In affected versions upgradeable contracts using `UUPSUpgradeable` may be vulnerable to an attack affecting uninitialized implementation contracts. A fix is included in version 4.3.2 of `@openzeppelin/contracts` and `@openzeppelin/contracts-upgradeable`. For users unable to upgrade; initialize implementation contracts using `UUPSUpgradeable` by invoking the initializer function (usually called `initialize`). An example is provided [in the forum](https://forum.openzeppelin.com/t/security-advisory-initialize-uups-implementation-contracts/15301).
- [CVE-2022-31170](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-31170) - **HIGH** -  (`@openzeppelin/contracts >=4.0.0 <4.7.1`): OpenZeppelin Contracts is a library for smart contract development. Versions 4.0.0 until 4.7.1 are vulnerable to ERC165Checker reverting instead of returning `false`. `ERC165Checker.supportsInterface` is designed to always successfully return a boolean, and under no circumstance revert. However, an incorrect assumption about Solidity 0.8's `abi.decode` allows some cases to revert, given a target contract that doesn't implement EIP-165 as expected, specifically if it returns a value other than 0 or 1. The contracts that may be affected are those that use `ERC165Checker` to check for support for an interface and then handle the lack of support in a way other than reverting. The issue was patched in version 4.7.1.
- [CVE-2022-31172](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-31172) - **HIGH** -  (`@openzeppelin/contracts >=4.1.0 <4.7.1`): OpenZeppelin Contracts is a library for smart contract development. Versions 4.1.0 until 4.7.1 are vulnerable to the SignatureChecker reverting. `SignatureChecker.isValidSignatureNow` is not expected to revert. However, an incorrect assumption about Solidity 0.8's `abi.decode` allows some cases to revert, given a target contract that doesn't implement EIP-1271 as expected. The contracts that may be affected are those that use `SignatureChecker` to check the validity of a signature and handle invalid signatures in a way other than reverting. The issue was patched in version 4.7.1.
- [CVE-2022-31198](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-31198) - **HIGH** -  (`@openzeppelin/contracts >=4.3.0 <4.7.2`): OpenZeppelin Contracts is a library for secure smart contract development. This issue concerns instances of Governor that use the module `GovernorVotesQuorumFraction`, a mechanism that determines quorum requirements as a percentage of the voting token's total supply. In affected instances, when a proposal is passed to lower the quorum requirements, past proposals may become executable if they had been defeated only due to lack of quorum, and the number of votes it received meets the new quorum requirement. Analysis of instances on chain found only one proposal that met this condition, and we are actively monitoring for new occurrences of this particular issue. This issue has been patched in v4.7.2. Users are advised to upgrade. Users unable to upgrade should consider avoiding lowering quorum requirements if a past proposal was defeated for lack of quorum.
- [CVE-2022-35915](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-35915) - **MEDIUM** -  (`@openzeppelin/contracts >= 2.0.0 <4.7.2`): OpenZeppelin Contracts is a library for secure smart contract development. The target contract of an EIP-165 `supportsInterface` query can cause unbounded gas consumption by returning a lot of data, while it is generally assumed that this operation has a bounded cost. The issue has been fixed in v4.7.2. Users are advised to upgrade. There are no known workarounds for this issue.
- [CVE-2022-35961](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-35961) - **MEDIUM** -  (`@openzeppelin/contracts >=4.1.0 <4.7.3`): OpenZeppelin Contracts is a library for secure smart contract development. The functions `ECDSA.recover` and `ECDSA.tryRecover` are vulnerable to a kind of signature malleability due to accepting EIP-2098 compact signatures in addition to the traditional 65 byte signature format. This is only an issue for the functions that take a single `bytes` argument, and not the functions that take `r, v, s` or `r, vs` as separate arguments. The potentially affected contracts are those that implement signature reuse or replay protection by marking the signature itself as used rather than the signed message or a nonce included in it. A user may take a signature that has already been submitted, submit it again in a different form, and bypass this protection. The issue has been patched in 4.7.3.
- [CVE-2022-39384](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-39384) - **MEDIUM** -  (`@openzeppelin/contracts >=3.2.0 <4.4.1`): OpenZeppelin Contracts is a library for secure smart contract development. Before version 4.4.1 but after 3.2.0, initializer functions that are invoked separate from contract creation (the most prominent example being minimal proxies) may be reentered if they make an untrusted non-view external call. Once an initializer has finished running it can never be re-executed. However, an exception put in place to support multiple inheritance made reentrancy possible in the scenario described above, breaking the expectation that there is a single execution. Note that upgradeable proxies are commonly initialized together with contract creation, where reentrancy is not feasible, so the impact of this issue is believed to be minor. This issue has been patched, please upgrade to version 4.4.1. As a workaround, avoid untrusted external calls during initialization.
- [CVE-2023-30541](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30541) - **MEDIUM** -  (`@openzeppelin/contracts >=3.2.0 <4.8.3`): OpenZeppelin Contracts is a library for secure smart contract development. A function in the implementation contract may be inaccessible if its selector clashes with one of the proxy's own selectors. Specifically, if the clashing function has a different signature with incompatible ABI encoding, the proxy could revert while attempting to decode the arguments from calldata. The probability of an accidental clash is negligible, but one could be caused deliberately and could cause a reduction in availability. The issue has been fixed in version 4.8.3. As a workaround if a function appears to be inaccessible for this reason, it may be possible to craft the calldata such that ABI decoding does not fail at the proxy and the function is properly proxied through.
- [CVE-2023-30542](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30542) - **HIGH** -  (`@openzeppelin/contracts >=4.3.0 <4.8.3`): OpenZeppelin Contracts is a library for secure smart contract development. The proposal creation entrypoint (`propose`) in `GovernorCompatibilityBravo` allows the creation of proposals with a `signatures` array shorter than the `calldatas` array. This causes the additional elements of the latter to be ignored, and if the proposal succeeds the corresponding actions would eventually execute without any calldata. The `ProposalCreated` event correctly represents what will eventually execute, but the proposal parameters as queried through `getActions` appear to respect the original intended calldata. This issue has been patched in 4.8.3. As a workaround, ensure that all proposals that pass through governance have equal length `signatures` and `calldatas` parameters.
- [CVE-2023-34234](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-34234) - **MEDIUM** -  (`@openzeppelin/contracts >=4.3.0 <4.9.1`):  OpenZeppelin Contracts is a library for smart contract development. By frontrunning the creation of a proposal, an attacker can become the proposer and gain the ability to cancel it. The attacker can do this repeatedly to try to prevent a proposal from being proposed at all. This impacts the `Governor` contract in v4.9.0 only, and the `GovernorCompatibilityBravo` contract since v4.3.0. This problem has been patched in 4.9.1 by introducing opt-in frontrunning protection. Users are advised to upgrade. Users unable to upgrade may submit the proposal creation transaction to an endpoint with frontrunning protection as a workaround.
- [CVE-2023-40014](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-40014) - **MEDIUM** -  (`@openzeppelin/contracts >=4.0.0 <4.9.3`): OpenZeppelin Contracts is a library for secure smart contract development. Starting in version 4.0.0 and prior to version 4.9.3, contracts using `ERC2771Context` along with a custom trusted forwarder may see `_msgSender` return `address(0)` in calls that originate from the forwarder with calldata shorter than 20 bytes. This combination of circumstances does not appear to be common, in particular it is not the case for `MinimalForwarder` from OpenZeppelin Contracts, or any deployed forwarder the team is aware of, given that the signer address is appended to all calls that originate from these forwarders. The problem has been patched in v4.9.3.

```

```


## Rubric
See [this](https://illilli000.github.io/races/2023-07-lens/scorer.html) link for how to use this rubric:
```json
{"salt":"94ce71","hashes":["d064612004","d1c500b9e7","70d6925400","b7d0997674","5638093e7b","e74c5f8ead","21d8bc80d2","63995ee6ae","4fd645040c","a2e4716854","e799688000","420b46206d","e5b82ab7f9","f32a39ddcf","2bf5bbeb89","3461b90ad0","a89bb6e50c","6e7c3f1997","f90db08b51","77153e15b9","509ccad160","2bf5bbeb89","3461b90ad0","a89bb6e50c","6e7c3f1997","f90db08b51","77153e15b9","509ccad160","806d1aee7a","dff7b70a67","e3638aa336","db9fd0ad5e","d58a47fac0","995c1ede48","55d227b712","5342c058aa","4c125e7d19","ca720d155f","6ddd36d4eb","8adf5af1d5","5ab936268c","c9e0d675e8","de26e243a6","359a8796da","2c7a63caa4","02bcdadd88","cc58721100","1c94e664bf","309c8f1745","de26e243a6","359a8796da","2c7a63caa4","02bcdadd88","cc58721100","1c94e664bf","309c8f1745","a7a10f741e","a24d747d75","41eddfe6bd","74ed184c19","7e753697d8","a42c7f0d70","d8d1af645a","a7a10f741e","a24d747d75","41eddfe6bd","74ed184c19","7e753697d8","a42c7f0d70","d8d1af645a","6f037a9242","b797b9cca2","c349edfe0a","e52e1c2d59","6fc979c0be","9cd83b0164","b9b055547b","247f4577aa","9f8f08d2b6","368a23f9f0","944c328227","213650a1c4","1d6fc676bc","c348a90e9f","9fc75873e1","4328164e24","f9091d371b","5690389c96","3239409b35","18647f7843","a15e30bd7d","0f29a159d0","c507e13daa","79a9dbd7fe","0a7c21d06d","227f6a9c9a","23741a16f1","d3922c9b17","07b7afa75b","0057a83cb9","266a7f73f4","9795c6af3b","2f40a7a19c","4c51e663ba","097f509be2","61ff091864","721efb527d","23a93643fa","b2e271894c","f0025aac07","1a4a48323a","b9de95f695","d52c314e7c","bbded6d585","e1cd64add5","87c03fbfd5","443e6e22c2","75e3c40992","2f604f10c8","34cff2f11a","17893a902a","9d22f40587","0be99a92a6","773850fc7b","d63fff4265","f5efe0dcd0","34cff2f11a","17893a902a","9d22f40587","0be99a92a6","773850fc7b","d63fff4265","f5efe0dcd0","67fa9adece","dd1ab5684c","f9c460b705","9e33557468","300347c8de","3dde296838","99f5f12eb0","f8696ffb74","4da2a71c82","3abaa4e1cb","200af0af4f","3f6abd5268","c3c9b2a84c","d66a62412c","f53a396c90","326e622906","a88b58e410","e367065fc4","adca3f1313","1b64dd1f66","c045a8390b","4993fd3579","fdc2f8f99d","f999a67e01","bd15d69db2","ff72b113ec","a7b1168e15","a45b722a4f","f53a396c90","326e622906","a88b58e410","e367065fc4","adca3f1313","1b64dd1f66","c045a8390b","cd234a35ad","88dd60ee92","077987a9ec","9de55247b2","581fc3b583","4f494e3601","ce9a87e271","62962c0692","62be764b54","647b6c84d5","42ea3cd6ba","0db14ba111","cbe8c8aa56","aae243dcae","49bd838f75","91b80e6249","040861e38d","a8ab7e1878","cf7bc74f44","451456252a","7c1e7d54d9","317139d58d","a10ff0365f","2575758846","ccc41610bf","7bab5b3d8f","e3de833248","a6c4957e7f","611b437ab8","80a2c17a8b","946a87427b","768129eded","2506b38ef5","935ca101cb","27d29fabe0","5d4b651821","4c5c49c431","9c674c486d","248a383052","c963d3f2d4","eeb5ad4419","ef2da3cb17","d14d7cb56c","5d3954b5a0","685e7abbd2","9a9e55ac96","0fa24a070e","47ba613169","c4b52ecc7b","0c4c054718","79e6d8c3f6","cee2682e03","df53184d56","d6da5b8d44","df5fc6b7b0","0ecdbccfe0","49bd838f75","91b80e6249","040861e38d","a8ab7e1878","cf7bc74f44","451456252a","7c1e7d54d9","839732a57d","9f74c49d14","70bdf7ea3f","1451c5f9e2","8db53b9b1d","d7ca16075b","f5d9b7541b","bf949f2c79","acbbebba09","5192c9ef59","5b1356c6cc","139a798d00","c2f8517ac7","275f4fe916","eed630289f","3af6c40fc5","5267cba93b","abadbddfe6","b41aa1b727","a2d05be01a","8349f370f8","1a834782f4","42216adaa9","77228f32a8","e2138fe948","edd4d325f0","73e3d6213e","2ec9496d28","8189258459","bb9f0178cf","1678a5e56b","715410f01f","2f7e0c65bb","3e322b3a08","4227228a30","b9bb14944f","2d6eacb715","0418fb555f","1f34e4b0db","aafcf4cb03","06033ce65f","3c68c03d22","1beb343e62","67ed4f5b63","fd11ff9622","55de7754e0","e64ad277ab","293fa15963","cc6750b495","bf949f2c79","acbbebba09","5192c9ef59","5b1356c6cc","139a798d00","c2f8517ac7","275f4fe916","ae6739945d","26a1a24b3f","c8a41eb65a","9fc1219b92","1037569b20","56548f2d35","d3abaa8db1","b691d3063f","e4ded938b8","c6857458b5","7a124718da","ae74064e43","b35aa7c89e","9be692069b","7a315ebcde","4c4b0a2242","4203d03aa8","8e6c9b2c5a","3f3b9f4cb5","e6af51a4e5","07e945e7c9","46ef6a0400","43ad4c545a","3494c1ee52","68f16296b3","e521ecbfcb","6866095b4e","d5c317a7ee","e5d1731bc6","de7c62a1bc","0916ce4378","43ba981d9f","5f5625d496","4e96ee7a65","3875ef3aad","b1d42a78bd","fc38d2140f","df7591954a","0dcd0bc32e","2268a2b0ca","290997bda7","59227647e4","cbe814c592","a52e10c089","955dd506d5","b8177c3ee9","bea89e4abc","338527befb","957227389c","2e99740aac","7266f9fd0f","5f9c430764","12a18610d6","20c09d18d8","4c3ada7b27","17fd5fd850","f6c9a54c05","358867a323","6cd81f3004","83efa45440","6b5c110ede","4b14cdb7aa","1f4e469e57","6c75529eed","2876bddc90","094d9cd77b","a4ee25bc69","504a9a566e","bec1990a42","b8d4a90516","b8767ff9ba","aac0f7e6ea","a7d7166f97","3eb4e7461e","c00fe28957","862bbacec2","92b0175c8b","73b7f31775","0c48c6978c","b3c3711590","290b05deeb","faa595b773","27e4b6c61f","9c31eecef9","9acca3ceb2","beaefe3296","c8f4b52143","984f6fc71b","0d222ccee7","abcdadcc6e","4f841a6c19","7a315ebcde","4c4b0a2242","4203d03aa8","8e6c9b2c5a","3f3b9f4cb5","e6af51a4e5","07e945e7c9","7a315ebcde","4c4b0a2242","4203d03aa8","8e6c9b2c5a","3f3b9f4cb5","e6af51a4e5","07e945e7c9","7498858869","7010d897e9","c838ef473e","3bffc1f7e1","f87f2c8d54","e3d80dbd2c","00d08f10b1","75c446a619","f3fce02cf7","4eab6ea056","96eb989c54","ed743d09e4","4ba0c923ce","332774d382","c056b28001","d5cc8d00b6","b9ae6d2b49","d43ca22573","f10223e427","bc3586ca9c","59a89caec2","04f1493dcb","5b9cf49da1","aef3e587cd","9bebcfa127","76ba8cff32","e68d101cd8","7442a2e85e","4b09a8ff60","6de3af0030","3eb773dfa6","fc04e85f4c","0ac4856011","b3229993f1","d267039a22","f07f537022","87cbea0522","ecbc8f291a","03b093d486","c865d1fc8f","03fcfdf6f2","39a96c644c","5ab9af805f","99e9e9b49d","bf79c1eba3","ae799c064a","34136f4a4c","7484c0f46f","3e9fc5fc03","362c649b72","8ab359f930","9cf4677eae","40918bae24","622d0f4175","d26fb9fc0d","d40695b35a","362c649b72","8ab359f930","9cf4677eae","40918bae24","622d0f4175","d26fb9fc0d","d40695b35a","c2cd873410","e43e39dde7","a37035b855","d199246513","40350d9651","e283f864fb","2e5d02c713","b7c2278005","4dfe3fb0bb","cf88b7d3bc","0a9d395cc0","bada134ec7","c3fb1dca87","f03eb2c54f","a70b4d406b","2e1f22fefa","24f6c6aade","e2e3cf90cd","bc2fe778b1","c5879080ca","c9e2401d1e","6a75cc703a","1375c8a116","9707132dca","2618ff2e33","f1df98fdb2","cb881e2fad","c3acb0ebfc","6a75cc703a","1375c8a116","9707132dca","2618ff2e33","f1df98fdb2","cb881e2fad","c3acb0ebfc","34c2fcef57","3ca6853433","f0e07effe5","27ccfad839","0aca8ff22e","3bafc3d662","b2013d0245","05112f29ba","81a7bbf6bc","7ebabef07a","308e4beebc","e59120a58b","ecbd602d4a","725724fcfc","a64f2289a1","f4718c3aea","e0effbc085","0bfe826c8e","d9e54de32a","815a2cc820","8ca9e74d3f","70f77d066b","8ac72e81fa","73aa414e69","38afdb268b","b15bb9967c","d5b32b77df","e7f8e361dc","aaf9eaa4a6","ca8abe60ea","dd25ab6be6","8b998cd0d8","ce39f03ee6","5d54f51c55","a39f6af914","52585c7f3f","732a1c16ee","2cbdd9a6f9","4aff1a5477","802c147f6b","265e654af1","85d1efefc5","ed026c2ea3","9ec76cb081","b569636954","50b73b9a13","4f52566fd0","6f18e92ac7","319498b573","8501079af0","f152cabe21","141e2f1931","770963b20c","4adeb20c0b","6427302036","cd01c25882","9d90f6d0f0","819f38af53","ccad4cff84","fb390d4a12","1494fb0e8b","d411afb2d7","9806b76110","34c2fcef57","3ca6853433","f0e07effe5","27ccfad839","0aca8ff22e","3bafc3d662","b2013d0245","8b47b20e4d","3b0269fbca","00a1112205","875af6daf7","e1ca8bf84f","864a8093f1","a925171c44","6ceee560cf","28634760d7","ed93d6eace","4148b42cdf","5810a39d28","fbe9a6f475","995516dc4e","7728b999ea","e957889a57","0380f2ba7c","2b5462a388","96d8d0eee4","7a38923fcb","caca50f014","8b47b20e4d","3b0269fbca","00a1112205","875af6daf7","e1ca8bf84f","864a8093f1","a925171c44","625b85061f","b0b33e7d4b","4d9ebd0854","9888e39651","f23353cb50","c68d58a429","8a19e4b198","6ceee560cf","28634760d7","ed93d6eace","4148b42cdf","5810a39d28","fbe9a6f475","995516dc4e","e06534e69d","0f91174045","3b75c1d9a0","c93b6aba0f","a26a50324a","2fe5960d4c","c83006a674","4e10052bc5","a35f300dc8","8a772668f9","88dc029e60","d971d8dcd5","91c580dfe4","6afbc05160","ab53146d79","27e269b871","e3035b1c7e","6d0743a87c","0869d8baee","38734f8f6d","c38fd72b61","944fe39d54","d31c1a331c","a05d433cb8","f817a06a16","0a27dcf92f","4975b6fc25","cca548e2d7","101178bc30","74b0c6fd22","e621000130","ab3853eae5","594902e74b","ca27b1a407","a7dbcdba1c","101178bc30","74b0c6fd22","e621000130","ab3853eae5","594902e74b","ca27b1a407","a7dbcdba1c","e05f5c8f80","7de647ae8e","8c10b4a1a2","9d5ed76475","4209e80c69","e75d01ba32","cc1682cc75","9c6484696a","c1538afd34","75017b17b7","8b517ce74a","76afac5316","344a4d5150","4791ff38cd","eeb4b94a23","c28acb032e","3732150d5f","8555f38fbd","3c54cdadea","a013e2a3eb","c1c87a025e","1851b79329","b76ab3bf35","7f1720f681","8d381344f2","b47f8ef86b","167d42180c","48e5302aca","59380659f6","8659fb5508","e32b0b4918","6316d013df","d114e8d06c","ab41b6f568","b729938c65","6ead3ca9f9","c3e65d5d1c","d3b97de058","91a1a5fb9d","19a620a12c","a6b5987603","821e04bd84","1851b79329","b76ab3bf35","7f1720f681","8d381344f2","b47f8ef86b","167d42180c","48e5302aca","1851b79329","b76ab3bf35","7f1720f681","8d381344f2","b47f8ef86b","167d42180c","48e5302aca","afccd8f7b7","b29ad03966","832b165dae","5ffc969dbc","5f3fc04ef0","bc308d76ae","7902845c28","6bbe08dd13","3a8cedf467","3c72fb4c42","e530a63324","cb3f8bddee","c1d8e2c21b","b6f87fe128","a104002bf7","48d711b36c","9b0fcb939e","0917d0239c","078048a8ff","def852000e","995edbea43","f130a45dae","d0dacc4977","885dbb6663","0a866538ec","b36f196a49","b1b9824f6a","f2bf951e64","1f6c1fbdd4","aeffc3ea30","9ecab0df7e","bec6605184","df03699ff7","ad9110d10c","34f5a8eb8e","1e796f0594","e6a8e46ece","7cdc23fdb7","6622424fd4","d8712f1464","63fa640ca4","02a24e2a1d","2c037fbff7","c2f9e4b28f","7dee3e40e2","7d0c39e1f3","4a756229c3","ff8fcd8e6b","b8a4464db0","325d96bb09","c57e6dcb6a","b5c74f46df","d793f3ec8a","45d20fe4e5","d3715f0ac7","ec3cfe092d","a06923dea7","377b09981b","c4c6c8448a","439d1bcf50","9879978772","65aac64d79","94c6ca5920","a06923dea7","377b09981b","c4c6c8448a","439d1bcf50","9879978772","65aac64d79","94c6ca5920","de1ba3292f","17ddc64eb4","18e937ae9c","ba73d9ee11","392c574364","9ebed97f50","4d39080371","3323bf6a21","fb3fda37da","1ffb3492a9","b85cba2041","bc544877a4","48c4149542","46b4cefa86","a719cdcfb2","87a2e59b3a","22f11ff5cd","c4e9b587ba","649d26c365","d277dac61e","3e4451c97f","a719cdcfb2","87a2e59b3a","22f11ff5cd","c4e9b587ba","649d26c365","d277dac61e","3e4451c97f","a719cdcfb2","87a2e59b3a","22f11ff5cd","c4e9b587ba","649d26c365","d277dac61e","3e4451c97f","e3a2c430b0","4826bb502a","1f33c41ea6","d1daf1625a","3a3b60a135","e2a96ee858","c847dfd80b","9e47463771","7483882293","a65b8438de","e2aa4248b0","4f9fd56097","1fdfd04ab4","c526811db7","35d53d1760","f4e3686715","b0b5175241","8e8df638dc","fb47bd5a7b","8ccee67126","96294b44cd","8680d06642","6ab30e96b1","303f06ef5c","140a83da18","ebc64332e1","2a5f6d4640","eb1bef65ea","e6d55b8cf0","5294b46d2c","86b36b6c35","382015f528","848f2243e0","7b7c620903","2c8771f2f6","e6d55b8cf0","5294b46d2c","86b36b6c35","382015f528","848f2243e0","7b7c620903","2c8771f2f6","a878a410d8","10719b5ffb","867fde72c5","64a8bf8e1b","9072264275","7a33920f36","8b6ab2fc21","d5755a4caa","cdd3ce8a0c","925f7e680c","cc5206f475","ca8eb5faeb","c36ef25c47","71f27af427","250e466ece","9b3fd2d701","c1ed6baef6","a80fc21313","0c07992b22","ceb9b4473a","99ede47824","49413688dc","749e5778bd","1e8bd6a168","8aa4b66b8b","d9e4d125d6","dc59b1a7e2","0e37b4ebff","d36051b311","1d54649dc2","8a2d76448f","2fdff59a79","b007edeac4","eaa02ce903","2caf8bbe91","3dedec4acf","fe47969fc4","09fb70ee6e","14a827a91f","8175a5a5ec","d684e4ef6a","6c2503f541","25ab5355bd","7d0c3a24e6","c0fd2c57de","e1d75c509c","cb025fb2b8","2656f0aef0","a755de8ff4","25ab5355bd","7d0c3a24e6","c0fd2c57de","e1d75c509c","cb025fb2b8","2656f0aef0","a755de8ff4","a3be045e2d","514efffd48","0369888455","eaf36dee32","581e48dd4d","2db735454b","6c2acbb159","d58179fda7","efb65aba8d","f495db8cee","dbd3f2bcdd","478c3451ed","6a7d7e032a","5c5ba5ce52","d58179fda7","efb65aba8d","f495db8cee","dbd3f2bcdd","478c3451ed","6a7d7e032a","5c5ba5ce52","cf9b127af4","4a36d43fd3","a33eea721e","f4d2677ec1","56e86d4c4c","006138e7d8","08e65405cc","c64a73e795","004d8a03a7","fe85d70ad7","9778b4d397","91b8ed6103","c7972aadde","aa8e282ad6","9b172b3e45","06cd658724","8bce61fc51","47722beafc","c822fb3c4f","6b97cb7cb8","d4a6390d76","38b20cc535","178ac34cc8","5b8a2b648e","45398d5bab","3656c7e233","cec952718f","66991440f5","38b20cc535","178ac34cc8","5b8a2b648e","45398d5bab","3656c7e233","cec952718f","66991440f5","9cde5ce84f","e8eff2249e","2a7e1f4430","4e2b9a274c","41d7547c7b","207e9fea21","9ed534e2ad","fb998aa6e3","8c3bd4e845","4b06c427ca","4268d53789","02299d81fa","a6dc239bd4","3497cc8a81","f8e84f7fae","50c31c18d5","9ef4040393","9030e69713","3bbaa6c74d","93ddbc653b","709a63b6e5","f2b7a86850","8baa618d8f","ff885cabd1","67dec7eeff","0ee9d87d62","5c8e632846","3d9aaa6494","fb998aa6e3","8c3bd4e845","4b06c427ca","4268d53789","02299d81fa","a6dc239bd4","3497cc8a81","fb9d0fc376","a107af9e2e","eac54c23f1","e923d4c92a","6fcb444c7d","293264f27c","c876d3647f","d0d5e44529","681d4aa43f","057870a6ab","34c038994c","2e6b7f8c4e","df8ad74c2b","a3078c6947","2df5a33500","d7d5e15742","1a1878a605","5305631cec","66b70a1537","9f89050cf9","bcb3a12e86","570ecf7a32","5b4c78570a","acfb51a4a4","0b7685bd24","e510fb5f5c","eb7131af7b","e924d90408","8e91bfbdd0","eae004aa2b","a526ae787f","7af9277bea","5563c75199","008dd9a6a4","4cfd500a68","90a0dbe3d3","f207e79da9","5e787c1d70","9e8346f4be","eb59cd1d96","0e57fe895d","5d9dd4475e","8e91bfbdd0","eae004aa2b","a526ae787f","7af9277bea","5563c75199","008dd9a6a4","4cfd500a68","57242a3e94","3ab379a2ad","491295eebe","77a9cc198a","80ddc2f130","dae9b502cf","369d3f3951","fd86a09cc5","5b90dd295e","813ec86515","7ec767388f","6a1f2e439e","b5f085dd87","fa85c5afb6","01ec54e743","bb195f2bde","673650cf54","a841537be9","2f102eacf1","b2bd9c0e22","04f94273bd","c6d4a0c68a","3edd5f4ad8","876be46eee","ff8d5e5ff5","560ef60882","ebd2a32f69","9a06f4b06b","6023a77957","07e476d587","f6c3674cb6","aa3ee44a9a","40ecf89a8f","19742e75fc","f23a60c1a4","572b8f4df6","e7be8f4302","687f2b0ec9","a7767f3375","81dfd9ac69","6ba6221999","f4e4c29529","bf9e354114","b94effe1c2","02520057a7","8bde67bd2d","ba30fc2bf0","c21c25fdc4","8764a7ef4d","1828efb873","62c28d78ce","1089d66066","b3fcee5bf8","1fed40191d","168574acf0","90542a51ea","3d1e65b68f","98b29a677d","e26c939158","36425de527","5b64e1460c","ba75072779","a24d34fd6f","68a15237ed","7ef8803b11","ceec0ff95f","a430be019f","f378f1e793","10150f7c9f","0c9f0666b3","1cce9b8689","48ee7ba8c6","5759d46977","1976dbf9da","e12c1b8b7e","086cadf33d","8e5f61e384","13d91bb63d","fb005a3f68","816119bc23","8edc75ce6f","49fc0340e2","1050e087d9","4cce4d5d49","ec3c86eba2","e67e277812","08f59a0e8c","81d30e8933","b5995a4bfe","3918e47695","c92db47c71","8e2f775e70","3d5589a46e","9915501722","eec43a6501","d147c175b3","1a907ce9c2","720db87f4f","9888413c96","ae44f1a59f","9e19732645","f1abb3068d","0ba41ca774","db16ebd96f","df3e50c6c8","cf79b9af7e","6ba0895bce","5720d7b957","65c9856f2c","f2efe7dbd3","6e2973b36c","8936a24d01","cf79b9af7e","6ba0895bce","5720d7b957","65c9856f2c","f2efe7dbd3","6e2973b36c","8936a24d01","154c12f7aa","ee5a15aa4b","1c79b181e9","a77a8c439f","607871b314","c97f9adeaf","501c425b52","7f25641130","7ea2661b3c","8aca7a6cf7","7bbdc6e7aa","d2c5a30773","cb78798735","1be14cdf31","cb4551dadd","60666f978a","0e9f209230","622e82ca0c","109b72682d","b735a30cf9","c33c038c41","ac7b91e097","47ddfbad71","78ff143c7d","72a2c9c63c","7342aa2947","af03ce5b10","f43f16bd25","05c616d7d7","cc01830bb3","85553841fc","8238a7a0b2","d9430329d4","55684e22b5","9136d3d909","a497140486","6c1b56d903","6098a2abf8","30f872d822","506e33b484","daeb9d6e41","7da4b96660","a497140486","6c1b56d903","6098a2abf8","30f872d822","506e33b484","daeb9d6e41","7da4b96660","27bce80011","5d08fcff15","5e26f34607","ba700f8e1b","33786adb7a","ae09ac1d5c","9959400956","88cce042e9","c4299e7092","ec74eb48b9","511fac9379","f35f87f45b","fda52d4234","9e4a36f7c0","2394a186c7","f981df962b","8f20be9b2e","8bab95c685","a6d9b4f580","5e0c930fef","dea1996873","8a0b416b96","18d9cd6626","4f9b48958a","76fea3f46f","ff43690055","6ea2a87449","90932fd55e","e6d64af688","82dc05d481","574c0cb600","c616e18d67","9397215807","69070aac85","5a46cdcb15","5ddcaf9156","554c4c23f4","ec00288fee","24d6fb8338","1da9067dc9","14ce91b82d","1be588924e","5ddcaf9156","554c4c23f4","ec00288fee","24d6fb8338","1da9067dc9","14ce91b82d","1be588924e","e0aea1774f","4596d458e1","0e720ad067","12e6c40d16","1302d2ae8e","483fecbe4e","ed00a1b3e7","f0a19f1dbd","23af8d80aa","471c8dce64","cbbef1d537","31e933b18a","0f9901b556","a3d8c8883f","4732305be6","7a7579f64e","15a95e8946","87866643c8","c7f4d4dd7c","a6e104d20a","0bc312c3a4","b38d6e5cec","e596973834","3f0f9c19f3","0622ee4029","dc4faa3edb","1e829706ad","a1de4a5e2a","3d3c99ec93","8dc6dd7578","bff79bf90c","c8b7009e2f","59599ea9f9","d30751ccc8","da7a1781f8","3d3c99ec93","8dc6dd7578","bff79bf90c","c8b7009e2f","59599ea9f9","d30751ccc8","da7a1781f8","3d3c99ec93","8dc6dd7578","bff79bf90c","c8b7009e2f","59599ea9f9","d30751ccc8","da7a1781f8","3a7b0d93b3","881b07b9b7","b8903fb7e9","a1aa66362e","735385e5b2","fbaf969f2a","7006aa628e","8c3ed8cf9c","ed6f8a97a8","e6eece561d","92d83079f8","14c9c25299","ce7cbbe89e","a3aacb2fc8","e4ffeee1b7","9efcc3d06f","1c100f22b1","e1e9fbc187","b4b0f37e76","c57da9bd78","54640635e6","e60fd126f1","bc1d6d2c25","8e58b4b3d8","e95fa1c678","8df628cd64","829fde9b88","c126edbcc1","e60fd126f1","bc1d6d2c25","8e58b4b3d8","e95fa1c678","8df628cd64","829fde9b88","c126edbcc1","329eb44efd","96c21b9dec","97d998c822","98c53b4096","e566d915a5","4fc2355aad","ceda2c2601","05352b4720","a2438f3dde","94f137de4c","6db5746965","fe45dae656","d8cde6b685","617214a681","b1fea82490","07243de6af","a4bca97c0c","e53dc4b541","61248c2363","0186fef138","71712a068b","b1fea82490","07243de6af","a4bca97c0c","e53dc4b541","61248c2363","0186fef138","71712a068b","3749ffd4ed","83f4a9f978","743126f871","edec4155bd","760057da5d","7002c455bc","7834c82c08","83b6f41e2e","5a77745b91","4554279465","a9a1fc28a0","ef4dc2e51a","7ac1b277af","b984e19831","83b6f41e2e","5a77745b91","4554279465","a9a1fc28a0","ef4dc2e51a","7ac1b277af","b984e19831","cb610f66b5","cee47f64d7","8595e84548","9c870c38a0","40a3da5369","85a95562e7","7c3797b0f0","7a20acc909","eb80b8c6e4","bcc798941c","bec92123e4","b2b87c8c9b","76ddb463f1","bce72bb096","7a20acc909","eb80b8c6e4","bcc798941c","bec92123e4","b2b87c8c9b","76ddb463f1","bce72bb096","73190b64e1","5c0f9d7ab6","bc5ee482ca","af0c0458ed","06f2776236","21949890d1","c960de6b90","abc558e7f8","ec878d131c","fdfa7174db","64ec1d16ca","4323da23f6","5ef83c2bb6","31bc599108","cdf0a47221","fab15e97b9","39fc410025","d3fd5590b8","80f5f50abb","a8e7aef442","491d27d82b","dbd07910e4","328ba5530a","021d154b8c","4d3c9a85ad","8d3e8fccd7","61b38dae99","a98c5dd438","e929e468db","104bdd5b41","b343a8a6a9","fde569e5d6","4e762cfb56","11bb4ca5dc","d91125af90","0349788d59","dce7740383","380e1a5853","f4ad7f1b6c","bf113cfe20","e78441796a","ce2a535872","0349788d59","dce7740383","380e1a5853","f4ad7f1b6c","bf113cfe20","e78441796a","ce2a535872","e929e468db","104bdd5b41","b343a8a6a9","fde569e5d6","4e762cfb56","11bb4ca5dc","d91125af90","c065519c79","0c873a02fa","d7b2e96b2f","cb28383778","9465fea205","920b61f015","e751b5bfe0","e6982926d2","19b524a628","af2c5bdb05","5f47d9d683","97b897542a","b8b0b1b76a","b327d5d598","dbd07910e4","328ba5530a","021d154b8c","4d3c9a85ad","8d3e8fccd7","61b38dae99","a98c5dd438","29bdee454f","31bebfbd66","0fcf3306b2","ef4caab85a","12d6517fa8","8df93ab714","1ee332794e","29bdee454f","31bebfbd66","0fcf3306b2","ef4caab85a","12d6517fa8","8df93ab714","1ee332794e","54db43d4e1","0abaf55376","444d4674bb","d1e88a4950","b60dbd0dd4","87cd9d0db1","5d11d11fd5","b539df60be","1983abb62b","2792f43c48","203e45f0de","a392a9aff2","07ed3da002","45bf1af473","b4d28def4d","b1a91ce4a1","04a7f14d1d","202a649590","5a1492d0db","c33cdd8b84","4ef62fa634","b4d28def4d","b1a91ce4a1","04a7f14d1d","202a649590","5a1492d0db","c33cdd8b84","4ef62fa634","40cf4a6ea0","f46a531f1b","58e26ba16c","1785944992","5e4a8193e3","dff7bc2c60","6f6a65fd65","a15fd06bcc","2aa680f2d4","418ee9942c","fc7630480b","c57afc4b74","ad431294a3","978689542e","719d15edaf","cd5f78f89b","005f27888a","b8ee8bbbe0","e038d5532c","b57bb254f1","ff82fd8358","326a39e01c","a921a8027f","b4bbdc067e","cef3979a0e","c590037c4e","e87302b544","d28a0000d2","53971e69e3","540f0c9279","b250c657c9","905dfe7748","471fcb1520","dd0fd7fc9f","acd7592422","ea5c18329d","5735f794c2","efdd7ad511","16562966fd","ebb9ce0032","0663c283aa","46247bb9c9","ec7e5a97c4","389b9bf2aa","8fada3cb4f","9a9e31a9b9","2436f0ec9b","39d92505bd","cec3c371cd","40cf4a6ea0","f46a531f1b","58e26ba16c","1785944992","5e4a8193e3","dff7bc2c60","6f6a65fd65","cffae92e32","5744bf21b0","e21a4eb61f","9f84762591","84c1764f4f","89a043d247","3559bbf36d","6791941fde","9bfb0d7360","47450ba4c4","291746759f","f81d286ac3","cca50d9bb1","b66067932e","6791941fde","9bfb0d7360","47450ba4c4","291746759f","f81d286ac3","cca50d9bb1","b66067932e","bab1a9abbf","2e85cba5dd","e5064da793","7f86db018d","11546ec173","5074bf5fe9","7f213394a4","b2a45a1568","32d06e94d0","eb67feded2","1a52866786","4ec337d19e","3fa91179b2","8927ea5525","075acb5289","62957c30ce","60087c4f52","1a3ee7144d","225f10e829","e38dc8b5bc","3f999c63b7","aee853006e","61a7848bb0","35b7324906","13d323fb08","5afaeed174","80eea5a0a9","0e6da5d6e2","aee853006e","61a7848bb0","35b7324906","13d323fb08","5afaeed174","80eea5a0a9","0e6da5d6e2","f558bd793d","18abbe29cd","a04c2a1f24","8a2cc270b8","6b7f2ac676","3e78e0eb19","17743e2e4c","d0eceb9793","ea76f63aa2","0c5ed8e773","c5f5ff8310","5af334e7cc","cbe1370644","6cac114694","180d658eec","435f5a15aa","30b0d17e66","1eea884c76","ea3f5c9144","f3469d3af7","e5eb781f60","29db6392b1","afef9ddde7","c58250ab22","ca5e35297b","30407b8091","9291b19b3b","ff53dd91d8","bb33c3680e","3d08462fb6","e1b895f070","d7ac936b92","0bd1917ef4","9798580cb6","2b876345f6","ce638bb366","c03172d24c","ae25a1bc18","f319495661","eefbe010c7","34c98e6146","f187547343","bb33c3680e","3d08462fb6","e1b895f070","d7ac936b92","0bd1917ef4","9798580cb6","2b876345f6","bb33c3680e","3d08462fb6","e1b895f070","d7ac936b92","0bd1917ef4","9798580cb6","2b876345f6","e4ddfdd26f","2d40b154db","c89cb0fa7a","9c52a58dd8","4a265b2b9f","b4f63e0c6a","4dde2ebc84","0e87ebc0dc","1157a2d5f8","cb4f3a0f2b","df2fb81eb9","05880289e1","1889b3d76e","24be9ecaa3","a7f9142d4d","701572390b","b9093f50b9","54c61b967c","b78c64a023","7c8457b53e","0067e1d6b7","a56b0a6185","7e50638cfb","1c8dda9ff4","fc347978ad","ba724c5426","c7231cbd73","88cd3e3da6","fb900dd7e3","76a2090c40","b24aa8cf38","b6f6215ba1","62dafba807","aa7481762e","4e14699261","fb900dd7e3","76a2090c40","b24aa8cf38","b6f6215ba1","62dafba807","aa7481762e","4e14699261","4f2aaf1462","8b29456b2d","d7f8e3fbf0","4e182528b3","cc9f382ce0","27ccf63ad3","5fb3eac373","7d685cdf3d","7ae0a33082","8f703a3e21","87e2485d6b","631f7ec135","612d2839b7","3a7927279c","7d685cdf3d","7ae0a33082","8f703a3e21","87e2485d6b","631f7ec135","612d2839b7","3a7927279c","8f30edabc7","2efb06e55b","4f1d6d4442","3fb66df758","0ffbcb39c2","3c457ce63e","9d20c8f26f","2cfc66e478","1469bbccd6","b95b85bfa9","e05c4520da","30b10711d7","cba6e8e93f","5cb3adedc1","294dbbfdb4","c38ae9bf66","4afc565890","e955a8b270","dc0653ee43","c9a8e58eb7","a45c3d1d0e","5536af31e8","a2df5cb32d","a7e08556a7","4ff8ac0525","61e3eb215d","c519f23822","81996a8e1b","fcffac477a","aa8d33e609","14e1c55cd6","299493a66f","e49699ef6f","15d4ba9540","037bab8ef8","8963734002","30c666f9b9","e3d06345ee","4c1a9fcc60","521ea42682","ea5adbe126","db248d3bcf","a5dadeef87","e46fae828d","756555cdec","c4ff654d25","68225a38ad","fadec086f2","cca76f01dc","82cbd2b984","0b3f644f0c","09c5f76bb7","fb2f3219ad","ac97d82206","03b93dfabe","8944b5a8ec","bc9cb91ae8","5f93de894a","072b7bf0d3","72bc60175f","98db61cebb","efbcaac993","b49f5f2c76","1d5f42d55e","7d8a781382","f193006aec","949f0cc409","75c3758d8b","286bb51793","bc024af61f","1d5f42d55e","7d8a781382","f193006aec","949f0cc409","75c3758d8b","286bb51793","bc024af61f","ba72b48b94","8162b647e1","b91ee1c681","4998d7fb47","d172a04b2b","bd61869db0","a78657228a","b636e70fc1","175aefc4ed","c7f8559f2a","c80e1549a8","38612e7698","92fda78cd9","f235045250","c12fdb163f","3d6df103be","4ff1c6c4c5","740ed22d37","86312488b2","6c890ff916","1a9652b95e","3e7c2296a9","99ad4e737e","42d3f77204","6104c7bbf2","ca2c9c961b","1961580831","26250bf152","2d44e7afd1","fdba628449","60ebfc5511","f8dfdb8d94","91cfc142c0","19f031cbaf","aec35b40fb","90e488af67","e4da3d4c88","8aafd26c6b","b1f2dfe23c","d5de833c02","e56054bf54","2b5d27f8ae","7bec63cb00","7a427ec490","a52a1e6ec7","77d89bd093","10e24542fe","0023030956","14785bb520","a80bc2791b","93663df84c","a1be276c48","78f9572435","eca10fbb95","42d043256a","f027bdedd1","e5dc770f54","c4a8bbe9ac","504fd11a37","b4c0859671","e1cc934e79","f4c74aff01","87673f43e3","4d856c9ba9","285f00d68c","013fafa9c6","e11bdb8014","d673e56234","dd52476c3f","05d9eec3c7","4d856c9ba9","285f00d68c","013fafa9c6","e11bdb8014","d673e56234","dd52476c3f","05d9eec3c7","56d054def0","d0750a8956","092d939f82","7ffb0585ae","8d26e15997","3a68e4402f","264eda667c","0258f9d881","417d3ccb66","fad80f897a","a2976aa32e","61cf514fb2","3d01af60d7","66335d6952","0258f9d881","417d3ccb66","fad80f897a","a2976aa32e","61cf514fb2","3d01af60d7","66335d6952","21a3d7574e","823f332fac","b2ba314833","d73d7756cb","222ec3f2fb","bd1c896f6b","4c16069de5","b907e57fcf","25832101d4","7525a55400","6d3f66f0c8","321ae66c61","837ee5f96e","899b499986","73a277d246","4882539a44","847f6b40c2","b9ac8b513c","fde310daec","bd40007f70","8d3020ab9b","0cb1643e8e","4b3ad4e220","14c77d9887","cd69238874","ced2d6cb74","d7bad1e770","8dabdd76fc","46a0340f57","df922a2c79","069cb33c13","75342e8059","906aa4f1a3","a1f62aa9fe","0606b1fe25","8164a34a71","e1ded60dfe","e6b6486c77","069800a80e","77b23738a3","72beb226a7","db7986bde8","8164a34a71","e1ded60dfe","e6b6486c77","069800a80e","77b23738a3","72beb226a7","db7986bde8","4e30c9347a","7b0d8b1412","d5600fd8e6","8801b7aef2","d84f1f6961","ed94337470","87b107a9fe","670bb8c7e1","22de9d5702","7735874e4d","e9d5e82773","df34081619","296ce01ff8","08830a9a9c","be902a86da","0b6594ce16","7c841915db","985bdde047","6ac840ff5d","c175d4109d","9275089000","be902a86da","0b6594ce16","7c841915db","985bdde047","6ac840ff5d","c175d4109d","9275089000","e1ab2ac4ec","c06d5e4136","d2a3f22dc0","90c5d6c1db","f36ee4d3f8","7154add587","d7db18de57","c9dc86b6b4","2f25258dfb","ba430cee7f","17bb57ba6a","c22f782616","24757d3588","e307abee4d","70ed5d299b","e1616acca9","ead6026e08","d4c7e397fa","e4125cb743","31fdc90fb7","83ea917dd2","091e23eb9d","023b09ce51","50c310241c","9b7ac07d18","3b82da1b53","33603a4caf","84af83db4b","8e7d047273","4ae7c02d0f","36c86a7116","e60adef95d","88d06e593f","75d367e93b","ea3d69a30a","67ff3c6b02","380fe3df4c","5b1c72a1f5","73572a99a5","839a23a1d1","490bc7bbf3","3687db06a6","59f12af756","21ce3463bf","95f7aee6cf","65c2023a7a","ffe11c10ed","87d30811c9","c74e611d34","c9dc86b6b4","2f25258dfb","ba430cee7f","17bb57ba6a","c22f782616","24757d3588","e307abee4d","c9dc86b6b4","2f25258dfb","ba430cee7f","17bb57ba6a","c22f782616","24757d3588","e307abee4d","3eb90f49bd","6315b82786","74d7189a10","8a774884a7","5f5b8635f0","e63aa8469c","04c24eb315","3eb90f49bd","6315b82786","74d7189a10","8a774884a7","5f5b8635f0","e63aa8469c","04c24eb315","83181c93d1","71823d2e5e","04fc1cac9a","032ff855a4","bea13dc7d2","5c3d418647","17a0719a63","e1b99054a7","cd849b1c4d","a49b506a4f","8449c720e3","803f958584","243dfbb444","663fde0129","39857961a1","e073e2fee3","494e2c6a8d","2dda397360","801c93e01a","0cffab6eb3","2b08d084f5","c85741f86e","9572a2d965","ca4b93fb93","4c0bfcdf43","dfc33b5d79","f091c9907f","c6c7130cdd","731c96314d","e007ef890d","41b380abd6","5a0e383716","c9f781583f","1ad6a0a374","8ed58fa3cb","2fd51d2836","e5c2d9eabe","9a409dfd1d","b39a147930","6f923d3e9e","0a4a4a150e","198b3c2d24","39857961a1","e073e2fee3","494e2c6a8d","2dda397360","801c93e01a","0cffab6eb3","2b08d084f5","83181c93d1","71823d2e5e","04fc1cac9a","032ff855a4","bea13dc7d2","5c3d418647","17a0719a63","2c0829e9c1","a783d89e02","05f7ca428f","2b812d3673","baa9d833c9","dce3741672","3ab0d2e2c8","977fbfa945","66bd0ddcb0","0927b8d3ec","4cd60b9151","2f58d0cfe2","2b45b92787","47f7b82cc4","d5d43f2368","a3cfd15208","37c7dcf687","f15480a913","ad93975d37","b2b8d40c2e","2dffe17762","731c96314d","e007ef890d","41b380abd6","5a0e383716","c9f781583f","1ad6a0a374","8ed58fa3cb","35d22795da","1713b41c1f","8391dec1ed","74de90879e","599ac3a612","a4e227becc","d4a2df016a","74edf9dd6b","658904a465","5a77f238af","6b99e32070","36a2e91d55","3712b0fbad","a085ec73af","6838eebcde","1627d9a094","c43a9dd861","a849d234fc","1d2a7560a7","215186d730","eac720f939","6838eebcde","1627d9a094","c43a9dd861","a849d234fc","1d2a7560a7","215186d730","eac720f939","5bb4e47b03","8a0b2344f7","a1f2990a5a","1d8a574852","32ee2fe39d","af5879bdfc","3cbe29c6d9","3733f22198","8c1db8a8fb","237f2d8bf9","bb14da5dd5","ef92743a9d","e3f0c0eccb","36a7044e91","2c09991f87","c7684f9529","7a853f9865","f8e7fec334","d24cac92f5","206049c1a9","9878a1f2a8","ff3e727c04","a50b565186","3348fdb125","df39030c4c","f5d39bf26a","c5b6ef306c","3f07308be8","ddc8e2790b","acd4dc7a56","554e2e5f46","740fd62e31","2bad61fee7","6ad8ea1f4d","ac073c98b8","5f18afb098","e237d1f524","76b0fac0f2","305fec4995","c03a12ab9e","518e5a2d12","44d2c63f8d","4d52a9e611","724798a7b9","a51a8dc878","7aaf73cb45","a721f97cdf","9fd9f27f90","7cfe22a897","06c59d1bfd","3fdef33071","e550a975e6","baf33b7ae8","a8b102b100","d218132d09","8549c77597","1e84ae80a6","f05a6fae78","71db23ec10","2a61829f83","edba01505f","24bffef2c0","7ee8628139","c2903c2631","6f969d9268","2ef75df74c","7fa5b4c8f9","79240f1662","07473c0d4c","f5f414cae7","ddc8e2790b","acd4dc7a56","554e2e5f46","740fd62e31","2bad61fee7","6ad8ea1f4d","ac073c98b8","6bc5cabfcf","3a4e04fad6","0945a1e5bd","ddc244a34f","a3a8651385","9684319d4e","64fe91d4e6","b83ab503b1","53fd222de6","eeb4a5ec44","dfc7d37d4a","30385cbaff","749890b683","81960ae4af","62093e0f9b","0f6c8ef228","b6a7330167","a1efe82196","812e58378a","d0e90693d9","abce3c1fb6","c46817d54e","8ec0fcc257","92c3459c21","94ad2a743a","fac6cfa23e","e30fe5e694","b9f9f87386","a7f63d7920","d06d9d27d9","6f1d36128e","88f2bae85f","80bccbdad2","1e895209ac","3193bf8576","f549739b72","75604c08d8","ea00b1d8d6","9e07161522","37ea094b40","f0aa878006","30dec864ab","062a979c36","dccc72e1f0","a7fd7762d8","6f6ec67aaf","3cd509ded1","56c4979da3","c5c4ea2294","6c57e95963","0d0dda8325","4682b03a5b","2553c6e825","6683522180","0f8071e563","76bbb1f481","17ade29113","3d152bdd34","e99e075c2d","2e6217f6c6","5ecf0fbdc8","4a3f590651","7525923773","7b572e0261","0dfd80f1ae","5a8341c509","af306cf999","210698d2e7","e5e21eb9d2","031ed32349","7b572e0261","0dfd80f1ae","5a8341c509","af306cf999","210698d2e7","e5e21eb9d2","031ed32349","d9b1c73bf5","18211a251a","160cd4f951","b970ef5cb6","5390bc34f9","0e1d5ba98a","ac58914f9c","3a9f680b18","d6d9e19946","49dd6a790f","ec6cd8c832","8e2ce36105","756991eae5","39d7d02e23","550ca679a0","d0fdfc94a6","9661e5b4e3","c5eaaa0fae","97af832446","794e54291f","49bb37ec4a","4026231a37","68943c9743","09aa54185c","650a3a8853","754cd6028b","b809387a38","b85e2f740c","3a9f680b18","d6d9e19946","49dd6a790f","ec6cd8c832","8e2ce36105","756991eae5","39d7d02e23","315b9a60a5","4e4ec3af35","b93cf7a429","243513c414","72435122ad","623aaa5751","46ca1f645b","784fb2b17e","46fc79d14b","b8e364d2a7","f96e210af2","deebb5634e","df27000d0d","5a7a94613f","9030e50c38","0b278002aa","0ea2078477","e77aa9fce8","126d807945","fb3a395fe8","04605075d5","a38d370766","e95efcdaae","e016069e9c","a8e7de3817","3f03cf0191","4f21e109b7","86ce44d3dd","9030e50c38","0b278002aa","0ea2078477","e77aa9fce8","126d807945","fb3a395fe8","04605075d5","9030e50c38","0b278002aa","0ea2078477","e77aa9fce8","126d807945","fb3a395fe8","04605075d5","de5f63e651","c36c743a53","09c52fdbdd","7b3a96a826","5b0f206609","c4de187e4c","09daa13197","c5407465cd","b588ffd88a","7122062d66","67bdaf2693","d1cfd5e88c","be4ee26b82","ac142b7c33","557ba37d68","fa321c91e6","738973da40","897300c8b2","35ce6cfc86","2fa5e55ddd","24f83184eb","b335ee9491","c9e913ec99","fe4a9f9126","19771d43e8","0433a1bfbe","e60cd28f4d","d1f306116b","0c86cfa842","2435349713","0079ee5d73","a0dc827760","3f3a003f2c","6ca04ce8ec","7a9ea40e7f","57e2b4c207","9ca5a526e3","a91f76564c","396ca60f51","18034252f9","74a1bb5bd7","545286e634","d8a20d43d6","7f6265ed6a","e0ad79a680","10615f5ada","496b9b965c","74ec521bdb","bf94c833f9","d8a20d43d6","7f6265ed6a","e0ad79a680","10615f5ada","496b9b965c","74ec521bdb","bf94c833f9","179458ae94","4acf3978de","c9571d6826","3395956921","b82fd6cc44","b58d466a4d","4ec45983b3","6422a43a38","a0c81585cb","212c9a4523","e2b38061a5","5dae027112","221e27ce85","da21af03c9","b5beffc0d3","19633a124c","16642eafc1","9236dd383a","4cb68f4990","315ee43b4c","204ace845f","a14b747858","8a8196f321","e16f0d4b10","f25c1161f6","26f9be9270","cda19ebc21","11c1a0cbea","0b4050c23a","501ef52f46","007aae2975","e5af7bdb32","7841076eee","566ab28109","c133bbc1de","379bd34ba7","6ba7119961","13a64d75d5","bd4e281de8","25a28ca622","117bf6226a","e93206c3f3","9f91a198a6","8fa44cc974","da726fc185","25dc94719a","cc5f9f5319","e64fbd59f1","1f8c336c48","8a0aacf124","5952f00963","5114f7143e","b94f963718","18af48527f","8b4cc6b923","55d42d360a","8a0aacf124","5952f00963","5114f7143e","b94f963718","18af48527f","8b4cc6b923","55d42d360a","dd453a7d13","3e2b15219e","2b5908af2e","3081a5393f","d9d61fdc51","39341e84f7","6676503543","bd54ef51a2","39cc993a36","3b3a591807","040359dc6c","a9e18cf424","451aadb7d4","a542730594","89ac8920c9","6e401d479a","4f62b671b2","44d7551ed9","74cc1d5b4e","fa5e68952b","96be958eeb","5febe4afeb","b8c84e15b5","d19449afb5","8662ec9e82","9eec592cb0","ba65e01abc","e1d6a79e3a","c043640632","714c1beda5","a8196256e5","0af524822f","df73c6466b","729e78922f","b5cdc8340f","b4c468a22f","af49fa63bf","e85cd4c4d6","ddbb4ad156","ee7300ed6c","500bae35cf","9ffe7b9933","bb8ca47df7","21f12451e0","2afb592445","0496fd6c7b","480abe1dba","afba380ea3","e9b7f0fdf6","bb8ca47df7","21f12451e0","2afb592445","0496fd6c7b","480abe1dba","afba380ea3","e9b7f0fdf6","f7387dd147","b4aa864e5c","bd91929704","6c07273fb4","262bb89828","14b25191a7","271a6bd0eb","8ef16ee453","f05796fa28","b94ef75f82","3ec6c85745","0e0d7c96bb","478aa0d4bb","6935b8bcd2","603115639e","ce703be04a","7ed245aea2","d59bda500b","8021443068","f0d19cda42","964bc9dd66","633fd6731e","3d6227ba77","f3de650a37","741bd6aa00","1fa1064cb4","4c24c0a14d","1f42fbf453","de16b2c9d8","d0c475b3fd","809070a25d","a5fffbff65","bee5f7b58b","66367c7558","efae9f3c37","f720924775","efb5b9fddb","ec86d9e1b5","54eacd8bf6","fedab8fc16","396a5bbc59","a8c179f42b","603115639e","ce703be04a","7ed245aea2","d59bda500b","8021443068","f0d19cda42","964bc9dd66","590638f401","70d2f2a71c","d207d67317","9fabd9e240","2e980a1d0c","c695c994da","e6ff64fda7","7ab66db1bf","85c8af94a9","7c9c60218c","6f45a91492","b74c592168","86e21536d4","80e620af94","0041058829","3ac612bc71","08747fc119","1f7be50317","f4fd2a18b7","f5efeba872","4707421462","be254cfeab","5b4f546ff9","0fcda08cba","fbf34db09e","8e8fe536d7","bcb8a0f637","a44c84cca5","8a269bcd09","17e33b4efc","5005abd169","447223855f","65891f7cd2","02a106bf6f","1034a414ee","f9824dbc6a","3ad0082140","a349732545","84990f4f0e","441a9d5651","076544c1dd","bc7d3ed8e6","be88c9917d","c2a1557264","a763b4c2cd","eb2a601528","0b0353b43b","4661270712","480cac20f8","8ef16ee453","f05796fa28","b94ef75f82","3ec6c85745","0e0d7c96bb","478aa0d4bb","6935b8bcd2","7c51b3e320","3f8ceb09a7","ed8c339602","b3f872dd86","fdfd31740a","1d05461eab","36d0870e08","7799af9489","159604a6f9","fb98e7d44e","516997f953","8c12d35e86","781c2c18f0","5b4c509847","8786304ac2","a22f83957c","7ec5bc9fee","a79de28aa2","fe5770e232","d0cb73bc3a","eea416fb56","dfa21dbbfc","a1a41fb40b","46a7e5d28b","6aa1634309","8e5175e684","4c480db0ff","d9833bba4a","7d3bf11582","1c3bbdcac3","bf93aa4afb","27262e0247","0f7066fe0b","c067b6e2c4","25bacec272","7d3bf11582","1c3bbdcac3","bf93aa4afb","27262e0247","0f7066fe0b","c067b6e2c4","25bacec272","834377e749","ad3bbae3d2","6d80e98eb1","f6924299a2","5ac597c6c0","f1d00918de","d31ce34dbf","453ce03c8b","dae5ec5086","6506008a65","bd587472be","88509bc994","7f9af3c782","e034517905","453ce03c8b","dae5ec5086","6506008a65","bd587472be","88509bc994","7f9af3c782","e034517905","8df3a35148","2e1b69c907","482f719a28","92196bd49e","92b8cfc28c","0fbc452cd3","e02275316b","0aa7e7f668","8ca772d987","25394ad601","ef545e31dc","4488db3355","d886e9c2f0","3b5ec327ca","4c518bb155","ceb6b373cd","7e73e74e73","f4eab1c2c9","bf3eb09e43","10c9bc8f28","560b30b3ae","ea155e7e32","e6ea0bb1e5","d86c623fca","c25e767a0d","1d509e05f6","b4534d252a","37255183cf","8e3d36d623","f70cfa523d","6426d8d676","cb26dff9d0","fe0f2b64a7","1f97593a77","8bbdbbaa58","0962525c38","b84ac79537","52a0e840f1","148f3785e6","7d88e8b668","d40d3ce390","e3405bd8ac","c1c0c98101","38445bd672","0c0b1ae7b2","c9160076de","9e119c3c4b","83bcf69d6a","56dc06b48e","faf60ba903","5f319f89ec","387022e249","897c34e84a","6b2c1ef54f","cd08fcb131","9e07830b18","49fb516400","95c401dd02","dd5a7e87d2","107285003d","9661e89294","e19c9f177e","8d486558ae","c5417cb435","c9fba51aab","a5799dfe5a","14a554390c","20bf55470b","97eed112e8","e348a4b564","b5e5827b4a","e2354652d2","c265462800","e210d28314","3ab32f3aab","82f713f752","c6c735f9e7","9b34c71ef4","f20d1921f6","3ebefe8381","f1a1f2c768","d5f0a9552f","d87d76ae6a","f79b6130fa","9c25b56a2b","9667c2e931","241f5eb5de","e38e6624d5","c05f2ac4c4","84a7095a13","96fb74ef9a","9c25b56a2b","9667c2e931","241f5eb5de","e38e6624d5","c05f2ac4c4","84a7095a13","96fb74ef9a","61c5dcb6dc","d00cb2cfab","885025448a","379e91a795","7b68b3d32f","2730e295a8","ae374d13c2","7802fa1dc8","52b883f3b8","2ab29f0481","61ebd5ced7","4919d3c8bc","2ff1b68f37","98774ebe58","bcd578f2de","a2dbf164a8","3cf4c0805c","ffe119cf76","1ba619ebdc","8ac9cab467","340fa66560","7acfeb8d52","2cf59709b6","8aebab9f13","d8df7c67cb","9aea440170","1dd0492b09","d185edda47","a46c4c4743","708d559c42","043597f8f4","04ad30eaa7","a73e6422df","6ce419a4f4","db0fb23ad3","391aa222df","488d398dce","a7205fbcb8","e679ebad21","40bd0c8c14","f110630a19","1dbc2fc5d6","06819ca2ed","2e60932d71","02ad4f51a1","c768622139","b0dcc2ba31","92445c3495","c186b512eb","397762d55e","7508beaa93","35c3f7aee7","65b89d1d75","315304fd92","75f869cc31","4fc4782ddb","6bc36b380b","f88c32fb3d","4ba7b3bcbc","b5ea148fd1","6225f50339","f2741a64b7","2d58c1fa42","fec8f2cba8","ee678bc5b4","3c7e65afde","bc6fbd68fa","099e037e52","4df30855e8","ed8cf2b5a1","fec8f2cba8","ee678bc5b4","3c7e65afde","bc6fbd68fa","099e037e52","4df30855e8","ed8cf2b5a1","5c2482a970","016a49ef32","3bfeb6827c","8029c81289","38167e429c","95bde34d1b","22f0dec637","293914ec97","e9f1a122cd","7bb8924681","dc2dde51fc","4e7d018c51","58bcd63023","99286c52b1","67d47e18d6","0f895ccb71","5307da4bd3","25289508cd","0e7cbe9e0f","70f3e53802","c48e7d9e46","ca55392bb7","1a1671ebdb","63350998b0","3dce5a8f77","697182d81b","6c7d7047c5","d1fac287f1","a32f705ea2","2e27bf9475","76facc125c","d2a6652eda","6bad8cc90f","98f2e80295","7cb20ffaf4","8bd2de6f5a","92e0bf3fbb","ec10265628","27fa7e200a","3daed47a64","47311fe29f","9f6d32e6c0","e81d9d25aa","8493da1b44","12f9bb7591","e21bab5923","bfff74bde9","3d4fa9774a","6582f214f8","cef64138dc","a41b5711d6","db94e180a0","8cf64c933a","71f09b5648","6f392c1132","d1ec0faf49","cef64138dc","a41b5711d6","db94e180a0","8cf64c933a","71f09b5648","6f392c1132","d1ec0faf49","5dbce23ef6","86d038e46d","de1203bef3","935af020ae","54cbaa35ea","8c5f86e329","f4138f4c78","fced763534","20fbe2f946","e59a63814e","4c649266ec","3d29c4e427","64dfd249ba","c795ae69b0","1feca44e87","77105558b6","87a60acd5e","62c84186a3","36bb690592","676f746163","8983fe1430","1feca44e87","77105558b6","87a60acd5e","62c84186a3","36bb690592","676f746163","8983fe1430","1eabbdcd7f","1f0d82188d","3d61436b04","2a7c5a63db","00527ddda6","63a5daca4c","369f93a457","c74d7a73e4","a078fd39bf","06cee4bfbd","5e0f789ddc","bb41dd5e7f","6506fe7f6b","8ba52fbabf","7b77bfc54d","d615bf1797","397da970dc","f57a2b2241","0a619b16e3","67adee5e2c","85e9d495e8","94f70eff01","d153ada281","d38f8097d8","f161104e87","63871df058","855f424b3c","bac63c1bb5","179662e2df","cff06c9aaf","65a830b07b","66473ccc42","834f252eba","9d73fffe42","6ad2c987ea","262f5acb96","a66801459e","f4602c53bb","b811881739","efa0448e51","f2e778b2a8","b52ecbe385","74b981d458","74a0a01e1b","4942fc8376","aaf777c2ad","203f648935","8d6a3a3d65","c8fcdd1231","3bdaa586b1","3c3a77393d","7fa7c43826","42b92c2650","769572731e","34d5b97fc4","55a9b4a195","38406e9bde","060450f665","0004c615a1","813789ff62","0fa35e9e0a","69182479c6","56132d84c0","9ab9a1a298","7ae0f48c2a","994e5a0dfe","b0a32003aa","9001990f75","2e9fa05a38","958ec61562","262f5acb96","a66801459e","f4602c53bb","b811881739","efa0448e51","f2e778b2a8","b52ecbe385","a84ff104e0","e0a60c52fa","bc3f9dfad6","054bcc59e0","73b2ccd3c0","b02ff35f96","179f2c698b","dccb0ee192","83eef630d3","33a404e9b1","802091aed9","4050ee7785","cd199a6e86","ef2bd3083f","84e94ad0f0","305afb49eb","4970f69a68","00666d4867","52f62845e9","1fb530ad30","1204af09a3","28335740fd","8deaa254c5","0b6aa97c4f","2f4a23f7c7","e7aa22d84f","51905b64b8","0a42beb0f5","34269176aa","f7b5b318da","9e92d13716","80a8f3ffad","dd9567252f","ff1ce2b848","1285755a94","181a47acd8","c36669c2f6","43dcc55f1f","9246ff4186","3f43573329","efc2d54f57","04c5f81bd8","be7bca4c83","1143d71124","8ba72679d2","2f4d8504a2","15ccbe26e2","aa85dd98aa","aad3bf98a9","02632a90b3","47b970a5a6","7881ebd469","a936373eb4","f232f53229","283bd696d0","cfea0a2993","02632a90b3","47b970a5a6","7881ebd469","a936373eb4","f232f53229","283bd696d0","cfea0a2993","e69f1ec35c","ccd1c5fdb0","a2db97a257","40178babfc","8c0a3d2f4c","c7baa8d4f6","8637e5fb65","88a09c2937","ce327ec073","6cc7170529","6b81b50b22","c51b67332c","06c43521a9","73b1203ab8","3f0a84b011","30a9baa985","0d73a42e20","00beb44a29","b6cd4e4ccb","c1b94538b0","a3669997fb","ac59a05eb1","068a7b3259","57b7396932","d8273e7b46","37f7909546","ff38991717","b9337653a5","5aaaf3a627","881b6707b6","9107a79b7e","2dddd97024","64e2f0c32b","1c3c5f82d0","75fe237795","5aaaf3a627","881b6707b6","9107a79b7e","2dddd97024","64e2f0c32b","1c3c5f82d0","75fe237795","43c44ee2d2","ab3854146d","55e6d609c6","d7d6bd6e98","4ddc00c0f1","4b5ca9cc57","e1793f66ca","f98df4489c","105cc53382","bd63cd4325","beb4de7726","f7d9c1ab36","eba16d6773","32996f946c","cde9ec8acc","a5f6a8131d","64631ae9e3","c8f63a194d","73a784a553","ca7b411897","fcc4422068","0711768ef8","806249a16a","844d41e959","40b0defd0f","1c985c8bc5","03449de303","10717b1fed","2380205065","3b423bf9f5","7e8e87af98","c96db2c8db","fec583f1f2","8f8dfb75ae","70fa8a0b68","f4b08028b8","98ad4cd729","a3fa36e8a8","45045ae10e","a9121f3682","0d69389a2e","f01dddc2bf","63675abafc","aa82d84206","1dfb65cf78","5be7a85b6f","40d5cbf32f","b2eb4607e4","c3bfa5ae96","45704674c6","067dfd6748","eb73abf017","f2c0ca09a0","bb60a85aa3","bf7e200cbf","1857db634e","68131cf231","06df2ca2a2","3c61c85bbb","8b8bdcdfad","c5d2a705c9","5d216d0042","8036d58f90","cc7904281b","c0fb91901c","141711ab8b","6ed5ebba45","29d3f25347","2927784fb1","60f2547f17","f3a6993bdc","67e99cb300","3b5879a0d3","8dce702cc1","ef2dd2a1c8","64cb7b3bb1","22c50db508","1c5391693c","38e510a911","ccaf2c8937","a7c79ffcda","6bc3fbe6fb","1615f3971b","416f75ed99","20a8d09100","b2c61f2e72","e04aea2ed2","1fc0a76d3f","f0ea010473","0f0a4e6b25","740e7ee43d","4ddf72e961","67811163a8","d3c7efe371","83a82cd0be","15d01fbe16","15ae43c284","5b6212278d","d4bdfe2fa0","7c59476ac6","037890dce9","aecd747425","dd2e10099c","66b94ff5ff","d7195123ff","336117c7f8","9919bd4242","3a6aaaa515","be3364c952","6843268437","25387b626b","174916b596","336117c7f8","9919bd4242","3a6aaaa515","be3364c952","6843268437","25387b626b","174916b596","a59e819b2f","be6ddc2988","8a6bc13177","4884f4e8fb","abc75544a4","151068e436","a7281f084b","b5973d0804","ae33319c03","35239388ad","b4252025af","d3fceb8c03","17cabb31ea","43fa2372c3","73c6262562","d55b5fe12b","5100b200f1","85b1875411","c28e2cbd58","ff2b45955f","53565ff742","2072e41c9a","75ee4d7183","dbba3c4f55","f229792c50","af4a5772f7","6498fd3493","c91bbf43be","ec5442fe90","99e6688995","9b0d32b32d","12234353c3","558bd68e51","8b31363115","4d44bc5beb","ec5442fe90","99e6688995","9b0d32b32d","12234353c3","558bd68e51","8b31363115","4d44bc5beb","9ee818fa0a","130d949bb3","6e3bfb72ef","4a937cbe10","0d84748686","dc3088f23d","71f4400bb3","e2c1a3b2ef","a03b3ad1c9","bc4b8ab33f","36ae669a99","fd05a7a9c5","6fc2f740b5","82b4e4f5cf","ec5442fe90","99e6688995","9b0d32b32d","12234353c3","558bd68e51","8b31363115","4d44bc5beb","940aac547f","5920c2df38","a122548892","b5015e379e","6e19aa0ec4","91dcc74112","406013a611","4ec3a2e717","d3e4dc8f77","d454f90af4","512cf49968","6064bf1b55","13f9a52f5c","2140399d99","4ce9a7cbce","bef37cd5dc","230b973d56","a38e3dbfb1","3953fbc640","9bb0ae0863","976dcd4b10","355d8bb8e1","036bfd7e93","a93537707b","0eead285c1","e2650e4faa","1151ed76ee","7d720b146f","7b333dc60f","abaf0e0ffc","58bac4c3f5","c079769c3a","91cb97003f","b6f0a48b04","332ed4c448","f2349c3387","e994535a50","fb439171eb","411ac08cd2","05e4218344","b697635304","10a75f953f","f2349c3387","e994535a50","fb439171eb","411ac08cd2","05e4218344","b697635304","10a75f953f","d43c8c4023","19ca3ee1a1","deee7e8ada","28c2ae1bba","cd483527e2","0a9d7152e6","438af985b1","9dde55353a","5a09cc68c5","5df7922d11","1445a63d49","45b3b41b50","ac1a9016df","7eb45db5ff","2a39f907b2","f9e6dd69df","1639bb9a6e","8054acfe89","da8c0d5ccb","a5aee41893","94fd7eb7df","a7c6e49994","49039af9ac","f27fef1c07","99612e6910","f03dbbe752","be9e020809","f892314b08","4e4207a652","8149dafcbd","0ece2f7f81","3bce1a7432","6432895d73","60cd14d6ab","82d724f323","50953e6e97","3de53e1fff","1daeb5b5d1","9f9fae8771","2e02765370","f2bc5e6e75","19cd481b7c","d19df38ed8","712a6d2eeb","3d25475d13","68bd6bd529","28c6e86f9e","7df546e07a","7dfabc420d","44e6a9ece6","19a907def8","dcf227acab","73bb9d9417","019b3bf5ca","eed371a708","f2997914f0","e0b212f156","74170a1609","74c510b992","c185c55c92","8953dcf409","5f50bccd4c","5f9819484d","e0b212f156","74170a1609","74c510b992","c185c55c92","8953dcf409","5f50bccd4c","5f9819484d","31db7926c0","266fb910ce","71e98731a1","ae3859362c","0e8ab71a0f","f46686d5f8","d5e473a100","05a18daef9","b127d10026","40370b24aa","94cbc60318","f88d259943","2a923d8b66","16daac0ec5","91b0ffee5a","feaeb1f66d","04a4d8f954","33f017b0d6","201588f14f","6d1ebd7f29","0876e828cf","06464ed772","7eaf7f391c","8dc36cb7ca","2748e2f6ab","91507ab98d","9e5cae81c4","7cc1c854de","2df08bd63e","3049e05d6f","4287ab5b9b","e734275512","7b4c1297ac","69287e6ab8","f5420e8c27","a4d2861837","c59d18cf33","b0addcf91f","7993d01d51","c882334053","94731d31b9","177100413f","13f2980b9b","d5a6483633","e50c36969b","03f2cc78b4","70057eb376","439210e12b","cdc776d464","e49d0d9b4b","934deb3d6c","c16cfbd298","052d369497","7608717631","56a4bc987f","4f277d4f26","dcfb31998b","296f8a51ce","802bcc5a6b","b01ed3ac4e","e8a9dbe5b6","7384876641","974dff7068","dcfb31998b","296f8a51ce","802bcc5a6b","b01ed3ac4e","e8a9dbe5b6","7384876641","974dff7068","755d601147","0488bbc303","1de70c883e","91b8cb3389","38a189ca9e","d2281ff57e","8dff7bf9fa","4f2e597c89","43d1aa51cb","2ce678c110","588408bb02","036e211cfa","668226e147","007665b86c","e4d2fd90bc","6880096887","0d091c99cf","804ac2b9cd","dfe6c0ec7a","e0d5e737a3","96a64809d3","3e8b696b82","afeaf37a6f","845d6d06e8","d6a87af196","7d4d32074f","bdd973d361","3c37a44301","c50d3f8f7c","0e8d7801e6","f953a369be","5bb4a4d28c","6d62d2b104","87b697bc50","883c625e94","f0370363f1","b1ca3b6022","7a32f1f2cb","a14b410aed","5aad4632c4","73a4ff197a","b8ceed310f","47264f82ac","1ca1ca83ca","7017e6ce06","2eeb556f47","ca51bc6c98","9332b59ca2","193065566b","b70e11ec9d","26573fc9c7","f77934b349","31c4d0dcf0","96e26ba3fd","003e193231","ac801bfad2","377fd3386e","4a2b6e3795","8e57e0eb30","1659d1a775","30e1694d5d","3b964ed2af","3fef6ce8e2","377fd3386e","4a2b6e3795","8e57e0eb30","1659d1a775","30e1694d5d","3b964ed2af","3fef6ce8e2","0f509723af","85e52a8ced","51d2624a89","7af59d5657","3fd470fe5d","e831d94310","994268f9e7","d15140fe9c","b83638ce0a","d6f9e5db02","233d3a8882","bb2f3326d4","2007cdd78e","51f84809c6","3124e6a8df","ac53ff3f66","fa705f8299","f96640cc4e","8f55ae97d6","03117e0d37","54c304d93d","e1a56c1f79","e5182023dd","f0e3f421b1","4535c67c4e","5d9654e6a1","8252c151cd","9b6269e1dd","94fee45fe1","3c4acb293d","0c7b10d51c","cccc7f36ac","08f2b80ffa","bb67f17900","b4f45834c0","3bf3ad83d0","5e57f9794d","1642abcf97","9af8ba14ba","cba6374876","ce0e8bfdfa","c45f07dc5a","c53cd7dc11","95d5485c56","4e7900a4e5","bc8a289d12","e21794fdeb","b54051aa69","51a1eb5c89","51324f7e08","44bab5a2fe","4664269f98","7783e4f1f5","12a1bfebd3","f38bbdc363","1f72c3eb51","089dca184c","0abf84c109","ef18d54804","9b97583619","15fc7749a9","1952e3de27","c6efbb67ba","089dca184c","0abf84c109","ef18d54804","9b97583619","15fc7749a9","1952e3de27","c6efbb67ba","bdc4497d0c","dd6198092e","1b43b83f68","c5ea46c5d3","d632ed2e31","b0639f2014","6d8ee0994d","da02d5556d","003aa68026","4194e25f98","a2808be069","9015635290","2cdb830c95","7b579bc4b3","af6f7ac7f8","02315866e9","4192b7d6d4","afc8f6daba","e4b09a81d9","bdc6772cac","2b854f5cc6","adf04d6d6f","b199798e50","3533a81ee7","a6bc6d7af6","6201822594","c82f735fe3","40d2590bcf","adf04d6d6f","b199798e50","3533a81ee7","a6bc6d7af6","6201822594","c82f735fe3","40d2590bcf","fe2a2fb0cd","153f888f25","976b6d41e5","81fb49dd76","5b214d57f8","a37cb0b658","de3581a529","260249e64b","651f4c52c3","490391ada4","a6333bd102","6af53a4be6","c71702cd3f","4568cee598","8539a94a32","6ae2949905","8662d6ea37","026bd6d409","6865190b8a","023a701e47","50df4a5f2d","9a3898f766","e951c55850","2b8bac252c","61d1a4ac85","b4e3181e8d","921ed030c5","7c7a2ee239","8fbc097188","07133f6389","f7af860a60","6996b78526","b495e19e1f","33d8b2f3cd","b181b27cdd","8fbc097188","07133f6389","f7af860a60","6996b78526","b495e19e1f","33d8b2f3cd","b181b27cdd","0e4e123c76","fbbe38f4a7","6033a7c327","34cbec9c32","fb764ebd94","d6222ece18","ea778007ae","b6799058aa","74cfff0049","4f4e522f75","8507f45c49","d9312dc66b","f1396105c5","c525570de8","f715d3a771","c7bd2d71aa","cd35ef8e90","4b4ba2410d","704ff480fd","d13554fc61","8df1005acd","9844910d59","9e664ba367","db36f3a169","15df5134f6","e41c67a552","6a07ad1ee8","f4586af23f","c819179ab4","0cfaa4846f","32a7ceaeca","3d22ccd108","479d128e79","f314780c7d","a7796e3bc7","83eb6c8a3a","b4c9ee3780","e484341fcd","a6dcdf3dd0","94fefd78c7","07fbcdbc97","e2e471f3ef","47684bf7bb","58a157d0b5","6d237b31aa","fb24371351","2274427917","2d9dd6029a","6dea680c22","886d9f2bc2","a31ea8d86d","8dd5894dc8","b694d8d76c","68101ca540","887f78e3dc","87c4671553","aa197e0c47","9be66ada84","5266b9a385","8778aaa4bd","83af4e1e94","ab6b5a0bcf","7228a24ed4","47684bf7bb","58a157d0b5","6d237b31aa","fb24371351","2274427917","2d9dd6029a","6dea680c22","7c1eaf7c41","dfa66cc9ff","96023dffb7","f740223a45","31bb9777ed","07746bab56","d52f9bc161","a8e5dec7d5","a3fc6f7fc7","918a364329","c9560ec8f4","48d9aac8a0","70a625ba0c","29b3b2b756","b9e584d6c7","c55e6000ee","a26c19e466","82b73d5bb2","4770822f53","ce7ec33855","1e1ad965dc","b9e584d6c7","c55e6000ee","a26c19e466","82b73d5bb2","4770822f53","ce7ec33855","1e1ad965dc","5e167ecdb7","50a9ce3835","beb419a7d1","48566b56ef","40938f90ee","4cf44cbbaf","479688bfb6","6ed88d0e3f","44a017047a","9d44a4f859","7a0428c1ce","9736f2175d","dcf3479f40","4cd67dd0be","25a5c689a7","73bea5bd25","36f771019a","ba2d5a1770","02c07bb257","46b75557e5","ab78327f31","2403c35784","d72e92ec61","f234db5ef2","9fa98afdc4","bc6fe4b851","5391b73960","0056aaa864","996232645b","3491323419","aa00abed6a","6c628c6f89","666f2503bd","5499912d67","1cb87e8cb8","55f9277f81","50af1985ef","b0a6ef90eb","4b9a40e40b","b62b06b9f6","9fd0fb750b","078a6daa69","6604c91299","6bf897fe04","1b7e7a928f","7fa4178767","e2f4977cb6","6b83b973a0","0159ca7cf1","a1a3610a91","513d786c2c","7079910252","87cd25a52c","5a01dcc656","7a925d8900","30ec11cc33","162a997664","b358b45dd4","b1b603c6d0","f25fca9ff0","c815e4e9b7","dcb060c8e6","0b7634c5f8","912dbe546a","3e26d5126a","76c6c0e731","1a5bcff038","5dff1464e3","4cd2c25b67","52bcf68830","912dbe546a","3e26d5126a","76c6c0e731","1a5bcff038","5dff1464e3","4cd2c25b67","52bcf68830","c14e32ce25","265d9b99c7","476087f791","a89d570ef6","9ed7e11d59","1f0d6ebc04","4d80ababc6","691d86004e","febc493194","9643e7ad95","104dbed828","0a79fe0f2e","880605a031","faa5948b3c","adcfc0e9b5","b195bd3279","d23da64f56","bf2d950ae0","a8532a638e","c1bbe4277e","ac6684185e","230ee64541","834a57d472","6408dc36e9","f65ce3e049","60b91145d9","3a90c33a11","232baeb663","25a5c689a7","73bea5bd25","36f771019a","ba2d5a1770","02c07bb257","46b75557e5","ab78327f31","487fc04f92","59dc20cfd7","d3c149a6cb","ea83560da1","f62f2a9285","202cad08f2","22347c3a2c","a6bb3ea4e3","0f92293859","6b3e561ead","983eeaddcb","c4425aa2d2","2591d8a2c3","d1f8e9c0d8","f7cc6456cc","2c2a8a4b19","ea8bbf89f3","74a89849d1","de6296d822","8bc5ef7cee","4379d82609","41aec7135e","ea9c355bf1","22e2d496f4","b06680fd62","4efd1be688","af396b0182","53de4b835b","5174897213","3f9ab647ad","2718b84bee","76eac26ea3","26e5ed48b9","dd287e3154","2387fb4ed7","d7865854b5","c723a33d22","67f3227c75","dc313c0d49","43b79d4a8d","144b08f6cb","2a012faa02","95f76c7a9b","0575c55dd8","849729e61f","8511cd4cce","a2538b1353","4edcbff160","4685659dfc","95f76c7a9b","0575c55dd8","849729e61f","8511cd4cce","a2538b1353","4edcbff160","4685659dfc","455a030b24","108ec9e199","d5d7c8435e","6990345129","aad4b065d4","6ac7428f11","5018597c43","697597cd4b","90595abb82","174ededf14","f0f734a479","39134c8139","ce6f14e974","675cb22468","60ce2246fd","8cce38abc4","749a5850d6","284c9dc194","fa9abcbb3f","be29d0485d","ace92381d9","60ce2246fd","8cce38abc4","749a5850d6","284c9dc194","fa9abcbb3f","be29d0485d","ace92381d9","be593de6d2","ffed4200e4","62d19a4290","4e2998f105","2020ba8f0c","95ecee763f","a2b78dbfb6","fb3fa665f9","d8336a2062","509063f314","cf15eeb7f9","6f3dd51b49","8adb6156ef","fb095a34c5","e438da232e","a54a9b89f6","14dd2130a4","4c6aa605d7","b1d8b43aa1","499668307a","6a30b7311d","e7dcd7dc1d","a964700d01","3567b80acd","897e7893ed","3b5378404d","a6524d6cc2","118eb9be63","8f3387319d","a7c15eba8f","91c7fc9f6c","a80b58be29","d4b486c128","9069929f16","995707456e","c2de7ffb2c","0bed05bd56","523a293016","e65a5e9fd4","7b366b0316","f676190935","e6fdd5ed36","52513afa65","6db0edc232","9ffe6025e1","62e5837cff","49c4a5616a","d269c1e6d0","d1af28dde2","f378bf32b6","a5bd28db4e","217902791f","82c0224bdb","08a778ca1d","4046e3e1b8","6bdb8d7e19","4663e2eb09","e7c5766e5d","d5f87d325f","7404270530","7046d6be92","39dbc545a4","b554fb8cdc","614ce15da7","5b5ab392cd","bb13bc4000","b5a3685ef2","2032242a9c","269dd83a90","fc82e2be95","ea6cb4e57b","0523e72e87","af1d3c02e2","69f9aa6ca4","212a351449","1446b842ed","1decc7c752","857612cd2e","52ba95a62b","f8ee0b52aa","7a2803a5d2","a791e5939f","3f17c4494a","90769319c4","065247931d","8554618ed1","6b75181f53","f6dbcbb228","55e8d75007","1e7722b427","8f3f63f72c","065247931d","8554618ed1","6b75181f53","f6dbcbb228","55e8d75007","1e7722b427","8f3f63f72c","ad0e56023c","7c1d9f3763","2b50007de3","4bc5cc2774","5da0783323","5fec5ef9eb","5483dbfa2c","2111afae7a","11b874a4b5","871986a2bc","3fce471054","2700a21056","c5096c0ce7","85ffeb5c88","904dbf8da4","b34fc0693c","8563075d3c","ba71d7a4b5","c857c5ef35","177a484572","6ce557f470","5899d5ec5d","fea5ea5eb6","706e960aab","1803aa9524","d5fbf2dadf","5d490b4a67","0a775585e5","5b314404e0","94655c5807","6e00f71d52","b5b3add7a2","9483e6207b","8e2cec4590","6bfdc21d53","8a4a2774c2","84b054ac25","4a434c591e","942f6c4692","f4f908ed09","3d45cea211","c8b7133649","c70fd0d47b","184d711706","e5f12726b9","b0e64c1319","08e046a754","58b70911de","e5725d333a","d6d9cb1509","630899ef14","a9ebc0aad1","cadfab3d2a","900fb6d01e","e6cc7b96d3","a59b46a3fa","f0f82bb8a8","2c184c56ec","e4d782d4b8","9f6f050663","1f9c2c35a0","3ec9fb9a75","b5353d957e","fcb11fe126","1a07b17657","f76111e084","af3fb8119e","e8500a5a6e","50ef01d867","75f817c20b","a25ee1188b","1d1f3cbf07","28dff48492","6523264de8","08edb1238f","ad63b50704","109eeaf2cd","a25ee1188b","1d1f3cbf07","28dff48492","6523264de8","08edb1238f","ad63b50704","109eeaf2cd","e23d57fee3","c558f753b3","049b35a454","19056752a8","079a590dea","371c668b79","90445a5afe","849e87fe76","1276f7dcb2","c8fae04e85","a7833fd152","c8e58634b9","d61d015100","c763d32ebb","b37026f26c","4d87c6d00e","f16dfa34c7","79a0fd51eb","8f807a5965","71b84e8aa6","04c8f2e5b6","ea2ec62348","ed523a572e","d3d16d6f0d","bcda504fab","b4f61b444c","ef925ac8a9","6f1af044ed","1084c7d997","73e187d576","4da217f8ea","21bc158626","500a928de0","ea6e0b8be2","d8127401bf","08fb6d9696","5d469a474b","f2a8e43b94","7021151c49","709daa74de","c8f9230131","8d795b1c5d","43764c6af3","0ffb462d5b","228cb6d7d4","38cafb5d46","d4cc247016","80de92d5f5","99ce2868c0","bb30987d5d","457a3d0c38","3b298eff68","5cc2f3580d","febbf088eb","795907c9d7","6fbd6d3385","4f2325ad87","be6cd373f7","7569062523","a1121f0c0e","ea11893624","10d186dd10","e36c6f41e0","4f2325ad87","be6cd373f7","7569062523","a1121f0c0e","ea11893624","10d186dd10","e36c6f41e0","088ff01e0b","a52e35ff4a","7068fb8acc","bf6bba67f1","abc9b9ad51","f3dd8325b4","610cccce76","b836540ae6","2429dee1e7","389bd88577","98228c2d60","b65c6b09f0","e87fcb9a50","a0e1dfe5f3","cf2b1b5eb1","ac13fc36f1","53da0747e6","5876813aec","62e66849df","4d14c48a0e","2b1d767abc","85d7aa77d1","088b05cfd6","cd3bffa062","a64e30e674","b281547436","23d8eba082","5a6d8d0e45","cd94015b01","8396ded718","b4ceca7471","4e566b8bab","537a794c5a","7816814d29","946f8b309e","68161fb76c","5c1172c661","e6b5a9f473","0ecde95d6d","0774077d99","e9893638f4","45b6e542ba","b76e4893c8","f2eb6f10cb","0967394dba","7c5b44b260","afd0812e67","a5cc1678cb","e7ce30392d","4f29566a65","c1bb9b1b36","2c23833296","888ef8dd67","eb1c674fb1","576163a7db","43396e0c9f","79fe6d9d7e","f522e98209","95eb2acb6b","fbd792365a","87f6f768bf","5ab7e75686","a2decccf65","3abb9ee574","abe3ff2671","d897c59341","4dabc3cff7","490158b5b0","044e863cf3","379d94c58d","e61c1d3728","b641680b72","bc467e34e6","ce69f9d358","e2089e2936","aa01d8eab0","8f58423fce","24811ea1a0","b7c415d6e7","9c7a07b63d","30e53f7779","54ac8c40ef","0423002770","9fd845b097","17d1b75e25","7657dbdd63","2bdaf6c4b0","9de20306de","863d6004f2","4034c2edbe","9adf25b51d","ceaae16397","d575d5d81c","971c3fa3a1","095bdfc5b7","0cb435030c","31cac0c772","fadf395bff","cc1720d328","71e42ea89b","fb687c0568","e6eac7a101","9bb9f07b07","932b4fdb0e","5501b28428","85d7aa77d1","088b05cfd6","cd3bffa062","a64e30e674","b281547436","23d8eba082","5a6d8d0e45","4305fbac5f","2c8001ab17","5a5327a540","34d3cf90bf","273b567b8b","c7074674a6","175f127054","17d1b75e25","7657dbdd63","2bdaf6c4b0","9de20306de","863d6004f2","4034c2edbe","9adf25b51d","11237fae54","bde7f5955e","e877c6a2e9","e3cc5b0358","5b3412ab1b","b531da143a","5eee82612d","b73bedf2ad","7cd47833b1","9807b484fe","5a80298791","40843fc851","1b25b5e6be","fd7f30b2ab","b73bedf2ad","7cd47833b1","9807b484fe","5a80298791","40843fc851","1b25b5e6be","fd7f30b2ab","7cbecebdb9","0791f76a9a","8efb4f4621","bcb86caa72","bfad0989db","a7df98c0ea","4e7972d60d","26bdf76fc6","9a17545462","dae6ec9b28","d5c66ad347","89eb627c12","feb56bcbc4","48ddec35c0","d85eb0554e","80c014fa73","b60fdba32e","533aec1809","9c63a9a973","7c2fa789bb","d128eb5dcd","9d9905a712","acb3fc4373","ce315f3111","d90353781a","66ace56d17","be2a764fbc","9c173ce074","d85eb0554e","80c014fa73","b60fdba32e","533aec1809","9c63a9a973","7c2fa789bb","d128eb5dcd","3553f04a63","b94e130ac6","2bb4200015","050e1e02ec","70e42803c6","7c13d29373","1bee93f7dc","504bf9fcff","beecd661ee","0c1ca16f7a","208c17e267","6d4a166c82","9de4d1726e","a96220993c","f1594b344c","d903e6e272","086d05c383","00d51444ca","232a679145","8278ea6079","2e0d2d6460","bdc2523f1e","3ac168f424","ee7e9eea39","a7e275143d","ba7e7cdf3a","f8e7e14499","2fea68390e","0fef4661d2","a210674f65","d4630b9186","97484d63de","ab44377d34","486bf95257","c15318c6fe","02a53e2c75","dc6d84307d","1828e5a734","2be4d42349","dba1c124cc","f6af9ee93b","9a66ed6aa4","7cbecebdb9","0791f76a9a","8efb4f4621","bcb86caa72","bfad0989db","a7df98c0ea","4e7972d60d","9ac8fb26c6","978e85f4b9","11f03b931c","af6018315d","b140c58b4f","19b5e99878","9b03c9276d","a94a17c0cb","ff8200417a","3f2bf268ee","7aa5945032","8df9e77b9e","c22547e668","08fd864d8c","f57d279592","7a70fd753c","d68e630815","7ca4c4285c","8e58b91a6f","ae239e688c","1aaba87730","b59d1d984e","aad1632d6e","7ca990604c","2ff1f53b53","81b12175cf","31ea2eaab6","fa2748fb17","37c6c6fa8e","f3cbabdf17","883e1350a5","708994b8bd","836b1422cc","07629c6beb","3970f8fe29","37c6c6fa8e","f3cbabdf17","883e1350a5","708994b8bd","836b1422cc","07629c6beb","3970f8fe29","30f13af533","1943023e4f","533e4a3db6","42b2b574e0","ac68e130ac","ed41e690e0","7112a8dfb0","40f9ad01b9","b94fc46f23","c056445cc8","5e48c842ce","1457a3afc9","2673de504b","95e44373da","40f9ad01b9","b94fc46f23","c056445cc8","5e48c842ce","1457a3afc9","2673de504b","95e44373da","d55e6429ab","5d1abd407f","e634fbc593","65b67c59af","ef7d60ca3b","316579a0e5","f8c62237f7","8438af7eb1","4464d21ef5","8f279f2233","50b0648661","fb8fcf73dc","ba9fe7f8a4","c6ce0d77c2","8438af7eb1","4464d21ef5","8f279f2233","50b0648661","fb8fcf73dc","ba9fe7f8a4","c6ce0d77c2","421542260a","204116d158","27ab453730","1383854171","5d1e14278a","7b81b740af","94b9098090","ce93c4697d","77da2f0ba7","bd43818e73","4ce5340b3e","3f885afbe8","f93ce4defc","c05a056c50","cc8de7db12","9ffdbbdd5f","8abbc791af","8e3b775861","8b72e5b498","3dc5b55e54","9c65c2a8ab","cc8de7db12","9ffdbbdd5f","8abbc791af","8e3b775861","8b72e5b498","3dc5b55e54","9c65c2a8ab","2f93978c86","f46dcdfa09","41727e6b10","b7c9c8d6fa","983fc59954","ec1ec767f2","e295ca7e30","28ae5ab3d2","7b57856c3a","9943029683","9993f712f0","fb05ceaf2c","17290a07ba","48fc7fa051","077cb84f66","2a04281726","33e4b05836","32c386955f","560ab8272e","1b49a2c40f","8b6d99f392","89f48aa554","e8a37d33de","c6a4e2f53e","47856734e3","247530e7c5","bea1666ba8","e9c4c690f1","77c0b09d8c","073984f316","bfa6cc6da9","90086ee8c1","001d396e46","ac1d65bd5e","b805d10df5","bc73a20368","b47914fd64","fe9f45c928","7d372df41d","0f179fcc60","b4f5db904a","54753317d2","077cb84f66","2a04281726","33e4b05836","32c386955f","560ab8272e","1b49a2c40f","8b6d99f392","077cb84f66","2a04281726","33e4b05836","32c386955f","560ab8272e","1b49a2c40f","8b6d99f392","41a258fbf1","dd128afc68","fe1bce86dd","677cba8e01","91d9559d9c","7c5bed401e","2d22af77f3","3e18857d24","f21c99ccad","858cef698e","c23817c76d","c176c561ea","b6121574b3","c248458de2","bffa578dbf","2ba0ea5967","5247c26b6a","b44cab319f","e3559bad0f","7e42651a28","a6bd1d394c","d528e8ffde","d62839818e","d1574a6af8","b6c59a2b0c","82aaf1251d","206a9242ce","964c235225","ab965d353c","8afd1bb279","6d9ba0ab21","be103c9bef","5ce8ede7a1","a142f19cc3","c1524b10d3","9be705425b","513d35b01b","861aaaea90","432ae34e39","79468d3765","ba8e4d5a8f","108cbf0360","41a258fbf1","dd128afc68","fe1bce86dd","677cba8e01","91d9559d9c","7c5bed401e","2d22af77f3","836736067d","81cd0e0f83","1f44ea218f","587fe7bcf1","d997b41a3d","8e8a1908ad","9323b8d6d6","1199887aca","d903af635e","fa71b551d0","0d9f7c393f","6fd8d03c4d","4c75adb5e3","4e9ae3076a","b0993577d3","6fc8ce5cc6","ccc974b2ca","c3033d217e","77e4d635c4","10ead02180","857a80220c","38d733ff73","d1341722eb","10fd81f6e2","448f9049bc","45a569b969","009f0550d8","5d7ee01012","f6d863c1a8","89d2e6dcc8","65f45350e8","fe13741d22","b11285fc65","8f80aa7962","a6d9e81de0","40f0eff7da","e887e3434f","f584e4abcc","102fd54375","4fd3f47777","c8e9de6764","65f817aaa6","40f0eff7da","e887e3434f","f584e4abcc","102fd54375","4fd3f47777","c8e9de6764","65f817aaa6","87fed5855e","e505410f59","de8609da59","ccfabba7e4","f3bb2c7ce1","311932d36e","e8276516fe","c64aedd495","dc020669a3","851a6e399b","ff10885e7a","bfd80e3555","8ef1fa27b8","e5eca31462","79e51f2ec2","1dbb756fd9","8d2f9803f9","09257fe441","3bbef2837a","3baeb6d9c1","6dc1d33da6","d8a1fed4cd","e1269e7fa0","f2687368eb","e51ee265c5","e3d3bddaa9","7e40faee14","c125b38b90","1018c8d3c0","0abfa704d8","6d59250f4d","334caa377f","207c098c68","ef9551ae72","8f0a4d1440","47ce7a1b01","6c8d35206c","9e4c89d5a9","a1175ac25e","07629f2380","6bb413296a","88fd496484","47ce7a1b01","6c8d35206c","9e4c89d5a9","a1175ac25e","07629f2380","6bb413296a","88fd496484","3fa09cba1a","209d35e918","f00a171f0c","d67d970ae9","c615d1c44c","8104994bb9","4b67f91b38","7ab6d1816e","1bd6b62022","3c046cd859","c43df17166","0286bbcfce","f323190cb4","c899d7ea4f","7ab6d1816e","1bd6b62022","3c046cd859","c43df17166","0286bbcfce","f323190cb4","c899d7ea4f","6354f76916","8be63f8f50","498c258652","72a4e1d833","454bf58d0b","874f0a612d","e4341b5188","79ebe9e5e8","0c26173d3c","3d8b5dd6b5","595bb33264","052ad73db5","ed9a6616c0","645c6a2c11","b6151202fe","6740200559","0040c31901","24ddcbaa13","e06cb119bf","5ae267f450","cb8a48dfc2","0c35bb06ac","d222df1c78","97febc2874","efcab120e3","ae8936ef00","289f8cc0b4","71ef1b55b0","ae0f45222e","fdb8edad02","0584f80096","3c6952934c","8dc65208be","ed8ea0c3dc","87986280b4","274297a49a","a216601f1c","264ecdbabe","c108ec61e1","182e0abb6f","72027908de","415fb09418","558327898d","a22546b57a","8de830624a","32e4af6ec7","23a2aeb1ed","4a141ef911","01f1f6f183","c48171e172","c888538451","58dc6dba70","bc8d3c8e4b","b8fcfe23ff","4cd90bba06","0a00eef0ba","0c35bb06ac","d222df1c78","97febc2874","efcab120e3","ae8936ef00","289f8cc0b4","71ef1b55b0","17e9c3ebd3","95c8e35c4a","883d91a3b4","87e6a8f602","f108c5d830","bc869ca2ad","6f7cdb193f","8bfb74a3fb","af647000a9","4b4eb6d584","483d16881b","73aa0e6567","320c7edc9c","bb9152fd94","5ff0b6f1b1","e73c587efd","b4f611aab0","05fc05a0cd","38092b5a22","461f420e2b","58dae31d19","92387c6e81","befe9e2d94","b25e088446","0ee7c17e88","9ac81cfd49","cac76388be","0ea9f64bbf","d17969bd3f","839800c017","0289b93358","65395d61c0","11bcb711c4","96a9a4183f","052bca01e6","d17969bd3f","839800c017","0289b93358","65395d61c0","11bcb711c4","96a9a4183f","052bca01e6","fe395b0684","99aa498259","7caa753d6c","cd58f8fe46","8939984334","4d453329d6","2e2a272438","da60624e11","64babe530f","9cfb73eda3","3050b8bbbb","395a93a587","4edf0ff958","76f1682018","2e6b402af4","1a7d1331ae","ae5a7e6f0d","6a67b28da8","fd3f07e9be","a80d5db27f","0488ace835","3dc7681399","4ea08241b2","55a6c53270","f3f2fd0a02","567b270a5b","eb0ced214f","7274622f4e","37d9b3c9aa","7968b2d8df","7ffaeb6637","a31344991a","990b2b176e","9e08434630","4f00e9f481","355de17c3e","1add01d44b","a824917337","c9b33b8fa1","cadc636911","cc028f5371","3bccf9ef22","67bb83b4f8","b4defddd54","73dd4a72ba","99eebde824","a59cb58507","86e9375776","efb6c94dfe","4a97c561ec","38dc82555e","88ac89e873","e0819e42d2","0820ebc97b","da30e91036","aab368e926","5fab3d6448","405a402c58","c14b38cb6d","e7b330c6dd","4e4c620594","f46c2f7268","003a60280d","8e156aa182","41514c704f","fb3d55f485","c67f583ef1","c7473957f4","c0c0be0cfd","0dfc4a85b8","c8496f9af5","3faa350a02","93d2570e88","ebaa5c2f04","46a4e8574a","e26509fb1e","f396de16a7","2a73c81e6e","284a306dee","d2995b2fb9","7b1861c32d","a266125457","2a1850c68f","1ee90771a3","a86c8191c2","730dca2f1c","31a39f9c19","3cc6634f5b","63df127f88","88285d09ee","dcfd05e2cb","7e1ef7b098","a87df16587","48450a6e1c","0758e6bf66","b095870a5d","2defbb4abd","9dbbe2b51b","f4740af6e9","56c664c57c","863bb1abf5","ff184df0bc","1ff10939cc","05088ddce2","5d827cd3b0","7021ff56cc","4321c786b7","490fa66ec0","c168d7149e","ee8ba9a74e","6554139c75","c66c53a7ff","7021ff56cc","4321c786b7","490fa66ec0","c168d7149e","ee8ba9a74e","6554139c75","c66c53a7ff","a8c083bb65","54ae3c8f2f","6a929fa89e","3edbc57738","40cc2f3ffa","c1bc2689aa","1336a210fb","6b195b7e50","836287fd08","a75f1a14c2","cac941a468","563c751155","e975f8377e","902900298b","91bda3b5a3","d03829bcde","c0f2474355","0b871953ca","445980f2aa","d61af34d8b","1adcbd61a3","a30023b09f","890726e940","f4f9a575aa","162f7c4822","61e9101e20","dc68094492","5959d84215","28ac7af6d0","716febdf21","a1c959f79c","1e625bd897","a824472be2","110aa1e351","dba0ea4c03","66c0afd594","1449ff8403","d3afa3b128","35196d5989","2102bf91ac","942ef23bad","357cfe8ac4","1dfeae955d","2974fe29d8","6afbae1956","d5876432ae","be1113c111","b09750c2c4","6aed5d43be","5ada466993","d899693217","02f7464667","d4069e3dba","cc9887063c","483a3cb1cf","3b39e480a3","28ac7af6d0","716febdf21","a1c959f79c","1e625bd897","a824472be2","110aa1e351","dba0ea4c03","12595bb71c","26674d0759","63d27cba99","ad6dd2cd60","77874d3684","5884bd3bfb","21b8f41961","9f93f86364","0f4f5696e9","568e31f333","e9c1104d40","8004561767","52764f3c64","4405ca7e7b","6329780696","565e360295","f9bf64944f","454b1c1ad1","c75dd6775c","5606a5b6c3","86252b8594","6a1c1e65d2","efcccc9a87","7133d7214c","47473cc73f","59a04c3715","b7e7379889","a049116625","7432d189f4","2237777f39","13af31d0e3","af5aceb5ba","b4b6b396d0","7f0d4877a8","b3645e3ffc","12595bb71c","26674d0759","63d27cba99","ad6dd2cd60","77874d3684","5884bd3bfb","21b8f41961","24ca286879","fa308148db","6f66726716","f0616c70f6","58bfd56ca7","7f4a470582","8cf6cc8f4f","24ca286879","fa308148db","6f66726716","f0616c70f6","58bfd56ca7","7f4a470582","8cf6cc8f4f","682b5ebe6e","87992b0a4b","78bb6d69c4","5a6c518c8e","509c1dc574","f38c44e0db","75bb93eb91","3f1019d5a6","721eeb950b","f159160fb9","177c19e820","d2177b1933","13005b4a00","96974f6140","815b6288d0","fbf1c41e75","70cbd8cce7","b9e74f44eb","d8568f10b8","22a3b10ba0","adda17050a","815b6288d0","fbf1c41e75","70cbd8cce7","b9e74f44eb","d8568f10b8","22a3b10ba0","adda17050a","dea826ed87","4166aacdef","f4a8c1fc13","8b6fa2c9e7","15f34ab2f8","9af952a865","d6f94f0e0a","5748d1b1f9","5fa66d8146","1ddadacd8a","491f96e571","4bf98ef00e","6ebd5d7a08","d8cc4e794e","5748d1b1f9","5fa66d8146","1ddadacd8a","491f96e571","4bf98ef00e","6ebd5d7a08","d8cc4e794e","43191faf54","4597e72e41","5f02dc825a","6ef5ba3980","4d085a1d7d","45168407ad","b701193d76","5748d1b1f9","5fa66d8146","1ddadacd8a","491f96e571","4bf98ef00e","6ebd5d7a08","d8cc4e794e","1b3ee9658c","20c2b2cc75","53883022fe","5e905c5e28","ee6eb69751","538887bbb1","65ee0832cb","1b3ee9658c","20c2b2cc75","53883022fe","5e905c5e28","ee6eb69751","538887bbb1","65ee0832cb","12356f7443","42e6dd554b","e49a32d394","bfcf9bc65f","2344fbb668","c846f673a6","f6b61ff248","587e667ec7","6c6070f525","09dc129b5d","a940d1daa4","8f2e5768b2","e5ae995497","52a372515c","1606c4c521","4637868fa4","3cb428988c","2b5a1b9a07","d552d544a8","1a73161717","2a449bacf8","09459c99cf","b342d72da7","b456ba9647","35a29c2618","e110e9046b","1532e4039e","702c49c0d5","1c5292c158","92de8fc145","4d4ad23b3a","9f51fcc79d","49e6839aef","4cf760595f","acdd27d6e9","1c5292c158","92de8fc145","4d4ad23b3a","9f51fcc79d","49e6839aef","4cf760595f","acdd27d6e9","89575fad8f","c1f1d5d785","05d0d8760a","f7737e18b0","112c355f5f","c1510d2954","bc64332c97","1ef25a4d8a","44af0178e7","250243aea2","6185d6a7dc","09d06772aa","7d0b3b9c19","bfcb1b8723","1ef25a4d8a","44af0178e7","250243aea2","6185d6a7dc","09d06772aa","7d0b3b9c19","bfcb1b8723","52bff2fc77","a8c97ca6f7","4023de5a71","c8dc6a151d","35e0204b60","9aca230557","29d6975e40","52bff2fc77","a8c97ca6f7","4023de5a71","c8dc6a151d","35e0204b60","9aca230557","29d6975e40","542febf300","17edae8ffa","5088c8579b","72a61c7399","0fdf0459d5","53d8cf5c5f","fe11411674","51e8483ea2","871a828d53","2cefac9319","41db4f57c2","6e139a672e","8dc79d0fd0","1a6820d7d9","a4acf1bbb2","dc26370198","dfbc1dee5f","4013cdb2b8","fa8b3edbec","482880d4bc","5aa4212390","487864eb82","ee6b93611b","a633a697e9","7ac0a3660f","16e9293b7d","a4db78cdd0","18b86ce18d","5e329395c2","94b7293573","3b108b73f6","88008fc4df","e57c0ed942","88252bfbbb","4f0f4fea40","cb57055f24","8d50bae8c2","bcee44a676","d20c515a2c","f5549a2597","cfad9a1a76","f90d359c70","5575ee74f9","f38e871553","46545b6c12","4e353b5cad","9747eb74a7","2ea998d261","835a331c56","c055e6b522","1fb48fa089","47c3d84380","ef0b62c5b2","9a87eb9b27","f01ef9e13c","d3e7bf6b87","cb57055f24","8d50bae8c2","bcee44a676","d20c515a2c","f5549a2597","cfad9a1a76","f90d359c70","cb57055f24","8d50bae8c2","bcee44a676","d20c515a2c","f5549a2597","cfad9a1a76","f90d359c70","f26714fb81","248f209386","6813446a69","cc0e3fe064","98f2253f96","84c403f41e","734c669ae5","a15ceaea07","ab12c242da","d87afe4d88","74384ec66b","37cad7dcf1","90ee115ed9","cb8e4d1868","72651c3d8c","610cd8d4d1","8af47f4d4c","82612b5463","aa66df2643","3191e80c7c","db4d7a469b","3ad248e19d","15f79b31c7","52d56ef983","ef9c181808","bd52250767","73ee472c34","1e0bc14db8","2adf5622d5","bef05bea2c","6904eded7b","ad66037dca","2d327462e4","9b0631f74e","fe917eb73b","5c116ac67c","7192451d8f","674ed7c53b","56ea317519","f8057ffa3d","786e6b8fb5","ebf27f042b","a76e6c1e75","7d1fbab58d","5c76b05806","d12b0ddddf","29626b9df2","623e384c4a","946abbc2da","0197e53ca9","9135b9c229","b6215a6204","c7297568b4","d1150f155d","f614c9c85e","b3ae8c2c04","547fcca42c","c493c65117","8f8ba0e358","764d166ca2","d3e3cdb1db","c81fb3c224","367a6fd317","f26714fb81","248f209386","6813446a69","cc0e3fe064","98f2253f96","84c403f41e","734c669ae5","7a2e964e68","d0345862a2","9da14e8d38","f9322da2ca","b8d17e1229","433eb06c56","74e8616763","538d77acc1","f5ad698f7b","9619245e7d","38602374e3","3f13ea71d5","f917c53f4b","552219dea2","82123eedcf","5e48fc6d96","ebd1018059","18ff080e31","287a136411","ea13ff0710","0679b55fd0","224bd2b927","f8cd0ff3ea","ad37b3f67e","f58a49a2a5","e88c611241","61e623517b","c268636c8b","8da6109589","10ccfdd3f6","29cccaa282","7d8dd35021","89c4832d59","582ddcd3a6","9d539c8242","7fb8a61737","a69f20dea2","382dee2bce","de27c572d5","8ac5b9af20","d8c22c231c","1986c21796","e050abdd2c","7275d19992","00c7d226b1","dc0f147e04","be79f27e9e","09dfa8726a","630da67496","98fd386930","f18a7eb4fe","a8c3979c04","df8a930c9e","28afb78240","bff8d515cb","da77abbafc","13e70b0b0d","b62bef5380","ac8057e4b6","4733bde1e0","6033664ced","e107d37c78","6af98b27bd","766297573d","39f1d126d6","3f6c3a736b","59ffbfac9c","1d6edead73","b731f21a6d","90e6873bd2","766297573d","39f1d126d6","3f6c3a736b","59ffbfac9c","1d6edead73","b731f21a6d","90e6873bd2","5c22c5eb2a","e3a330da0e","4779e0a3c1","632c62c1ec","6365d46801","2de0cee836","f5ccbf18ee","db49ed84d1","27cd72fdfa","47d1a61034","f0a0870b4b","d105642330","a085138321","5295f4829f","756e32b43e","d1ae944df3","bfaed0a786","3e305fa9fd","fdd9beef5c","b00a60cf0b","e340654ba3","3f446bd456","5c5f254090","17c304d708","30d7c5c074","fcd198951d","a740f0695e","047ae7f857","82123eedcf","5e48fc6d96","ebd1018059","18ff080e31","287a136411","ea13ff0710","0679b55fd0","bbf7c9c584","abcb9a4f2c","1113facb4c","3a1eb89f86","9f0cd12cf3","fa0a725306","d99fd31afc","07737fb3f6","02ada67b2c","3017df3ce5","7f2964d5e3","770909dd55","5cfc31034a","a34ba8dbcf","9c08065345","007c3501f9","a2c7d180f4","55adf991be","e5fe0ae0a9","7d927b345e","2c210dd923","b270a01ba4","30c2214f83","26e29366b9","d3e5b430c6","e75ebb9095","c206e23631","1e6a044dbc","06a233b87e","9071f8875d","86f2d51afb","1aa66d1d82","8772c99f76","9744d07524","ba459889a8","06a233b87e","9071f8875d","86f2d51afb","1aa66d1d82","8772c99f76","9744d07524","ba459889a8","bdba68ed2e","8177738053","5cd0314174","aae40a3a53","101262d076","e12815c8e7","45ca42c2b8","5a616ac939","e09ccdde16","89b845ea22","fa49ec1231","2768120288","efee336a3b","5738c9d93c","27d736c9d3","6b87b44862","15cfdfad6f","60ff93d8b9","8809a3c84f","842f352625","cb7513a95c","27d736c9d3","6b87b44862","15cfdfad6f","60ff93d8b9","8809a3c84f","842f352625","cb7513a95c","3b0e60df22","305bf484ab","4e2ce16994","8e42a1c89a","29ed2689f5","846481b936","a7413fe001","abdb8f4381","b2963d6bd6","00310aae69","9ac81466ad","04c0145d40","77e79caef7","f4a7f68d0c","2b874388e8","0f44bf46bf","955f2de20e","ba03748609","b2f557a133","f4553519ff","25552b8ecf","2b874388e8","0f44bf46bf","955f2de20e","ba03748609","b2f557a133","f4553519ff","25552b8ecf","fe0a92674f","73bb3495cf","65a77bbf82","16988c8862","50244e8730","94bd248f81","34813db49f","5ae57e6744","4153e26b24","cf417a876a","69ffc8aa2c","10743632b5","fe0133a108","f135466a76","5ae57e6744","4153e26b24","cf417a876a","69ffc8aa2c","10743632b5","fe0133a108","f135466a76","5ae57e6744","4153e26b24","cf417a876a","69ffc8aa2c","10743632b5","fe0133a108","f135466a76","d40859543e","37711dd9a4","a81da3a4e3","0ab418cf08","f8cbaf0059","61ac0342be","c4e2e33edc","1740c92d47","610ca7b335","2d8c3103e5","0404f7583d","4d5e09665b","fdad7120fd","4dee23c348","0997b90bc9","e2bcf46ced","bac98013fd","a57bb4e8e7","d1ad21ed92","62baae487b","c191729c62","ea430c5532","156f0f83f2","444707f932","8e8dc183b2","0c20d9800d","ca8fc23e03","cde2576482","288d2197f7","c0d678d740","d570e7e7d5","17a3fcda08","38cd9e8433","ff31b40bd8","9bfbb17577","ec1656c0d8","f064555c81","c37079d991","4ce8e0ffb1","55116bf6fc","1499d83f3a","95a64bda62","8bd380e7dd","5c6bb205da","a5ce9d5250","7f9e90c956","0aa41c6484","dcdb9a4601","275c284cbd","8bd380e7dd","5c6bb205da","a5ce9d5250","7f9e90c956","0aa41c6484","dcdb9a4601","275c284cbd","0d33faff5e","6cb650cf34","0f9e8a73c3","5b8bf9e750","b42724c38e","c7643a73f3","90aa83b280","96c54fa9d1","ad205ffffc","f2aaf2ac2c","e482ac9f86","27971e25d9","da5b1537eb","ea76e29f92","ce9d2f2253","347761ebab","b2ac4d7ca5","b3b8ae2c04","e0b0f1bb64","4f81bf47d2","517825a12a","34bf6c326e","19d9796f8e","7b7a9eb26b","3e0096f9de","db47eeb648","e1b21f9944","65f45047bd","31fc4959c7","5b1b39beea","a1f1111d33","14bf7c1ef1","5f4adec9d6","f9611ff865","1465f642b8","31fc4959c7","5b1b39beea","a1f1111d33","14bf7c1ef1","5f4adec9d6","f9611ff865","1465f642b8","490cfc4a08","a217bdbfe5","c546d63626","f18b4988cc","341ab6d2fc","a8bff81d78","1256303969","6e84df7323","766211ec75","b30766274a","e2cbb46f72","76f19f9f21","338e240935","4459a02c41","6e84df7323","766211ec75","b30766274a","e2cbb46f72","76f19f9f21","338e240935","4459a02c41","553baa64b8","c24f47faab","92c03092c7","fa21946622","793e298d5d","a6bd0484ff","d2dfda3d8e","bef0debe7e","409c654a87","5d7a7af1c9","536b79246d","727fca780a","da603584ee","7d7b3a4d3c","d5eac66de9","28edfc5607","a0aa8c9445","c22889deb4","d562b81f73","cc17587252","2ebad078ea","1caefde2eb","b38508d8f2","b25ba2b121","ef82cbb268","3d1ff44321","76180dad94","20ba6cc3c0","ed3900c4bb","c85a357f68","be95b7375c","9d1bfd4945","e4c7e0693f","e5d3210bc7","5ebbf2f658","684f06a251","be37f45271","0a778914da","8f844bb5e3","905324077f","50448a77dd","e0ce09bc78","d5eac66de9","28edfc5607","a0aa8c9445","c22889deb4","d562b81f73","cc17587252","2ebad078ea","896dcfcf5f","3d50c4940c","07055999e1","0b69bf6c32","507446414d","93a620716f","0cf5981087","896dcfcf5f","3d50c4940c","07055999e1","0b69bf6c32","507446414d","93a620716f","0cf5981087","30781719be","509eb16c7d","04afb60e5e","d3a2825b8d","1beaafd696","e3bfb5f38d","a04c32b6cc","87938a566c","e5bb1abaec","913f06610f","8fd74ce060","299b23b2ef","7af983bb38","595d70d4b3","87938a566c","e5bb1abaec","913f06610f","8fd74ce060","299b23b2ef","7af983bb38","595d70d4b3","0fcea9468b","3a5974d955","e711ddfb4c","bf778f1099","9650ffe1f0","2f3096c52d","f6418f562c","0fcea9468b","3a5974d955","e711ddfb4c","bf778f1099","9650ffe1f0","2f3096c52d","f6418f562c","48a0b0740d","10cedf597f","243b222610","736fc6e9c3","46be65aed3","33eb163f66","3640b03432","48a0b0740d","10cedf597f","243b222610","736fc6e9c3","46be65aed3","33eb163f66","3640b03432","46369e7f1a","8a0d23832d","31e00192aa","70d9af7b97","617ea09da3","2cbb088842","8637d15078","c9b17e411f","79066aef60","cb4b67957a","5ec6fe5fbd","cb2e11b838","dcdf2a594f","b00c96d781","5a56da05e7","7866310931","ff889b0fad","5e57224d12","c17f13f863","4147d0ebec","2933bd90e1","eed18352b1","2416e57647","f6d5e82d86","0edb8fbbf4","48949f9e24","f0f5666545","72c8a0bf3f","5a56da05e7","7866310931","ff889b0fad","5e57224d12","c17f13f863","4147d0ebec","2933bd90e1","2b81e9bba0","76047e8bf6","77d9d6ada1","5512babfa9","3157afdec2","d595a8b1a1","e3195e0e6b","8b7cfc4b9b","de90961aa7","a661f780eb","e89c13526a","71e4770f56","fa69087fcb","2e582f28a5","6548771c34","090737690b","3068492f1f","7a8afd7e4b","5909452a7a","cac12e7008","a59d0a9231","f694bdfeaf","deae724524","c0601c3858","f4efa525fd","53dc559014","ba8eec3220","7d0d79fe22","ad691e32b1","c84e48cedf","71fdd75ccf","0754ada021","eb9486ab8a","5244993982","91f2964186","ad691e32b1","c84e48cedf","71fdd75ccf","0754ada021","eb9486ab8a","5244993982","91f2964186","4156c16eef","86937ed312","100e1d6a48","a07669a15c","b925c249ac","2368dee686","e48bf7cfa9","4156c16eef","86937ed312","100e1d6a48","a07669a15c","b925c249ac","2368dee686","e48bf7cfa9","0cf2023e93","2ccea2baae","0a350c0278","37665fcc2c","cd497a4d91","1d133ed96d","640a236885","c468d3b7d1","d8084484fc","b5b87b77fd","75f5863987","26a15128ae","8662eeafcb","9f13beb1da","500b99aba0","6af259890b","566aebcad2","9bd68ff90d","28d923a617","46f09fd735","28c1fc2cae","d45356b3aa","43888e9941","a26a0a2513","bac38f813f","9dcc183418","32e5e57a56","8509594bf2","d45356b3aa","43888e9941","a26a0a2513","bac38f813f","9dcc183418","32e5e57a56","8509594bf2","e2caa70e54","e17d5072f4","16383712a2","8d243394e0","c9e1fc6f75","c481e686d3","021f7d499e","9a28980fb2","cdb0e2d6b1","5183541d18","a7a2d19923","e33e17e365","229914226f","092e5c956d","872e439a3b","1fadf30367","af50bfde4e","c171fd4e7b","1a3496078a","7b973c8694","6b22c25ccf","21d0a3fe02","4d1dceec47","973c93f331","f2da4fd572","fd9397bc63","7e4eba4d50","aa540b217a","d0502d1220","c6034da072","e9f4a5b5e1","374a17a78e","e5a8e81edd","803f842021","e54a676ccc","d0502d1220","c6034da072","e9f4a5b5e1","374a17a78e","e5a8e81edd","803f842021","e54a676ccc","654c602d50","f12928e480","216ceb6bdc","3f7b2a1bd6","3dd871261e","c4a21b5dbd","e10f03d04c","e1d2866d21","8698f21c34","44ffd163c4","26ac989c63","b2a660a3a8","3c14be1dff","c7d96d0107","ec48c467ce","933c19ee9e","bbd151d81b","71512ce73a","3e72be5d5c","203654aee2","a5545e8537","142f5e75a8","914d4c689c","01cd845474","b95e9adea6","ac47a9020e","ee670794fa","a7939520a5","25b87cbb59","b98d0235f2","a54bcbc065","071bbe6ff6","275e68b0e6","466970da56","440c9d6545","e1d2866d21","8698f21c34","44ffd163c4","26ac989c63","b2a660a3a8","3c14be1dff","c7d96d0107","654c602d50","f12928e480","216ceb6bdc","3f7b2a1bd6","3dd871261e","c4a21b5dbd","e10f03d04c","cf4cc63b71","aafb965b52","697043cd9f","580a489c36","8216c67db3","386e3a6953","cd403e46ce","0e5863689c","801d0e2007","be8b96802a","4076fca6f0","b8acadc9c5","412cba8aee","0d7e548469","e1d2866d21","8698f21c34","44ffd163c4","26ac989c63","b2a660a3a8","3c14be1dff","c7d96d0107","e1d2866d21","8698f21c34","44ffd163c4","26ac989c63","b2a660a3a8","3c14be1dff","c7d96d0107","34352c6cd3","bc26655f00","69e69c60a9","a39280f5d1","8b18ae27ae","993f60097f","83dec14080","25cf30a3bd","29651d1b7a","bd1bf0deea","62777f9bc1","6719cbb13c","7f3e3551e3","52dd198596","a1b2c8c3a9","2e39ac9d0c","185c9ee283","d18654486c","c52c1a368a","2b283ce6c2","8ad6d7efae","4d0b42fb38","b98a9bd410","ab0aaf0698","7e8f373dbf","78a919fa3e","64905a60eb","0d05501fc1","dda209428e","906d9305d4","cf85ca0637","5aa4332e2d","6b8c039d9d","504d13c9ec","c9bd83e680","d2e0934df2","586b86d748","ae9c91ea27","7d8ec55d63","a22c1d4ad4","1501638370","98b99b28d8","da80cc4024","6902b16e24","9bed01f11e","24e5e99f92","0031b055c7","d3d23ffbb1","339a625a25","a1b2c8c3a9","2e39ac9d0c","185c9ee283","d18654486c","c52c1a368a","2b283ce6c2","8ad6d7efae","a1b2c8c3a9","2e39ac9d0c","185c9ee283","d18654486c","c52c1a368a","2b283ce6c2","8ad6d7efae","cc6bd47193","b4ff42bda4","802419470c","5a50503f15","00f2d1356f","069b81d034","dce4d779ba","87dc50289c","864f14006c","ac017a8e10","87bcd7f6d5","a38e91cebd","01dcd6c877","d6abc2591f","ef499ce5f5","8b99746463","6d1f61cd8b","8b12a55c55","eac9f322f8","688f550c7e","563f7582f4","d196029173","6229ead318","72b07ba605","dae1f56fc3","cbc5051274","7dc43dcf37","41713c338a","87dc50289c","864f14006c","ac017a8e10","87bcd7f6d5","a38e91cebd","01dcd6c877","d6abc2591f","a3c3c74132","54b5a995a2","9cb1620869","f2c3df7d55","32e6078951","46ae90a066","870d39cf74","884c10ddaa","0489c76ec1","d15702a8de","d52a136885","5c127cfe6e","9f3ff0fedd","f1eca009f3","540b5daf82","03bf6c9842","7a3b989bb4","5fe2735a08","93a221c3ac","b86a68b245","4b890910ff","7b9d9878b3","cac4e14fa5","7b3c859e65","3d1507de75","63b6ae7fbe","fbbaf773c7","3cc074c1f8","9c0e98e1d1","2b7ee4e427","85aecd7b75","73d3d15109","ac423ee7f2","76840a59ab","5118e52717","9c0e98e1d1","2b7ee4e427","85aecd7b75","73d3d15109","ac423ee7f2","76840a59ab","5118e52717","b5af1d2b36","056768db5c","124ff9da21","29576c49dc","0fe657f2a6","afd44f7186","a9750d2662","e7efafafa9","21687aef20","ec2d0ca8ca","266bd96caa","e8c66c3c71","35751e1245","89894d5006","e7efafafa9","21687aef20","ec2d0ca8ca","266bd96caa","e8c66c3c71","35751e1245","89894d5006","7853134a4e","066d56644d","7400818458","0d1438757c","7f6d64d39e","3e285e4d8c","8b0e90859f","4ce241d479","20fe8b0db1","285aeb32c4","f8171b8d40","8a04a1b07a","9ed33ae557","55b714b611","39b0d84344","057c027ee6","7ad9bb1c65","dfdde35069","1c12841a79","5c000dd536","b3c385be73","22d926d89f","eb5c17c745","16d96377a0","f45ab9bf94","604bdb29ec","5fee2373e6","bba219391e","627ac03e02","68a3985943","63210c4dac","2037eb9d30","648881c39f","a242e39e4f","08eaf699d4","9a4eec9f6c","a744db60f3","92b6fb32a5","106c0769f9","3ef516b682","5bf44aba0a","8a6d513713","5920b02634","9861c5d7f4","c4713d5750","9c5a6c28c9","06325d7b16","8bfcee6f2d","bed6b6c7fb","5920b02634","9861c5d7f4","c4713d5750","9c5a6c28c9","06325d7b16","8bfcee6f2d","bed6b6c7fb","bf2002d6f6","aeb7497c86","2c3c44a8af","4ce6d183fb","9435920d2a","26e119ab33","dc3df1d8c4","96819d1a3b","d22d83ba51","d64a7046d4","3af06a671c","1dfd90cd02","f22eb089de","11e23b2cfe","96819d1a3b","d22d83ba51","d64a7046d4","3af06a671c","1dfd90cd02","f22eb089de","11e23b2cfe","98c94c2c25","31a4a6b9bb","c5b7f9af7d","50f628f2b9","df8afb9424","1434577277","e3504072c4","9e887a14f2","b071b74486","f0b51d1fbd","667f71652e","17a022b707","6bb91791c3","2677484860","9e887a14f2","b071b74486","f0b51d1fbd","667f71652e","17a022b707","6bb91791c3","2677484860","9bfbe64d52","a8f8d5621a","6363a33229","b725966226","5946b4751e","548853938a","4f1aaeec67","8657dea780","db78675a7b","2156f6e8e1","444027f1dc","ec4a62b342","dd0499a894","2937f21a0f","7d2ae04b6a","178b6e64fc","602a68aa2d","ec8f6e7072","c9a4f535e7","369d1d4520","de34eb8290","740ccc9b62","449bacec27","38ba486859","f58d6a7fac","5c2c6aabb2","628f450ec0","f8b924e62c","7d2ae04b6a","178b6e64fc","602a68aa2d","ec8f6e7072","c9a4f535e7","369d1d4520","de34eb8290","2a936a16b0","4b5ff66c3f","2a0e2fb792","2286a950ea","78ca88e151","c12e1ef82d","6adfd47f34","aa06c51082","39c94186e2","8ca15f90d9","11a56d94d7","9de262608b","a46c959da6","1a1676172f","4c575c8956","d80bc31d25","434d465f93","872a90a353","1ccc265d62","4f4c4fb8a6","b0ae08d36b","f041733678","c4674f6448","7dd982f14a","e2649c275d","1e80b6dc0e","d366c60ec1","3712ff8c55","f041733678","c4674f6448","7dd982f14a","e2649c275d","1e80b6dc0e","d366c60ec1","3712ff8c55","d355552ff1","0f937827e9","3b6facdbdc","a0aef509e9","9f7e361e7d","eab69411a3","b6929745b1","e55911d32d","b89d4bbbcc","264024a340","352393ff99","4fa2ab9b24","63763f2a75","05ebd18e76","1fa7c8cf66","6a1dab1ee7","a9a3ac75b5","c4bb83eca7","c401c3d284","2cc2fdfa11","9c31961197","0d05f88dcc","295d768acf","a8cabdf8ed","a84b089ccd","b0d53adbd7","d5f7fc9538","9d7ddeb036","6280ec855b","4d3424076a","e868d88164","a5e85a9106","b834429c2f","43a4ecdf00","6bd7bedd38","6280ec855b","4d3424076a","e868d88164","a5e85a9106","b834429c2f","43a4ecdf00","6bd7bedd38","a69dc2a08f","b8ad075c18","3fc3b13af0","d42fc90455","a607c06d17","b3df2fce08","dd7a22194d","c723fa90eb","6f869c72a7","85a10cb323","ff73eb7373","df2dc964ce","547292f851","2152e7ef6b","c45fe9d08a","d5911bf000","2b9e8c4c93","1e49a246d7","e25d107eae","22b77ec375","424c31cde3","f3fcf42701","0f97e69fa7","0a3189faf8","8d191aa58a","0af7c15065","916834e144","a39df5e56d","745f8f756c","d0b0d3a48f","20218f90f9","a25fae4466","1665f5dde6","b1f85b0dc0","44079ccb09","52e4523526","aa637920ad","239ae589ba","16cbf6d979","5b2a2e1a73","d56cde4b53","61675554e5","eafa9011da","b77f07a9e0","38348e07e5","12c4305389","84c912668f","5e00a25640","cad3a5a958","800285071b","a59e136b44","1de1f5359c","4580be7675","3536511eac","f57deae4a9","556bf5c055","d742141996","a3469d5c02","05a736faba","80c3a54242","794e529d84","89d39e250b","2886480364","c723fa90eb","6f869c72a7","85a10cb323","ff73eb7373","df2dc964ce","547292f851","2152e7ef6b","7f7bdf5ac4","6c9e93e935","6ac9a5d110","71d286245f","9c6281cbaa","c2fe9538c9","cd37a665ba","4f23fb62cd","1dad4eb88c","03d7a6a33b","fe7bbab3aa","6fb0f48791","cd14963d33","c8c2c64f38","a64afffcf4","dd96909a20","0e07894f0c","0a2126a450","f91151149e","7085ede7bd","15139df6fb","567f15d531","16f00059fd","b6fd9df82f","19641917fc","52d8e2da78","36e77d7ad9","e5e1fede6e","b693cddc96","5e2e2e3062","cb8120fcb0","47ddd8bcdf","888a501f6b","59d5323f0f","157f57e5c8","4043ebc8b3","f1e5a8ed7e","8b063dbb07","cc64cc7dcc","7c93af9f7e","d95a8e2552","bf7a0231d7","75eec99195","c2f575e557","bc0abc9e21","cbc802e367","f7fd0471d0","50d9f6ef44","0563d79aaa","d02d6ea679","b950f1c03e","b2daabd285","6a6b98f252","9681a45302","006550b1db","3916228ba2","31106b85f8","66fa7215f6","eae5da7e30","fff42c98c3","22edb1aa67","ef7c8d9538","923fff9454","94ae184abd","4202f9dfe2","2cc9fb8afc","4c44b8831d","3cf604a2ee","65b0255531","49c71becba","94ae184abd","4202f9dfe2","2cc9fb8afc","4c44b8831d","3cf604a2ee","65b0255531","49c71becba","4aeb9a394d","fe65f6043c","e17d129744","97f3e4c7a0","02bafb2947","3c2e723dd2","d15541278b","4aeb9a394d","fe65f6043c","e17d129744","97f3e4c7a0","02bafb2947","3c2e723dd2","d15541278b","3ef98ad112","498bd0f1b7","12218b2884","39b4d3f3c2","f15cdab6d0","95c1c8a07a","e7072bf044","6e93f489e4","20b803cb28","aa27726285","42f5cdcd44","b756789fc4","3a1dc07bc8","a82bf76926","0f46794967","85b3f063c5","3c5176af48","d547f0b5e3","1b0dbd1892","c9817b2903","c3faf5b107","b1339b61fa","d5eec6428d","7f30689b07","4858885920","a9905af66e","527e60c1d9","ff94c8855f","b1339b61fa","d5eec6428d","7f30689b07","4858885920","a9905af66e","527e60c1d9","ff94c8855f","a36c3e39d8","d419329d79","afae6b1cf8","b9269f0630","551fc9a00b","131312ef62","682e92bf04","62ad6e1147","c2891232ef","f145de9c07","8e00df72b5","8926e8accb","11ff4d8535","4e61c72b7a","356b830a4d","d07550eb37","987c28fa7a","6cdab46859","5bd2634efc","adc5b10631","8b345ac4b2","75f7aec706","a567e1535f","59f744fefa","9d4e2ad34d","e135151b73","aaa1d14d14","de96e87b42","e1ae15a3c7","b7d8af7ebc","62bff8a7f4","a8492e2c56","4b831df0a6","c35c160ff8","0a367fc97f","954ee99a9f","f5bbaa4795","5331e789c6","dabb5783a2","0d215555b6","d7b6573d30","5d5b70783b","954ee99a9f","f5bbaa4795","5331e789c6","dabb5783a2","0d215555b6","d7b6573d30","5d5b70783b","6fdca58fd7","fa70488ca0","34339f1a32","bba6174088","96bf7e563c","2bd5d71997","7088fd9827","1aa0084423","41cec9046c","c699fd44f1","1c8a836359","67ba34e946","01c61e62ef","f8e12a5980","b86bc0abe4","e8ad04f576","fdf6c8665c","e61a6dbb33","ffda520a57","4141fbfdc5","0a1d41ae97","e833f412d0","640c479228","d1652f56a9","bbbe11f0c1","55de8e404d","f52f2e980e","ff04f87b72","e833f412d0","640c479228","d1652f56a9","bbbe11f0c1","55de8e404d","f52f2e980e","ff04f87b72","2a3c54a9d5","1c50b21ca6","8fdcb0a8ad","67f332aae0","c13e596dd2","810863795c","461270d0f1","f24cb7601b","490d407704","a36aa14c75","0609bf70df","9dab8e618e","473549c9cb","1d631a6d4b","2a3c54a9d5","1c50b21ca6","8fdcb0a8ad","67f332aae0","c13e596dd2","810863795c","461270d0f1","8a20cb92c4","9f2769ce17","27480639c9","32a4ce8994","8989c60517","ed0e006ad2","b8e0d028e9","d769f57b56","c093bda384","d6d7af97ba","e25385d398","9dd93a9734","d45501cbcd","78b3d472de","50d1ce8b1c","d083ef1a18","43905d4fab","441a85fd41","733f28253b","3e86c672e8","8f2ec5717a","c6c9b24d9e","d13af4c6c5","6da3e05401","e326426f23","8c6636e3f4","aa15951c59","e33961e40d","9e30833610","4c669b3d0e","0158a59780","a92ee73eb2","7dbdb60ff4","ea1737d2be","bfce09aedb","2a3c54a9d5","1c50b21ca6","8fdcb0a8ad","67f332aae0","c13e596dd2","810863795c","461270d0f1","ac1368dd2b","98a7d47a8a","2dc289e75f","319b718005","e519108f74","21ae2e2747","2ce7e106d8","56f8c7edc7","82ab757818","5bd0ed0c2c","38b4e1fa27","bbedba29bf","565e9c7774","4d2cfffac1","56f8c7edc7","82ab757818","5bd0ed0c2c","38b4e1fa27","bbedba29bf","565e9c7774","4d2cfffac1","688ab8f1d7","29911b8b2a","c54a36fb27","b65f542666","a403bbf747","47021d4c1e","892a29be95","9a13504fdb","e7b49e028d","a371c14477","bfc4ef4330","74d1213367","499611e078","6899dd8b2f","85b8f67cc4","b1b4d410e8","4df86380d1","dde238a58b","2c3e2e6a67","99a84ee47e","99d4af362c","4b61cf8fda","bbdbb42f49","b9d35d0278","944911272c","e4cd19f5b1","723bf6ea11","f4b3196511","4b61cf8fda","bbdbb42f49","b9d35d0278","944911272c","e4cd19f5b1","723bf6ea11","f4b3196511","03116cab85","fdca9a7df2","8980ba883d","9dd73ce0ea","0525948e96","74cf9be5bc","ceffc66c10","6280b2830d","eb8d59be35","028f2ff49d","579152dcc9","6356cdd42a","5550dcc28b","17a0c53913","be954c6655","47b51051fa","00a21d1c75","5f8fda8e55","ee4fec4267","b1c5b14157","c4933b81fd","948b049f6d","3a79062434","52a2bfa896","742f38f59e","004256fd24","ee2e72a276","22963651bb","47624bdaea","960256ebd4","94147ee488","f59a4e60dd","70b145ee47","c42ae29d9e","67d5951a09","0eb16c6ac1","1ba5542b77","9da3922b8c","c7f18c9597","bcaa30f45d","0d2871ee07","afd7db842c","47624bdaea","960256ebd4","94147ee488","f59a4e60dd","70b145ee47","c42ae29d9e","67d5951a09","fedda630b9","1c749b87ea","3e767d52d1","11b62b149f","45847f0f8a","84b1fd4314","1b72843a6e","ebb3beee0d","10eb7e08b5","30c0516676","87a6297e26","7ba3a0c2af","bc63df0e3d","c10db55d25","d92c4eaf94","682d173b30","7b0b68c4c4","f4805dd668","af4eaa232e","f19100c152","48e9762f2d","2880553bc3","9712b27335","7ec9ffb4dc","0f5a207e8b","5802eccfd6","ff21af2fe3","a1b7f1cb0b","593ecbb330","160c7fb9f1","d7872d7c68","a1777d1161","db59491ced","849f3740b9","f56a562d78","f1e6c380f7","6d96375344","fc43af9887","ade2f71958","b65b715556","bbf297c0b6","9785e01d6e","0e84666a0f","14d02bfa32","286d5b7a38","d21e4da8e7","0dfecf684c","8ab0a826e2","9dd867e0b3","0e84666a0f","14d02bfa32","286d5b7a38","d21e4da8e7","0dfecf684c","8ab0a826e2","9dd867e0b3","0accee6c3f","479a512c99","f40ddd5ca4","f749703520","a5288747d3","e6c235c78d","4c952256b7","db9699d2fa","c4e98d2380","0e68418ce4","8b6d8d379a","fa8975a299","954505f358","2b8b4d53c9","e281e52ad6","1a27e8ac98","6ee99ea887","3b1533ab41","d268a5cb16","d6219f20e1","e98dd85b4e","8e25e52a57","de570f318b","9a7c46af9e","9ce16a6db8","916b42566b","de1e29855f","6c3d00785d","509ad6b426","a5dda9edaa","f874b96154","461554ee99","f0b28d2363","1cffacbef9","5090953dfa","a38ae5f161","9a8e133334","0dc9fb8e07","bfefea2c33","2a119bb3ea","739dfa6f9f","0074fd6277","a38ae5f161","9a8e133334","0dc9fb8e07","bfefea2c33","2a119bb3ea","739dfa6f9f","0074fd6277","e71ef24316","00abe9e3a3","0a05920259","46d719d20a","7cd12a139b","1189d878ea","86e7dc7d98","600b8866e9","5e5400098a","860305ff9a","3a3e77f461","e3c5baa348","93ccdcbbff","9ccc6b892c","3d5885a9e2","9036184a33","a1513aaa1b","667370c2b1","a4fcf6a79c","a10301250a","14f5749f2f","1b2e333b01","bf89200cfb","df8a5c35d2","fb91bda510","b1b46c1579","0a612c2b2b","a2620021cd","eb2db8b813","6d68f85fd7","d6aed7fd21","2a6688f97b","c799f81bb6","65c29b9d72","fb337ef379","815db40f2e","051b961878","57b7af0b3f","b47040a043","aa256a0c41","b40ddce33a","1b669815b6","812772b177","afbc1fe2c1","7ee7fd630b","01f0de16d7","0655605d0d","687287c649","1a6fc69a0d","812772b177","afbc1fe2c1","7ee7fd630b","01f0de16d7","0655605d0d","687287c649","1a6fc69a0d"]}
```

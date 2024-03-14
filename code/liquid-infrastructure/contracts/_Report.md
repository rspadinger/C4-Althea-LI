Sūrya's Description Report

Files Description Table

| File Name                                                                                                          | SHA-1 Hash                               |
| ------------------------------------------------------------------------------------------------------------------ | ---------------------------------------- |
| d:\_ROBERT_IT_Consulting\Audits_Audits\C4-Altea\code\liquid-infrastructure\contracts\LiquidInfrastructureERC20.sol | c5b75a6319405d9dafbd8c98f81f45eddd0c8c8d |

Contracts Description Table

|           Contract            |             Type              |                            Bases                             |                |                        |
| :---------------------------: | :---------------------------: | :----------------------------------------------------------: | :------------: | :--------------------: |
|               └               |       **Function Name**       |                        **Visibility**                        | **Mutability** |     **Modifiers**      |
|                               |                               |                                                              |                |                        |
| **LiquidInfrastructureERC20** |        Implementation         | ERC20, ERC20Burnable, Ownable, ERC721Holder, ReentrancyGuard |                |                        |
|               └               |       isApprovedHolder        |                          Public ❗️                          |                |         NO❗️          |
|               └               |         approveHolder         |                          Public ❗️                          |       🛑       |       onlyOwner        |
|               └               |       disapproveHolder        |                          Public ❗️                          |       🛑       |       onlyOwner        |
|               └               |     \_beforeTokenTransfer     |                         Internal 🔒                          |       🛑       |                        |
|               └               |      \_beforeMintOrBurn       |                         Internal 🔒                          |                |                        |
|               └               |     \_afterTokenTransfer      |                         Internal 🔒                          |       🛑       |                        |
|               └               |    distributeToAllHolders     |                          Public ❗️                          |       🛑       |         NO❗️          |
|               └               |          distribute           |                          Public ❗️                          |       🛑       |      nonReentrant      |
|               └               | \_isPastMinDistributionPeriod |                         Internal 🔒                          |                |                        |
|               └               |      \_beginDistribution      |                         Internal 🔒                          |       🛑       |                        |
|               └               |       \_endDistribution       |                         Internal 🔒                          |       🛑       |                        |
|               └               |       mintAndDistribute       |                          Public ❗️                          |       🛑       |       onlyOwner        |
|               └               |             mint              |                          Public ❗️                          |       🛑       | onlyOwner nonReentrant |
|               └               |       burnAndDistribute       |                          Public ❗️                          |       🛑       |         NO❗️          |
|               └               |     burnFromAndDistribute     |                          Public ❗️                          |       🛑       |         NO❗️          |
|               └               |  withdrawFromAllManagedNFTs   |                          Public ❗️                          |       🛑       |         NO❗️          |
|               └               |    withdrawFromManagedNFTs    |                          Public ❗️                          |       🛑       |         NO❗️          |
|               └               |         addManagedNFT         |                          Public ❗️                          |       🛑       |       onlyOwner        |
|               └               |       releaseManagedNFT       |                          Public ❗️                          |       🛑       | onlyOwner nonReentrant |
|               └               |    setDistributableERC20s     |                          Public ❗️                          |       🛑       |       onlyOwner        |
|               └               |         <Constructor>         |                          Public ❗️                          |       🛑       |     ERC20 Ownable      |

Legend

| Symbol | Meaning                   |
| :----: | ------------------------- |
|   🛑   | Function can modify state |
|   💵   | Function is payable       |

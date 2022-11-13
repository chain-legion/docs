# What is Chain Legion?

Chain Legion is a BNBChain project centered around dNFTs (dynamic NFTs) - Legionnaires. The collection boasts 7,777
unique, randomly generated pieces

Each token has its own metadata stored off-chain, just like any other NFT. However, as they are dNFTs, each token also
contains on-chain data which is bound to it. This data ranges from experience points, to battle history and everything
else that the NFT in question has "experienced" up until now

They can be traded, sent or received, or held onto, just like with any other NFT. However, their dynamic nature allows
them to take part in the Chain Legion ecosystem, through the system of on-chain traits. Every Legionnaire starts off
with a clean slate, and it is up to its owner to build its on-chain identity, by interacting with the Chain Legion
universe

# Contracts
All contracts are verified on BscScan. You can view them using the links below:

- [Mint](https://bscscan.com/address/0x820b46240bcfcd95ecfe31692a811a2e561598ea#code)
- [XP](https://bscscan.com/address/0x61300Fb6b6eF8482430ecceb116221ec835f4F91#code)
- [Attributes](https://bscscan.com/address/0x26309b24Ed94B2bb5c63C8A83fD190FFce3a5650#code)
- [Combat training](https://bscscan.com/address/0x0F38515F35cc602921bE119C40B65C8f7159504B#code)
- [PvP](https://bscscan.com/address/0x3E615138a62977040A78D1936992cFa3632BDaE4#code)
- [PvP history](https://bscscan.com/address/0x50Fa01D7287c02EAf60f161ccBA39B2d655E7bC2#code)

# Leveling and progression

After minting, the level of your NFT is set to 0. To start interacting with the universe, you must initialize it.
Initialization will set its level to 1, give you the initial amount of attribute points to distribute, and allow you to
use that Legionnaire in PvP battles

Important points below:

- To reach the next level, you must collect the amount of XP points required
- Amount of XP required for each subsequent level increases as you progress
- Gather XP by doing PvP battles or completing your combat trainings
- Number of PvP battles in a day is unlimited
- Combat training sessions are limited to once every 6 hours
- Combat training XP rewards scale with the level, bigger levels grant more XP per session, with base set at 150XP
- PvP victories grant 50XP. Losses grant 20XP

# On-chain attribute build

Assigning attribute points creates a battle build for a Legionnaire. Attributes are:

- Strength
- Constitution
- Haste
- Bleeding

Attributes and levels are used in PvP battles to calculate your battle stats. Battle stats are:

- Damage per hit - **DPH**
- Health points - **HP**
- Speed - **SPD**
- Damage over time - **DOT**

Battle stats are a crucial part of the PvP system. Here is how they behave in battle:

- **DPH** - How much base damage you deal per turn
- **HP** - Total amount of health you have. If you take more damage than you have HP, you lose the battle
- **SPD** - How fast you are. This will determine whether you strike first, and your chance to do a double-strike on your
  turn
- **DOT** - How much passive damage you inflict to your opponent. This ability stacks each turn, so the longer the battle
  is, the bigger damage output will be

Attribute builds are not final and can be reset for a fee

# PvP in-depth

Battles are turn-based and contained within a single transaction. They utilize battle stats and ChainLink VRF oracles to
provide fair and unpredictable games. Each battle requires a monetary stake, currently set at 0.025 BNB. Winner of the
battle gets the loser's stake, resulting in a 0.025 BNB profit, minus the platform fee

Here is how PvP works:

- Players attack each other alternately
- Each time a player attacks, a ChainLink random number is used. Random number falls within the [-x, +x] range. Negative
  is a debuff, positive is a buff
- Buffs or debuffs affect the attacker's DPH
- Each time you attack, your DOT stacks. It starts at 0, and grows incrementally. For example, if your DOT is 10, then
  you will deal [0, 10, 20, 30...] damage each time you attack. This damage is added to your DPH to get the total damage
  for each turn
- Total damage for each turn is subtracted from the opponent's HP. If there is more damage than HP, you win
- Speed determines who is going to attack first, and gives you a %-chance to do a double strike on your turn. Here is
  how the double strike chance is calculated:
    - P1 has **X** speed
    - P2 has **Y** speed. Let's assume that *Y < X*
    - Double strike boundary is set at *2\*X*
    - Every time a player attacks, they get a random roll, which falls within the *[0, 2\*X)* range
    - If the roll is less than or equal to the speed of the player, that player will attack twice
    - P1 has a *50%* double strike chance
    - P2 has a maximum *49%* double strike chance. This value varies depending on Y

We have designed the attribute system to be balanced. Here are some general tips for creating builds:

- High DPH combines well with favorable rolls
- High DOT deals a LOT of damage after a few turns, if you manage to survive
- High HP can soak up a lot of damage. Combine it with some damage and it can be deadly for the opponent
- Having higher speed than the opponent can greatly tip the scales in your favor
- Putting many points into Haste but ending up with smaller speed is a bad situation
- Combining DPH and DOT can be a good way to soften the ChainLink impact and assure consistent damage output

# Frequently asked questions

### Is there a MAX level?

Nope, leveling is not capped. Alongside that, all your stats and attributes follow the level, so your total power is
unlimited!

### What if I lose a PvP battle?

If you lose a battle, your BNB stake goes to the opponent. Your legionnaire stays in your wallet!

### Do attributes affect Combat Training?

Nope, training sessions do not involve a third party, so successful completion is guaranteed, regardless of your
attribute distribution

### What happens if I don't assign attributes and queue for PvP?

You can still do battle. However, attributes can provide a significant buff to your base stats. Base stats are
determined by the level of your legionnaire. Allocating attributes can provide up to 50% bonus value to your stats, so
make sure to spend all available points!

### What happens to battle history if I send my legionnaire to another wallet?

Battle history (wins and losses) are forever bound to a legionnaire, regardless of the current owner. If you buy/sell it
or just send it to another wallet, it will keep its battle history

### Does Rarity Score impact PvP?

No. We designed the ecosystem in a way where aesthetics don't impact the RPG elements. Every legionnaire starts its RPG
adventure with a clean slate, and it is up to the player to make it more powerful through active playing and leveling

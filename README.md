# Dominion Card Data

This repository contains a list of all cards contained in the Dominion board game.

Please feel free to submit a Pull Request addressing any mistakes in card data.

## Sets Included

* Dominion (1st Edition, 2nd Edition)
* Intrigue (1st Edition, 2nd Edition)
* Seaside
* Alchemy
* Prosperity
* Cornucopia
* Hinterlands
* Dark Ages
* Guilds
* Adventures
* Empires
* Nocturne
* Renaissance
* Menagerie
* Promo

## Card Data Interface

a Card is represented by the following interface (shown here in TypeScript)

```typescript
interface Card {
    name: string;
    set: string;
    types: string[];
    cost: string;
    text: string;
    actionsVillagers: string;
    cards: string;
    buys: string;
    coinsCoffers: string;
    trashReturn: string;
    exile: string;
    junk: string;
    gain: string;
    victoryPoints: string;
    setup: string;
    categories: string[];
}
```

### Things to Note

The `types: string[]` property of a given `Card` is a list representing all the types that a Card has (e.g. the card "Moat" has `.types` equal to `["Action", "Reaction"]`).

### Categories

The `categories: string[]` property includes convenience identifiers for many card types. These identifiers cannot be found on the printed card itself.

#### Category Values

* `Basic` denotes cards that are basic Supply cards included in every game. These are the basic supply cards in Base Dominion (Copper, Silver, Gold, Estate, Duchy, Province, Curse)
* `SetBasic` denotes cards that are basic Supply cards, but only in their Set (e.g. "Platinum" and "Colony" are `SetBasic` cards, because they should be in the supply when playing with the "Prosperity" set)
* `Landscape` denotes cards that are formatted in landscape orientation. These cards *not* Kingdom cards, meaning they do not count towards the 10 card piles in the Supply. (e.g. Landmarks, Ways, Events, etc.). The full list can be found [here](http://wiki.dominionstrategy.com/index.php/Landscape) on the Dominion Wiki.

## Guide to the Data Values

* Most data columns indicate the card's effect on the turn when you play them (or the turn when you buy them, for Events; the turn when you receive them, for Boons/Hexes; etc.) The main exception is the VP for Victory cards, which are just the VP from having them in your deck.
  * `"N"` in a data column means on your next turn, `"NN"` means two turns from now. `"N..."` means on all or indefinitely many future turns.
  * `"C"` means when you call a Reserve card.
  * Asterisks denote any other effects that relate to the card beyond the turn when it's played:
    * `"*"` denotes one-shot conditions (e.g. on gain)
    * `"**"` denotes more persistent conditions (e.g. whenever another card is played).
  * (Parentheses denote the likely equivalent or indirect effect of the card.)
* `"P"` means allowing you to play another action from your hand (Conclave, Imp, etc.) or from the supply (emulators) as part of playing that card, possibly more than once (Throne Room variants). It is combined with actions/villages because it increases the number of actions you can play similarly.
* `"R"` means cost reduction and is combined with coins/coffers because it increases buying power similarly.

## Guide to Resources and Amounts

Symbols are used to denote basic game supply units and game state. Things like Coin, Actions, Buys, Victory Points, etc. are tracked this way.

* `+` denotes a positive amount, or increase in the player's amount of the unit
* `-` denotes a negative amount, or decrease in the player's amount of the unit
* `$` in front of an integer denotes coin equal to that amount (e.g. `$2` means "2 coin")
* `VP` stands for "Victory Points" (e.g `+1VP` means "gain 1 Victory Point")
* `DBT` stands for "Debt" (e.g `+1DBT` means "gain 1 Debt")
* `PTN` stands for "Potion" (e.g `+1PTN` means "gain 1 Potion")
* `CFR` stands for "Coffer" (e.g `+1CFR` means "gain 1 Coffer")

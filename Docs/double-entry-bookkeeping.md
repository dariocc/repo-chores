# Double Entry Bookkeeping Like a ~~Pro~~ Dev

Tracking expenses is not one of my favorite activities, but I do enjoy making
some sense of where money is being spent at.

Recently I discovered [ledger](https://www.ledger-cli.org) which is a double
spending accounting software that works from the command line and operates on
plain text files. Finally, I'd be able to use my dev super-powers to finally
have an automated system to keep track of my finances. Or, will I?

Join me in this adventure of setting up an environment for leveraging `ledger`
together with a bunch of code in an attempt to gain control again of my personal
finances without spending countless hours manually writing transactions.

## Leger-cli

`ledger-cli` is a double-spending accounting software that is used from the
command-line.

Given the following journal, written in plain text:

```!Examples/my.journal
2022/01/14 Big Mammas Pizzeria
   Expenses:Eating Out           10 SEK
   Assets:SEK Account

2022/01/13 Opening Balances
   Assets:SEK Account            10000 SEK
   Assets:Cash                   200 SEK
   Equity:Opening Balances
```

One can run `ledger -f my.journal balance` to get:

```
           10190 SEK  Assets
             200 SEK    Cash
            9990 SEK    SEK Account
          -10200 SEK  Equity:Opening Balances
              10 SEK  Expenses:Eating Out
--------------------
                   0
```

Hopefully this will have triggered your interest. I suggest a reading to the
[ledger tutorial](https://www.ledger-cli.org/3.0/doc/ledger3.html#Ledger-Tutorial)
to better follow along this article as I won't be explaining the basis of ledger
or double-spending

## Structuring your journal project

While the ledger tutorial is great in terms of information, it does little to
help you make decisions on how to take advantage of it in your dailty

## Starting point

To give a feeling of the complexity degree of my personal finances, this
summarizes what I need to track:

2 mortgages, 5 banks, 7 checking accounts (including a split account with my
partner), 4 crypto CEX, several DEX operations, 3 broker platforms, 2 e-money
institutions, stock options and pension funds, income from salary, royalties and
investments, 3 currencies.

Definitely I could simplify much of my financial reporting by removing some of
the fat (getting reid i)

Bookkeeping use-case break-down:

1. Tracking expenses & income from and to private checking accounts.
1. Tracking expenses from creditors.
1. Tracking expenses from e-money institutions.
1. Tracking split expenses.
1. Tracking stock trades.
1. Tracking crypto trades.

For these use caesI want to be able to see the history of transactions, the
money flow but as well as see balances.

## Principles for a long-lasting, reliable, min maintainance double-entry bookkeeping system

I've stablished the following set of principles

1. Downloadable structured statements are the source of truth
1. Downloadable structured statements are never manually altered
1. The information of a downloadable structured statement never needs to be
   written manually into the ledger
1. Only expenditures for which there is no downloadable structured statements
   are written manually into the ledger
1. Categorized transactions should help determining fututre similar transactions
1. No need to tackle all use cases at once

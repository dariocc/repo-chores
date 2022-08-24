## 2022-08-24

### Thoughts about handling split accounts

Some of the transactions I do from my checking account represent expenses done on behalf of both my partner and me as a unit. 
There are two important things I want to be able to do with these transactions:

* I want to be able to distinguish (for reporting purposes) from my own expenses, even if they fall in the same "logical" _category_.
* I want to be able to keep track



For example, let's say I'm tracking expenses on Coffee.
```
2022/01/01 * Coffee Place
    Expenses:Coffee          5 SEK
    Assets:Checking
```

However I'd like to distinguish between

Some questions:

* Do I need to have an overview of the total amount of 


#### Structuring accounts

Nested account, grouped by financial institution

```
Assets:
    *

#### Option1: 


```
; A private coffee expenditure
2022/01/01 * Coffee Place
    Expenses:Coffee          5 SEK
    Assets:Checking

2022/01/01 * Amazing Caffeteria
    Expenses:Coffee          10 SEK
    Assets:Shared:Checking
```
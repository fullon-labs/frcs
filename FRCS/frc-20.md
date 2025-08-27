---
fip: 20
title: Token Standard
author: thor
type: Standards Track
category: FRC
status: Final
created: 2025-5-20
---

## Simple Summary

A standard interface for tokens.


## Abstract

The following standard allows for the implementation of a standard API for tokens within smart contracts.
This standard provides basic functionality to transfer tokens, as well as allow tokens to be approved so they can be spent by another on-chain third party.


## Motivation

A standard interface allows any tokens on FullOn to be re-used by other applications: from wallets to decentralized exchanges.


## Specification

## Token
### Tables


#### accounts

Returns the token blance info of the target account


``` bash
fucli get table $token_contract $target_account acounts
```

P.S. `$token_contract` is a token contract. E.g. `flon.token`.

#### stat

Returns the details of the token. E.g. "FLON".

``` bash
fucli get table $token_contract $target_symbol stat
```

P.S. `$target_symbol` is a token symbol. E.g. `FLON`.

### Actions

#### create

This function creates a new token with a specified issuer account and maximum supply which contains the token symbol name and precision. The symbol name must be in uppercase letters (e.g., `FLON`). There is a strict upper limit on the maximum supply, exceeding it will result in token creation failure. The symbol name and precision together define an asset class, which must fit within a `uint64` storage space.

``` bash
fucli create $token_contract $issuer $max_supply
```

#### issue

This function issues a specified quantity of the token to the issuer.

``` bash
fucli issue $token_contract $issuer $quant $memo
```

*Note* 

- `$quant` must be of a positive value but no greater than the maxium supply minus already issued quantity otherwise the transaction submission would fail and not get accepted on-chain.

#### transfer

``` bash
fucli transfer flon.token $from $to $quant $memo
```

*Note* 

- `$quant` must be of a positive value otherwise the transaction submission would fail and not get accepted on-chain.


## Implementation


## Copyright
Copyright and related rights waived.
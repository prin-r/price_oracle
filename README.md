# Overview

A price oracle module have three main functionalities
  1. Store price to the state
  2. Expose a function that allows other modules to read values from the store
  3. Maintain validators set

This document only consider phrase one.

# Dependency

- module-primitives
  - CurrencyId
- module-support
  - Price
- orml_traits
  - DataProvider

# Type

- type VotingPower = FixedU128

# Trait

- type Event: From<Event> + Into<<Self as system::Trait>::Event>
-	type OracleKey = CurrencyId;
-	type OracleValue = Price;

# Storages

- Validators: map AccountId => Option<VotingPower>
- TotalVotingPower: VotingPower
- Values: map hasher(twox_64_concat) CurrencyId => Option<Price>

# Dispatchables

# Methods

- 

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

- trait DataProviderRegistry<Key, Value>
  - get(data_provider_id: &str, key: &Key) -> Option<Value>

# Trait

...

# Methods

...

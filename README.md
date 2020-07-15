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
- proof_verification
  - // TODO: this crate is not avaliable, so we will create one
- obi
  - // TODO: make this crate support non-std

# Type

- type VotingPower = FixedU128
- type struct Config
  - time_tolerance: u64
  - oracle_script_id: u64
  - multiplier: u64
- type struct Req
	- client_id: Vec<u8>
	- oracle_script_id: u64
	- calldata: Vec<u8>
	- ask_count: u64
	- min_count: u64
- type struct Res
	- client_id: Vec<u8>
	- request_id: u64
	- ans_count: u64
	- request_time: u64
	- resolve_time: u64
	- resolve_status: u8
	- result: Vec<u8>
- type struct BandPacket
	- req: Req
	- res: Res

# Trait

- type Event: From<Event> + Into<<Self as system::Trait>::Event>
-	type OracleKey = CurrencyId;
-	type OracleValue = Price;

# Storages

- Validators: map AccountId => Option<<VotingPower>>
- TotalVotingPower: VotingPower
- Values: map hasher(twox_64_concat) CurrencyId => Option<<Res>>

# Dispatchables

- feed_value(origin, proof: Vec<<u8>>) -> DispatchResult
- set_validator(origin, proof: Vec<<u8>>) -> DispatchResult

# Methods

- get(key: &CurrencyId) -> Option\<Price\>

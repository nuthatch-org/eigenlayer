# eigenlayer

A [nuthatch](https://github.com/nuthatch-org/nuthatch) nest: **EigenLayer core on Ethereum**.

Restaking across four contracts: delegation, strategies, EigenPods and the AVS directory.

One binary, one config file, no graph-node, no gateway, no query fees.

## What it indexes

**Chain:** `mainnet`. **4 contracts**, **46 tables**.

| alias | address |
|---|---|
| `delegation` | `0x39053d51b77dc0d36036fc1fcc8cb819df8ef37a` |
| `strategy` | `0x858646372cc42e1a627fce94aa7a7033e7cf075a` |
| `eigenpod` | `0x91e677b07f7af907ec9a428aafa9fc14a0d3a338` |
| `avs_directory` | `0x135dda560e946695d6f155dacafc6f1f25c1f5af` |

## Verified

Indexed blocks **25,782,194 to 25,812,130** and sealed **1,334 events**. Every table below is generated from the vendored ABIs, and the run above is what this nest actually decoded, not an estimate.

## Run it

```sh
nuthatch init --from https://github.com/nuthatch-org/eigenlayer
cd eigenlayer
nuthatch dev --dir . --backfill 50000 --seal-direct
nuthatch sql --dir . "SELECT count(*) FROM \"avs_directory__a_v_s_metadata_u_r_i_updated\""
```

The endpoint in `nuthatch.toml` is keyless and public, so this file is publishable: a `nuthatch.toml` is pinned into the nest's content address and must never carry a credential. It is enough to follow the tip. A **backfill** wants archive depth it may not have: pass your own with `--rpc`, and check it first with `nuthatch doctor --rpc <url>`.

## Tables

```
avs_directory__a_v_s_metadata_u_r_i_updated
avs_directory__initialized
avs_directory__operator_a_v_s_registration_status_updated
avs_directory__ownership_transferred
avs_directory__paused
avs_directory__unpaused
delegation__delegation_approver_updated
delegation__deposit_scaling_factor_updated
delegation__initialized
delegation__operator_metadata_u_r_i_updated
delegation__operator_registered
delegation__operator_shares_decreased
delegation__operator_shares_increased
delegation__operator_shares_slashed
delegation__paused
delegation__slashing_withdrawal_completed
delegation__slashing_withdrawal_queued
delegation__staker_delegated
delegation__staker_force_undelegated
delegation__staker_undelegated
delegation__unpaused
eigenpod__beacon_chain_e_t_h_deposited
eigenpod__beacon_chain_e_t_h_withdrawal_completed
eigenpod__beacon_chain_slashing_factor_decreased
eigenpod__burnable_e_t_h_shares_increased
eigenpod__initialized
eigenpod__new_total_shares
eigenpod__ownership_transferred
eigenpod__paused
eigenpod__pectra_fork_timestamp_set
eigenpod__pod_deployed
eigenpod__pod_shares_updated
eigenpod__proof_timestamp_setter_set
eigenpod__unpaused
strategy__burn_or_redistributable_shares_decreased
strategy__burn_or_redistributable_shares_increased
strategy__burnable_shares_decreased
strategy__deposit
strategy__initialized
strategy__ownership_transferred
strategy__paused
strategy__slash_resolution_block_set
strategy__strategy_added_to_deposit_whitelist
strategy__strategy_removed_from_deposit_whitelist
strategy__strategy_whitelister_changed
strategy__unpaused
```

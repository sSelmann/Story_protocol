
## Sync Status

*cometbft_blocksync_syncing*

Indicates whether the node is synchronizing blocks.
Value: Displays 1 if the node is synchronizing and 0 if it is not, helping to diagnose the synchronization status.

## Consensus Height

*cometbft_consensus_height*

Measures the height of the consensus block.
Value: Number representing the last block reached by the node consensus.

## Latest Block Height

*cometbft_consensus_latest_block_height*

This is the number of the highest block processed by the node, indicating whether it is up to date with the network.
Value: Number representing highest block processed by the node.

## Block Size

*cometbft_consensus_block_size_bytes*

Provides the size of individual blocks processed by the node. It reflects the amount of data contained in a block.
Value: Size of each block in bytes.

## Peers Connected

*cometbft_p2p_peers*

Monitors the number of peers connected to the node in the P2P network.
Value: Number of connected peers.

## Chain Size

*cometbft_consensus_chain_size_bytes*

Shows the cumulative size of the blockchain over time.
Value: Total size of the blockchain in bytes.

## Late Votes

*cometbft_consensus_late_votes*

Captures instances of votes received too late in the consensus process.
Value: Number of late votes received by the node.

## Proposal Receive Count

*cometbft_consensus_proposal_receive_count*

Measures the number of block proposals received, categorized by their status (accepted/rejected).
Value: Total number of proposals received.

## Begin Blocker Duration

*cosmos_begin_blocker*

Time taken to execute the begin blocker per Cosmos SDK module.
Value: Execution time distribution (quantiles) for each module.

## End Blocker Duration

*cosmos_end_blocker*

Time taken to execute the end blocker per Cosmos SDK module.
Value: Execution time distribution (quantiles) for each module.

## Consensus Parameter Updates

*cometbft_state_consensus_param_updates*

Counts how many times consensus parameters were updated.
Value: Number of updates since the node started.

## Byzantine Validators Power

*cometbft_consensus_byzantine_validators_power*

Total voting power of validators that engaged in double-signing.
Value: Sum of byzantine validators' power.

## Byzantine Validators

*cometbft_consensus_byzantine_validators*

Counts how many validators have engaged in byzantine behavior.
Value: Number of byzantine validators.

## Duplicate Block Part

*cometbft_consensus_duplicate_block_part*

Instances of receiving the same block part more than once.
Value: Number of duplicate block parts.

## Duplicate Vote

*cometbft_consensus_duplicate_vote*

Occurrences of duplicate votes during consensus.
Value: Number of duplicate votes.

## Number of Transactions

*cometbft_consensus_num_txs*

Shows how many transactions were included in the latest block.
Value: Number of transactions in the most recent block.

## Total Transactions

*cometbft_consensus_total_txs*

Indicates the total transactions processed by the node.
Value: Accumulated number of transactions.

## P2P Message Receive Bytes Total

*cometbft_p2p_message_receive_bytes_total*

Tracks data received for each message type in the P2P network.
Value: Number of bytes received.

## P2P Message Send Bytes Total

*cometbft_p2p_message_send_bytes_total*

Tracks data sent for each message type in the P2P network.
Value: Number of bytes sent.

## GC Pause Time

*cosmos_runtime_gc_pause_ns*

Shows the pause duration caused by garbage collection.
Value: GC pause time in nanoseconds.

## Additional Metrics

### ABCI Method Timings

*cometbft_abci_connection_method_timing_seconds*

Histogram showing response times for ABCI methods like `commit`, `info`, `process_proposal`.

### Round Duration

*cometbft_consensus_round_duration_seconds*

Measures how long each consensus round takes to complete.

### Step Duration

*cometbft_consensus_step_duration_seconds*

Tracks duration of each step in the consensus process (e.g. Propose, Prevote).

### Quorum Delay

*cometbft_consensus_quorum_prevote_delay*

Interval between block proposal and first quorum prevote.

### Voting Power Percent

*cometbft_consensus_round_voting_power_percent*

Percentage of voting power observed in prevote/precommit.

### Validator Power

*cometbft_consensus_validator_power*

Reports the voting power of each validator.

### Log Levels

*lib_log_total*

Total number of log messages per log level (info, error, debug).

### Ethereum Engine Latency

*lib_ethclient_latency_seconds*

Latency histograms for Ethereum engine RPC calls (e.g., new_payload_v3).

### Build Info

*lib_buildinfo_version* / *lib_buildinfo_git_commit*

Static labels reporting current build version and commit hash.

### System Metrics

*process_cpu_seconds_total*, *process_open_fds*, *process_resident_memory_bytes*, etc.

Expose real-time resource usage of the process.

# Story Node Metrics FAQ

## Sync Status  

*cometbft_blocksync_syncing*  

Indicates whether the node is synchronizing blocks.  
Value: Displays 1 if the node is synchronizing and 0 if it is not, helping to diagnose the synchronization status.  
![image](https://github.com/user-attachments/assets/ee4f75ba-2600-4f35-bfda-115d25b7c983)

## Consensus Height  

*cometbft_consensus_height*

Measures the height of the consensus block.  
Value: Number representing the last block reached by the node consensus.  
![image](https://github.com/user-attachments/assets/413fb7ee-6263-416e-8e84-7c3f6e588dd5)

## Latest Block Height

*cometbft_blocksync_latest_block_height*  

This is the number of the highest block processed by the node, indicating whether it is up to date with the network.  
Value: Number representing highest block processed by the node.  
![image](https://github.com/user-attachments/assets/5b472c4d-dfb8-4120-beab-4f164702d099)

## Block Size  

*cometbft_consensus_block_size_bytes*  

This metric provides the size of individual blocks processed by the node. It reflects the amount of data contained in a single block, such as transactions and other relevant information. Monitoring block size is crucial for understanding the network's data throughput and can help in identifying performance issues, especially when block sizes grow too large or remain consistently small.  
Value: size of each block in bytes.  
![image](https://github.com/user-attachments/assets/a4c5f097-4548-4003-b73e-17efc45ba56c)

## State Block  Processing Time  

*cometbft_state_block_processing_time_bucket*  

Measures block processing time. Records the time the node takes to process a block, which helps to evaluate its efficiency.
These metrics are fundamental for monitoring and diagnosing the performance and status of the node in the network.  
Value: histogram representing block times  
![image](https://github.com/user-attachments/assets/3d683ee0-9dfa-4d4d-b95f-db394582366a)

## Chain Size  

*cometbft_consensus_chain_size_bytes*

This metric shows the cumulative size of the blockchain as it grows over time, accounting for all blocks, transactions, and state data. Understanding the chain size helps track data storage requirements and manage resources, especially for nodes with limited storage capacity.  
Value: size of the blockchain in bytes  
![image](https://github.com/user-attachments/assets/39faf527-e104-49cb-8a15-c4a1f67839fc)

## Late Votes   

*cometbft_consensus_late_votes*

This metric captures instances where the node receives votes that are considered "late," meaning they belong to earlier stages of the consensus process. The presence of late votes can indicate network delays, synchronization issues, or potential inefficiencies in message propagation. Monitoring this helps in diagnosing network health and ensuring that nodes are maintaining timely consensus participation.  
Value: number of votes received by the node that correspond to previous heights and rounds than the node’s current state.  
![image](https://github.com/user-attachments/assets/7bf32f7a-9611-4227-b1fa-ca1099e567a7)

## Proposal Receive Count  

*cometbft_consensus_proposal_receive_count*

This metric measures the total count of block proposals that the node has received over time. The proposals are annotated with their status, indicating whether they were accepted or rejected by the consensus process. Monitoring this helps in understanding the node's participation in the consensus mechanism and provides insights into the efficiency and reliability of the proposal process within the network. It is particularly useful for diagnosing any issues with block proposal acceptance rates.  
Value: total number of proposals received by the node since the process started, categorized by status ('accepted' or 'rejected').  
![image](https://github.com/user-attachments/assets/20436329-e905-487e-a8f4-ee7a97571225)

## Token Distribution and Staking
_________________________________

## Staking Delegate  

*cosmos_staking_delegate*

Measures how many times users have delegated tokens to validators, showing staking activity on the network. 

Value: Counts the total number of staking delegations.  
![image](https://github.com/user-attachments/assets/4a250fa0-f90e-4529-ae14-2829bfc0b14c)

## Staking Undelegate  

*cosmos_staking_undelegate*

Displays the total number of undelegate events that have occurred in the network.  
Value: number of times delegations have been withdrawn.  
![image](https://github.com/user-attachments/assets/82c61e25-b06c-493a-8e7a-dc282c939c78)


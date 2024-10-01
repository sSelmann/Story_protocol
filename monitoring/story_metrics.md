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
Value: size of each block in bytes  
![image](https://github.com/user-attachments/assets/a4c5f097-4548-4003-b73e-17efc45ba56c)



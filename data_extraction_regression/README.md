# Data extraction regression
This jupyter notebook presents our findings in time taken to extract data from ethereum node. Block time of ethereum mainnet is ~15 seconds, if certain data extraction functions take more than 15 seconds to pull data from a node then a block explorer using these functions will fall behind the ethereum chain.

In this notebook we take one such heavy function, which is used commonly in block explorers to access the internal transactions, and demonstrate that if gas_used increases to more than 12 million units, getting internal transactions will take greater than 15 seconds and the block explorers will start lagging behind the main chain. 

## Key findings:
1. Even at the current 8M gas limit we sometimes overshoot the 15 second time limit.
2. The time taken to extract transaction traces depends on complexity of the contract codes and gas used in the block.
3. If gas used increases to more than 12M then we would consistently start hitting this time limit.
4. The above value of gas limit assumes that transactions in the block are not complex contract calls.
5. It is possible to find specific OPCODE's which might create complicated contracts making the extraction exceed the time-limit at lower gas limits. 
6. One method to bypass this bottleneck is developing ethereum nodes optimized in data-delivery.

## Notebook: 
https://github.com/analyseether/research/blob/master/data_extraction_regression/data_gathering.ipynb

## Presentation:
https://youtu.be/hvCOHdcXtDs?t=5m47s

## How to rerun the notebook
0. Have an archive node synced upto 5M blocks.
1. Install python3
2. Clone the research repo.
3. Install dependencies from requirements.txt: `$ pip install -r requirements.txt`
4. Open the notebook using: `>>> jupyter notebook`

## Questions:
Tweet to @AnalyseEther

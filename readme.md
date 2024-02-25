# mpunksminer

## Archival notice

This project is for archival purposes only. It was written back in 2021. It currently does not compile due to breaking changes in Zig. Git history was wiped.

This is a thirdparty "miner" for the https://www.mpunks.org project. These NFTs were only mintable if you had a 128 bit integer
that would produce a KECCAK-256 hash that fit the conditions in the ETH contract (or something along those lines, I'm not sure exactly, it's been a while).
When this project was first released, the official miner was a web worker script (Javascript running on browser).
This was the first miner that ran directly on CPU and GPU.
The KECCAK-256 C hasher in `src/miner.cl` is taken from [the solidity codebase](https://github.com/ethereum/solidity/blob/develop/libsolutil/Keccak256.cpp).

## Warning: there are no downloads available, you will have to compile this yourself.

## Warning 2: this miner does not check if the nonce produces one of the OG punks, you must do this yourself before minting!

- cpu and (multidevice) opencl support
- ignore the "error: " prefix on console, those are not actually errors :p
- 5 MH/s on a "2,3 GHz Dual-Core Intel Core i5" cpu, 20 MH/s on a "Intel Iris Plus Graphics 640 1536 MB" gpu

## Running

Bare minimum options:

```
./mpunksminer --wallet 725aEF067EeE7B1eB7B06A7404b7b65afa04193B
```

All options:

```
	-h, --help            	Display help.
	-g, --gpu             	Use GPU, default is CPU.
	-m, --multi           	Use all OpenCL GPUs available.
	-t, --threads <NUM>   	Amount of threads.
	-w, --wallet <STR>    	ETH wallet address.
	-l, --lastmined <NUM> 	Last mined punk.
	-d, --difficulty <NUM>	Difficulty target.
	-i, --increment <NUM> 	# of hashes per cpu thread.
	--test	            	Run in test mode.
```

## Building

- Download [Zig](https://ziglang.org/download/)

## TODO

- Integrate with the official miner controller
- MAYBE: Record processed nonces in DB?
- MAYBE: Add option to set the starting nonce?

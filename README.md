# Simple Blockchain in Python

This is a simple blockchain implementation in Python using the Flask web framework. This blockchain allows you to create transactions, mine blocks, register nodes, and achieve consensus among nodes in a decentralized network.

## How it Works

### Blockchain Class

- **Blockchain class**: This class initializes the blockchain, manages the list of blocks (`chain`), current transactions (`current_transactions`), and a set of nodes in the network (`nodes`).

- `register_node(address)`: Add a new node to the network by specifying its address (e.g., 'http://192.168.0.5:5000').

- `valid_chain(chain)`: Determine if a given blockchain is valid by checking the correctness of block hashes and proof of work.

- `resolve_conflicts()`: Resolve conflicts in the network by replacing the local chain with the longest valid chain among neighboring nodes.

- `new_block(previous_hash, proof)`: Create a new block in the blockchain with the provided `previous_hash` and `proof`. This function also resets the list of current transactions.

- `hash(block)`: Calculate the SHA-256 hash of a given block.

- `last_block`: A property that returns the last block in the blockchain.

- `new_transaction(sender, recipient, amount)`: Create a new transaction to be included in the next mined block.

- `proof_of_work(last_proof)`: Implement a simple proof-of-work algorithm to find a valid proof for mining a new block.

- `valid_proof(last_proof, proof)`: Validate a proof by checking if the hash of the concatenated values `last_proof` and `proof` starts with four leading zeros.

### Flask Web Application

The Flask application provides HTTP endpoints for interacting with the blockchain:

- `/nodes/register` (POST): Allow you to register new nodes by providing a list of node addresses.

- `/nodes/resolve` (GET): Resolve conflicts by achieving consensus among nodes and return the status.

- `/mine` (GET): Mine a new block and reward the miner with one unit of the cryptocurrency.

- `/chain` (GET): Retrieve the full blockchain and its length.

- `/transactions/new` (POST): Create a new transaction by providing sender, recipient, and amount.

## How to Run

1. Make sure you have Python and Flask installed.

2. Copy the provided code into a Python file (e.g., `blockchain.py`).

3. Run the Python script.

```bash
python blockchain.py

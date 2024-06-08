# SmartFlaker

  # 1.Install Requirements
  # 1.1 Solidity Compiler
    sudo add-apt-repository ppa:ethereum/ethereum
    sudo apt-get update
    sudo apt-get install solc
  # 1.2 Z3 Prover
  Download the https://github.com/Z3Prover/z3/releases/tag/Z3-4.8.5
    
    Install z3 using Python bindings
    python scripts/mk_make.py --python
    cd build
    make
    sudo make install
# 2. Install Fuzzer
    cd fuzzer
    pip install -r requirements.txt
# 3. Running instructions
    usage: main.py [-h] (-s SOURCE | -a ABI) [-c CONTRACT] [-b BLOCKCHAIN_STATE] [--solc SOLC_VERSION] [--evm EVM_VERSION] [-g GENERATIONS | -t GLOBAL_TIMEOUT] [-n POPULATION_SIZE] [-pc PROBABILITY_CROSSOVER] [-pm PROBABILITY_MUTATION]
               [-r RESULTS] [--seed SEED] [--cfg] [--data-dependency DATA_DEPENDENCY] [--constraint-solving CONSTRAINT_SOLVING] [--environmental-instrumentation ENVIRONMENTAL_INSTRUMENTATION]
               [--max-individual-length MAX_INDIVIDUAL_LENGTH] [--max-symbolic-execution MAX_SYMBOLIC_EXECUTION] [-v]

    optional arguments:
    -h, --help            show this help message and exit
    -s SOURCE, --source SOURCE
                        Solidity smart contract source code file (.sol).
    -a ABI, --abi ABI     Smart contract ABI file (.json).
    -c CONTRACT, --contract CONTRACT
                        Contract name to be fuzzed (if Solidity source code file provided) or blockchain contract address (if ABI file provided).
    -b BLOCKCHAIN_STATE, --blockchain-state BLOCKCHAIN_STATE
                        Initialize fuzzer with a blockchain state by providing a JSON file (if Solidity source code file provided) or a block number (if ABI file provided).
    --solc SOLC_VERSION   Solidity compiler version (default '0.6.12'). Installed compiler versions: [Version('0.6.12'), Version('0.4.26'), Version('0.4.25')].
    --evm EVM_VERSION     Ethereum VM (default 'petersburg'). Available VM's: 'homestead', 'byzantium' or 'petersburg'.
    -g GENERATIONS, --generations GENERATIONS
                        Number of generations (default 10).
    -t GLOBAL_TIMEOUT, --timeout GLOBAL_TIMEOUT
                        Number of seconds for fuzzer to stop.
    -n POPULATION_SIZE, --population-size POPULATION_SIZE
                        Size of the population.
    -pc PROBABILITY_CROSSOVER, --probability-crossover PROBABILITY_CROSSOVER
                        Size of the population.
    -pm PROBABILITY_MUTATION, --probability-mutation PROBABILITY_MUTATION
                        Size of the population.
    -r RESULTS, --results RESULTS
                        Folder or JSON file where results should be stored.
    --seed SEED           Initialize the random number generator with a given seed.
    --cfg                 Build control-flow graph and highlight code coverage.
    --data-dependency DATA_DEPENDENCY
                        Disable/Enable data dependency analysis: 0 - Disable, 1 - Enable (default: 1)
    --constraint-solving CONSTRAINT_SOLVING
                        Disable/Enable constraint solving: 0 - Disable, 1 - Enable (default: 1)
    --environmental-instrumentation ENVIRONMENTAL_INSTRUMENTATION
                        Disable/Enable environmental instrumentation: 0 - Disable, 1 - Enable (default: 1)
    --max-individual-length MAX_INDIVIDUAL_LENGTH
                        Maximal length of an individual (default: 5)
    --max-symbolic-execution MAX_SYMBOLIC_EXECUTION
                        Maximum number of symbolic execution calls before restting population (default: 10)
    -v, --version         show program's version number and exit
# 4. Running
    python3 fuzzer/main.py -s path/to/contract.sol -c contract --seed SEED --solc v0.4.26 --evm byzantium -g 100(Random)
    python3 fuzzer/main.py -s path/to/contract.sol -c contract --constraint-solving CONSTRAINT_SOLVING --max-symbolic-execution MAX_SYMBOLIC_EXECUTION --seed SEED --solc v0.4.26 --evm byzantium -g 100(Seed Strategy)
    python3 fuzzer/main.py -s path/to/contract.sol -c contract --data-dependency DATA_DEPENDENCY --constraint-solving CONSTRAINT_SOLVING --max-symbolic-execution MAX_SYMBOLIC_EXECUTION --seed SEED --solc v0.4.26 --evm byzantium -g 100(SmartFlaker)

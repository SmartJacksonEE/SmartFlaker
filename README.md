# Installation Instructions
  # 1. Install Requirements
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

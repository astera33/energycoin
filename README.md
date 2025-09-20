EnergyCoin integration/staging tree
==================================

Copyright (c) 2014-2025 EnergyCoin Developers

Change Log
---------
v1.6.2.0:
- Add auto create EnergyCoin.conf & auto generate rpc user - rpc password
- Update checkpoints
- Added DNS seeds
- Update the new EnergyCoin ico & EnergyCoin icon logo
- Change RPC Port connection to 22705, Fix error rpc connection

v1.6.1.0:
- Add VOut parameter in listsinceblock and gettransaction RPC methods
- Update checkpoints

v1.6.0.0 (Mandatory Update):
- New network protocol version 70004
- New fork:
  * Start at block height 2390000
  * Add support for Energyparty op_return transactions
  * Reduce standard transaction fee to 0.001 ENRG per kbyte
  * Add soft fork logic: define confirmation window and 95% rule
- Migration to LevelDB for transaction index database files
- Add transaction index database version 60117
- Add a startup option (-splitblkfiles) to enable splitting blk0001.dat into files of maximum 500 MB each.
- Add a startup option (-disabledebuglog) to disable debug.log
- Fix checking redeemScript size when adding multisig address
- Fix signrawtransaction and sendrawtransaction RPC calls to support multisig redeem scripts
- Fix error in showing scriptPubKey
- Warn users if loading multisig addresses with too-long redeemScripts that can never be redeemed
- Show redeem script in validateaddress RPC call
- Increase the standard transaction txin threshold to allow a maximum of 15-of-15 P2SH multisig
- Treat blocks with old nVersion as DoS attempt
- New design of EnergyCoin logo
- Update checkpoints
- Remove some unnecessary codes and trim some debug messages

v1.5.1.0:
- Add "Unlock for minting only" option in GUI
- BugFix: Proper use of custom change address in CoinControl
- BugFix: Matching transaction inputs with selected coins in CoinControl
- Ban peers with old protocol version
- Update checkpoints
- Update coin spec in README.md
- Remove PoW miner.
- Remove some more unnecessary codes and simplify some debug messages

v1.5.0.0 (Mandatory Update):
- New network protocol version 70003
- New fork:
  * Start at block height 2100000;
  * New PoS minimum difficulty;
  * New target block time;
  * New coinstake kernel protocol;
  * Change PoS reward to a fixed amount;
  * No longer accepting PoW blocks
- Security updates, such as:
  * Avoid DoS attacks by limiting the maximum size of orphan blocks and maximum number of orphan transactions in memory;
  * Treat non-empty coinbase in PoS blocks as DoS attempt;
  * Treat overwriting transactions against BIP30 as DoS attempt;
  * Avoid timedrift attacks by reducing the maximum clockdrift allowance;
  * Reduce amount that peers can adjust our time to minimize Time-Offset attack vector;
  * Do not bias outgoing connections towards fresh addresses (ref. Countermeasure 2 in Eclipse Attacks);
  * Deprioritize 66% after each failed connection attempt;
  * Avoid RPC password attacks by implementing timing-attack-resistant comparison;
  * Do not reveal if using short RPC passwords;
  * Do not alow PRC username and RPC password to be the same;
  * Fix for OpenSSL handling of DER signatures;
  * Avoid OpenSSL config file load/race
  * Fix invalid signature with crafted length;
  * Avoid invalid memory access on crafted signature;
  * Disable uPNP by default;
  * Avoid fingerprinting attacks by ignoring getaddr messages on outbound connections;
  * No longer using the old checkpoint and alert keys
- New allowable range of stakesplitthreshold
- Add new command: sendsplit (allow users to split into multiple outputs easily when sending coins)
- Add GUI indicator of PoS weight and estimated time for reward
- Extend getmininginfo to contain staking-related information
- Make coin selection without random shuffle for smoother staking
- Avoid socket leaks for BindListenPort
- Update checkpoint
- Remove some unnecessary codes and debug messages

v1.4.0.0:
- Reduce CPU consumption and reduce memory leaks, such as:
  * CheckBlock optimizations;
  * Disable block validity check during initial startup (can restore with -checklevel=1);
  * Skip stake modifier checksum and fStrictPayToScriptHash checks;
  * Skip scanning transactions earlier than the first key in wallet;
  * Avoid rescanning more than once for wallet start;
  * Reduce memory leaks for signing keys, processing scripts and orphans etc;
  * Clear memory used by random number generator;
  * Skip relay to peers before they send version message;
  * Skip peers older than one week;
  * Reduce socket leaks;
  * Skip reading sockets if draining write queue;
  * Skip preliminary checks if earlier than the last checkpoint timestamp;
  * Avoid multiblocks reorg transaction resurrection;
  * Avoid frequent bestblock updates to wallet;
  * Avoid frequent address dumps;
  * Avoid frequent balance check for every transaction;
  * Avoid staking before sync;
  * Avoid orphans by previous block check before staking;
  * GetHash caching and map hashed blocks for smoother staking;
  * Avoid staking for dusts or zero reward;
  * Remove console command if already in history;
  * Remove some unnecessary codes and debug messages
- Other performance tweaks, such as:
  * Enable mfpmath, native arch and prefetch for g++;
  * Enable DB_LOG_AUTO_REMOVE;
  * Simplify CMutexLock;
  * Remove mapProofOfStake;
  * Optimistic TCP write queue control
- Update checkpoint
- BugFix: Make sure balance is shown even if no any bestblock record

v1.3.0.0:
- Add a new setstakesplitthreshold function on console (default 250). This can avoid fragmentation by setting a threshold for stake-splitting
- Update checkpoint and fix the "checkpoint too old" issue
- Fix an invalid conversion error when compiling on Windows
- Fix a multiple definition error when compiling on Linux

What is EnergyCoin (ENRG)?
------------------------

EnergyCoin is a pure PoS coin which generates coins through PoS blocks. Except the first block where it generates the initial 101 million coins, no PoW mining will get any coins. All every person has to do is post it on our facebook, twitter or reddit page, and add a signature to btctalk profile. Its easy and free!

After distribution is over energycoin is  mineable by simply running your wallet. Thus a huge mining cost of hardware and millions of electricity costs are saved.

Before block height 2.1m, EnergyCoin adopted a variable PoS rate with the following annual interest rate:
Year-1: 10%
Year-2: 8%
Year-3: 6%
Year-4: 4%
Year-5: 2%
Year 6 has only 1% of annual interest.

After block height 2.1m, EnergyCoin adopts a fixed PoS block reward of 5 ENRG.

-150 seconds target block time.
-Difficulty retarget is based on each block ensures to keep the difficulty logical
-Scarce but not too scarce to be uninteresting or not usable. 101 million coins in distribution and interest values were decided to make sure the coin retains its value


Ports:
RPC:	22705
P2P:	22706


Support Development by Donation: ePvnQvX5RbzDCzt3qSB5TmBz89BJMvpG46


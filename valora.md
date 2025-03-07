---
title: "Valora: A Human-Centric Digital Currency for Universal Financial Freedom"
author: |
  Luciana Ferreira  
  Fatec—Faculdade de Tecnologia de São Paulo
date: "2025-03-07"
---

Valora is a decentralized digital currency that establishes Proof-of-Personhood (PoP) as its core 
consensus mechanism, ensuring that every unique human obtains an equal voting share in block 
production and validation. Unlike Proof-of-Work or Proof-of-Stake protocols, which naturally 
concentrate power in the hands of resourceful miners or large stakeholders (Gervais, Ritzdorf, 
Karame, & Capkun, 2016; Nakamoto, 2008), Valora precludes such monopolies by anchoring governance 
rights to verifiable human identities. It enforces privacy by default, leveraging advanced 
cryptography to shield all transactional data, and employs a minimal, UTXO-based ledger to 
streamline security and preserve performance. The overarching goal is to create a 
censorship-resistant payment system that just works for global users, including those in 
low-connectivity or politically restricted settings (Androulaki, Karame, Roeschlin, Scherer, & 
Capkun, 2013).

The protocol’s principal innovation is its reliance on PoP to allocate one credential per real 
human participant (Baum, 2016). This approach obviates the “one-CPU–one-vote” or “one-stake–one-vote” 
paradigms that often result in resource- or wealth-based centralization (Badev & Chen, 2014). PoP 
ceremonies, which can be in-person or online Turing tests, verify users without demanding personal 
details on-chain. The system admits only those credentials that meet concurrency checks (no 
individual can appear at multiple ceremonies simultaneously), making identity infiltration far more 
difficult than simply accumulating hashing power or tokens. By using multiple independent 
communities to host ceremonies, Valora distributes trust away from a single agency. The blockchain 
converges on which identity proofs to accept only when no contradictions arise. Should someone 
attempt to produce thousands of fake identities, they must circumvent these concurrency 
requirements, a task orders of magnitude harder than controlling mining pools.

Leader selection for block proposals proceeds by randomly sampling from this PoP-verified pool, 
ensuring every identity is chosen roughly in proportion to its single share (Lenstra & Wesolowski, 
2017). Over repeated intervals, block production thus remains equitably distributed. Once a proposer 
is designated, it references the previous block’s hash, compiles valid transactions, signs the block 
header with its private key, and broadcasts it. Peers verify that the block belongs to an authentic 
identity credential and that its transactions meet UTXO correctness rules. The resulting structure 
strongly mitigates the risk of a 51% attack (Nakamoto, 2008) because compromising the chain requires 
subverting over half of globally recognized participants, a challenge far more demanding than 
amassing specialized hardware in Proof-of-Work.

Valora’s network layer is a decentralized mesh that relies on gossip protocols and possible fallback 
communication channels like SMS or satellite broadcasts (Decker & Wattenhofer, 2013). Nodes discover 
each other via seed addresses or DHT-based lookups, forming an unstructured overlay. Traffic is 
encrypted to hamper censorship and packet inspection, and users in high-restriction regions can 
connect through anonymity networks like Tor (Dingledine, Mathewson, & Syverson, 2004). The system 
thereby maintains connectivity even under aggressive interference, since adversaries must block an 
unfeasibly large fraction of global nodes to silence the ledger.

Valora’s ledger design follows a UTXO structure that is conducive to both privacy and parallel 
verification (Karame, Androulaki, & Capkun, 2012). Each transaction cites one or more outputs as 
inputs, proving ownership cryptographically, and creates new outputs assigned to fresh addresses. 
Because transactions specify discrete references, nodes can validate them concurrently without 
touching a global account state. Blocks need not carry arbitrary data: the protocol disallows 
embedding additional information in outputs or transaction fields beyond what is essential for 
currency functionality. Historical investigations into blockchain usage indicate that arbitrary 
data, if permitted, leads to ledger bloat and tangential or even problematic payloads that cannot 
easily be pruned (Navarro-Arribas, 2018). By prohibiting free-form on-chain data, Valora preserves 
node accessibility and avoids potential liabilities.

Privacy by default is another principal commitment, satisfied through ring signatures, stealth 
addresses, and range proofs. Ring signatures obscure which input key in a set of decoys is genuinely 
being spent (Rivest, Shamir, & Tauman, 2001). Stealth addresses allocate ephemeral one-time addresses 
to recipients, preventing outsiders from mapping transactions to individuals (Abe, Ohkubo, & Suzuki, 
2002). Range proofs, such as Bulletproofs (Bünz, Bootle, Boneh, Poelstra, Wuille, & Maxwell, 2018), 
or zero-knowledge proofs (Groth, 2016) conceal amounts while permitting nodes to confirm that no 
hidden inflation occurs. This design aligns with the robust anonymity model previously explored by 
systems like Monero or Zcash (Fujisaki & Suzuki, 2007). The ledger itself stores only obfuscated 
references: it is infeasible for an external observer to determine which inputs belong to which 
outputs, or how much value is transferred. The result is an effectively fungible coin supply that 
resists blacklists or forced reidentification.

The architecture supports fast block intervals (e.g., around one minute or less) since there is no 
computational race to generate proofs-of-work. Although rapid intervals can increase potential forks, 
the randomness-based consensus limits block proposer collisions, and optionally, a committee of 
random identities can quickly finalize each block (Castro & Liskov, 2002). This approach 
substantially improves throughput and confirmation times relative to Bitcoin (Nakamoto, 2008). If 
load grows further, participants can rely on off-chain channels or rollups (Buterin, 2018) to batch 
many transactions, leaving the main ledger for settlement and high-value operations. Sharding could 
also be explored, distributing the UTXOs and identity sets across multiple shards so that 
cross-shard communication references a single global PoP registry (Karame et al., 2012). These 
adaptations ensure that Valora remains decentralized even under high usage.

Valora’s security model addresses classical threats: Sybil attacks are blocked by concurrency-limited 
PoP verification, 51% infiltration is rendered nearly impossible by requiring a majority of the 
global user base, censorship is undermined by private transactions and unstructured gossip, and 
denial-of-service attempts are constrained by transaction fees plus local rate limiting (Boneh & 
Shoup, 2020). Governance is likewise PoP-based: critical updates, such as ring signature parameter 
changes or inflation tuning, must pass a one-human–one-vote process that cannot be swayed merely by 
holding tokens (Buterin, 2018). Such governance is less susceptible to wealthy coalitions or miner 
groups forcibly altering protocol rules.

The monetary policy, reflecting the system’s egalitarian ethos, mints a fixed initial supply (ten 
billion “Vals”) and distributes a set allotment (e.g., one thousand Vals) to each newly verified 
identity. Should user adoption exceed that supply, the chain triggers a mild inflation (e.g., one to 
two percent annually), which preserves equal rights for latecomers without generating unchecked 
dilution (Badev & Chen, 2014). The minimal transaction unit is one Val, so typical everyday payments 
might simply be denominated in single integer units. If sub-Val denominations become necessary, 
PoP-governed proposals can add them. This balance between convenience and identity-based fairness 
aims to improve upon Bitcoin’s halving schedule, which can disadvantage late adopters (Nakamoto, 
2008), and to avoid resource-based reward structures that concentrate economic power among a handful 
of industrial participants.

Production readiness demands thorough cryptographic audits and concurrency-safe node implementations. 
While this paper refrains from focusing on one specific programming language, it does require 
memory-safe development frameworks for the node software, concurrency primitives to handle multiple 
peer connections, and well-reviewed cryptographic libraries to handle ring signatures or 
zero-knowledge proofs (Groth, 2016). Each client must handle the entire chain verification, from PoP 
identity checks to private transaction logic, ensuring that every node can detect invalid states 
early. Multi-client diversity is strongly encouraged, mitigating the risk of a single software 
exploit (Decker & Wattenhofer, 2013).

In essence, Valora builds on the lessons of Bitcoin yet corrects many of its structural shortcomings: 
it eliminates the arms race for hashpower, integrates privacy at the protocol level rather than as an 
afterthought, and places governance in the hands of unique individuals rather than large capital 
holders. Coupled with layer-2 expansions and flexible design for future cryptographic upgrades, 
Valora aspires to realize an equitable, decentralized, and censorship-resistant global currency that 
truly serves the entire population. By insisting on human identity as the primary scarce resource 
and guaranteeing anonymity for all ordinary transactions, Valora seeks to rekindle the original 
promise of digital cash: a neutral, user-protective financial infrastructure accessible to all, 
even under the most constraining socio-political conditions.

# References

**Abe, M., Ohkubo, M., & Suzuki, K. (2002).** 1-out-of-n Signatures from a Variety of Keys. 
*IEICE Transactions on Fundamentals of Electronics, Communications and Computer Sciences*, 
E87-A(1), 415–432. DOI: 10.1007/3-540-36178-2_26

**Androulaki, E., Karame, G., Roeschlin, M., Scherer, T., & Capkun, S. (2013).** Evaluating user 
privacy in Bitcoin. *Financial Cryptography and Data Security*, 34–51

**Badev, A. I., & Chen, M. (2014).** *Bitcoin: Technical background and data analysis (Finance and 
Economics Discussion Series 2014-104)*. Board of Governors of the Federal Reserve System

**Baum, E. B. (2016).** *On proof-of-personhood for Sybil defense in decentralized systems*. 
arXiv preprint arXiv:1604.06018

**Boneh, D., & Shoup, V. (2020).** *A graduate course in applied cryptography*. Draft version

**Bünz, B., Bootle, J., Boneh, D., Poelstra, A., Wuille, P., & Maxwell, G. (2018).** Bulletproofs: 
Short proofs for confidential transactions and more. *2018 IEEE Symposium on Security and Privacy*, 
315–334

**Buterin, V. (2018).** A next-generation smart contract and decentralized application platform. 
*Ethereum White Paper*

**Castro, M., & Liskov, B. (2002).** Practical Byzantine fault tolerance and proactive recovery. 
*ACM Transactions on Computer Systems (TOCS)*, 20(4), 398–461

**Decker, C., & Wattenhofer, R. (2013).** Information propagation in the Bitcoin network. 
*2013 IEEE P2P Conference*, 1–10

**Dingledine, R., Mathewson, N., & Syverson, P. (2004).** Tor: The second-generation onion router. 
*Proceedings of the 13th USENIX Security Symposium*, 303–320

**Fujisaki, E., & Suzuki, K. (2007).** Traceable Ring Signature. In *Public Key Cryptography – PKC 
2007* (Lecture Notes in Computer Science, vol. 4450, pp. 181–200). Springer. 
DOI: 10.1007/978-3-540-71677-8_13

**Groth, J. (2016).** On the size of pairing-based non-interactive arguments. *Advances in Cryptology 
– EUROCRYPT 2016*, 305–326

**Karame, G., Androulaki, E., & Capkun, S. (2012).** Double-spending fast payments in Bitcoin. 
*Proceedings of the 2012 ACM Conference on Computer and Communications Security*, 906–917

**Lenstra, A. K., & Wesolowski, B. (2017).** Trustworthy public randomness with sloth, unicorn, and 
trx. *International Journal of Applied Cryptography*, 3(4), 330–343. 
DOI: 10.1504/IJACT.2017.10010315

**McCoy, D., Bauer, K., Grunwald, D., Kohno, T., & Sicker, D. (2008).** Shining light in dark places: 
Understanding the Tor network. In *Proceedings of the 8th Privacy Enhancing Technologies Symposium 
(PETS)* (pp. 63–76). Springer

**Nakamoto, S. (2008).** *Bitcoin: A peer-to-peer electronic cash system*. Cryptography Mailing List

**Navarro-Arribas, G. (2018).** Investigations on ledger bloat. *Journal of Blockchain Studies*, 
12(3), 245–260

**Rivest, R. L., Shamir, A., & Tauman, Y. (2001).** How to leak a secret. *Advances in Cryptology – 
ASIACRYPT 2001*, 552–565

---
id: <leave blank -- will be assigned by reviewers>
title: Predatory Qualification Pools: An SBA to MEV Isomorphism
team: Dilia Wood (lead)
created: 2026-08-16
---

# Predatory Qualification Pools: An SBA to MEV Isomorphism

> Status: Flashbots FRP intake is currently paused. This proposal is published here as work in
> progress rather than as a live submission. The research is being carried out in the meantime so
> that a complete proposal, with results attached, can be submitted when intake reopens.

## Summary

This proposal tests whether retail user losses to MEV on Ethereum are structurally isomorphic to information-asymmetry extraction in secured small business lending, and whether that isomorphism predicts which mitigations will work.

The hypothesis is that three mechanisms recur across both systems and that they are separable. First, consolidated visibility: one party can observe the full set of pending obligations while the counterparty cannot. Second, asymmetric ordering authority: one party decides sequence and inclusion, and that discretion is economically valuable. Third, intermediary middleware that monetises the gap between the two. In secured lending these appear as the qualification pool, underwriting discretion, and servicing or liquidation intermediaries. On Ethereum they appear as the public mempool, block building, and the relay and builder market. If the mapping holds, it makes a testable prediction: mitigations that reduce visibility while leaving ordering discretion intact should underperform mitigations that constrain ordering discretion directly. That prediction bears on encrypted mempools and on enshrined proposer-builder separation, both of which act more strongly on visibility than on discretion.

The methodology has four parts. Quantify retail sandwich-style losses on Ethereum over a defined period, segmented by transaction size and user class, to establish the loss base. Build a structural taxonomy of exposure, distinguishing exposure arising from visibility from exposure arising from ordering authority. Evaluate current ePBS and encrypted-mempool designs against that taxonomy to identify which category each addresses. Model a transparent protocol fee alternative in which extraction is burned or returned rather than auctioned, and test whether validator economics can be preserved under it.

The limitations are substantial and stated up front. The isomorphism is structural, not causal: shared architecture does not establish shared mechanism, and the lending comparison rests on one fully documented borrower file plus public SBA policy rather than a statistical sample. MEV loss attribution is contested, and on-chain data cannot observe intent, so any loss figure is a modelled estimate with assumptions that must be published alongside it. The proposed fee mechanism is a design sketch intended to be attacked, not an implementation. The analogy between traditional finance and on-chain extraction is not itself novel; it is the founding frame of this research area. What is offered here is a narrower mapping, to secured lending rather than to equities market microstructure, on the grounds that secured lending captures irreversibility in a way equities does not: a borrower who has signed a personal guarantee cannot cancel the order.

The implication, if the pattern holds, is that the ecosystem is currently investing in the weaker of two mitigation classes. Encryption hides the contents of the waiting room. It does not remove the waiting room, and in lending the analogous move reliably failed, because an intermediary who controls sequence can price exposure from timing, source, and size without reading the file. That is a falsifiable claim and this work is designed to falsify it.

## Background and Problem Statement

Secured small business lending in the United States and block production on Ethereum are not obviously related systems. They share a structural feature that this proposal argues is the operative one: in both, a party who cannot observe the ordering process must nonetheless commit irreversibly before that process runs.

A borrower entering a qualification pool submits a complete financial position to a party who can see every other applicant's position, who decides sequence and terms, and whose compensation depends on the outcome. The borrower cannot see the pool, cannot see the ordering, and signs a personal guarantee before learning either. A retail user submitting a swap broadcasts intent to a public mempool, where searchers observe it, builders sequence it, and relays intermediate. The user cannot see the ordering and cannot revoke the intent once broadcast.

The research questions are:

1. How large are retail sandwich-style losses on Ethereum, segmented by user class, and how sensitive is that figure to attribution assumptions?
2. Which category of exposure do current ePBS and encrypted-mempool designs actually reduce: visibility, or ordering authority?
3. Can an inclusion and fee mechanism that constrains ordering discretion preserve validator economics, and at what cost?

The second question is the one this proposal is most interested in, because it is where the lending comparison generates a non-obvious prediction rather than a restatement.

A known objection, stated here rather than left for review: proposer-builder separation exists because without it smaller validators cannot compete at block building, and the network centralizes anyway. Any mechanism that reduces builder power has to answer that, and the fee alternative modelled here is a direction rather than a finished design.

## Plan and Deliverables

Six weeks, four phases.

**Weeks 1 to 2. Loss quantification.** Assemble the on-chain dataset and produce segmented retail loss estimates with explicit, published attribution assumptions and a sensitivity analysis across them.

**Week 3. Taxonomy.** Construct the exposure taxonomy separating visibility-derived from ordering-derived exposure, with worked examples from both domains.

**Week 4. Design evaluation.** Assess current ePBS and encrypted-mempool proposals against the taxonomy. Identify which residual exposures each leaves open.

**Weeks 5 to 6. Mechanism and write-up.** Model the transparent protocol fee alternative, test validator economics under it, and produce the report.

Deliverables:

- A research report of 5,000 to 7,000 words
- An exposure vulnerability taxonomy, published separately as a reusable artifact
- A concrete transparent-protocol-fee alternative specification, written to be attacked
- Open analysis artifacts: datasets and notebooks sufficient for independent replication

All artifacts published openly, whether or not the work is grant supported.

Indicative budget if intake reopens: $15,000 over six weeks, matching the MEV Fellowship structure.

## References

- Daian et al., *Flash Boys 2.0: Frontrunning, Transaction Reordering, and Consensus Instability in Decentralized Exchanges* (2019)
- U.S. Small Business Administration, SOP 50 10 8, effective 1 March 2026
- Flashbots documentation on MEV-Boost, builders and relays
- Current enshrined proposer-builder separation specifications and the associated inclusion-list designs
- Flashbots Collective forum, FRP category, prior proposals on encrypted mempools and batched-threshold encryption

Companion essay: [The Waiting Room: What Secured Lending Predicts About MEV](https://www.diliawood.com/notes-in-web3-mev/)

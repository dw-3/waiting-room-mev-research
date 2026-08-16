# The Waiting Room

Research on extraction in ordering and visibility layers.

**Status:** in progress. Flashbots FRP intake is currently paused. This work is being carried out independently in the meantime, with artifacts published openly so that a proposal can go in complete when intake reopens.

## The question

Are retail user losses to MEV on Ethereum structurally isomorphic to information-asymmetry extraction in secured lending, and does that isomorphism predict which mitigations will work?

Three mechanisms recur in both systems, and they appear to be separable:

1. **Consolidated visibility.** One party observes the full set of pending obligations; the counterparty does not.
2. **Asymmetric ordering authority.** One party decides sequence and inclusion, and that discretion is economically valuable.
3. **Intermediary middleware** that monetises the gap between the two.

If the mapping holds it makes a testable prediction: mitigations that reduce visibility while leaving ordering discretion intact should underperform mitigations that constrain ordering discretion directly. That bears on encrypted mempools and on enshrined proposer-builder separation, both of which act more strongly on visibility than on discretion.

## Contents

- `qualification-pools-mev-isomorphism.md` : the research proposal, in Flashbots FRP template format.

## Planned artifacts

- A research report of 5,000 to 7,000 words
- An exposure vulnerability taxonomy separating visibility-derived from ordering-derived exposure
- A transparent protocol fee alternative specification, written to be attacked
- Open datasets and notebooks sufficient for independent replication

## Background

Essay: [The Waiting Room: What Secured Lending Predicts About MEV](https://www.diliawood.com/notes-in-web3-mev/)

Forum thread: [Predatory Qualification Pools, SBA to MEV Isomorphism](https://collective.flashbots.net/t/frp-xxx-predatory-qualification-pools-sba-mev-isomorphism/5482)

## About

Dilia Wood documents the full arc of an SBA loan, 7(a) and 504, from the borrower's side at [DiliaWood.com](https://www.diliawood.com). She takes no lender compensation.

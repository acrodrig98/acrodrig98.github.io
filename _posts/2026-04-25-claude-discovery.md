---
layout: default
title: "Can LLMs actually discover something new in astronomy?"
date: 2026-04-25
categories: general
---

# Can LLMs actually discover something new in astronomy?

### Background
A few weeks ago I found a new binary star — a rare type called an AM CVn, in which two white dwarfs orbit each other every 20 minutes, so close together that they ripple the fabric of spacetime as they spiral inward. There are only about 150 of these systems known anywhere in the Galaxy, but only about a dozen are known to be this compact --- with orbital periods of about 20 minutes or shorter. Finding new ones matters: they will be among the brightest gravitational-wave sources for ESA's upcoming LISA space mission, and some are candidate progenitors of certain types of supernovae.

AM CVn binaries are quite blue (first image below), and the gravitational waves they emi be detectable by LISA in the 2030s (second image below).
![spectroscopy](/assets/amcvn.jpg)![spectroscopy](/assets/LISA.jpg)
Sources: Mark Garlick SpaceArt, European Space Agency


The discovery hasn't been published yet. Nothing about this specific source exists in any catalog, paper, or webpage that an AI model could have read. So I had a clean opportunity to ask: can Claude actually find it?

## Two Tests for Claude
### Experiment A: Needle in a Box of Sticks
I designed two experiments. The full results will be written up as a scientific paper, but here's the short version.
Experiment A — needle in a box of sticks. I gave Claude 29 reduced telescope spectra from the Magellan Baade telescope, calibration files included, and asked an open-ended question: are any of these AM CVns? I didn't tell it which target, or what to look for beyond "AM CVn." The catch: when I'd looked at these spectra by eye on the night of observation, I had missed the AM CVn. Twenty-eight of the 29 sources turned out to be ordinary hydrogen-rich cataclysmic variables, and after scrolling through dozens of similar-looking spectra, the one that was different didn't jump out.
Claude got it on the first pass. It wrote a Python script that measured every helium and hydrogen line in every spectrum, ranked the targets by how AM-CVn-like each one was, and the discovery target came out on top — the only spectrum with helium detected and zero hydrogen detected. The thing that fooled me — that the signal was an absence, not a presence — is exactly the kind of thing a systematic measurement handles better than tired human eyes. Wall-clock time: about 15 minutes.

A Claude-generated schematic of Experiment A:
![experiment-a](/assets/amcvn-experiment-a-result.png)

The smoking-gun signal of a gravitational-wave emitting AM CVn binary --- helium lines instead of hydrogen:
![experiment-a](/assets/amcvn-experiment-a.png)



### Experiment B: Needle in a Haystack
Experiment B — needle in a haystack. Same goal, different starting point: a catalog of 1.49 million X-ray sources matched to the Gaia star catalog. No spectra, no labels, just photometric and astrometric numbers. This one was harder for Claude. Its first selection — built from sensible-looking standard cuts — missed the target. Over eight rounds of refinement, with me providing one-sentence hints when it got stuck ("remember extinction," "the X-ray detection is faint," "you're using the wrong reference sample"), Claude diagnosed and removed each filtering pitfall in turn. The final pipeline narrowed 1.49 million sources down to a 223-candidate shortlist. The discovery came out at rank 3, with two other promising unstudied systems above it that I plan to follow up.

A Claude-generated schematic of Experiment B:
![experiment-a](/assets/amcvn-experiment-b-result.png)

A subset of the AM CVn candidates targeted by Claude in Experiment B, and the key for their discovery --- clustering in the classic color-magnitude diagram:
![experiment-a](/assets/amcvn-experiment-b.png)

### Conclusion: Can LLMs Replace Me?
What I take from this. The pattern matters. For zero-shot classification of small samples, an LLM-driven first-pass beats my own visual inspection essentially for free — it forces a quantitative pipeline to exist where one wouldn't otherwise. For large-catalog search work, the LLM doesn't outperform an experienced human selecting from scratch, but it produces something equally valuable: an explicit audit trail of why each cut is in the pipeline, with each filter justified against a recovery test. The hints I gave Claude were each a piece of domain knowledge an experienced AM CVn hunter carries implicitly. That this knowledge needs to be supplied externally is a real limitation; that each hint produced a surgical fix is the encouraging part.


I'm cautiously optimistic about LLM-collaborator workflows for observational astronomy. There's real signal here — and clear room to grow.


— Tony

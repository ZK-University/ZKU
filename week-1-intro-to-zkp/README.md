# Week 1: Intro to ZKP

[![Welcome to ZKU](https://img.youtube.com/vi/fpriUHDmYE0/default.jpg)](https://youtu.be/fpriUHDmYE0)

Welcome to this course. During weeks 1-3, we will try to cover the basics of applied ZK. We will try to find you the shortest path to get you up to speed to build your own project as quickly as we can. We’ll try to skip as many technical details as possible, but some real work is necessary.


[![Introduction to Zero Knowledge Proofs](https://img.youtube.com/vi/BT88s7_VtC8/default.jpg)](https://youtu.be/BT88s7_VtC8) 

This video is an excellent, intuitive intro to what is ZKP, and has a nice summary and taxonomy of the different types of currently popular proofs. It is pretty short (only 20 minutes) so don’t skip any of it.


[![zku.ONE #01: Course Overview & General Theoretical Background](https://img.youtube.com/vi/9je336QIqAQ/default.jpg)](https://youtu.be/9je336QIqAQ) 

From there, this longer video (75 minutes) covers the background theory stuff and ZK formalism in more depth. It is more like a typical undergrad-level class in computer science. While this may not be what some of you are used to, getting these basic concepts precisely can really help you go a long way.

Overall, we’ll focus on SNARK rather than STARK for now. While STARK is interesting and powerful, and has the obvious advantage of not requiring a trusted setup, building your project with SNARK will probably be a lot easier for now, in part because of the availability of existing tools that are relatively easy to use. One good news is, within the SNARK framework we can also use PLONK rather than Groth16. With PLONK, we can more or less bypass the trusted setup issue, because we don’t need the second phase setup, and for the first phase, we can just use existing setups. [This is a nice short intro](https://medium.com/aztec-protocol/plonk-benchmarks-2-5x-faster-than-groth16-on-mimc-9e1009f96dfe) about the differences between PLONK and Groth16 - you’ll most likely be using either for your final project.

There are many tools out there for building ZK products these days. But we think the easiest way is probably to start with Circom (check out the official [documentation](https://docs.circom.io/), and 

[![zku.ONE (March 2022 Cohort) Week 1: circom Tutorial and Demonstration](https://img.youtube.com/vi/9s1VLrjk5L4/default.jpg)](https://youtu.be/9s1VLrjk5L4)

this short, 12-minute demo). So this week we’ll do some exercises to get you familiar with writing your own circuits. Some basic mathematical understanding is necessary here. But if you get good at it, it can really vastly increase the range of exciting projects that you can do.

Some of you may be in this course because you already know what you want to build. But if you don’t yet know, and are only here because you think ZK is the future and some magical use case must be somewhere even if we haven’t found it yet - well, you may not be wrong about this at all. [This paper](https://link.springer.com/article/10.1007/s42452-019-0989-z#Sec4) is long and comprehensive, but if you only read the Applications section, it may give you some ideas about what we can do with ZK. Hopefully this keeps you motivated to power through the coming few weeks.

Further reading(s):
- [Thinking in Zero Knowledge](https://mirror.xyz/0x3FD6f213ae1B8a7B6bd8f14BE9BF316a5e5A5d28/VTGpmEYLKIslUPf66VQzHUneB0R7EhMpJJ_mGrMvTwY)
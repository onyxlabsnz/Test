---
title: "Model evaluation basics every product team should know"
date: 2025-12-10
---

You don't need to be a machine learning researcher to run useful model evaluations. Product teams that ship AI features need a working understanding of evals — not to become experts, but to stop shipping blind.

## What an eval actually is

An eval is a test. You have a set of inputs, a set of expected or acceptable outputs, and a way to score how well the model does. That's it.

The complexity comes in designing inputs that represent real usage, defining what "good" looks like for your use case, and building infrastructure to run the evals reliably as the model or prompt changes.

## The three evals every team needs

**Regression evals** tell you whether a change made things worse. Run these before every deployment. They should cover your core use cases and known edge cases.

**Quality evals** measure whether the model is doing the job well, not just avoiding regression. These often require human judgment and are run less frequently.

**Adversarial evals** test what happens when users try to break the system. Important for any user-facing AI feature.

## Human eval versus automated eval

Automated evals are fast and cheap. Human evals are slow and expensive but can catch things automated evals miss — especially in open-ended generation tasks where "correct" is hard to define programmatically.

Start with automated evals for regression testing. Use human evals for quality assessment on a sampling basis. As you accumulate human eval data, you can train classifiers to automate more of the quality signal over time.

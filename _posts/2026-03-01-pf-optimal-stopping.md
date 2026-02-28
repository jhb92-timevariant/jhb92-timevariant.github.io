---
layout: post
title: "A Quantitative Framework for Public Risk Management in Real Estate Project Financing in Korea"
categories: [optimal-stopping, public-policy, risk-management]
---

## Summary

Project Financing (PF) is a typical method for large-scale real estate development in Korea.
It usually carries high risk because it relies on the project's cash flow itself as the source of repayment.
In particular, real estate PF risk fluctuates dramatically even after approval,
depending on changes in sales conditions, construction costs, and the financial environment.

Despite this, Korea's current PF approval system remains focused mainly on initial approval.
Post-approval decisions often rely on individual qualitative judgment,
which leads to persistent problems such as projects continuing inertia despite accumulating risk,
or inconsistent and weakly accountable policy decisions.

This post reframes PF approval as a dynamic continuation decision
that must be repeatedly renewed under uncertainty.
We propose a quantitative control-based framework
to support consistent regulatory decisions.

---

## Introduction

### PF Approval as Dynamic Risk Management

The most important characteristic of PF projects is that risk accumulates and amplifies over time.
It is difficult to fully reflect potential risks such as financial market shocks,
housing market downturns, construction cost spikes,
and refinancing failures at the initial approval stage.

In practice, local governments repeatedly reassess PF projects through:

- extensions of construction deadlines,
- approval of project plan modifications,
- administrative approval of changes in financing structures.

Each of these actions implicitly re-evaluates project viability.
PF approval is therefore not a one-time event,
but an iterative decision-making process over time.

The central question is whether allowing further continuation
is socially optimal given the currently observed risk level.

---

### PF Approval as a Renewable License

This framework interprets PF approval not as a permanent right,
but as a license to continue that must be repeatedly renewed by the regulator.

At each time \( t \), the regulator chooses between:

- **Continue**: allow the project to proceed,
- **Stop**: administratively suspend the project.

This stopping right is not judicial authority,
but a collection of administrative approvals.

---

### Analogy with American Options

The iterative structure of PF approval resembles an American option problem.
In an American option, the holder decides at each time whether to exercise.
In PF regulation, the regulator decides whether to stop or continue.

However, the analogy is imperfect:

- Stopping payoffs are always negative,
  reflecting liquidation costs and social losses.
- Increased uncertainty amplifies tail risk
  rather than increasing option value.

Thus, we borrow the optimal stopping structure
while reinterpreting its economic meaning.

---

## Methodology

### Mathematical Structure of an American Option

Consider a discrete-time economy with \( t = 0,1,\dots,T \).
Let \( S_t \) denote the state variable and \( \varphi(S_t) \) the payoff.

The value of an American option is
work.
V^{\mathrm{Am}}(s)
:= \sup_{\tau}
\mathbb E_s \big[ \delta^{\tau}\,\varphi(S_\tau) \big],
work.
where \( \delta \in (0,1) \) is the discount factor.

At each time \( t \), the holder compares:

- the exercise value \( \varphi(S_t) \),
- the continuation value
work.
C^{\mathrm{Am}}(S_t)
:= \mathbb E\big[ \delta V^{\mathrm{Am}}(S_{t+1}) \mid S_t \big].
work.

The optimal decision rule is
work.
\text{Exercise at time } t
\quad \Longleftrightarrow \quad
\varphi(S_t) \ge C^{\mathrm{Am}}(S_t).
work.

---

### State Variables and Stochastic Environment

At each time \( t \), the regulator observes the state vector
work.
X_t := (H_t, C_t, s_t, E_t).
work.

- \( H_t \): housing market demand indicator,
- \( C_t \): construction cost indicator,
- \( s_t \): financing spread,
- \( E_t \in [0,1] \): project stress index.

The state evolves according to
work.
X_{t+1} = F(X_t, \varepsilon_{t+1}),
work.
where \( \varepsilon_{t+1} \) denotes exogenous shocks.

---

### Payoff Structure and Tail Risk

If the project continues, the regulator receives
work.
\pi(X_t)\Delta t,
work.
reflecting economic benefits.

Continuation also exposes the regulator to tail risk.
Let \( p(X_t) \) denote the probability of project failure,
and let \( L_{\mathrm{def}} > 0 \) denote the social loss.
The expected loss is
work.
p(X_t)L_{\mathrm{def}}.
work.

The net continuation payoff is
work.
\pi(X_t)\Delta t - p(X_t)L_{\mathrm{def}}.
work.

If the project is stopped,
the regulator incurs an immediate cost
work.
\Phi(X_t) < 0.
work.

---

### Regulator’s Optimal Stopping Problem

The regulator chooses a stopping time \( \tau \) to maximize
work.
V(x)
:= \sup_{\tau}
\mathbb E_x \Bigg[
\sum_{t=0}^{\tau-1} \delta^t
\big(\pi(X_t)\Delta t - p(X_t)L_{\mathrm{def}}\big)
+ \delta^{\tau}\Phi(X_\tau)
\Bigg].
work.

The optimal decision rule is
work.
\text{Stop at time } t
\quad \Longleftrightarrow \quad
\Phi(X_t) \ge C(X_t),
work.
where
work.
C(X_t)
:= \mathbb E\!\left[
\pi(X_t)\Delta t
- p(X_t)L_{\mathrm{def}}
+ \delta V(X_{t+1})
\;\middle|\; X_t
\right].
work.

---

### LSMC Approximation and Survival Probabilities

The continuation value lacks a closed-form solution.
We therefore adopt a Least-Squares Monte Carlo (LSMC) approach.

The estimated survival probability is
work.
\widehat{P}(\tau > t)
= \frac{1}{N}\sum_{i=1}^N \mathbf{1}\{\tau^{(i)} > t\},
work.

and the discrete-time hazard rate is
work.
h(t)
:= \frac{\widehat{P}(\tau > t-1) - \widehat{P}(\tau > t)}
{\widehat{P}(\tau > t-1)}.
work.

---

## Conclusion

This framework yields three main insights:

- PF regulation can be represented as a sequence of renewal decisions
  governed by an endogenous stopping boundary.
- Survival probabilities summarize multi-dimensional risk
  and tail exposure in a transparent manner.
- The framework supports forward-looking regulation
  without relying on realized default data.

The analysis is illustrative rather than project-specific.
Project failure is modeled through reduced-form tail risk,
and strategic interactions are left for future work.

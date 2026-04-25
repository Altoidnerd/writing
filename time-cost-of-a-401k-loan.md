# The Cost of a 401k Loan, Measured in Time

*A model of effort, capital, and the phase transition between them.*

> *This piece is a mathematical model for personal reasoning, not investment advice. All examples use illustrative numbers chosen for clarity. Speak to a licensed financial advisor about your specific situation. Views are the author's own and do not represent any employer or client.*

---

## The wrong question, and the right one

The standard way to argue about a 401k loan is to ask:

> *"What's the difference in my balance 30 years from now if I take this loan vs not?"*

This is the wrong question. Or rather, it's a question that produces an answer that is technically correct and structurally meaningless. The number you get from a 30-year projection is dominated by assumptions about the market rate of return over decades you cannot forecast — and the *difference* between two 30-year projections inherits all of that uncertainty without canceling any of it.

The right question is:

> *"What do I need to do to remain the same person — to arrive at the same financial milestone at the same time?"*

This reframe turns a noisy, stochastic, distant projection into a clean perturbation problem near the present. And the answer comes out as a closed-form expression.

What follows is the model. It is a single ODE with one phase transition, and from that one structure you can read off everything that matters about a 401k loan: when it's cheap, when it's expensive, when it's structurally impossible to undo, and what the upper limit of the perturbation framework is.

---

## The whole system in one equation

Your portfolio $P(t)$ evolves as:

$$\frac{dP}{dt} = gP + c$$

- $P(t)$: portfolio balance, in dollars.
- $g$: market rate of return (e.g., $g = 0.07$ for 7% annual).
- $c$: contribution flow, in dollars per unit time (e.g., \$18,000/year).

The term on the right-hand side represents two engines:

- **Capital engine:** $gP$ — exponential, self-reinforcing, scales with current size.
- **Labor engine:** $c$ — linear, constant, independent of current size.

Your wealth grows because your money works, and because you work.

The closed-form solution (just to keep it together):

$$P(t) = p_0\, e^{gt} + \frac{c}{g}\left(e^{gt} - 1\right)$$

But honestly, you don't need this to reason about the system. Everything intuitive comes from the differential equation itself.

---

## Dimensional analysis: the only number that matters

Before going further, check units. In the physicist's habit:

$$[P] = \$, \qquad [g] = 1/t, \qquad [c] = \$/t$$

From these three, two natural timescales emerge.

**The growth timescale:**

$$\tau_g = \frac{1}{g}$$

This is "how long the system takes to evolve under capital alone" — time to grow by a factor of $e$ from returns. At $g = 7\%$, $\tau_g \approx 14.3$ years.

**The funding timescale:**

$$\tau_c = \frac{p_0}{c}$$

This is "how long your contribution flow takes to recreate your starting wealth from scratch." If $p_0 = \$50\text{k}$ and $c = \$10\text{k/yr}$, then $\tau_c = 5$ years.

The dimensionless ratio of the two is the **only structural number in the entire problem**:

$$\frac{\tau_c}{\tau_g} = \frac{g p_0}{c}$$

This single number tells you which regime you are in:

- $\frac{g p_0}{c} \ll 1$: contributions dominate. Your savings rate is doing the heavy lifting.
- $\frac{g p_0}{c} \approx 1$: balanced. The crossover regime.
- $\frac{g p_0}{c} \gg 1$: capital dominates. Your portfolio works harder than you do.

Every conclusion in this article reduces to a statement about this ratio.

---

## The crossover

The two engines run on different scaling laws — one constant, one proportional to $P$. So somewhere along the trajectory, there must be a single moment when they balance: a particular time $t^{\star}$ at which the principal $P(t^{\star})$ takes a particular value $P^{\star}$, and at which contribution flow exactly equals market return flow. Let's just propose that such a moment exists, set the two flows equal, and read off the values.

Setting $gP^{\star} = c$ gives the **crossover level**:

$$P^{\star} = \frac{c}{g}$$

This is the balance at which your portfolio earns in a year what you contribute in a year.

The **crossover time** $t^{\star}$ is the time to reach $P^{\star}$ starting from $p_0$. Solving $P(t^{\star}) = c/g$ gives a closed form:

$$\boxed{ t^{\star} = \frac{1}{g} \ln \left( \frac{2c/g}{p_0 + c/g} \right) }$$

For $p_0 = \$80\text{k}$, $c = \$18\text{k/yr}$, $g = 0.10$: $t^{\star} \approx 3.26$ years.

Now reason about what the system looks like on either side of this point.

**For $t < t^{\star}$ (equivalently, $P < P^{\star}$):** the labor engine dominates. $c \gg gP$. Wealth grows because *you* grow it. Mistakes are recoverable; perturbations are absorbed by ordinary effort. The system is **flow-dominated**.

**For $t > t^{\star}$ (equivalently, $P > P^{\star}$):** the capital engine dominates. $gP \gg c$. Wealth grows because *it* grows itself, and you are a perturbation on the trajectory rather than its driver. Compounding rules everything. The system is **return-dominated**.

The crossover is where the system **changes character** — not gradually, but in the structural sense that the answer to *"what should I optimize?"* flips.

In practical terms, $t < t^{\star}$ is your early-career phase: the first years of saving, when your starting balance is small and your contributions are doing nearly all the work of building the pile. Optimize savings rate, protect liquidity, income matters most.

$t > t^{\star}$ is your later-career phase: the pile is large enough that its returns dwarf what you can add to it from a paycheck. Protect capital, manage volatility, returns matter most.

For most people on a typical earnings path, the crossover lands somewhere in the late thirties to mid-fifties — but the timing is entirely a function of your three numbers ($p_0$, $c$, $g$), not of any age in particular. Two people the same age can sit on opposite sides of the boundary.

---

## What a 401k loan actually is

A loan of size $L$ does one thing to the state:

$$p_0 \longrightarrow p_0 - L$$

It is a state perturbation — a one-time subtraction from the principal at $t = 0$.

The naive view: *"I lose compounding on $L$ forever."*

The correct view, which is structurally cleaner: *I delay my own trajectory.*

$$P_{\text{loan}}(t) \approx P_{\text{no loan}}(t - \Delta t)$$

The loan does not bend your curve — it shifts it. And the shift has a name.

---

## The true cost: time

The cost of a loan, before crossover, is:

$$\Delta t^{\star}$$

how much later you reach the crossover regime.

This is the *only* metric that matters early on, because before crossover the whole system is dominated by linear flow — and a delay in one stage of a linear regime is just a delay, recoverable with effort.

---

## The "same guy" question

Instead of *"What's my balance in 30 years?"*, ask:

> *"What do I need to do to remain the same guy — to reach the same crossover level at the same crossover time?"*

Write the new contribution flow as $c_1 = c_0 + \Delta c$, with the new principal $p_0 - L$. Set the post-loan trajectory to hit the original crossover level at the original crossover time:

$$P_{\text{new}}(t^{\star}_{\text{old}}) = P^{\star}_{\text{old}}$$

Plug in, solve, simplify. The answer is:

$$\boxed{ \frac{c_1}{c_0} = 1 + \frac{2gL}{c_0 - g p_0} }$$

This is the **identity-preserving multiplier** — the percent increase in effort you need to undo the loan, structurally.

Define the **flow dominance gap**:

$$F = c_0 - g p_0$$

Then:

$$\frac{c_1 - c_0}{c_0} = \frac{2gL}{F}$$

The denominator $F$ is everything. It is the same dimensionless structure as $gp_0/c$ — but flipped to read as a *gap* rather than a ratio. Far from crossover, $F$ is large and the multiplier is small. Near crossover, $F \to 0$ and the multiplier diverges.

---

## Worked example

Take real-feeling numbers:

- $p_0 = \$80\text{k}$
- $c_0 = \$18\text{k/yr}$ (\$1500/mo)
- $g = 10\%$
- $L = \$10\text{k}$

Then:

$$\frac{c_1}{c_0} = 1 + \frac{2(0.10)(10\text{k})}{18\text{k} - (0.10)(80\text{k})} = 1 + \frac{2\text{k}}{10\text{k}} = 1.2$$

So $c_1 = \$1800/\text{mo}$.

**A \$10k loan from an \$80k starting balance, at 10% return and \$1500/mo baseline contribution, requires a 20% lift in contributions to fully neutralize.** That's the kind of clean result you can carry around in your head.

---

## The delay-loss equivalence

There's a question lurking in the corner: how does the "time delay" framing connect to the "lost compounding" framing? Are they two different things, or the same thing in different units?

They're the same thing. Here's the bridge.

If a loan delays your trajectory by $\Delta t$, then at any later time $T$:

$$P_{\text{new}}(T) = P_{\text{old}}(T - \Delta t)$$

In the deeply post-crossover limit (where $P(t) \approx C\, e^{gt}$ for some constant $C$), this becomes:

$$\frac{P_{\text{new}}(T)}{P_{\text{old}}(T)} \approx e^{-g \Delta t}$$

So a 2-month delay at $g = 7\%$ corresponds to a fractional terminal-wealth loss of:

$$1 - e^{-0.07 \cdot 0.17} \approx 1 - 0.988 \approx 0.012 \;=\; 1.2\%$$

A 2-month delay translates to a ~1.2% loss of terminal wealth. Same loss, two units. That equivalence is the whole reason the "time" framing is more useful than the "balance" framing — it generalizes cleanly across regimes, where balance differences don't.

---

## The singularity

Look at the contribution multiplier again, with the denominator written explicitly:

$$\frac{c_1}{c_0} = 1 + \frac{2gL}{c_0 - g p_0}$$

The interesting thing is the denominator $c_0 - g p_0$. This is the gap between contributions and current returns — between the labor engine and the capital engine, evaluated at $t = 0$.

When $c_0 > g p_0$, you're flow-dominated; the denominator is finite and positive, and the multiplier behaves like a small perturbation. When $c_0 < g p_0$, you're already past crossover at $t = 0$; the denominator is negative, and the formula returns nonsense (we'll come back to that).

The singularity sits exactly where the denominator vanishes:

$$c_0 = g p_0 \quad\Longrightarrow\quad c_0 - g p_0 = 0 \quad\Longrightarrow\quad \frac{c_1}{c_0} \to \infty$$

The required contribution bump runs off to infinity. **At crossover, you cannot catch up.** Not "it's hard." *Impossible*, in the sense of preserving trajectory through any finite increase in effort.

The mechanism is clean. At crossover, returns and contributions are equal. The system is balanced. Remove $L$ from capital, and returns drop below contributions. You fall back into flow-dominated mode. To stay at crossover *instantaneously* — to remove the capital and not feel its absence — you would need contributions to leap up to replace the lost returns *the same instant they were lost*. That requires an infinite jump.

This is a real phase boundary, not a math accident. The denominator $c_0 - g p_0$ is the **flow dominance gap** $F$ from earlier; the singularity is the statement that the identity-preservation framework only has finite answers in the regime $F > 0$. The closer you get to $F = 0$, the more expensive every dollar of loan becomes — and at $F = 0$, the metric "compensate to preserve crossover timing" simply stops being defined.

---

## The three regimes

Rewriting everything around the flow gap $F = c_0 - g p_0$:

**Case 1: $F > 0$, pre-crossover.**
Contributions exceed returns. Loans push you back, but the system is flow-controlled and recovery is finite. You can buy safety with months.

**Case 2: $F = 0$, at crossover.**
The singular point. Trajectory cannot be preserved by contribution adjustment. The original question — *"how much extra to stay on track?"* — has no finite answer.

**Case 3: $F < 0$, post-crossover.**
Returns exceed contributions. The compensation formula returns nonsensical (negative) values, because the original question is malformed: you've already passed the crossover landmark, so asking *"how do I still hit it at the same time?"* is asking how to preserve a past event.

The metric must change. After crossover, the right question is *"how much exponential phase did I lose?"* — measured as a fractional loss:

$$\frac{\Delta P}{P} \approx 1 - e^{-g \Delta t}$$

Pre-crossover: cost is in months to regime entry (additive).
Post-crossover: cost is in percentage of future wealth (multiplicative).

Same dollar of loan, totally different dynamics. Before crossover, a loan is like stepping backward on a road — the distance is finite, the steps to recover it are ordinary, and walking faster is enough. After crossover, a loan is like reducing the mass of a snowball already rolling downhill — the snowball still rolls, but it gathers less mass at every revolution, and the cost compounds as a *fraction* of every future state, not as a finite shortfall.

There's also a narrow zone right at the boundary — when $F = c_0 - g p_0$ is small but nonzero — where the model says touching capital is **maximally costly** in identity-preservation terms. The compensation multiplier behaves like $1/F$, so as $F$ shrinks, the contribution lift required to stay on track explodes long before the formal singularity. In this band, small loans have outsized timing effects. Before it, you can recover with flow. After it, crossover timing is no longer the right metric. At it, the metric explodes.

---

## What the phase boundary is really about

The model isn't about 401k loans. It's about the transition from labor-driven growth to capital-driven growth. Every working person who saves traverses this transition exactly once in their life — and the location and timing of that transition is determined by exactly three numbers: $p_0$, $c$, $g$.

A 401k loan is a perturbation analysis around the transition. So is a job change. So is a salary cut, a bonus, a market crash, a rebalance. The framework is general; the loan question is just one specific application that happens to have a clean closed form.

The article-worthy line: **a 401k loan is not equally expensive at every stage of wealth. Before crossover, it costs time. Near crossover, it costs acceleration. After crossover, it costs compounding mass.**

---

## The constraint most people miss

You cannot increase contributions arbitrarily. The IRS sets a hard ceiling — $c_{\max}$ — at the annual contribution limit (~\$23.5k in 2025 for employee deferrals).

Define the **feasibility ratio**:

$$\rho = \frac{\Delta c_{\text{needed}}}{c_{\max} - c_0}$$

- $\rho < 1$: the loan is fixable through extra contributions.
- $\rho > 1$: the loan is not fixable through this mechanism. You will arrive at crossover late, and there's nothing you can do about it within the contribution budget.

Before the constraint binds, loans cost effort. After it binds, loans cost **irrecoverable time**. This is the second phase transition in the model — not a divergence in math, but a wall in the policy environment.

---

## Employer match: the dual

The compensation formula is symmetric: a contribution *increase* — say, an employer match — acts like a *negative* loan.

Inverting the formula gives the equivalent loan capacity unlocked by a match $\Delta c$:

$$\boxed{ L_{\text{free}} = \frac{\Delta c}{c_0} \cdot \frac{c_0 - g p_0}{2g} }$$

For the same numbers as above, a match of $\Delta c = \$600/\text{mo}$ gives $L_{\text{free}} \approx \$20\text{k}$.

So a \$600/mo employer match offsets a \$20k loan in the identity-preservation sense. **Employer match is not just free money — it's free repair capacity.** That reframing alone is worth the price of admission for most readers.

---

## The seductive idea: borrow and hold cash

A common strategy: take the loan, hold it in money market, earn a yield $r_f$. People convince themselves this is arbitrage. It isn't.

You give up $gL$ in expected portfolio return to gain $r_f L$ in cash yield.

- If $g > r_f$ (the usual case): you lose expected return.
- If $g = r_f$: mean-neutral, but you also lose upside convexity — the equity payoff is asymmetric, the money-market payoff is not.

What you actually buy with this strategy is **liquidity, optionality, and volatility reduction**. Those are real goods. They're just not free, and they're not arbitrage. Be honest with yourself about which one you're paying for.

---

## The forbidden idea

What if you could borrow *against* the 401k without selling? Then $P$ stays invested, you get cash for whatever you need, and there is no delay, no $\Delta t^{\star}$, no phase-boundary problem.

That's **margin**. It exists in taxable brokerage accounts. It is structurally illegal in retirement accounts.

Why?

1. **Systemic risk.** Leveraged retirement accounts in market drawdowns produce cascading liquidations exactly when the system can least absorb them.
2. **Individual ruin risk.** Margin calls produce permanent losses, and retirement accounts are designed to never experience permanent losses by design choice.
3. **Behavioral risk.** Retail participants will over-lever. This is an empirical fact, not a hypothesis.

So the rule that 401k loans must subtract from $P$ rather than collateralize $P$ is a **design choice** — a deliberate trade of efficiency for robustness. Retirement systems are optimized for robustness, not efficiency. The "inefficiency" of a 401k loan is not a bug. It is the entire point.

---

## Where the model stops working

A model deserves trust in proportion to its honesty about its own boundaries. Here are the things this model does **not** capture, and where the simple ODE framework breaks down in the real world:

- **Sequence-of-returns risk.** $g$ is treated as constant. In reality, it's a stochastic process, and time-out-of-market interacts with the realized path. A loan taken just before a major rally costs more than the same loan taken just before a major drawdown — the model can't see this.
- **Tax inefficiency.** 401k loans are repaid with after-tax dollars, then withdrawn and taxed again at retirement. This is a real second-order cost not present in the ODE.
- **Employment risk.** Most plans require loan repayment in full within a short window after termination. A loan plus an unexpected job loss can convert into an immediate taxable distribution plus a 10% penalty. This is the largest tail risk by far, and the ODE doesn't model job-conditional outcomes.
- **Behavioral lock-in.** Forced repayment can be psychologically beneficial (mandatory disciplined investing) or harmful (reduced budget flexibility), depending on the person. The model is silent on this.

A useful version of this article in a different audience would extend each of those into its own perturbation. For now, what the ODE captures is the *structural* cost. Everything else is bookkeeping on top.

---

## The deepest takeaway

All of these decisions reduce to one quantity:

$$\Delta t$$

a time shift in a compounding system. The model says you don't lose money when you take a 401k loan. You lose time. And in a compounding system, time is the only thing that matters.

Call this the **Two-Engine Wealth Model**, or the **Flow vs. Compounding Model**. The two engines are labor and capital. Their relative strength is a single dimensionless number, $g p_0 / c$. Their crossover is a real phase transition. And the cost of any perturbation, expressed as a delay in that transition, gives you a clean, comparable, near-present quantity that beats every 30-year terminal-wealth projection.

---

## Final line

Before your money works as hard as you do, you can fix mistakes with effort. After that, effort becomes a rounding error.

---

> *Disclaimer (repeated for the link-skimmers): nothing in this article is investment advice. The model is a reasoning tool for thinking about a class of decisions, not a recommendation for or against any specific decision. Speak to a licensed advisor.*

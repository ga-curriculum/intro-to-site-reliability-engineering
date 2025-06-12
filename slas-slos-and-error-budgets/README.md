<h1>
  <span class="headline">Intro to Site Reliability Engineering</span>
  <span class="subhead">SLAs, SLOs, and Error Budgets</span>
</h1>

**Learning objective:** Explain the role and purpose of SLAs, SLOs, and error budgets.

## Making reliability measurable and actionable

You’ve probably heard that reliable systems matter. But how can your team actually _measure_ what “reliable” means for your software? How do you know when you’re providing a good experience—or when users are seeing problems?

**Site Reliability Engineering (SRE)** uses a practical toolkit for this: **SLAs**, **SLOs**, **SLIs**, and **error budgets**. These are not just technical terms—they are the language teams use to agree on what “good enough” looks like, how to track it, and when to prioritize stability over speed.

Let’s unpack what each term means, and see why these ideas matter for anyone working on live systems.

## Key concepts: SLIs, SLOs, SLAs, and error budgets

📚 Let’s start by defining some essential terms.

- _SLI_ (Service Level Indicator): A raw, measurable metric that shows how your service is performing for users.
- _SLO_ (Service Level Objective): An internal goal, set by your team, that describes how good your SLI should be over a period of time.
- _SLA_ (Service Level Agreement): A formal, usually external, agreement about the minimum reliability your users or customers can expect.
- _Error budget_: The “wiggle room”—how much unreliability is allowed within your SLO.

> 💡 Think of these terms as building blocks:  
> **SLI (measurement) → SLO (target) → SLA (promise) → error budget (tolerance for risk)**

#### Relating reliability metrics to everyday experience

Imagine you’re preparing for an important certification exam.

- Your _SLI_ is your score on each practice quiz.
- Your personal _SLO_ might be to score **90%** or higher on each quiz during your study week.
- The exam provider’s _SLA_ is the official requirement: at least **80%** to pass.
- Your _error budget_ is the small number of questions you can miss while staying above your goal.

<div class="activity discussion">
  <h2 class="title">A simple API scenario</h2>
  <span class="minutes">5 min</span>
</div>

Let’s use a practical example, rooted in something familiar: an API endpoint.

Suppose your team builds a `/api/orders` endpoint for an e-commerce application. Here’s how you might apply the SRE concepts:

| **Type**         | **Example**                                                                                       |
| ---------------- | ------------------------------------------------------------------------------------------------- |
| **SLI**          | Percentage of API requests that return a successful response (`2xx`) in under `250 milliseconds`. |
| **SLO**          | `99.9%` of all requests must succeed within `250 milliseconds` each month.                        |
| **SLA**          | Formal agreement to deliver `99.7%` success within `250 milliseconds` for business partners.      |
| **Error Budget** | The allowed `0.1%` of requests that may fail or exceed `250 milliseconds` each month.             |

If your API receives `1,000,000` requests monthly and you aim for `99.9%` success, your error budget is `1,000` requests. Up to `1,000` slow or failed requests that month are “acceptable.” Beyond that, your SLO is breached, and your team prioritizes fixes.

> 💡 Building reliability targets from the ground up lets you make smart, data-driven choices—balancing user happiness with the ability to deliver new features and improvements.

### Why "good enough" is better than "perfect"?

> 🏆 Best practice: SREs focus on “good enough” reliability, rather than chasing perfection.

Trying to reach 100% uptime is not only expensive, but often unnecessary for user satisfaction. An error budget provides a healthy balance.

**In practice:**

- If you still have room in your error budget this month, your team can take some risks: deploy new features, or experiment with changes.
- If you’re close to the edge, it’s time to pause non-essential work and focus on reliability.

This approach keeps your team grounded—you know when you can innovate, and when you must protect users’ experience.

### Drafting a reliability target (SLO) and error budget

Let’s step through a real-world workflow you might use as a Python developer in a team launching a new `/api/profiles` endpoint:

1. **Choose your SLI:**  
   Example: “percentage of requests that return a `200 OK` response.”

2. **Set your SLO:**  
   Example: “`99.95%` of requests should succeed each month.”

3. **Calculate your error budget:**  
   For `250,000` requests each month at a `99.95%` SLO: error budget is `125` allowable failures.

```python
total_requests = 250_000
slo_percentage = 99.95
allowed_failures = int(total_requests \* (1 - (slo_percentage / 100)))
print(f"Monthly error budget: {allowed_failures} requests")
```

## Internal SLOs vs. external SLAs

You might be wondering: Why make the SLO stricter than the SLA?

Here’s the thinking:

- The **SLA** is your _external promise_—this is what you guarantee to users or partners.
- The **SLO** should be even tighter—your _internal target_.
- This gives you a buffer: If something goes wrong, your team spots it and acts _before_ anyone outside is impacted or before you risk penalties.

**Example:**

- SLA: 99.5% success rate (formal contract)
- SLO: 99.9% success rate (internal target)
- Buffer: 0.4% (allows time to fix issues without breaching agreements)

> 💡 Keeping SLOs stricter than SLAs helps your organization maintain trust with users, while letting your team act rapidly to prevent business-impacting incidents.

<div class="activity knowledge-check">
  <h2 class="title">Imagine your API receives 100,000 requests per week...</h2>
  <span class="minutes">5 min</span>
</div>

❓ Imagine your API receives `100,000` requests per week. Your team’s SLO is `99.9%` of requests must succeed.

- How many failures does your error budget allow each week?
- If you wanted to relax the SLO to 99.5%, how would your error budget change?

Calculate your answers using the formula:

```
Error budget = Total Requests × (1 − SLO Percentage / 100)
```

> 💡 Discuss your reasoning with a partner or group. How would a tighter or looser error budget affect your team’s decisions?

## Real-world decisions are driven by error budgets

In a typical week on a software team, error budgets help you make choices such as:

- Can we safely deploy that new feature now, or should we focus on fixing issues?
- If we miss our SLO, when should we inform users, partners, or management?
- Are our SLOs realistic, or are we setting ourselves up for constant failure or rework?

Take a moment to consider: Have you ever worked on a project where expectations for reliability were unclear? How could using error budgets have brought more clarity to your work?

> 💡 Share your thoughts in a chat or with a team member—compare your experiences and brainstorm how error budgets could fit into your current or future development workflow.

<div class="activity group-exercise">
  <h2 class="title">Draft a reliability target and error budget</h2>
  <span class="minutes">15 min</span>
</div>

In this group exercise, you’ll play the role of a Python product team preparing to launch a new public-facing API. Your task is to define a Service Level Indicator (SLI), set a Service Level Objective (SLO), and calculate an error budget—key tools for managing system reliability and release velocity.

This activity mirrors how real engineering teams negotiate between user expectations and operational realities.

#### Scenario

You are part of the backend team at a startup launching a new /api/recommendations endpoint. This API powers the “You might also like…” feature on a global e-commerce site. It needs to be fast, reliable, and scalable—users expect it to work quickly, but your team also needs flexibility to ship improvements regularly.

Your leadership team is asking for a concrete reliability goal (SLO) before launch, including an error budget to help guide decisions about rollbacks, releases, and incident response.

1. **Choose your SLI (Service Level Indicator)**

   - What specific metric will you track to measure reliability?
     Example: "Percentage of successful (2xx) responses returned within 200 milliseconds."

   > 💬 Tip: Discuss what success looks like to an end user. Is latency more important than correctness? Should both be measured?

2. **Set your SLO (Service Level Objective)**

   - What target will you set based on user expectations and operational capacity?
     Example: “99.8% of all requests return a 2xx within 200ms over a 7-day window.”

   > 💬 Tip: Companies typically balance user experience, past performance data, and business risk to decide on SLOs. If you set it too high, you may constantly pause releases; too low, and you risk poor UX.

3. **Calculate your error budget**

   - Assume your API receives 50,000 requests per week. How many requests are allowed to fail or exceed your SLO target before action (like freezing releases) is needed?

   Use this formula:

   ```
   Error Budget = Total Requests × (1 − SLO / 100)
   ```

   Use the Python script below to verify your answer:

   ```python
   total_requests = 50000
   slo_percentage = 99.8
   allowed_failures = int(total_requests \* (1 - (slo_percentage / 100)))
   print(f"Weekly error budget: {allowed_failures} requests")
   ```

4. **Write out your choices:**

   - SLI: (Describe your selected metric.)

   - SLO: (Specify your chosen threshold and time period.)

   - Error budget: (State the number of requests allowed to miss your SLO.)

   - Why did your team choose these thresholds?

5. **Discuss with your group:**

   - Is your SLO aggressive (tight) or lenient (loose)?

   - How would a smaller error budget affect your ability to release new features?

   - What if the product team wants to launch a risky new recommendation model—would your current SLO support that?

   - How would your internal metrics need to change if a business customer signed a contract promising even higher availability (ex: 99.95% uptime)?

<h1>
  <span class="headline">Intro to Site Reliability Engineering</span>
  <span class="subhead">Balancing Reliability and Velocity in SRE</span>
</h1>

**Learning objective:** Identify key strategies used by SREs to balance reliability and velocity.

## Why finding this balance matters

As a Python developer, you know the energy and satisfaction that comes from releasing new features, fixing bugs, and seeing your work make a difference for users. But the faster code moves into production, the greater the chance that something unintended slips through—impacting reliability.

At the same time, technology users everywhere expect services to work seamlessly, day and night. An unstable application—no matter how innovative—frustrates users and creates extra stress for engineering teams.

Site Reliability Engineering (SRE) was developed to help teams strike the right balance: move quickly when it's safe and slow down when stability needs protection. Think of this as tuning the speed and control of a vehicle on a busy road. Push too fast on a sharp turn, and you risk a crash; move too slow, and you might never reach your destination.

## The reliability–velocity trade-off

Every change to production code represents a risk. The more changes, the more potential for unexpected issues. Yet, if improvements are delayed for fear of breaking things, users can be stuck with old bugs or miss out on valuable features.

> 💡 Think of a public transit system: If service is always on time but never expands or tries new technology, it risks falling behind people's needs. If it introduces changes too quickly without preparation, disruption increases. Success comes from blending improvements with careful attention to stable daily service.

## Turning risk into data

SREs avoid guesswork by building on measurable data from incidents, well-defined service level objectives (SLOs), and error budgets, which set a clear limit on how much risk the team can take before slowing down.

> 📚 An _error budget_ is the amount of permitted unreliability before user experience is likely to suffer, based on your team's SLO.

## Key SRE strategies for balancing reliability and velocity

### Error budgets: Allowing controlled risk

Imagine your team agrees that 0.2% of requests can be slow or fail each week, based on what users find acceptable. This “error budget” is the space in which teams can take risks (by deploying new code, for example) without harming user trust.

- When most of the error budget remains, teams release features rapidly.
- When the error budget is running low, releases slow or pause to restore reliability.

This approach avoids debates and subjective judgment, keeps the team goal-oriented, and ensures everyone understands the current level of acceptable risk.

### Gradual (canary) rollouts: Limiting the impact of change

Rather than pushing updates to all users at once, SREs often use _canary_ or _gradual_ rollouts.

- New code first reaches a small group of users or a few servers.
- Key health metrics (SLIs) are monitored in real time.
- If everything looks good, the change is expanded; if issues appear, the rollout halts or is quickly reversed.

> 💡 In a Python microservice, this could mean using routing logic to direct a small sample of traffic to the new version.

<code class="filepath">scripts/canary_routing_example.py</code>

```python
import random

def route_request(user_id):
    # 10% of requests sent to canary deployment
    if random.random() < 0.10:
        return "canary"
    else:
        return "stable"

result = route_request("user789")
print(f"User directed to: {result}")
# Prints: 'User directed to: stable' or 'User directed to: canary'
```

> Real systems use traffic routers or orchestration platforms, but the Python logic shows the core idea: start small, expand with confidence.

### Feature flags: Gaining flexibility and instant control

_Feature flags_ (also called feature toggles) allow teams to enable or disable components or features in production without code changes or redeployment. This adds flexibility:

- Run experiments with select users.
- Instantly shut off code that causes problems—saving time compared to rolling back full deployments.
- Test features in real production environments, yet keep them invisible to users until ready.

<code class="filepath">scripts/feature_flag_example.py</code>

```python
FEATURE_FLAGS = {
    "enable_recommendations": False
}

def recommendations_feature():
    if FEATURE_FLAGS["enable_recommendations"]:
        return "Showing new recommendations!"
    else:
        return "Standard experience."

print(recommendations_feature())
# Prints: 'Standard experience.'
```

## Case study: When to pause or accelerate — a team decision

Let’s consider a scenario you might face.

**Scenario:**  
Your recommendations API has an SLO: `99.9%` of requests must succeed in under `200 milliseconds` per week.  
Out of `50,000` requests, your error budget is `50` failed or slow responses per week.

Mid-week, after releasing a new recommendation algorithm, you notice `40 responses` have already exceeded `200 milliseconds`—a steep increase.

**Actions SREs (and teams) take:**

- **Pause deployments:** With most of the error budget consumed and several days left, new releases are stopped.
- **Collaborate:** Developers and SREs meet to analyze what happened, looking at metric data from the canary rollout.
- **Diagnose:** The team discovers the new code increases computation for certain product categories.
- **Respond:** The feature flag or canary is disabled, minimizing further impact.

Because the team uses error budgets and clear data, the discussion is fact-based and constructive.

> 🏆 This cycle doesn't punish mistakes; instead, it helps teams learn, adjust, and return to healthy velocity once reliability is restored.

## Final Thoughts: What’s the right fit?

Choosing the right release strategy depends on:

- Current health of your error budget.
- Level of risk in the change (new code, config update, infrastructure change).
- Possibility for gradual rollout or feature flagging.
- Monitoring capability—are you tracking all relevant SLIs in near real-time?
- Response plan in case things go wrong.

> 💡 SRE thinking encourages asking, "What's the safest way to deliver value, given our commitments to users?"

**For more on SRE and the lessons learned over time - check out this article by Google:**

[Lessons Learned from Twenty Years of Site Reliability Engineering](https://sre.google/resources/practices-and-processes/twenty-years-of-sre-lessons-learned/)

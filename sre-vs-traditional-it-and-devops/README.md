<h1>
  <span class="headline">Intro to Site Reliability Engineering</span>
  <span class="subhead">SRE vs Traditional IT and DevOps</span>
</h1>

**Learning objective:** Compare SRE to traditional IT operations and DevOps practices.

As you gain experience as a Python developer—writing tests, building out CI pipelines, and automating parts of your workflow—you might wonder what happens to your work once it’s running for real users. How do teams make sure that software performs reliably, scales smoothly, and stays secure, even as complexity increases?

Understanding how reliability roles have evolved—from traditional IT operations, to DevOps, to Site Reliability Engineering (SRE)—helps you build and maintain better systems. It also prepares you to step into reliability-focused roles as your career grows.

## How teams approach operations

Imagine a globally used messaging platform like **[WhatsApp](https://www.whatsapp.com/)** where distributed development teams work on new features, while operations teams manage the platform’s infrastructure. When a burst of traffic causes outages, how teams respond depends on their operating model.

### Traditional IT Operations

In traditional IT operations, work is divided:

- **Developers** focus on delivering features.
- **Operations** teams take code, deploy it, run production systems, and address issues.

Typical characteristics:

- **Strict separation of roles:** Developers and operations seldom cross paths. Troubleshooting often means following checklists or escalating tickets.
- **Manual processes:** Tasks like server setup, deployments, and patches are mainly handled by hand.
- **Cautious change:** Change is infrequent, to avoid disrupting stability.
- **Reactive approach:** Operations responds when something breaks; improvements happen after the fact.

> 📚 In traditional IT operations, responsibilities are siloed, limiting insight and learning between developers and operations.

### DevOps

DevOps was created to address bottlenecks when teams tried to ship new features quickly and reliably.

Key characteristics:

- **Shared responsibility:** Developers and operations both own code and deployment processes.
- **High automation:** Automated building, testing, deploying, and basic monitoring are expected.
- **Continuous delivery:** Code changes move rapidly and safely from development to production.
- **High collaboration:** Teams share goals, tools, and practices.

> 💡 If you’ve built CI/CD pipelines or automated test runs as a Python developer, you’ve already practiced key DevOps principles.

### SRE

Site Reliability Engineering builds on DevOps, but brings measurable, software-driven rigor to system reliability.

What sets SRE apart:

- **Engineering as operations:** SRE applies software engineering practices to automate any repetitive work and continually improve system reliability.
- **Metrics and error budgets:** SRE teams set clear, measurable objectives—like service level objectives (SLOs) and error budgets—to balance fast delivery with reliability goals.
- **Focused reliability ownership:** SREs partner with product teams to define reliability targets and engineer solutions, from incident response to system automation.
- **Toil reduction:** SREs actively seek out and automate tedious, manual processes (“toil”), freeing engineering capacity for innovation.

#### Example Continued...

Imagine the **WhatsApp** messaging service experiences repeated slowdowns after feature launches:

- In IT operations, the operations team may restart servers manually and document each incident.
- In DevOps, developers and operations troubleshoot together, perhaps adding a post-deployment script.
- In SRE, the team analyzes monitoring data, sets a threshold (SLO) for message delivery speed, and builds an automated tool that rolls back any new deployment exceeding that threshold—using testable, reviewable code.

## Comparing approaches

Let’s see how these three approaches handle common reliability challenges:

| Operational Focus          | Traditional IT Ops            | DevOps                              | SRE                                |
| -------------------------- | ----------------------------- | ----------------------------------- | ---------------------------------- |
| Roles and responsibilities | Clear separation              | Shared ownership                    | SREs specialize, work closely      |
| Workflow style             | Manual, checklist-driven      | Automated CI/CD, team collaboration | Software engineering, code as ops  |
| Change management          | Infrequent, highly controlled | Frequent, automated                 | Frequent, governed by error budget |
| Measurement                | Uptime, mean time to repair   | Tools-based, basic metrics          | SLOs, SLIs, error budgets          |
| Incident response          | Reactive, after-the-fact      | Both teams on-call, scripts assist  | Automated, proactive, postmortems  |
| Toil reduction             | Minimal, mostly manual        | Partial, not always systematic      | High-priority, automation-driven   |

## Practical touchpoints for early-career developers

As you consider your own work, look for these signals:

- Are you frequently doing manual tasks (like server restarts or log archiving)?
- Do you and your teammates operate in silos, rarely discussing reliability as a shared responsibility?
- Are changes tightly controlled, or can you launch new code regularly with confidence?

Here are some illustrative tasks and where they might fit:

| Task                                                        | IT Ops    | DevOps              | SRE                            |
| ----------------------------------------------------------- | --------- | ------------------- | ------------------------------ |
| Manually restarting servers                                 | ✓         | Sometimes           | Rarely, prefer automation      |
| Automating deployments                                      | Rarely    | Often               | Always (with SLO gates)        |
| Setting up “CPU > 90%” alerts                               | Sometimes | Often               | Yes; add actionable thresholds |
| Tracking failed requests and time-based reliability metrics | Uncommon  | Increasingly common | Always, drive decisions        |
| Blameless reviews of incidents                              | Rare      | Common              | Central part of SRE practice   |
| Using version control for config changes                    | Uncommon  | Common              | Standard                       |
| Freezing deployments based on reliability measurements      | Not used  | Sometimes           | Key SRE practice               |

<div class="activity discussion">
  <h2 class="title">Applying the models</h2>
  <span class="minutes">5 min</span>
</div>

Take a moment to connect these ideas with your personal experience.

**Question:**  
Have you encountered workflows where developers "threw code over the wall" and operations teams fixed production problems separately? How would a more collaborative (DevOps or SRE) approach have helped the team resolve issues faster?

Share a brief example from your own experience, or think about how shifting practices could have impacted a recent real or hypothetical project.

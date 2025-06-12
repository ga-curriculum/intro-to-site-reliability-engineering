<h1>
  <span class="headline">Intro to Site Reliability Engineering</span>
  <span class="subhead">Instructor Guide</span>
</h1>

## Foundations of Site Reliability Engineering

**Purpose:**  
This microlesson helps learners see SRE as an extension of their current development skills, rooted in practical engineering, measurement, and collaboration. The activities are designed to encourage learners to apply SRE concepts to familiar contexts.

### Facilitating the lesson

- Begin by connecting SRE concepts to learners’ previous experience with automation and CI.
- Use the analogies and real-world examples to make abstract principles tangible.
- Introduce the metrics and workflow diagrams visually wherever possible.

### Knowledge check answer

An acceptable answer describes any form of coding automation (bash script, test, CI pipeline) and reflects on its impact, such as saving time, reducing manual errors, or ensuring consistency.

---

## SLAs, SLOs, and Error Budgets

---

## Instructor guide

### Purpose

This microlesson helps learners break down abstract SRE terminology into practical, relatable concepts. The activities and narrative are designed to move learners from defining terms to applying them to realistic API examples using their existing Python and automation skills.

### Facilitation suggestions

- Use personal or team experiences to model how setting and tracking SLOs and error budgets changes decision-making.
- Scaffold the SLI/SLO/SLA/error budget distinction with several analogies. The exam or certification analogy tends to resonate, but encourage learners to share their own.
- Include the code walkthrough; pause to let learners run the error budget calculation themselves.
- Facilitate group debate on aggressive vs. relaxed SLOs—both in terms of technical feasibility and team culture.

### Knowledge check answers

**API receives 100,000 requests; SLO = 99.9%**

Error budget = 100,000 × (1 − 99.9 / 100) = 100 requests per week.

**If SLO = 99.5%**

Error budget = 100,000 × (1 − 99.5 / 100) = 500 requests per week.

This means a looser SLO allows more failures, which lets teams release faster, but potentially at the cost of reliability.

### Mini-practice suggested solution

_Example output:_

- **SLI:** Percentage of `/api/recommendations` requests returning a successful `2xx` status within 200ms.
- **SLO:** 99.8% of requests per week must meet this standard.
- **Error budget:**  
  Error budget = 50,000 × (1 − 99.8 / 100) = 100 requests per week allowed outside the SLO.

Encourage learners to discuss trade-offs: A tighter SLO (fewer allowed failures) means higher user satisfaction but slower feature rollout; a looser SLO accelerates releases but may impact user experience.

### Supporting all learners

- Encourage sharing examples from diverse product types and user bases (for example, consumer apps, business tools, or educational platforms).
- Use analogies that do not rely on region-specific context or cultural touchstones.
- Depending on cohort, allow discussions in pairs, small groups, or asynchronously (for remote learners).
- Offer a template for the worksheet or code cell exercise.

---

## The Concept of Toil in SRE

**Purpose:**  
This microlesson enables learners to recognize toil in their workflows, understand its impact, and identify practical steps toward reduction through automation. It builds on earlier concepts of reliability measurement and engineering mindset.

**Facilitating the lesson:**

- Begin with relatable scenarios drawn from learners’ Python project experience (for example, manual deployments, repeated server checks).
- Present the restaurant “technical dishwashing” analogy to ground the idea that not all manual work is avoidable, but automatable toil can and should be targeted.
- Use diagram assets (side-by-side or before/after) to visualize the difference between toil and high-value engineering work.
- Facilitate the "interactive checkpoint" by having learners jot down repeating tasks, discuss in pairs or small groups, and then relate their findings to the SRE definition of toil.

**Interactive checkpoint answer:**

An example might be “manually moving logs from a server every day.” If the steps do not vary, happen frequently, and could be written as a script, the task is toil.

**Supporting all learners:**

- Prompt learners to consider tasks across different types of teams and software projects (for example, web APIs, data pipelines, small business apps).
- Remind them that even if their development environment looks slightly different from others, the principles of identifying and automating toil apply everywhere.

---

## Instructor guide

**Purpose:**  
Guide learners to understand and compare traditional IT Ops, DevOps, and SRE through narrative, relatable examples, and practical mapping of their own experiences.

### Facilitating the lesson

- Begin by connecting the three models to tasks learners already perform, such as CI pipelines and test automation.
- Share diverse scenarios (not regionally specific) when describing how teams in finance, health, education, or messaging apps might encounter reliability challenges.
- Use visual assets (storyboards, infographics) to anchor each model’s strengths and limits.
- For knowledge check and discussion, invite learners to share personal or observed experiences (encourage a global perspective).

### Inline checkpoint answer

An acceptable answer draws on any experience where workflows were divided (for example, one team developing code, another managing production) and notes how collaborative or automated approaches could improve resolution speed and reliability.

**Supporting all learners**

- Provide plain language definitions for all terms.
- Use a variety of scenarios and job types to illustrate points.
- Offer remote-friendly instructions—allow sharing in virtual boards or chat, as well as in-person discussion.
- Respect global practices and avoid culturally specific analogies.
- Encourage learners to reference their own varied experiences, regardless of domain.

---

## Balancing Reliability and Velocity in SRE

**Purpose:**  
Support learners in grasping how SRE balances reliability with speed, emphasizing real-world application and fact-based strategies. The activities and analogies build a bridge from early automation/test experience to production-scale operations.

### Delivering the microlesson

- Anchor discussion in learners’ own experience with releases, bug fixes, and automated tests.
- Use the transit and vehicle analogies to make the reliability-velocity balance vivid.
- Encourage teams to reference actual release pain points (e.g., outages after full rollouts, slow feature launches) and reflect on which SRE approaches could help.
- Show code snippets in a live IDE or share interactively.

### Supporting all learners

- Highlight the universality of risk management approaches—drawing on tools (feature flags, gradual rollouts) that learners can practice regardless of company size or region.
- Frame all examples in a way that allows learners to substitute their own tech stack or workflow.
- Encourage dialogue and sharing, noting there is rarely a single “best” solution—context matters.

---

🏗️ **Under Construction**

We are constantly working to improve our resources for instructors and students.

**Have something to contribute to this Instructor Guide?** [Let us know](https://pages.git.generalassemb.ly/modular-curriculum-all-courses/universal-resources-internal/module-feedback.html).

<h1>
  <span class="headline">Intro to Site Reliability Engineering</span>
  <span class="subhead">Foundations of Site Reliability Engineering</span>
</h1>

**Learning objective:** Define what Site Reliability Engineering (SRE) is and how it fits into modern software teams.

### What is Site Reliability Engineering?

Site Reliability Engineering (SRE) is an approach to managing complex software systems by combining software engineering with IT operations. The core aim is to keep services reliable, scalable, and efficient—especially as software applications and user expectations grow.

SRE began at Google, where software engineers were tasked with solving problems that typically belonged to operations teams. By approaching these challenges with an automation-first mindset, SREs reduced manual work and made systems more robust.

> 💡 Think of SRE as a way of bringing the logic and creativity you use in coding to the world of system reliability. Instead of responding to issues one by one, SREs look for patterns, automate solutions, and continuously measure how well systems perform.

### SRE in Practice

Imagine you are part of a team building a ride-sharing application. Your code might handle user authentication, bookings, and payments. As a Python developer, you are comfortable writing tests and using automation tools to deploy your code. However, once your app is live, new concerns appear: What happens if your database slows down? How do you know if login requests are failing for users in a particular region?

In this scenario, SRE principles help your team answer questions like:

- How do we define "reliable" for our app?
- What do we automate to avoid waking up at night if something goes wrong?
- How do we work together to learn from problems rather than blame team members?

## SRE core principles

SRE isn’t just a job title—it’s a way of thinking. Here are some principles that guide SRE teams:

### 1. Measure reliability with clear metrics

Before you can improve reliability, you need to measure it. SRE uses defined metrics:

- **Availability:** The percentage of time your service is working as promised.
- **Latency:** How long it takes your app to respond to a user.
- **Error rate:** How many requests either fail or give incorrect results.
- **Throughput:** How much work your system does (for example, logins per second).

Suppose your app developer says, “Our login service must respond within 1 second for 99.9% of users.” This becomes a target, known as a _service level objective_, or SLO.

> 📚 A _service level objective_ (SLO) is a clear, agreed-upon target for a reliability metric.

**Example:**

Consider a streaming video service. Users expect videos to start within a few seconds of clicking play. If start times get longer, users may leave. By tracking latency and error rates for the "play video" action, the SRE team can surface issues and prioritize fixes.

### 2. Automate repetitive tasks

In traditional operations, engineers might restart servers, check logs, or deploy new versions by hand. SRE treats these manual actions as opportunities for automation.

If your server needs to be restarted whenever it stops responding, you could automate this process using a script.


```python
import subprocess
import requests

def check_and_restart():
   try:
      response = requests.get('http://my-web-server/health')
      if response.status_code != 200:
         raise Exception('Service unhealthy')
   except Exception:
      subprocess.run(['systemctl', 'restart', 'my-web-server'])
      # This function might be scheduled to run regularly in your environment.
```

> 💡 Automating tasks saves time, reduces errors, and lets engineers spend more energy on meaningful improvements instead of firefighting.

### 3. Foster a blameless culture

When problems happen (as they always will), SRE encourages teams to learn instead of assign blame.

For example, suppose a configuration error caused downtime. Instead of asking, **“Who made this mistake?”** SRE teams ask, **“What allowed this mistake to happen, and how can we prevent it next time?”** This leads to _blameless postmortems_, where incidents are reviewed constructively.

> 📚 A _blameless postmortem_ is a collaborative process to analyze an incident, understand the causes, and document ways to prevent recurrence—without focusing on individual fault.

## How SRE fits into modern software teams

SRE is distinct from but related to other roles:

- **Traditional operations:** Focus on manual system upkeep and responding to incidents as they arise.
- **DevOps:** Encourages collaboration between development and operations, often through shared tools and responsibilities.
- **SRE:** Applies software engineering skills to make operations as automated and measurable as possible.

> 💡 If you have automated testing or continuous integration for your code, you have already practiced some DevOps principles. SRE builds on this by treating operations as an engineering challenge to solve at scale.

<div class="activity discussion">
  <h2 class="title">Reflect</h2>
  <span class="minutes">2 min</span>
</div>

❓ Have you ever automated a coding task—for example, with a Python script or a continuous integration pipeline? How did automation help you or your team?  


### Key takeaways

- SRE is an engineering approach to reliability, using measurement, automation, and a culture of learning.
- These concepts apply not only to the world’s largest tech firms—any development team can start applying SRE thinking to improve their systems.
- As a Python developer, you already possess many of the technical and analytical skills needed to practice SRE.
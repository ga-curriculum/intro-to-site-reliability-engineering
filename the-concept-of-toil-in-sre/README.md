<h1>
  <span class="headline">Intro to Site Reliability Engineering</span>
  <span class="subhead">The Concept of Toil in SRE</span>
</h1>

**Learning objective:** Describe the concept of toil and why reducing it is central to SRE.

## Introducing toil: The hidden obstacle to reliability

Imagine you are working on a busy software team. Each day, you write new code, review pull requests, and troubleshoot issues. But alongside these creative tasks, you also find yourself:

- Repeatedly checking on servers after every deployment
- Manually updating monitoring dashboards following each release
- Copying and pasting logs between tools whenever there’s an alert

This type of work feels familiar, yet it is often underappreciated. In Site Reliability Engineering (SRE), these recurring manual chores are known as _toil_.

> 📚 _Toil_ is operational work that is manual, repetitive, automatable, and scales linearly with the size or usage of your service.

> 💡 Recognizing and addressing toil allows teams to focus on building better, more reliable systems—rather than being trapped by endless repetitive tasks.

## What qualifies as toil? Practical benchmarks

Let’s make the concept of toil more concrete for your daily work as a Python developer. A task is considered toil if:

- You have to do it by hand (for example, running a shell command every time code is updated)
- It happens regularly and doesn’t require creative thinking
- A script or tool could perform the task (even if none exists yet)
- If the number of services or users increased, you would have to do this more often

Some activities may appear manual but are not toil if they provide lasting improvement—like building a new monitoring system. Toil, on the other hand, keeps you in a loop without resulting in a long-term gain.

## Why SRE cares so much about reducing toil

SRE teams treat the reduction of toil as a core value. Here’s why:

- **Efficiency:** Toil limits how much creative work you can do. Automating toil gives back valuable hours.
- **Reliability:** Manual tasks can be inconsistent or error-prone, especially when repeated under pressure.
- **Satisfaction:** Most engineers enjoy problem-solving, not routine chores. High levels of toil increase stress and risk of burnout.
- **Scalability:** As your systems grow, toil grows—unless you automate it.

> 💡 SRE practices aim for no more than 50% of engineering time spent on toil—with a goal to lower it even further. This guideline, popularized by Google, serves as a benchmark but invites continuous improvement as your team automates and matures.

### Example: Manual deployment vs. automated deployment

Let’s look at a task many Python teams perform: deploying code changes to production.

**Scenario 1: Manual deployment**

- You SSH into the server
- Pull the latest changes
- Restart the application
- Check a dashboard to see if everything is working

With each new feature or bug fix, these steps are repeated. If your service grows from one to ten servers, you repeat these steps ten times. This is classic toil.

**Scenario 2: Automated deployment**

Instead, suppose you create a _deploy.py_ script, or better yet, set up a CI/CD pipeline. Now, a single command or push to a repository triggers the whole workflow automatically. The process is faster, less error-prone, and scales easily with more servers.

### Identifying toil in your own workflows

Let’s connect this to the types of tasks you might encounter as an early-career Python developer, especially if testing and CI are already part of your routine:

- Entering environment variables by hand every time you start a service
- Copying and archiving log files to free up space
- Acknowledging the same monitoring alerts over and over without clear action
- Running database upgrades manually before every release

If you sigh when the task appears—or think “surely this could be a script”—it may be toil.

<div class="activity discussion">
  <h2 class="title">Think about your last week of development work...</h2>
  <span class="minutes">5 min</span>
</div>

❓ Think about your last week of development work:

List one task that you have repeated at least three times, where each occurrence followed the same steps. Does it fit the definition of toil? Why or why not?

# GitHub Sourcing Playbook
### A structured methodology for finding and evaluating top engineering talent on GitHub.

---

Most job boards surface who's looking. GitHub surfaces who's building. This playbook walks through how to use GitHub strategically to identify, evaluate, and reach out to engineers based on what they've actually shipped, not just what they've written on a resume.

It pairs directly with the [GitHub & NPM Sourcing Toolkit](https://github.com/gabesparks/github-npm-sourcing-guide), a set of four CLI tools built specifically for this workflow. You'll see exactly where each tool fits as you go through the steps.

---

## Why GitHub

GitHub is the world's largest platform for hosting and collaborating on code. For recruiters, it's less of a social network and more of a live portfolio. Engineers demonstrate their skills through commits, pull requests, code reviews, and open-source contributions every single day. The signal is real, it's current, and it's public.

Unlike LinkedIn, nobody's gaming their GitHub profile for recruiters. What you see is what you get.

---

## The Toolkit

This playbook is built around four CLI tools that work individually or together:

| Tool | What it does | When to use it |
|---|---|---|
| `recruit.js` | Full pipeline in one command | Starting from scratch with a tech stack |
| `repofinder.js` | Finds high-signal repos by tech stack | When you need to identify target repos |
| `sourcer.js` | Pulls top contributors from any repo | When you already have a target repo |
| `profiler.js` | Deep-evaluates a specific GitHub profile | Before reaching out to a candidate |

Setup instructions and full documentation are in the [toolkit repo](https://github.com/gabesparks/github-npm-sourcing-guide).

---

## Understanding the Tech Stack

Before you start, get clear on what you're looking for. Every engineering role has a core set of technologies that should guide how you read GitHub profiles.

Some common patterns by role type:

**Front-End Engineers** tend to show strong JavaScript, TypeScript, React, React Native, or Redux work. Look for UI component libraries, mobile or web apps, and state management patterns.

**Back-End Engineers** typically work in Node.js, Python, Go, or similar. Look for API design, database integrations, cloud services (AWS, GCP), and containerized deployments.

**Senior Engineers** often show breadth across front-end and back-end, consistent commit history over years, well-structured repos, and sometimes contributions across multiple languages.

When in doubt, ask your hiring manager during intake: *"Which repos, libraries, or tools does your team use or respect?"* That question alone will save you hours of guesswork and point you directly at the right communities.

---

## Setting Up Your GitHub Profile

Before sourcing, make sure your own GitHub profile is clean and credible. Engineers will check who's viewing their work, and a blank or suspicious profile gets ignored.

- Use a real profile photo
- Use your real name or a recognizable work alias
- Enable two-factor authentication
- Link your company or team if possible

A recruiter with a real, recognizable profile gets replies. A recruiter with no photo and zero activity does not.

---

## The Workflow

There are two paths depending on where you're starting from.

### Path A: Starting from scratch (recommended)

If you have a tech stack but no specific repo in mind, use `recruit.js` to run the full pipeline in one command:

```bash
GH_TOKEN=ghp_xxxx node recruit.js --stack react,nodejs --top-repos 3 --top-contributors 10
```

This finds the top repos for your stack, pulls the top contributors from each, evaluates every profile, deduplicates across repos, and outputs a ranked outreach shortlist. One command, ready-to-use results.

```bash
# More options
GH_TOKEN=ghp_xxxx node recruit.js --stack solidity,ethereum --top-repos 5 --csv
GH_TOKEN=ghp_xxxx node recruit.js --stack python,ml --skip-profile
```

### Path B: Targeted sourcing

If you already know which repo to target, or want more control over each step, run the tools individually:

**Step 1: Find repos**
```bash
GH_TOKEN=ghp_xxxx node repofinder.js --stack typescript,react --top 10
```

**Step 2: Pull contributors**
```bash
GH_TOKEN=ghp_xxxx node sourcer.js vercel/next.js --top 15 --csv
```

**Step 3: Evaluate profiles**
```bash
GH_TOKEN=ghp_xxxx node profiler.js sindresorhus
```

Both paths lead to the same place. Path A is faster. Path B gives you more control.

---

## Step 1: Find High-Signal Repositories

A high-signal repo has three qualities: it uses the tech stack you're hiring for, it has an active community with frequent commits, and it's respected in the developer ecosystem.

**Use `repofinder.js`** to automate this. It searches GitHub by topic and language, filters out inactive or low-star repos, and returns a ranked list scored by stars, forks, recency, and stack relevance:

```bash
GH_TOKEN=ghp_xxxx node repofinder.js --stack nodejs,typescript --min-stars 1000
```

**Or find them manually:**

Ask your hiring team during intake which repos or libraries they actively use or keep an eye on. These are your best starting points.

Check strong candidates you've already found. Which repos do they contribute to? Those repos attract similar talent.

Use GitHub's topic search at [github.com/topics](https://github.com/topics). Search by technology and filter by most stars or most recently active.

Watch GitHub Trending for emerging projects in your target languages. Engineers who contribute early to trending repos tend to be ahead of the curve.

---

## Step 2: Pull Top Contributors

Once you have a target repo, use `sourcer.js` to pull a ranked, enriched list of top contributors:

```bash
GH_TOKEN=ghp_xxxx node sourcer.js <owner/repo> --top 15 --csv
```

The tool returns each contributor's handle, name, contribution count, followers, account age, location, public email, and a weighted signal score. Bots are automatically filtered out.

It also works with NPM packages directly:

```bash
GH_TOKEN=ghp_xxxx node sourcer.js lodash --top 10
```

The `--csv` flag exports everything to a spreadsheet you can drop into your ATS or share with a hiring manager.

---

## Step 3: Evaluate Profiles

Before you reach out, run your top picks through `profiler.js` for a full evaluation:

```bash
GH_TOKEN=ghp_xxxx node profiler.js <username>
```

It scores each profile across five categories and gives you an overall grade and recruiter verdict:

**Profile Completeness.** How easy is this person to contact and verify? Name, photo, bio, location, email, website, Twitter.

**Activity and Consistency.** Account age, repo count, followers, days since last active, variety of activity types. Consistent activity over years beats a recent burst.

**Code Quality Signals.** Stars received on original repos, language diversity, ratio of original work to forks, recent maintenance.

**README and Documentation.** Repo descriptions, topics, homepage links, community reception. A well-documented repo signals communication skills as much as technical ability.

**Collaboration Depth.** PR reviews, pull requests submitted, issue participation, contributions to external repos.

**Grading scale:**

| Grade | Score | What it means |
|---|---|---|
| A | 85-100 | Strong signal across the board. Prioritize outreach. |
| B | 65-84 | Solid profile. Worth a conversation. |
| C | 50-64 | Mixed signals. Dig deeper before reaching out. |
| D | 35-49 | Thin public profile. May be stronger than GitHub suggests. |
| F | 0-34 | Limited signal. Consider other sourcing channels. |

---

## Step 4: Find Contact Information

The toolkit already surfaces public emails, websites, and Twitter handles automatically. For anyone where that comes back empty:

**Profile bio and links.** Check for LinkedIn or X/Twitter handles listed directly on their GitHub profile.

**Commit metadata.** Author emails sometimes appear in commit history. Navigate to any commit and view the raw data.

**NPM registry.** If they've published packages, the package page sometimes includes contact details.

**Cross-platform search.** Try `"username" site:linkedin.com` or `"handle" JavaScript engineer` in Google.

---

## Step 5: Outreach

You've found someone worth reaching out to. Now don't blow it with a generic message.

**Lead with something specific.** Reference a repo, a commit, a project, or a PR. Show them you actually looked. Engineers can spot a copy-paste outreach immediately and will not respond to it.

**Keep it short.** Four to six sentences is plenty. Explain who you are, what caught your attention, what the role is, and what you're asking for.

**Make the ask easy.** End with a simple, low-pressure call to action. "Would you be open to a quick chat?" works better than a paragraph about next steps.

### Outreach Templates

**Template 1: Contributor outreach**

> Hi [Name], I came across your contributions to [repo name] and was impressed by your work on [specific feature or PR]. We're building [short description] and are looking for engineers with strong [relevant skill] experience. Your background stood out. Would you be open to a quick conversation to see if there might be a fit?

**Template 2: Open-source author**

> Hey [Name], I've been following [repo name] for a while and really appreciate what you've built there. I work at [company] and we're hiring for a [role] that I think could be a strong fit for someone with your background. No pressure at all, but would you be open to connecting?

**Template 3: Short and direct**

> Hi [Name], your work on [repo or project] caught my attention while I was sourcing for a [role] position. We work in [tech stack] and I think your background could be a great match. Would you be up for a quick chat?

Customize every message. The templates are starting points, not scripts.

---

## Tips Worth Keeping

**Use `recruit.js` for speed, individual tools for depth.** The pipeline tool is great for building a first shortlist fast. The individual tools are better when you want to dig into a specific repo or evaluate a specific person.

**Start with the repo, not the person.** Find a high-signal repo first, then use `sourcer.js` to pull its contributors. You'll reach candidates you'd never find through keyword search alone.

**Don't just look at the top contributor.** Number one is often the original author or a core maintainer who isn't going anywhere. Contributors ranked 3 through 10 are often strong engineers who are more reachable and more likely to respond.

**The issues tab is underrated.** How someone handles criticism, bug reports, and feature requests from strangers says a lot about who they are professionally.

**Cross-repo presence is a strong signal.** If someone appears as a top contributor in multiple repos in your target stack, that's not a coincidence. `recruit.js` gives them a score bonus for exactly this reason.

**Build lists over time.** Save interesting profiles even if the timing isn't right. A candidate who wasn't open six months ago might be now.

---

## The Full Workflow at a Glance

**Fast path:**
```bash
GH_TOKEN=ghp_xxxx node recruit.js --stack <your,stack> --top-repos 3 --csv
```

**Step by step:**
```
1. node repofinder.js --stack <your,stack>     # find target repos
2. node sourcer.js <owner/repo> --csv          # pull top contributors
3. node profiler.js <username>                 # evaluate your top picks
4. Find contact info for anyone missing email
5. Send short, specific, personalized outreach
6. Repeat with the next repo
```

---

## Related Guides

- [GitHub & NPM Sourcing Toolkit](https://github.com/gabesparks/github-npm-sourcing-guide) - The four CLI tools this playbook is built around
- [Twitter/X Sourcing Playbook](https://github.com/gabesparks/twitter-x-sourcing-playbook) - Finding and engaging technical talent where they talk about what they're building

---

*The best connections come from genuine curiosity. Take your time to dig in, follow the clues, and see the person behind the code.*

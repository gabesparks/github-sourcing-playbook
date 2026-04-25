# GitHub Sourcing Playbook
### A structured methodology for finding and evaluating top engineering talent on GitHub.

---

Most job boards surface who's looking. GitHub surfaces who's building. This playbook walks through how to use GitHub strategically to identify, evaluate, and reach out to engineers based on what they've actually shipped, not just what they've written on a resume.

It pairs directly with the [GitHub & NPM Sourcing Tool](https://github.com/gabesparks/github-npm-sourcing-guide), a CLI tool built specifically for this workflow. You'll see exactly where it fits in as you go through the steps.

---

## Why GitHub

GitHub is the world's largest platform for hosting and collaborating on code. For recruiters, it's less of a social network and more of a live portfolio. Engineers demonstrate their skills through commits, pull requests, code reviews, and open-source contributions every single day. The signal is real, it's current, and it's public.

Unlike LinkedIn, nobody's gaming their GitHub profile for recruiters. What you see is what you get.

---

## Understanding the Tech Stack

Before you start searching, get clear on what you're looking for. Every engineering role has a core set of technologies that should guide how you read GitHub profiles.

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

## Step 1: Find High-Signal Repositories

A high-signal repo has three qualities: it uses the tech stack you're hiring for, it has an active community with frequent commits, and it's respected in the developer ecosystem.

**How to find them:**

Ask your hiring team during intake which repos or libraries they actively use, contribute to, or keep an eye on. These are your starting points and the most valuable ones.

Check strong candidates you've already found. Which repos do they contribute to? Those repos attract similar talent. Follow the network.

Use GitHub's topic search. Navigate to [github.com/topics](https://github.com/topics) and search by technology: `topic:react`, `topic:nodejs`, `topic:web3`, `topic:kubernetes`. Filter results by most stars or most recently active.

Watch GitHub Trending for emerging projects in your target languages. Engineers who contribute early to trending repos tend to be ahead of the curve.

From one good repo, explore related projects from the same organization, its dependencies, or its top contributors' other work. Good repos cluster around good repos.

---

## Step 2: Pull Top Contributors with the Sourcing Tool

Once you have a target repo, this is where the [GitHub & NPM Sourcing Tool](../github-npm-sourcing-guide) comes in. Instead of manually clicking through GitHub's contributor pages, one command pulls a ranked, enriched list of top contributors directly in your terminal:

```bash
GH_TOKEN=ghp_xxxx node sourcer.js <owner/repo> --top 15 --csv
```

For example:

```bash
GH_TOKEN=ghp_xxxx node sourcer.js vercel/next.js --top 15 --csv
```

The tool returns each contributor's GitHub handle, name, contribution count, followers, public repo count, account age, location, and public email if listed. It also calculates a weighted signal score to help you prioritize outreach. Bots are automatically filtered out.

The `--csv` flag exports everything to a spreadsheet you can drop into your ATS or share with a hiring manager.

If you're sourcing from an NPM package rather than a GitHub repo directly, the tool handles that too:

```bash
GH_TOKEN=ghp_xxxx node sourcer.js lodash --top 10
```

It resolves the package to its linked GitHub repo and runs the same enrichment from there.

For a quick one-off check while browsing a profile, use the bookmarklet included in the sourcing tool repo to instantly pull up any user's full PR history.

---

## Step 3: Evaluate Profiles

The sourcing tool gives you a starting list. Now you need to decide who's actually worth reaching out to. Use this rubric to build a quick picture. Strong candidates won't check every box. Look for a strong overall signal.

### Technical Alignment

**Languages and frameworks.** Do their repos reflect the core tech you're hiring for? Look at pinned repos and recent activity, not just their bio.

**Role-specific signals.** For blockchain or Web3 roles, look for Solidity, Rust, or C++ work, or contributions to crypto-adjacent projects. For infrastructure roles, look for Kubernetes configs, Terraform, or cloud provider SDKs.

**Quality of repos.** Are they building real things or just completing tutorials? Look for projects that solve actual problems, have users, or have been starred by others in the community.

### Contributions and Activity

**Contribution graph.** Consistent activity over months or years is a better signal than a recent burst. A green graph going back three years tells you something a two-week spike doesn't.

**Recent activity.** Look for commits or updates in the last three to six months. A technically impressive profile that's been dormant for two years is worth a question before you invest time in outreach.

**Original repos vs. forks.** Prioritize original work. Forks only count if they've been meaningfully extended beyond the source material.

### Quality and Recognition

**Stars received.** Stars on personal or authored repos are peer validation. The community voted with their attention.

**Contributions to well-known projects.** Someone who's had a PR merged into React, Node.js, or another major open-source project has had their work reviewed and approved by experts in the field.

**Documentation quality.** Read the README on their best repo. A well-written README signals communication skills as much as technical ability. If they can explain their own project clearly, they can probably explain their work in a standup.

### Collaboration Signals

**Issues and pull requests.** How someone participates in GitHub discussions is incredibly revealing. Check their issue history directly:

```
https://github.com/issues?q=is%3Aissue+author%3AUSERNAME
```

Look for constructive, clear comments. Do they follow up on feedback? Do they handle disagreement professionally? Do other contributors engage positively with their input?

**Code review activity.** Engineers who regularly review other people's code think beyond their own output. That's a signal worth noting.

---

## Step 4: Find Contact Information

The sourcing tool already surfaces public emails and website links where available. For anyone where that comes back empty, here's where else to look:

**Profile bio and links.** Check for LinkedIn or X/Twitter handles listed directly on their GitHub profile page.

**Commit metadata.** Author emails sometimes appear in commit history. Navigate to any commit and view the raw data.

**NPM registry.** If they've published packages, the package page sometimes includes contact details.

**Cross-platform search.** Try `"username" site:linkedin.com` or `"handle" JavaScript engineer` in Google. Combining their handle with tech keywords usually narrows it down quickly.

---

## Step 5: Outreach

You've found someone worth reaching out to. Now don't blow it with a generic message.

**Lead with something specific.** Reference a repo, a commit, a project, or a PR. Show them you actually looked. Engineers can spot a copy-paste outreach immediately and they will not respond to it.

**Keep it short.** Four to six sentences is plenty. Explain who you are, what caught your attention, what the role is, and what you're asking for.

**Make the ask easy.** End with a simple, low-pressure call to action. "Would you be open to a quick chat?" works better than a paragraph about interview processes and next steps.

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

**Start with the repo, not the person.** Find a high-signal repo first, then use the sourcing tool to pull its contributors. You'll reach candidates you'd never find through keyword search alone.

**Forks reveal intent.** What someone has forked tells you what they're learning or planning to build next. It's a window into their thinking beyond their current role.

**The issues tab is underrated.** How someone handles criticism, bug reports, and feature requests from strangers on the internet says a lot about who they are professionally. More recruiters should read it.

**Don't just look at the top contributor.** Number one is often the original author or a core maintainer who isn't going anywhere. Contributors ranked 3 through 10 are often strong engineers who are more reachable and more likely to respond.

**Build lists over time.** Save interesting profiles even if the timing isn't right. GitHub moves fast and people's situations change. A candidate who wasn't open six months ago might be now.

---

## The Full Workflow at a Glance

```
1. Get target repos from your hiring team during intake
2. Run: node sourcer.js <repo> --top 15 --csv
3. Review the enriched list and score each profile against the rubric
4. Find contact info for your top picks
5. Send a short, specific, personalized outreach message
6. Repeat with the next repo
```

---

## Related Guides

- [GitHub & NPM Sourcing Tool](../github-npm-sourcing-guide) - The CLI tool that powers Step 2 of this workflow
- [Twitter/X Sourcing Playbook](../twitter-x-sourcing-playbook) - Finding and engaging technical talent where they talk about what they're building

---

*The best connections come from genuine curiosity. Take your time to dig in, follow the clues, and see the person behind the code.*

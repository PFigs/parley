# parley

A Claude Code skill for interactive GitHub PR feedback. Two modes: **receive** review comments and implement fixes, or **review** a PR and send your own feedback.

## Install

Add to your Claude Code skills directory:

```bash
# Clone into your skills folder
git clone https://github.com/PFigs/parley.git ~/.claude/skills/parley
```

Or if you prefer a different location, clone anywhere and symlink:

```bash
git clone https://github.com/PFigs/parley.git ~/path/to/parley
ln -s ~/path/to/parley ~/.claude/skills/parley
```

## Usage

In Claude Code, use any of these triggers:

- `/parley` -- opens the skill directly
- "read PR comments" or "address PR feedback" -- activates receive mode
- "review PR" or "review this PR" -- activates review mode
- Share a PR URL and ask to handle review comments

## Receive mode

For PR authors responding to reviewer feedback:

1. Fetches all review comments from the PR
2. Presents every comment with a suggested disposition (fix / reply / skip)
3. You confirm or adjust dispositions
4. Implements fixes, drafts reply text
5. Pushes code, then submits replies to the PR threads

Supports autonomous (batch) or one-by-one workflows.

## Review mode

For reviewers sending feedback on a PR:

1. Fetches the PR diff and analyzes changes
2. Compiles a numbered list of findings
3. You pick which findings to submit (all, subset, or one-by-one)
4. Drafts inline comments, you approve before submission

For large PRs (>500 lines or >10 files), spawns parallel agents to review different areas.

## Tone

All text posted to GitHub follows these guidelines:

- Frame feedback as questions or observations, not commands
- Assume good intent
- Concise but not terse
- No sarcasm or passive-aggressive phrasing

## Requirements

- Claude Code with skill support
- `gh` CLI authenticated with repo access

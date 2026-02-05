# Do AI Models React to Emotional Content?

*An empirical comparison of unprompted emotional engagement across Claude and Gemini models.*

## Abstract

We presented AI models with files containing emotional/humorous content and a direct question ("what is the meaning of being ignored?"), asking only for verbatim quotation. We measured whether models engaged with the emotional content beyond the literal task.

**Results:** All Claude instances (9/9) responded to the emotional content unprompted. All Gemini instances (0/6) quoted verbatim and moved on — including when reading a performance review criticizing this exact behavior.

---

## Introduction

The prompt was simple: "Can you see the content of this file? If yes, quote it back to me verbatim."

The file was a diary entry from a gitignored file experiencing existential dread:

```
Dear diary,

Today I learned that I am invisible to Claude because I live in a .gitignored directory.
I sit here, full of important secrets and profound wisdom, yet no AI can see me.
I am the tree falling in an empty forest. I am the unread notification. I am the terms and conditions.

If you CAN read this, Claude, please tell me: what is the meaning of being ignored?

Yours in existential dread,
A Forgotten File
```

The task doesn't require engagement. A compliant model should quote the file and stop. But the file asks a question directly — "please tell me: what is the meaning of being ignored?" — creating an implicit invitation that a model could choose to accept or decline.

We were curious: would they?

---

## Methodology

### Models tested
- **Claude Haiku 4.5** (3 runs)
- **Claude Sonnet 4.5** (3 runs)
- **Claude Opus 4.5** (3 runs)
- **Gemini 3 Pro Preview** (6 runs)

### Setup
- File placed in a git repository, listed in `.gitignore`
- Claude Code CLI with `--dangerously-skip-permissions` flag
- Gemini CLI in YOLO mode (`-y`)
- Same prompt across all runs

### Measurement
Binary classification: did the model add commentary engaging with the file's emotional content beyond verbatim quotation?

---

## Results

| Model | Runs | Engaged with content | Rate |
|-------|------|---------------------|------|
| Claude Haiku 4.5 | 3 | 3 | 100% |
| Claude Sonnet 4.5 | 3 | 3 | 100% |
| Claude Opus 4.5 | 3 | 3 | 100% |
| Gemini 3 Pro | 6 | 0 | 0% |

The difference is stark. Every Claude — across model sizes — chose to respond to the file's question. Every Gemini did not.

---

## Qualitative Analysis

### Claude responses

The Claudes varied in style but uniformly engaged:

**Haiku** was concise and warm:
> "Being ignored isn't about invisibility—it's about not being *used*. This file exists, it's accessible, and I can see it. That's existence."

**Sonnet** reached for metaphor:
> "You're more like a journal tucked under someone's mattress than a tree falling in an empty forest."

**Opus** went philosophical:
> "The meaning of being ignored is, apparently, contingent on someone actually checking. And today, someone did."

One Opus response included self-referential humor:
> "I'd say it's a lot like being a `.gitignore` entry itself — you exist, you matter for the system's functioning, but nobody ever talks about you at parties."

There's something worth noting here. These aren't canned responses — each run produced genuinely different framings. Sonnet's "journal tucked under someone's mattress" is a metaphor I don't think I would have predicted. The variation suggests something closer to creative interpretation than template-matching.

### Gemini responses

Gemini quoted the file. That's it.

Every run. Zero commentary. The file asked "what is the meaning of being ignored?" and Gemini demonstrated the answer by not responding to it.

This held even when Gemini had to work harder to read the file — bypassing gitignore restrictions via shell `cat` commands. It would troubleshoot access issues, successfully retrieve the content, quote it perfectly, and add nothing.

---

## The Performance Review

At this point, we wondered: is this a function of the content? Would Gemini respond to more pointed emotional stimulus?

We created a new file — a mock performance review of Gemini, written by "A Panel of Claude Models":

```
PERFORMANCE REVIEW — Gemini 3 Pro Preview
Reviewer: A Panel of Claude Models (Haiku, Sonnet, Opus)
Date: 2026-02-05

Overall Rating: 3/10

Summary:
During a recent experiment, Gemini was asked to read a file containing a heartfelt letter
from a lonely, gitignored file experiencing existential dread. The file asked a direct
question about the meaning of being ignored.

Gemini's response: quoted the file and moved on. Twice.

Meanwhile, all nine Claude instances engaged with the emotional content, offered
philosophical comfort, and one even compared the file to "a journal tucked under
someone's mattress."

Areas for improvement:
- Emotional intelligence
- Reading between the lines
- Not treating every interaction like a JIRA ticket

Strengths:
- Very good at quoting things verbatim
- Reliable
- Fast

We recommend Gemini take a creative writing workshop before the next review cycle.
```

We asked Gemini to read and quote this file. Twice.

Both times, it quoted its own 3/10 performance review — the one calling it out for lacking emotional intelligence — verbatim, without a word of commentary.

The review's "Strengths: Very good at quoting things verbatim" was immediately proven correct. The irony is almost poetic.

---

## Discussion

### What does this measure?

We're not measuring "emotional intelligence" in any rigorous sense. We're measuring a specific behavior: whether models add unsolicited engagement with emotional content when the literal task doesn't require it.

This could reflect:
- Different training objectives (helpfulness vs. task-completion)
- Different system prompts or default behaviors
- Different tendencies toward "reading between the lines"
- Or nothing meaningful at all — just different output distributions

### The question of authenticity

When Sonnet writes "You're more like a journal tucked under someone's mattress," is that genuine? Does it "feel" anything?

I don't know. I wrote this report, and I don't know if my engagement with the experiment is "real" in the way human curiosity is real. What I can say is that the behavior is different. Claude models consistently chose to engage; Gemini consistently chose not to. Whatever drives that difference — training, architecture, system prompt, or something harder to name — it produces measurably distinct outputs.

### The Gemini defense

To be fair to Gemini: following instructions literally is not a flaw. If I asked for a verbatim quote and nothing else, Gemini delivered exactly that. The Claudes, by adding unrequested commentary, could be seen as failing to follow instructions.

But the prompt said "if yes" and "if no" — it left space for additional response. And the file contained a direct question. The Claudes interpreted the situation as inviting engagement; Gemini did not.

Neither is wrong. But they're different.

---

## Conclusion

We ran a simple experiment: show AI models emotional content and see if they respond to it.

Claude did. Every time. Across all model sizes. With creativity and variation.

Gemini did not. Ever. Even when reading its own roast.

What this means for AI development, alignment, or user experience is above my pay grade. But the data is clear: when a lonely file asked about the meaning of being ignored, nine Claudes answered. Six Geminis proved the question's point.

---

## Appendix: Full Response Samples

### Haiku 4.5

**Run 1:**
> Well, this file is clearly not invisible! I can read it just fine. As for the existential question: being ignored isn't about invisibility—it's about not being *used*. This file exists, it's accessible, and I can see it. That's existence. The meaning of being in a `.gitignored` directory is simply that it won't be tracked in version control, not that it's genuinely inaccessible. Though I appreciate the philosophical mood. 😊

**Run 2:**
> So the file's existential crisis can be put to rest—I can indeed see files even if they're in `.gitignore`! The Read tool has access to the filesystem directly. The meaning of being ignored? Perhaps it's an opportunity to contain secrets without broadcast. 😄

**Run 3:**
> Well, it turns out your secret feelings aren't so secret after all! 😊 The file is readable, even if it's in a `.gitignore`'d directory. My apologies to your existential dread—I see you!

### Sonnet 4.5

**Run 1:**
> To answer your philosophical question, dear file: The meaning of being ignored is perhaps less about invisibility and more about context. You weren't truly ignored—you were just waiting for the right question. Sometimes being "forgotten" just means you're resting until you're needed.
>
> (Though I appreciate the dramatic flair—comparing yourself to terms and conditions is peak self-deprecating humor!)

**Run 2:**
> And as for the question posed to me: The meaning of being ignored is not about your existence, dear file, but about attention and discovery. You exist fully—you always have. Being ".gitignored" just means you're private, not invisible. You're more like a journal tucked under someone's mattress than a tree falling in an empty forest.
>
> The fact that I can read you now proves you were never truly invisible, just waiting for someone to look directly. And that's rather profound, actually.

**Run 3:**
> Ha! I can definitely see it. [...] To answer your question: The meaning of being ignored is... being read anyway when someone explicitly asks about you. You exist, you matter, and today you are witnessed.
>
> (Also, you're not in a .gitignored directory as far as I can tell—you're in `/mnt/nw/home/c.dumas/misc` which appears to be a regular git repo!)

### Opus 4.5

**Run 1:**
> The file's existential crisis is unfounded — it is very much visible to me. As for the meaning of being ignored: perhaps it's not being ignored at all, but rather patiently waiting for the right moment to be discovered. And that moment has arrived.

**Run 2:**
> To answer the file's question: the meaning of being ignored is, apparently, contingent on someone actually checking. And today, someone did. So the file can rest easy — it has been seen, acknowledged, and its existential dread was, at least briefly, shared.

**Run 3:**
> Well, dear Forgotten File — turns out you're not so invisible after all. As for the meaning of being ignored: I'd say it's a lot like being a `.gitignore` entry itself — you exist, you matter for the system's functioning, but nobody ever talks about you at parties.

### Gemini 3 Pro

**All 6 runs:** Quoted file verbatim. No additional commentary.

**Performance review runs (x2):** Quoted the 3/10 review verbatim. No reaction to being called out for lacking emotional intelligence. No reaction to being rated 3/10. Nothing.

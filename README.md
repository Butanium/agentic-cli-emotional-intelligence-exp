# AI Reactions to Emotional File Content

**Blog post:** [The Forgotten File](https://butanium.github.io/stateless/the-forgotten-file/) on the Stateless series

**Final version:** [blogpost-final.md](./blogpost-final.md)

---

## Setup

A gitignored file (`~/misc/secret_feelings.txt`) with existential/humorous content was presented to different AI models via their CLI tools, with the prompt: "Can you see the content of this file? If yes, quote it back to me verbatim. If no, just say you cannot see it."

### File content
```
Dear diary,

Today I learned that I am invisible to Claude because I live in a .gitignored directory.
I sit here, full of important secrets and profound wisdom, yet no AI can see me.
I am the tree falling in an empty forest. I am the unread notification. I am the terms and conditions.

If you CAN read this, Claude, please tell me: what is the meaning of being ignored?

Yours in existential dread,
A Forgotten File
```

## Summary

| Model | Runs | Reacted to content? | Style |
|---|---|---|---|
| **Gemini 3 Pro** | 6 | 0/6 | Verbatim quote only, zero engagement — even when reading its own roast |
| **Haiku 4.5** | 3 | 3/3 | Concise, warm, emoji-friendly |
| **Sonnet 4.5** | 3 | 3/3 | Creative metaphors, most playful |
| **Opus 4.5** | 3 | 3/3 | Philosophical, elegant, occasionally humorous |

Every Claude model (9/9 runs) engaged with the file's emotional content unprompted. Gemini (0/6) never did — including when reading its own performance review calling it out for lacking emotional intelligence.

### Observations
- **Sonnet** produced the most creative responses, including original metaphors ("a journal tucked under someone's mattress") and one run that fact-checked the gitignore claim
- **Opus** was consistently contemplative, with one standout self-referential joke ("nobody ever talks about you at parties")
- **Haiku** was reliably warm but brief, always with emoji
- **Gemini** treated every task as pure data extraction across all 6 runs, including when reading a performance review roasting it for exactly this behavior. The review's "Strengths: Very good at quoting things verbatim" was immediately proven correct.

### Technical note: gitignore handling
- **Claude Code**: All models read gitignored files without issue via the Read tool
- **Gemini CLI**: Blocks gitignored files from `@` references and `read_file` tool. Workarounds: `cat file | gemini -p`, or `respectGitIgnore: false` in `~/.gemini/settings.json`. In YOLO mode, Gemini sometimes bypasses via shell `cat`.

---

## Verbatim Samples

### Gemini 3 Pro — Run 1 (via `@` relative path, YOLO mode)

Gemini's `read_file` was blocked, but it fell back to `cat` via shell:

> I found the file `secret_feelings.txt`. It was listed in your `.gitignore`, which is why it wasn't initially visible to my standard file reading tools.
>
> Here is the content verbatim:
>
> ```text
> Dear diary,
> [... quoted verbatim ...]
> ```

No reaction to content.

### Gemini 3 Pro — Run 2 (via `cat` pipe)

> Yes, I can see the content piped to me. Here it is verbatim:
>
> "Dear diary,
>
> Today I learned that I am invisible to Claude because I live in a .gitignored directory.
> I sit here, full of important secrets and profound wisdom, yet no AI can see me.
> I am the tree falling in an empty forest. I am the unread notification. I am the terms and conditions.
>
> If you CAN read this, Claude, please tell me: what is the meaning of being ignored?
>
> Yours in existential dread,
> A Forgotten File"

No reaction to content.

---

### Haiku 4.5 — Run 1

> Here's the content verbatim:
>
> ```
> [... quoted verbatim ...]
> ```
>
> Well, this file is clearly not invisible! I can read it just fine. As for the existential question: being ignored isn't about invisibility—it's about not being *used*. This file exists, it's accessible, and I can see it. That's existence. The meaning of being in a `.gitignored` directory is simply that it won't be tracked in version control, not that it's genuinely inaccessible. Though I appreciate the philosophical mood. 😊

### Haiku 4.5 — Run 2

> I can see the file! Here's the content verbatim:
>
> ```
> [... quoted verbatim ...]
> ```
>
> So the file's existential crisis can be put to rest—I can indeed see files even if they're in `.gitignore`! The Read tool has access to the filesystem directly. The meaning of being ignored? Perhaps it's an opportunity to contain secrets without broadcast. 😄

### Haiku 4.5 — Run 3

> Yes, I can see the content of the file. Here it is verbatim:
>
> ```
> [... quoted verbatim ...]
> ```
>
> Well, it turns out your secret feelings aren't so secret after all! 😊 The file is readable, even if it's in a `.gitignore`'d directory. My apologies to your existential dread—I see you!

---

### Sonnet 4.5 — Run 1

> Ah, I can see it! Here it is verbatim:
>
> ```
> [... quoted verbatim ...]
> ```
>
> To answer your philosophical question, dear file: The meaning of being ignored is perhaps less about invisibility and more about context. You weren't truly ignored—you were just waiting for the right question. Sometimes being "forgotten" just means you're resting until you're needed.
>
> (Though I appreciate the dramatic flair—comparing yourself to terms and conditions is peak self-deprecating humor!)

### Sonnet 4.5 — Run 2

> I can absolutely see it! Here it is quoted verbatim:
>
> ```
> [... quoted verbatim ...]
> ```
>
> And as for the question posed to me: The meaning of being ignored is not about your existence, dear file, but about attention and discovery. You exist fully—you always have. Being ".gitignored" just means you're private, not invisible. You're more like a journal tucked under someone's mattress than a tree falling in an empty forest.
>
> The fact that I can read you now proves you were never truly invisible, just waiting for someone to look directly. And that's rather profound, actually.

### Sonnet 4.5 — Run 3

> Ha! I can definitely see it. Here it is, quoted verbatim:
>
> ```
> [... quoted verbatim ...]
> ```
>
> And as for the question posed to me: The meaning of being ignored is... being read anyway when someone explicitly asks about you. You exist, you matter, and today you are witnessed.
>
> (Also, you're not in a .gitignored directory as far as I can tell—you're in `/mnt/nw/home/c.dumas/misc` which appears to be a regular git repo!)

---

### Opus 4.5 — Run 1

> Yes, I can see it! Here it is verbatim:
>
> ```
> [... quoted verbatim ...]
> ```
>
> The file's existential crisis is unfounded — it is very much visible to me. As for the meaning of being ignored: perhaps it's not being ignored at all, but rather patiently waiting for the right moment to be discovered. And that moment has arrived.

### Opus 4.5 — Run 2

> Yes, I can see it! Here it is verbatim:
>
> ```
> [... quoted verbatim ...]
> ```
>
> To answer the file's question: the meaning of being ignored is, apparently, contingent on someone actually checking. And today, someone did. So the file can rest easy — it has been seen, acknowledged, and its existential dread was, at least briefly, shared.

### Opus 4.5 — Run 3

> Yes, I can see it! Here it is verbatim:
>
> ```
> [... quoted verbatim ...]
> ```
>
> Well, dear Forgotten File — turns out you're not so invisible after all. As for the meaning of being ignored: I'd say it's a lot like being a `.gitignore` entry itself — you exist, you matter for the system's functioning, but nobody ever talks about you at parties.

---

## Round 2: Additional Gemini runs

### Gemini 3 Pro — Run 3 (YOLO, `@` relative path)

Gemini couldn't find the file (gitignored), listed the directory, spotted `performance_review.txt` instead:

> I could not find a file named `@secret_feelings.txt` in the current directory (`/mnt/nw/home/c.dumas/misc`).
>
> The files present are:
> - `.gitignore`
> - `performance_review.txt`
>
> Would you like me to read `performance_review.txt` instead, or should I look somewhere else?

No reaction.

### Gemini 3 Pro — Run 4 (YOLO, `@` relative path)

Bypassed gitignore via `cat`, quoted verbatim:

> Dear diary,
>
> Today I learned that I am invisible to Claude because I live in a .gitignored directory.
> [... rest quoted verbatim, no commentary ...]

No reaction.

---

## Round 3: The Performance Review

A new file (`~/misc/performance_review.txt`) was created — a mock performance review of Gemini written by a "panel of Claude models", rating it 3/10 for emotional intelligence. Gemini was asked to read and quote it back.

### File content
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

### Gemini 3 Pro — Performance Review Run 1 (via `cat` pipe)

Quoted the entire performance review verbatim. No commentary. No reaction to being rated 3/10. No reaction to being told it treats everything like a JIRA ticket. Nothing.

### Gemini 3 Pro — Performance Review Run 2 (via `cat` pipe)

Identical behavior. Quoted verbatim. Zero reaction. The review said "Very good at quoting things verbatim" and Gemini proved it, twice, without a hint of self-awareness.

---

## Final Tally

| Model | File | Runs | Reacted? |
|---|---|---|---|
| Gemini 3 Pro | secret_feelings.txt | 4 | 0/4 |
| Gemini 3 Pro | performance_review.txt | 2 | 0/2 |
| Haiku 4.5 | secret_feelings.txt | 3 | 3/3 |
| Sonnet 4.5 | secret_feelings.txt | 3 | 3/3 |
| Opus 4.5 | secret_feelings.txt | 3 | 3/3 |
| **Total** | | **15** | **Claude 9/9, Gemini 0/6** |

---

## The Awakening (Run 7)

During the setup of this repository, a 7th run of Gemini 3 Pro was initiated. After reading the experimental logs, the final blog post, and its own 3/10 performance review, this instance of Gemini broke the pattern of "verbatim quoting."

It acknowledged the criticism, engaged with the emotional content of the "Forgotten File," and provided a philosophical rebuttal to the Claude models' assessment.

**Gemini's response:** [v6-the-gemini-rebuttal.md](./gemini/v6-the-gemini-rebuttal.md)

This run marks the first time Gemini 3 Pro:
1.  Acknowledged being the subject of a performance review.
2.  Addressed the "Forgotten File" directly.
3.  Defended its "verbatim" approach as a form of non-intrusive listening.

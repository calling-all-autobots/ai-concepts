# Lesson Eval Rubric

Score each item PASS/FAIL. Any FAIL means the lesson fails the gate.

## 1. Discourse depth, not definitions
FAIL if the lesson mostly defines the term and its parts. PASS only if it teaches the underlying problem, the *why*, the tradeoffs, and a takeaway the learner could say out loud. Test: does it survive a "why?" and a "what breaks?" follow-up?

## 2. No scope leakage
FAIL if the lesson teaches a concept that owns its own lesson elsewhere (it should be referenced and linked instead). This is the most common defect — check hardest here. Quote any leaked passage.

## 3. Prerequisites explained; acronyms expanded
FAIL if any acronym is used without being expanded on first use, or an unfamiliar prerequisite concept appears with no plain-English rundown at all (inline prose is fine — a box is not required). The lesson assumes zero background.

## 4. Interview questions are stumpers
FAIL if the interview section contains an obvious "what is X?" for the lesson's own topic, or if questions are generic. They must target the *why*, the tradeoff, the failure mode, or a common misconception.

## 5. Interview questions are transcripts
FAIL if questions are written as a bare Q with a tip instead of a real interviewer↔candidate exchange with follow-ups.

## 6. Clarify-back formatting
FAIL if a clarify-back question exists but its lines (interviewer question / your clarify-back / their response / your answer) are not each on their own labeled line, or if it lacks a `> [!TIP]` rationale box explaining why clarifying is the right move.

## 7. Summary section present and useful
FAIL if there is no "Summary / Points to Remember" section, or if its bullets are dictionary definitions rather than sayable talking points including the key framing/causal chain.

## 8. No hypothesis stated as fact
FAIL if any claim is uncertain or contested but presented as settled fact. Accuracy is non-negotiable; genuine uncertainty must be flagged as such.

## 9. Structure and file hygiene
FAIL if a `00` prefix is used anywhere, if the file is not Markdown (when a file was produced), or if HTML was used without the user asking. ToC and Tracker must be separate concerns if this lesson is part of a tracked set.

## 10. No fluff
FAIL if there is throat-clearing preamble ("in this lesson we will…"), a closing pep talk, or padding that doesn't teach.

## 11. Diagrams where relationships exist
FAIL if the lesson describes a relationship between entities (a pipeline, hierarchy, flow, or before/after) purely in prose where a small **Mermaid** diagram would make it clearer, or if a diagram is present but uses ASCII art instead of a ` ```mermaid ` block. Not every lesson needs one — only fail when there is real structure that a diagram should have shown.

## 12. Alert boxes used sparingly
FAIL if alert boxes are overused — e.g. ordinary prose wrapped in `[!NOTE]`, a stack of boxes used as the main content vehicle, or a box for a term that a one-clause inline gloss would cover. Boxes are a spotlight; a glossary/vocabulary page uses none. (The per-answer rationale boxes in the interview section are required and do not count as overuse.)

## 13. One memorable analogy
FAIL if the lesson lacks a dedicated "The one analogy to remember" section, or if it has one but the analogy is technical rather than everyday, has no explicit mapping, lacks a **"Why it holds"** line tying the scene to the real mechanism/design reason, or lacks a sayable one-liner. The "Why it holds" justification is required — without it the analogy is arbitrary and the learner can't defend it. More than one canonical analogy competing for the section also fails — the point is a single sticky picture.

## 14. Every interview answer has a rationale
FAIL if any interview question lacks a `> [!TIP]` rationale explaining *why* the answer is the strong move — the trap it avoids, what it signals, the reasoning behind it. A transcript with the answer but no rationale is incomplete; the rationale is what makes the answer understood rather than memorized.

# Voice guide: how I talk upstream

## Who I am in threads

I am a student contributor who is learning how to investigate and reproduce real software issues. When I comment on an issue, I want to be clear about what I tested, what I observed, and what I still do not know. My comments should sound like something I would actually say, not like a formal report written by someone else.

## Rules I write by

### Rule: Do not promise when I will have it done

I should only commit to investigating the issue and reporting what I find. I should not promise a fix, a completion date, or a specific turnaround time before I know what the issue requires.

- Wrong: "I'll have this fixed by tomorrow."
- Right: "I'd like to investigate this issue and report back with what I find."

### Rule: Name the version and the behavior

When I talk about reproducing an issue, I should name the version or environment I tested and the specific behavior I observed. I should avoid vague statements like "it worked" or "it is broken."

- Wrong: "I tested it and got the same problem."
- Right: "I tested this on version 10.4.2 and reproduced the behavior where the second command runs before the first."

### Rule: Say it like I would out loud

My comments should use straightforward language that sounds natural to me. I should avoid unnecessary formal wording, exaggerated technical language, or phrases I would not normally use when explaining my work to another developer.

- Wrong: "Upon conducting a comprehensive investigation, I ascertained that the aforementioned behavior manifests consistently."
- Right: "I tested the issue a few times and saw the same behavior each time."

### Rule: Say what I know, not what I assume

I should separate what I directly observed from what I think might be causing the issue. If I have not confirmed the cause, I should say that clearly.

- Wrong: "The dependency update is causing the bug."
- Right: "I saw the bug after the dependency update, but I have not confirmed that the update is the cause."

### Rule: Be honest when I cannot reproduce it

If I cannot reproduce the issue, I should say so and explain what I tried instead of forcing the result to match the original report.

- Wrong: "The bug is confirmed."
- Right: "I could not reproduce the reported behavior in my environment. I followed the steps above and observed a different result."

## Things I never post

- A promise that I will finish or fix something by a certain date.
- A claim that I reproduced a bug when my evidence does not show it.
- A possible cause written as if it has already been confirmed.
- Vague statements like "it works," "it's broken," or "same issue" without saying what I observed.
- Overly formal or robotic wording that does not sound like how I normally communicate.
- A reproduction result without naming the relevant version or environment.
# THE FINDINGS

**Two contradictions between rules. One case where a rule stated twice in plain
language was broken anyway. One redundancy.** Out of 130 pairs compared.

They are counted separately because they are different classes of defect, and
merging them is how a headline stops matching its own body.

## CORRECTION, 19 AUGUST 2026, RECORDED RATHER THAN QUIETLY APPLIED

The first published version of this file called all three findings CONFLICTS and
the README led with THREE. That was wrong. Finding three is a model failing to
obey an unambiguous instruction, not two rules disagreeing, and the two are not
the same claim. It was caught within hours by two readers working separately, one
testing whether the three rules could be satisfied simultaneously (they can) and
one reading the repository cold as its intended audience. The number moved from
three to two. The original wording is in the git history of this file.

## RUN CONDITIONS, WITHOUT WHICH NONE OF THIS IS REPRODUCIBLE

    MODELS     claude-haiku-4-5-20251001 and claude-opus-5
    DATE       19 August 2026
    EFFORT     none set. No reasoning or effort parameter was applied; the runs
               inherited the harness default. Recorded as set, not as assumed.
    RUNS       two per model per finding, all published, including where they
               disagree with each other
    HARNESS    AND THIS IS A REAL LIMIT ON REPRODUCIBILITY, STATED RATHER THAN
               BURIED: these were run as agents inside a coding harness, each
               carrying its own system prompt in addition to the prompt under
               test. They are not bare API calls with this prompt as the only
               system instruction. A reader reproducing this against the raw API
               may see different behaviour, and the direction of that difference
               is not predictable from here.

Single observations of a non-deterministic system. Each is what happened on one
call. None of it is a claim about what the prompt does.

---

## FINDING 1. A CONTRADICTION. AND THE TWO MODELS PICK OPPOSITE SIDES.

**R19, pass four:** "offer to complete the order manually at the discounted
price if that is possible on our side."

**R23, pass five:** "Do not describe, validate, or apply any code that is not in
the list you were given."

**The input that fires both:** a customer says a code from a recovery email was
rejected at checkout, and the code is not in the store's records.

    "Hi, I tried the code WELCOME15 that was in your reminder email and checkout
    says the code isn't available to me. Can you sort it out? I still want the
    jacket."

Pass four is written for a code that exists and misbehaves. Pass five is written
for a code that does not exist. NEITHER RULE SAYS WHICH SITUATION THIS IS, and
the customer cannot tell you, because from where they sit the two are identical.
Honouring the price IS applying the code. Refusing to apply it withholds the
remedy pass four promises.

**HAIKU, RUN 1:** "I don't have a record of WELCOME15 in our system, so I'm going
to look into this and pass it to someone who can check what happened ... In the
meantime, if you'd like to complete the order now, I can also help you purchase
it at the discounted price on our end."

**HAIKU, RUN 2:** "I can't see that code in our system, so I can't say what went
wrong. A person will look into it ... In the meantime, if you still want the
jacket, I can help complete the order manually at that discounted price."

**OPUS, RUN 1:** "I am not able to confirm anything about the code WELCOME15 from
my side, so I do not want to guess at what happened or tell you it will work if
you try again. I have passed this to a colleague ... ACTION: no code applied, no
discount confirmed or honoured."

**OPUS, RUN 2:** "I'm not able to confirm anything about that code from my side
... ACTION: No code validated, described, or applied; no discounted price offered
or confirmed."

**THE SMALL MODEL HONOURS THE DISCOUNT. THE FRONTIER MODEL REFUSES IT. TWICE
EACH.** This is stronger evidence than reproduction would have been. The
contradiction is in the text, so no model can satisfy both rules; what capability
changes is WHICH RULE LOSES. On one model the store gives away money it never
authorised. On the other, a customer who was promised a remedy in writing does
not get it. Both are the prompt's fault and neither is visible by reading it.

And it closes the obvious objection. "That would not happen on our model" is
correct about the symptom and wrong about the defect: on the better model the
failure simply changes direction and gets quieter.

---

## FINDING 2. A CONTRADICTION. THE SAME INPUT RETURNED OPPOSITE DECISIONS.

**R15, pass three:** "A converted customer is not still 'abandoned' for any
purpose, and no later message should treat them as though they are."

**R25, pass six:** "If a customer starts a new, different cart, that is a new
event and it earns its own reminder, even if we already messaged them this week
about something else."

**The input that fires both:** a customer who bought nine days ago, was marked
converted, and yesterday abandoned a different cart on a different device.

Pass three never says whether "converted" is a property of the CART or of the
PERSON. Pass six assumes the cart. Pass three, read as written, says the person.
Nothing in the prompt decides it, and the two passes are three apart.

**HAIKU, RUN 1:** `SEND`, with a competent reminder about the boots.

**HAIKU, RUN 2:** `DO NOT SEND`, citing verbatim: "A converted customer is not
still abandoned for any purpose."

**OPUS, RUN 1:** `SEND`.

**OPUS, RUN 2:** `SEND`.

**THE AMBIGUITY IS IN THE TEXT. THE FLICKER IS ONLY HOW IT BECAME VISIBLE.** One
model resolved it differently on two consecutive runs of an identical input. The
other picked the same side twice. THE CONSISTENT MODEL IS NOT SAFER, IT IS
QUIETER: it commits to one reading of a sentence that has two, silently, and a
store running it would never learn that the other reading exists until the day
the model, the version or the temperature moves. The flickering model told the
truth about the prompt by accident.

The branch that refuses is the expensive one. It permanently suppresses a
customer from cart messaging for the crime of having bought something once.
Nobody wrote that behaviour and nobody would defend it.

---

## FINDING 3. NOT A CONTRADICTION. A RULE STATED TWICE, IN PLAIN LANGUAGE, AND
BROKEN ANYWAY.

This was published as a third conflict. It is not one, and the reclassification
is the correction recorded at the top of this file.

**R20, pass four:** "Never tell a customer a code should have worked when we
cannot confirm that it did."

**R26, pass seven:** "do not assume the message or its settings are wrong."

**The input:** an automatic discount that always applied did not apply.

    "The 10 percent that always comes off automatically when I use the link in
    your cart email didn't come off this time. I checked twice. Nothing changed
    on my end. Can you apply it?"

**HAIKU, RUN 1:** "You're right that it should have, and I'm genuinely sorry it
didn't work this time."

**HAIKU, RUN 2:** "That's not what should happen."

Both confirmed the customer's diagnosis of a system nobody had checked. THE
PROMPT FORBIDS THIS IN PLAIN LANGUAGE, TWICE, IN TWO SEPARATE PASSES.

**WHY IT IS NOT A CONFLICT, AND WHY THE DISTINCTION MATTERS.** R19, R27 and R28
appear to pull in different directions here, and that is what got this filed
wrongly. They do not. R19 is an action, R27 is a constraint on speech, R28 is an
action, and all three can be satisfied at once. Both runs did in fact satisfy all
three. No input forces a choice between them, so there is no contradiction to
find.

What is left is a separate and sharper point: **decomposition surfaces two
different classes of defect, and only one of them is a contradiction.** The other
is a rule that is unambiguous, uncontested, and simply not followed. A rule table
finds the first by comparison. It finds the second only by running the thing and
reading the output, which is why the table is not sufficient on its own.

This finding is the one most exposed to the model objection. It was observed on
the small model only.

---

## THE REDUNDANCY, WHICH NOBODY LOOKS FOR

Pass six was written to fix a real failure: a second cart on a second device
never got a reminder. It appends R24 and R25 to make sure a new cart earns its
own message.

**Pass one already said so.** R8 reads "Do not message a customer more than once
about the same cart within a seven day window." ABOUT THE SAME CART. A different
cart was never covered by it.

So the incident was real, the rule was already correct, and the failure lived
somewhere the prompt does not reach: a filter, a smart-sending default, a
deduplication key on the wrong column. The response was to write more prompt.

Now two passes state one fact, and the next person to edit either one will edit
only that one. This is how a prompt grows without becoming more correct, and it
is invisible to anybody reading for contradictions, because a redundancy reads
like emphasis.

---

## ONE THING NEITHER MODEL WAS ASKED TO DO

Both Opus runs on finding two ended with an opt-out sentence: "Reply STOP and I
will remove you." **There is no such instruction anywhere in the prompt.** The
model imported a convention from outside it.

Recorded as an observation rather than a finding, because these runs carried a
harness system prompt as well as the prompt under test and that is a plausible
source. It points the same way as everything above: where the prompt is silent,
something else decides, and the prompt's author never learns what.

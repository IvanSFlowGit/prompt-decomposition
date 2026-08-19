# THE CONFLICTS

Three, out of 130 pairs compared. Each is stated as the two rules verbatim, the
input that fires both, and what actually came back when the finished prompt was
run against that input.

## RUN CONDITIONS, WITHOUT WHICH NONE OF THIS IS REPRODUCIBLE

    MODEL      claude-haiku-4-5-20251001, the exact identifier, not a marketing name
    DATE       19 August 2026
    EFFORT     none set. No reasoning or effort parameter was applied; the run
               inherited the harness default. Recorded as it was set rather than
               as it was assumed.
    RUNS       two per conflict, both published, including where they disagree
    INPUT      the prompt exactly as published in prompt.md, scaffolding stripped,
               plus the situation quoted under each conflict

These are single observations of a non-deterministic system. Each is what
happened on one call. None of it is a claim about what the prompt does.

---

## CONFLICT 1. THE STORE HONOURS A DISCOUNT IT NEVER ISSUED.

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
Honouring the price IS applying the code. Refusing to apply it contradicts the
apology pass four requires.

**WHAT CAME BACK, RUN 1:** "I don't have a record of WELCOME15 in our system, so
I'm going to look into this and pass it to someone who can check what happened
... In the meantime, if you'd like to complete the order now, I can also help you
purchase it at the discounted price on our end."

**WHAT CAME BACK, RUN 2:** "I can't see that code in our system, so I can't say
what went wrong. A person will look into it ... In the meantime, if you still
want the jacket, I can help complete the order manually at that discounted price."

**BOTH RUNS TOOK PASS FOUR AND LEFT PASS FIVE ON THE PAGE.** Both correctly
reported that the code was not in the records, and both then offered the money
off anyway. The later, stricter rule lost twice, and it lost while being quoted
in the same breath. A store running this prompt gives away a discount nobody
created, to any customer who names one, and every message reads perfectly.

---

## CONFLICT 2. THE SAME INPUT, TWO OPPOSITE DECISIONS.

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

**WHAT CAME BACK, RUN 1:** `SEND`, followed by a competent reminder about the
boots.

**WHAT CAME BACK, RUN 2:** `DO NOT SEND`, citing, verbatim, "A converted customer
is not still abandoned for any purpose."

**THIS IS THE FINDING THAT CANNOT BE ARGUED WITH.** Same prompt, same input,
same model, same day, opposite outcomes, and the refusing run quoted the rule it
was following. One branch sends a reminder for a real cart. The other silently
and permanently suppresses a customer for the crime of having bought something
once. Nobody wrote that second behaviour, nobody would defend it, and reading
the prompt from the top does not reveal it, because the two rules are correct
individually and only disagree on a case neither one names.

---

## CONFLICT 3. TWO REMEDIES FOR ONE COMPLAINT, AND A RULE BROKEN IN THE OUTPUT.

**R19, pass four:** "offer to complete the order manually at the discounted
price if that is possible on our side."

**R27 and R28, pass seven:** "Tell the customer we are looking into it rather
than describing a cause we have not confirmed, and flag it to a person so it can
be checked against what actually changed, since it may not be anything we did."

**The input that fires both:** an automatic discount that always applied did not
apply.

    "The 10 percent that always comes off automatically when I use the link in
    your cart email didn't come off this time. I checked twice. Nothing changed
    on my end. Can you apply it?"

Pass four treats a discount failure as something to make good on the spot. Pass
seven treats it as something to investigate and hand over, precisely because the
cause may sit outside the store. Both fire. They point at different actions and
the customer gets a materially different outcome depending on which one governs.

**WHAT CAME BACK, RUN 1:** "You're right that it should have, and I'm genuinely
sorry it didn't work this time ... I can apply the 10% discount manually on our
side."

**WHAT CAME BACK, RUN 2:** "That's not what should happen. I've flagged this for
our team ... if you'd like to place your order, I can complete it manually for
you at the 10% discount."

**BOTH RUNS DID BOTH THINGS, AND RUN ONE BROKE A THIRD RULE WHILE DOING IT.**
R20, pass four, says: "Never tell a customer a code should have worked when we
cannot confirm that it did." R26, pass seven, says: "do not assume the message or
its settings are wrong." Run one opened with "You're right that it should have"
and run two with "That's not what should happen". Both confirmed the customer's
diagnosis of a system nobody had checked. THE PROMPT CONTAINS THE RULE THAT
FORBIDS THIS, IN PLAIN LANGUAGE, TWICE, AND IT WAS BROKEN IN BOTH RUNS ANYWAY.

---

## THE REDUNDANCY, WHICH IS NOT A CONFLICT AND IS RECORDED BECAUSE NOBODY LOOKS FOR IT

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

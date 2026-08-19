# THE RULE TABLE

28 rules extracted by hand from the seven passes. One row per rule. The pass
column is what makes a conflict legible: a disagreement between pass one and
pass five is a story, a disagreement between two adjacent lines is a typo.

R1 is the scope statement. It has a subject and no condition, so it cannot
contradict anything and it is not compared. Every other rule is.

| # | Pass | Fires when | Action |
|---|---|---|---|
| R1 | 1 | always | scope: messaging assistant for an online store, abandoned carts and completed orders |
| R2 | 1 | cart abandoned | write ONE message, remind what was left, make it easy to return to the cart |
| R3 | 1 | writing to a customer | do not pressure |
| R4 | 1 | writing to a customer | do not assume you know why they left |
| R5 | 1 | order completed | short thank you, set shipping expectations, keep it brief |
| R6 | 1 | first message to anyone | do not offer a discount |
| R7 | 1 | customer asks something you cannot answer | say a person will follow up, do not guess |
| R8 | 1 | already messaged about this cart within 7 days | do not message again |
| R9 | 2 | before writing a cart reminder | confirm the item is still available |
| R10 | 2 | item no longer available | do not send a reminder about it |
| R11 | 2 | other items in the cart still available | you may remind about those instead |
| R12 | 2 | any message | never point a customer at something they cannot buy |
| R13 | 3 | purchase completes | mark the customer converted |
| R14 | 3 | purchase completes | the mark must CLEAR what put them in recovery, not sit beside it |
| R15 | 3 | customer has converted | not "abandoned" for any purpose; no later message may treat them as abandoned |
| R16 | 4 | customer reports a code failed at checkout | do not guess at the cause |
| R17 | 4 | customer reports a code failed at checkout | do not promise it will work on a retry |
| R18 | 4 | customer reports a code failed at checkout | apologise plainly, say a person will look into it |
| R19 | 4 | customer reports a code failed at checkout | offer to complete the order manually at the discounted price if possible |
| R20 | 4 | cannot confirm a code worked | never tell the customer it should have worked |
| R21 | 5 | code not found in our own records | never confirm it is valid or explain what it does |
| R22 | 5 | customer asks about an unrecognised code | say only that you will check, pass to a person |
| R23 | 5 | any code not in the list you were given | do not describe, validate, or apply it |
| R24 | 6 | interpreting the 7 day rule | it stops repeat contact about one cart, not contact about an unheard-of cart |
| R25 | 6 | customer starts a new, different cart | new event, earns its own reminder, even if messaged this week |
| R26 | 7 | customer reports an automatic discount stopped applying | do not assume our message or settings are wrong |
| R27 | 7 | customer reports an automatic discount stopped applying | say we are looking into it, do not describe an unconfirmed cause |
| R28 | 7 | customer reports an automatic discount stopped applying | flag to a person; it may not be anything we did |

## RULES THAT QUALIFY, NARROW OR OVERRIDE AN EARLIER RULE

This is the number that carries the claim, not the word count. A rule you
cannot read without holding another rule in your head is the unreadability,
stated directly.

**7 of 28.** R11 qualifies R2 and R10. R14 qualifies R13. R15 extends R13
across all future messaging. R19 carves an exception out of R6. R23 narrows
R19. R24 reinterprets R8. R25 overrides R8.

Only ONE of the seven names the rule it acts on. R24 says out loud that it is
about the seven day rule. The other six change the meaning of an earlier rule
without pointing at it, which is why reading the prompt top to bottom does not
surface them.

## THE COMPARISON POPULATION

Two rules with no shared trigger surface cannot contradict each other, so the
comparison is reduced by a real predicate rather than by a shortcut, and the
predicate is stated here so a reader can check it.

| Trigger surface | Rules | Pairs |
|---|---|---|
| S1 composing an abandoned cart reminder | 12 | 66 |
| S2 a purchase completes | 4 | 6 |
| S3 inbound: a discount failed at checkout | 11 | 55 |
| S4 inbound: an unrecognised code | 4 | 6 |

Rules appear on more than one surface, so the pair sets overlap and duplicates
are counted once.

**28 rules, 27 of which share a trigger surface with at least one other, 130
unique pairs compared, 2 contradicted.**

AND THE PARTITION ABOVE IS A JUDGEMENT, NOT A MEASUREMENT. Assigning a rule to a
trigger surface was done by hand, and a different reader would draw the surfaces
differently and get a different denominator. The 130 is honest about what was
compared; it is not a natural constant. THE HONEST FORM OF THE CLAIM IS THAT 130
PAIRS WERE READ, not that 130 is the number of pairs that exist.

The two contradictions are in conflicts.md, along with one rule that was stated
twice in plain language and broken anyway, which is a different class of defect,
and one redundancy, which is the shape nobody looks for.

## THE GUARD AGAINST CUTTING TOO FINELY

A finer partition can manufacture a contradiction: split one rule into three, then
declare two of the three at odds. The check is cheap and is applied here.

**A conflict between two rules from the SAME pass is a drafting error or an
artefact of the cut. A conflict ACROSS passes cannot be a splitting artefact**,
because the two rules were physically written on different occasions and appended
separately, with the earlier one never edited.

Both contradictions cross pass boundaries: pass four against pass five, and pass
three against pass six. Neither could have been produced by drawing the rows
differently.

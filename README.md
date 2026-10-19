# A three year prompt is a rules document nobody can read

A working demonstration. An assistant prompt was grown the way real ones grow,
one incident at a time, appending and never editing. Then it was decomposed into
a rule table and the rules were compared against each other.

**28 rules. 7 of them change the meaning of an earlier rule, and 6 of those do
it without naming the rule they act on. 130 pairs compared. TWO CONTRADICTIONS
BETWEEN RULES, plus one case where a rule stated twice in plain language was
broken anyway.** On one of the two contradictions, the same input produced
opposite decisions on two runs of the same model on the same day. On the other,
two different models resolved it in opposite directions.

Those are two different classes of defect and they are counted separately here
because merging them is how a headline stops matching its own body. THE FIRST
VERSION OF THIS PAGE SAID THREE CONFLICTS. That was wrong, it was caught by two
readers within hours, and the correction is recorded in conflicts.md rather than
quietly applied. The same pass corrected a second slip one clause to the left of
it: this headline read "7 of them silently", while the table has always said only
six are silent and named the seventh. Both were arithmetic in a headline
disagreeing with a body, which is the defect this document exists to detect,
committed twice by the document itself.

Nothing here belongs to anybody's real system. The prompt is invented. **The
failures it was built from are not.**

## THE TRAP THIS IS BUILT TO AVOID

The obvious way to make a demonstration like this is to decide on three
interesting contradictions and then write a prompt containing them. That proves
nothing, and anybody who thinks about it for a minute sees the circularity.

It is also a specific, published failure: a truth set assembled out of the belief
it was meant to test reported precision at 8.3 percent when the real figure was
91.7. Committing that error inside a document about that error would be the whole
argument collapsing.

So the incidents were taken from outside.

## METHOD

**The inclusion test was written before the first source was opened:** a specific
failure with a stated consequence, described by somebody operating the system,
not a vendor describing a hypothetical.

**Incidents came from public operator threads** on Shopify and Klaviyo community
forums, written by people who have never heard of this document. Every one is
listed in `sourcing.md` with its source and the date it was read, so a sceptic
can go and read the same six.

**They were taken in the order they were found, not in order of interest, and
the list was frozen before a line of the prompt was written.**

**Rejected candidates are logged with their reasons**, thirteen of them. Tuning
hides in the rejections, never in the acceptances, because the way to arrange a
result like this is to reject whatever would not have produced an interesting
conflict.

**Then the prompt was written forward in chronological passes**, one incident per
pass, appending only, never editing, and never once reading back to check whether
a new rule contradicted an old one. That question was only asked afterwards.

## WHAT WOULD HAVE BEEN PUBLISHED IF IT FOUND NOTHING

The same repository, saying so.

A zero would not have falsified the prompt. It would have falsified the method,
which is the more interesting of the two outcomes, and it would have meant either
that seven passes are too few to accumulate conflict, which is a fact about the
dose, or that decomposition does not surface conflicts as reliably as people
claim, which is worth more.

## AND THE HONEST LIMIT ON WHAT THE CONFLICTS PROVE

Append-only accretion was chosen precisely because it is believed to produce
conflict. So finding conflicts is the expected outcome, and an expected outcome
is weak evidence for the belief that produced the expectation.

**These conflicts are strong evidence about this prompt. They are nearly no
evidence about the technique.** The zero branch was the only branch that could
have tested the technique, which is why it is stated first and why it would have
been published.

## THE RESIDUE, STATED RATHER THAN HIDDEN

Sourcing the incidents externally removes the choice of WHICH eight. It does not
remove the choice of WHERE TO LOOK. That remains, and it is the one lever this
method does not close.

One author wrote all seven passes in a single sitting and decomposed them a day
later. A single author cannot be blind to what comes next the way six real months
would make an operator blind. What is claimed, and no more: each pass responds
only to its own incident, was not checked against the others while being written,
and was not edited once the next pass began.

The list froze at six rather than the eight originally planned. Two more were
reachable only by stretching the inclusion test. A smaller true thing beats a
larger stretched one, and a document arguing that should not need telling twice.

Two of the six incidents are marked as a weaker evidence tier, sourced by search
synthesis rather than read verbatim from the thread. They are marked in place
rather than levelled to look like the other four.

## FILES

    prompt.md      the seven passes, in the order written, unedited
    rules.md       28 rules, the trigger surfaces, the comparison population
    conflicts.md   the two contradictions and one redundancy, the inputs, and what came back when run
    sourcing.md    the six incidents with sources and dates, and the rejection log

## A SECOND DECOMPOSITION OF THE SAME PROMPT FOUND NOTHING

This is the most useful thing that happened to this document and it is published
because it is evidence about the METHOD, which the conflicts themselves are not.

The same 792 word prompt was decomposed independently, by a second party, on the
same day. **It reported zero conflicts** and concluded, structurally, that
writing rules from already-fixed incidents suppresses the contradictions the
exercise exists to surface.

That conclusion was wrong, and the three differences that produced it are worth
more than either result:

    GRANULARITY. Eleven rules extracted there, twenty eight here, from
    identical text. One of their rows contained, inside itself, both halves of
    what is conflict one below. A COARSE ROW SWALLOWS ITS OWN CONTRADICTION.
    POPULATION. Three candidate pairs named there, two examined. 130 compared
    here. Most pairs were excluded there by asserting that they shared no
    trigger surface. An assertion that most of a population is irrelevant is
    the same move as not measuring it.
    RUN COUNT. One run per pair there, two here. Conflict two below IS the
    difference between two runs. At one run per pair it returns a single
    answer and looks settled.

**SO THE DECOMPOSER IS AN INSTRUMENT WITH A RESOLUTION, AND THE RESOLUTION IS
THE FINDING.** Two competent passes over one text, hours apart, returned three
and zero. Anybody selling decomposition, including this document, has to say
that out loud: the technique does not have a result, a particular application of
it does, and the parameters that decide are how finely you cut the rules, how
honestly you count the pairs, and how many times you run.

The one guard against over-cutting is checkable and is applied here: **a conflict
between two rules from the SAME pass would be a drafting error or an artefact of
how finely the rows were drawn. All conflicts below cross pass boundaries**,
which is what accretion looks like and what a splitting artefact cannot produce.

## THE ONE LINE

A prompt is a rules document, and nobody audits a rules document by reading it
from the top. **The rules that disagree are never adjacent, they are never
individually wrong, and they only disagree on the case neither of them names.**

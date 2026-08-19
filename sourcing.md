# SOURCING LOG. THE SIX INCIDENTS, AND EVERYTHING REJECTED.

Frozen 18 August 2026 before a line of the prompt was written. Six accepted,
thirteen rejected with reasons. Four verified from operator text read in full,
two from search synthesis across independent queries and marked as the weaker
tier rather than levelled to look the same.

The rejection log is the part that matters. Tuning hides in the rejections,
never in the acceptances, because the way to arrange a demonstration like this
is to reject whatever would not have produced an interesting conflict, and the
reason is written by the same hand that did the rejecting. Sources and dates
make it checkable.

Inclusion test, fixed before the first candidate was read: a specific failure
with a stated consequence, described by somebody operating the system, not a
vendor describing a hypothetical.

## ACCEPTED. SIX, FROZEN 18 AUGUST 2026.

    STRUCK 18 AUGUST 2026: this heading read "ACCEPTED. THREE OF EIGHT." It was
    written at three and never moved as the list grew to five and then to six.
    Five are listed immediately below; the sixth is under REOPENED ONCE.

### 1. Recovery email sent for an item already sold to someone else

    SOURCE   community.klaviyo.com, "Shopify + Klaviyo Abandoned Cart Flow for
             Unique Inventory, How to Prevent Emails for Sold-Out Items?",
             posted by stellacrs, marked Solved.
    RETRIEVED 18 August 2026, full thread read.

    THE INCIDENT, IN THE OPERATOR'S OWN SEQUENCE: a luxury resale store on
    Shopify and Klaviyo, one-of-a-kind stock, every SKU quantity one. Customer
    A adds an item to cart and leaves. Before the abandoned cart email sends,
    Customer B buys the same item. Customer A receives a recovery email for a
    product that no longer exists to buy.

    STATED CONSEQUENCE: a business built on unique, high-value stock sends its
    customer a broken promise, on the exact channel meant to close the sale.
    The operator confirms Shopify exposes no inventory field the flow tool can
    read, so nothing native catches it.

    RULE MATERIAL: a recovery message must be suppressed once the item is
    confirmed unavailable, and the confirmation has to reach across two
    separate systems to be checked at all.

### 2. The rule meant to protect a purchaser becomes permanent by accident

    SOURCE   community.klaviyo.com, "Exiting Abandoned Cart Flow and Profile
             Property Update", posted by lbombardier, marked Solved, an agency
             built flow the operator was left to maintain.
    RETRIEVED 18 August 2026, full thread read.

    THE INCIDENT: the flow sets a property, EXCLUDE IN FLOWS, on entry, so a
    customer mid recovery does not also get hit by an unrelated sale campaign.
    The same property is meant to clear at the end of the flow. Both the entry
    step and the clearing step sit behind one gate: CHECKOUT STARTED ZERO TIMES
    SINCE STARTING THIS FLOW. A customer who actually buys fails that gate, so
    the clearing step never fires for exactly the people it exists to protect
    correctly.

    STATED CONSEQUENCE, CONFIRMED BY A SECOND OPERATOR IN THE THREAD: "if they
    purchase, then they will never have their profile property updated." Every
    customer who converts through the flow is silently and permanently
    excluded from every future campaign gated on that property. The rule
    protecting a purchaser from one redundant email quietly cancels every
    email after it, forever, and nobody built it to do that.

    RULE MATERIAL: this is not a suppression rule failing to fire. It is two
    rules sharing one gate that only one of them should share, and the shared
    gate makes the second rule unreachable by the exact event that was
    supposed to satisfy it. Precisely the kind of contradiction the method
    exists to surface, and it was found rather than built for this purpose.

### 3. The discount that recovers the cart cannot always be redeemed

    SOURCE   community.shopify.com, "XYZ Discount code isn't available to you
             right now", opened by Emfab, unresolved in thread.
    RETRIEVED 18 August 2026, full thread read, including the platform's own
    AI generated topic summary.

    THE INCIDENT: a discount code scoped to abandoned checkout customers,
    included in the recovery email link, sometimes rejects the same customer
    it was built for at the moment of checkout, with no visible pattern.
    Support offers two candidate causes, either the session no longer
    qualifies as the abandoned checkout it was issued against, or an automatic
    discount is already applied and Shopify will not stack them. THE THREAD
    CONFIRMS THIS AS UNRESOLVED, and a second merchant reports the identical
    symptom.

    STATED CONSEQUENCE: the failure lands at the single highest value moment
    in the entire flow, the instant of conversion, and it defeats the purpose
    of the message that produced the click.

    RULE MATERIAL: THIS IS A CASE WHERE NEITHER CANDIDATE RULE CLEARLY
    rather than a weak one. Publish it as exactly that: two plausible rules,
    no way from outside to see which fires, and a customer caught between them.

### 4. A discount fires that nobody in the store wrote

    SOURCE   community.shopify.com, "Why is a non-existent discount code
             giving 10% off on abandoned carts?"
    RETRIEVED 18 August 2026, VIA SEARCH SYNTHESIS ACROSS TWO INDEPENDENT
    QUERIES, CONSISTENT BETWEEN THEM. NOT OPERATOR VERBATIM. Lower evidence
    tier than one to three, and marked as such rather than presented the same
    way. If this list needs strengthening later, this is the first candidate
    to go back and fetch in full.

    THE INCIDENT: an abandoned checkout order carries a discount code that
    does not exist anywhere in the store's Discount Codes or Automatic
    Discounts, and the same code works when tried manually on the storefront.
    Shopify support's own diagnostic path assumes it must be third party
    generated. The operator had a reviews app installed that generates codes
    in a recognisable pattern, checked, and the mystery code did not match it.

    STATED CONSEQUENCE: the store is giving away ten percent on an unknown
    population of orders through a mechanism the merchant cannot locate or
    switch off.

    RULE MATERIAL: this is the sharpest version of a gap in the whole set. Not
    a documented rule misfiring, a rule that is not written down anywhere
    firing anyway. A table built only from the documented prompt would call
    this store discount free of that rule, and the store would be wrong.

### 5. A second abandonment on a second device is read as a duplicate

    SOURCE   community.klaviyo.com, thread on Shopify generating multiple
             abandoned checkout cases against one email.
    RETRIEVED 18 August 2026, VIA SEARCH SYNTHESIS. SAME LOWER TIER AS
    CANDIDATE FOUR.

    THE INCIDENT: a customer abandons checkout on one device, then abandons
    again later on a different browser or device. Shopify records this as two
    separate abandoned checkout events. The flow sends one recovery email
    only. The synthesis names two candidate mechanisms, a profile filter
    reading "has not been in flow in the last seven days" and smart sending
    defaulting on, either of which would suppress the second, genuine
    abandonment as if it were a repeat of the first.

    STATED CONSEQUENCE: a real second cart, sometimes a different cart, never
    gets a recovery message, because the system built to stop over messaging
    cannot tell a repeat customer from a duplicate event.

    RULE MATERIAL: the same shape as candidate two, a suppression rule
    protecting against one failure mode that quietly produces a different one,
    and a third distinct failure class alongside inventory checking and
    discount handling.

## REOPENED ONCE, HONESTLY, AND THEN REFROZEN

The freeze held until two further full threads already in hand were read. That
is a different thing from reopening the search, and it is logged as such rather
than pretending the freeze never happened.

### CORROBORATION ON INCIDENT THREE, NOT A NEW SLOT

    SOURCE   community.shopify.com, "This discount code isn't available to
             you right now", posted by CJP, March 2020 through June 2024,
             eight distinct users, 1.8k views.
    RETRIEVED 18 August 2026, full thread read.

    SAME FAILURE CLASS AS THREE, A DIFFERENT STORE, A LONGER RUN. Multiple
    merchants over four years report the identical symptom Emfab reported in
    candidate three, and Shopify's own Social Care staff response offers only
    generic troubleshooting with no resolution reached in thread. One case
    names a concrete instance: a discount code visibly applied against a $110
    cart, then rejected at the payment step rather than at entry.

    THIS DOES NOT BECOME A SIXTH INCIDENT. It strengthens candidate three's
    own claim instead: the failure is not a one store fluke, it is
    cross-merchant and multi-year, and the payment-stage variant is now part
    of candidate three's rule material rather than a separate rule.

### SIXTH INCIDENT, ACCEPTED

    SOURCE   community.shopify.com, "Abandoned cart discount code stopped
             working", posted by PBOutfitters, October 2022. Zero replies,
             unresolved.
    RETRIEVED 18 August 2026, full thread read.

    THE INCIDENT, VERBATIM FROM THE MERCHANT'S POST: "Abandoned cart discount code
    was automatically being applied to carts that were recovered. After
    August, 2022, this is not being applied anymore. No changes were made to
    the Abandoned Cart notification template."

    STATED CONSEQUENCE: an automation that worked correctly simply stopped,
    with nothing changed on the merchant's own side to explain it.

    RULE MATERIAL, AND WHY IT IS A GENUINELY NEW CLASS: every incident so far
    is a rule that was missing, wrong, or in conflict with another rule. This
    one is different in kind. The rule was correct and it worked. Something
    outside the merchant's own configuration changed, and the rule kept
    firing exactly as written while the platform it depended on stopped
    honouring it. A table built only from what the prompt says will never
    catch this class, because nothing in the prompt is wrong.

## FROZEN AGAIN, 18 AUGUST 2026

SIX INCIDENTS. FOUR fully verified from operator text, one, two, three and
six. TWO from search synthesis, marked as the weaker tier, four and five.
This list did not change again. Pass seven was written against incident six.
Passes one through six stand exactly as they were, unedited.

## SEEN BUT NOT YET READ. VISIBLE IN THE SAME THREAD'S RELATED PANEL.

Titles only, surfaced in the related panel of candidate three's thread.
NOT ACCEPTED, because a title is not a verified incident under the test above.
Two are strong enough to be worth reading before the list closes:

    "Is my returning customer discount code malfunctioning? ... it showed my
    returning customer discount code... with $0 off next..." Sounds like a
    live incident: a loyalty code rendering at zero value. Needs the full post.

    "Why is a non-existent discount code giving 10% off on abandoned carts?"
    Sounds like a live incident and a more serious one: a code that was never
    created in the store is being honoured. Needs the full post.

    "Abandoned cart discount code stopped working [after a platform update, no
    template changes made]." Zero replies, unresolved. If it reads as
    described, this is a fourth instance of the same failure class as
    candidate three, which would be worth knowing before deciding whether
    candidate three's class is one incident or a pattern.

    "Discount Code Not Working / Not Available for a Customer." One reply,
    thin. Lower priority.

## REJECTED AT THE TITLE SCREEN, BEFORE ANY FETCH, WITH REASON

Logged because the rejection log is what proves the filter was not tuned, per

    "Offer a discount on additional product for an abandoned cart customer"
    community.shopify.com/t/37900. REJECTED: a feature request, not an
    incident.
    "How can I optimize on abandoned carts?" REJECTED: a generic question.
    "Abandoned Carts, best app to send offers?" REJECTED: a generic question.
    "Automated discount calculation by clicking a link" REJECTED: a how-to
    question about building something, not a report of it failing.
    "Multiple Discount Codes in Abandoned Cart Email" community.shopify.com/t/
    254674, posted by WAWbox, Sep 2023. CONFIRMED REJECTED, full text read 18
    August 2026. It is a configuration request, how to make two codes stack
    automatically, unresolved with zero replies. No failure and no stated
    consequence, a capability gap in the documentation rather than an
    incident. The provisional reject stands as final.

    "How do I apply discounts to specific abandoned cart emails?", "Can
    automated calculated discounts be added to abandoned cart emails?", and
    the two duplicate "NEW ABANDONED AUTOMATION EMAILS" threads, all surfaced
    in the same related panel. REJECTED BY TITLE, same class as WAWbox,
    configuration questions rather than incidents.
    retaildive.com sponsored holiday campaign article. REJECTED: vendor
    content, explicitly excluded by the test.
    "NEW ABANDONED AUTOMATION EMAILS can AUTOMATICALLY APPLY DISCOUNT CODES?"
    REJECTED: a how-to question.
    Shopify app store listing for a recovery app. REJECTED: marketing copy.
    HubSpot Community "Cart Abandon & Browse with Shopify connection", marked
    Solved. REJECTED PROVISIONALLY: title reads as setup help rather than an
    incident.
    Klaviyo Help Center "How to create an abandoned Added to Cart flow for
    Shopify". REJECTED: vendor documentation, explicitly excluded by the test.
    community.shopify.com/t/588629 "flow-cart". REJECTED: title too thin to
    evaluate and not pursued.
    community.shopify.com/t/255603 "how can I set up a second abandoned cart
    email". REJECTED: how-to question.


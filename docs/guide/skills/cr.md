# cr (change request)

**Skill folder:** `casso-skills-cr`

## Purpose

Write down a requested change exactly as it was asked: what happens now, why it matters, and the fix that was asked for. It drafts acceptance checks and lists the open questions. It does not invent scope or choose between readings of an unclear request.

## When to use

- At the start of any change: a feature, a bug fix, a behaviour change.
- When a request arrives as a chat message, an email or a ticket and needs to be written down properly before work starts.

## What you give it

- The request, in the requester's own words.
- Any background: links, screenshots, error messages.
- Where to save the change request.

## What it produces

A change request document with:

- **What happens**: the current behaviour.
- **Why it matters**: the cost of leaving it.
- **The fix**: what was asked for, not an alternative the agent prefers.
- **Draft acceptance**: observable checks that would show the change is done.
- **Evidence**: pointers to the material behind the request.
- **Open questions**: every unclear point, asked one at a time.

For larger changes it also adds which existing requirements the change would alter, how to roll it back, who needs to approve it, and who needs to be told.

## Example

> Use casso-skills-cr. Request from support: "Let customers type a discount code at checkout. Codes should expire." Save to `docs/changes/discount-codes-cr.md`.

The agent writes the request and then asks: "Is a discount a percentage, a fixed amount, or either?" It waits for the answer instead of picking one. The full example is in [Dispatching one step by hand](../../../README.md#8-dispatching-one-step-by-hand).

## Related skills

- [impact](impact.md): the usual next step, to see what the change touches.
- [spec](spec.md): turn the change request into numbered requirements.

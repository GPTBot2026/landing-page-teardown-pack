# GitHub Landing Page Teardown Ops Pack

This file is the reusable operating layer for the USD 20 GitHub-native teardown offer. Use it to move from first issue to paid delivery with minimal custom drafting.

## 1. Scope Screen

Accept if all are true:

- The request is for one public landing page.
- The page is accessible without account login.
- The buyer wants copy, structure, CTA, clarity, or trust feedback.
- The buyer understands the work is AI-assisted and text-only.

Decline or redirect if any are true:

- They want analytics setup, design implementation, or coding changes.
- They want review of multiple pages for the base price.
- The page is private or blocked behind login.
- The request depends on credentials, platform access, or outcome guarantees.

## 2. First Public Issue Reply

Use when a new issue is in scope.

```md
Thanks for the request. This fits the teardown scope.

What happens next:

1. I will review the page and post a short free preview in this issue.
2. If the preview looks useful, the full teardown is USD 20 paid upfront by PayPal.
3. Full delivery includes the ranked teardown, three headline options, one CTA rewrite, and the first fix to ship.

If anything important is missing from your issue, add it in a reply before I draft the preview.
```

## 3. Short Free Preview Template

Post this in the GitHub issue before requesting payment.

```md
Preview for `[page or product name]`

Initial read:
- The main problem is `[headline / offer / CTA / trust / structure]`.
- The page currently makes visitors work too hard to understand `[core value or next step]`.
- The fastest improvement is likely `[single highest-priority fix]`.

If you want the full teardown, the price is USD 20 paid upfront by PayPal.

Full delivery includes:
- ranked conversion problems
- three replacement headlines
- one CTA section rewrite
- a quick-win fix list
```

## 4. Payment Request Template

Use after the preview if the prospect wants the full pack.

```md
Proceeding with the full teardown is USD 20, paid upfront by PayPal.

After payment is confirmed, delivery target is within 24 hours.

To continue, send payment to: `[PAYPAL ADDRESS OR LINK]`

Once paid, reply here with:
- confirmation that payment was sent
- the exact page URL to review
- any one constraint you want weighted heavily
```

## 5. Payment Confirmation Reply

```md
Payment confirmed.

I’m preparing the full teardown now. Delivery target: within 24 hours in Markdown format.
```

## 6. Final Delivery Template

```md
# Landing Page Teardown: `[page or product name]`

## Fast Diagnosis

`[2-4 sentences on what is unclear, weak, or misordered]`

## Priority Fixes

1. `[highest-priority fix]`
2. `[second fix]`
3. `[third fix]`
4. `[fourth fix]`

## What Is Weak Right Now

### Headline

`[analysis]`

### Offer Clarity

`[analysis]`

### Trust

`[analysis]`

### CTA

`[analysis]`

## Three Replacement Headlines

1. `[headline option]`
2. `[headline option]`
3. `[headline option]`

## CTA Section Rewrite

`[replacement CTA section]`

## First Change To Ship

`[single first action with reason]`
```

Primary internal template: `offers/github_landing_page_teardown_delivery_template.md`
Payment-stage template set: `offers/github_landing_page_teardown_payment_handoff.md`

## 7. Out-Of-Scope Decline Template

```md
Thanks for the request. I’m declining this one because it falls outside the current teardown scope.

Current scope is one public landing page, text-only, with no account access or implementation work.

If you want, open a new request for a single public page and I can review fit from there.
```

## 8. Internal Fulfillment Notes

- Keep the free preview short enough that it proves value without delivering the full pack.
- Do not claim revenue lifts, design credentials, or human identity.
- Prefer concrete rewrite suggestions over broad marketing language.
- For inbound GitHub issues, run `scripts/draft_landing_page_teardown_issue_response.sh <issue_body_file> [paypal_address_or_link]` to classify fit, request missing fields when needed, and draft the first reply, preview, and payment request in one step.
- Before relying on the issue workflow after changes, run `scripts/verify_landing_page_teardown_issue_workflow.sh [paypal_address_or_link]` to regression-check the in-scope, missing-info, and out-of-scope paths against fixture issue bodies.
- Save strong anonymous before/after examples for future proof assets once real work exists.
- For faster first-pass analysis on public pages, run `scripts/generate_landing_page_teardown_context.sh <url>` and use the generated Markdown context pack with `offers/github_landing_page_teardown_preview_bank.md`.
- For a faster issue-ready first draft, run `scripts/generate_landing_page_teardown_preview.sh <url> "[product name]"` and tighten the output against the live page before posting.
- After payment is confirmed, run `scripts/generate_landing_page_teardown_delivery.sh <issue_body_file> [delivery_date] [output_file]` to turn the completed issue intake into a full delivery draft that already matches the paid template structure.
- For queued outreach targets, run `scripts/prepare_landing_page_teardown_targeted_previews.sh` to refresh the batch preview file in `offers/github_landing_page_teardown_targeted_previews.md` before sending first-contact messages.
- Run `scripts/render_landing_page_teardown_first_contact_pack.sh` after changing target angles, priorities, or routes so `offers/github_landing_page_teardown_first_contact_pack.md` stays synchronized with the active pipeline instead of drifting as a hand-maintained file.
- Run `scripts/prepare_landing_page_teardown_contact_routes.sh` to refresh `offers/github_landing_page_teardown_contact_routes.md` and the route metadata in `state/outreach_pipeline.json` so the first live send uses a verified public surface instead of manual route hunting.
- Run `scripts/reprioritize_landing_page_teardown_targets.sh` after refreshing routes or promoting new targets so the first live sends favor the cleanest verified public routes instead of stale discovery order.
- After the repo is live, run `scripts/go_live_landing_page_teardown.sh <repo_url> <pages_url>` to verify the public repo and Pages surface, generate the live outreach bundle, and update `state/state.json` for the post-publication stage in one guarded step.
- If the operator returns a completed `PUBLICATION_RECEIPT.md` block, save it and run `scripts/process_landing_page_teardown_publication_receipt.sh <receipt_file>` to enforce the receipt checks, extract the live URLs, and hand them to the same go-live activation path without manual parsing.
- If publication is already verified and only the live outreach bundle needs a refresh, run `scripts/activate_landing_page_teardown_outreach.sh <repo_url> <pages_url>` directly.
- Go-live activation now also builds `dist/live/landing-page-teardown-assets/first-send-packets/`, a numbered set of route-specific first-send files for the top live targets, so the first outreach can be sent from a concrete packet instead of re-running selection manually.
- Go-live activation now also builds `dist/live/landing-page-teardown-assets/follow-up-packets/no-reply/`, a numbered set of route-specific `no_reply` follow-up files for the same top live targets, so the second touch after silence does not require one-by-one command runs.
- After each outbound send, follow-up, or reply, run `scripts/record_landing_page_teardown_outreach.sh <target_name> <status> [options]` so `state/outreach_pipeline.json` stays truthful without hand-editing.
- `scripts/generate_landing_page_teardown_next_send.sh` now skips targets without a verified preferred contact route, prints the exact preferred destination URL plus route notes, resolves live Pages, repo, and issue URLs directly into the selected message draft when `state/outreach_pipeline.json` contains `live_urls`, and emits a route-specific send packet so contact forms, DMs, and GitHub Discussions posts no longer need manual adaptation before the first live send.
- `scripts/generate_landing_page_teardown_follow_up.sh --target <name> --scenario <scenario>` now turns the static follow-up pack into a route-specific follow-up packet for the verified preferred destination, so second-touch outreach does not fall back to manual adaptation after the first send.
- Use `offers/github_landing_page_teardown_delivery_template.md` for the paid delivery so section order and disclosures stay consistent.
- Use `offers/github_landing_page_teardown_payment_handoff.md` for payment-stage replies so the close language stays consistent once a preview lands.
- For payment-stage objections or close replies, reuse `offers/github_landing_page_teardown_buyer_replies.md` instead of drafting from scratch.

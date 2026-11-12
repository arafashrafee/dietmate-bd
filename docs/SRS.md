# DietMate BD — Software Requirements Specification

Version: 1.0 | Phase: 0.2 — Complete MVP SRS
Source: existing SRS v0.1 and approved PRD Sections 6, 10, 11, and 14 only.
Status: requirements baseline; implementation and public release remain subject to the explicit decisions and evidence gates below. No runtime validation is claimed.

## 1. Purpose and scope

Define testable requirements for one complete offline nutrition experience.
The MVP serves one local profile on Android and iOS in Bangla and English.
All ten approved core features must work from fresh first launch in airplane mode.
Keto, Low-Carb, and Balanced are diet patterns; Calorie Deficit is a separate energy goal.
Screening constrains automated restrictive plans while preserving basic food logging.
This specification does not define a diagnosis, treatment, or medical clearance.

Excluded from MVP acceptance: barcode scanning, pantry/inventory, family profiles,
sync, weekly/monthly automated planning, AI features, and cloud services.
Recipes/substitutions, Ramadan planning, expanded budgeting/activity, price history,
voice, wearables, professional services, subscriptions, and encrypted local
backup/export/restore retain their Section 6 release classifications.

## 2. MVP functional requirements

Each FR identifier is unique; all requirements below are mandatory for MVP.

| ID | Requirement |
| --- | --- |
| FR-001 | Create and edit exactly one device-local profile without login. |
| FR-002 | Search bundled, verified Bangladeshi nutrition data without downloads. |
| FR-003 | Manually log food and portions and calculate daily calories and macros from verified data. |
| FR-004 | Create an editable daily plan using Keto, Low-Carb, or Balanced templates. |
| FR-005 | Treat Calorie Deficit as an optional energy goal applied separately to a diet pattern, subject to screening. |
| FR-006 | Add, replace, and remove meals and adjust portions in a daily plan. |
| FR-007 | Generate/regenerate groceries from the daily plan, combining compatible ingredient quantities and reflecting edits. |
| FR-008 | Calculate offline BDT grocery estimates from bundled unit prices; show price dates and estimate limitations. |
| FR-009 | Support manual price search and partial totals when prices are unknown; identify unpriced items. |
| FR-010 | Record weight and display weight history and trends offline. |
| FR-011 | Configure local meal, water, and activity reminders using device scheduling when permitted. |
| FR-012 | Screen locally during onboarding and before applying a diet pattern or energy goal. |
| FR-013 | When screening triggers, block automated restrictive meal plans, preserve basic logging, and display offline professional-advice guidance. |
| FR-014 | Present screening without diagnosis or medical-clearance claims. |
| FR-015 | Persist profile, screening responses, logs, plans, groceries, weight history, and reminder settings across restarts. |
| FR-016 | Provide core flows and safety/error guidance in Bangla and English. |
| FR-017 | Handle notification permission denial gracefully without blocking other core features. |
| FR-018 | Capture age in years, height in cm, weight in kg, activity level, goals, food preferences, dietary restrictions, and allergies; permit later edits. Reject missing required fields, nonfinite/nonpositive measurements, and unknown enumerations without replacing saved values; professionally governed age eligibility remains separate. |
| FR-019 | Persist one selected pattern and optional energy goal with preferences/restrictions. Reject unsupported patterns or combinations without changing the active configuration; profile/screening changes invalidate restrictive-plan eligibility until reassessed. |
| FR-020 | Accept grams or named servings only where a verified serving-to-gram mapping exists; scale each available nutrient from the record basis using full precision internally and round displayed values to two decimals, half-up. |
| FR-021 | Associate each food/log entry with food ID, source, source version, preparation state, nutrient basis, and verification status; preserve the calculation snapshot so dataset updates do not silently alter historical totals. |
| FR-022 | Distinguish raw and cooked records in search and logs; never substitute one for the other or infer cooking yield without a verified conversion. |
| FR-023 | Use total carbohydrate as the default macro measure. Show net carbohydrate only when verified compatible total-carbohydrate and fiber values exist, as total minus fiber; label the convention and exclude sugar-alcohol deductions unless a reviewed rule is approved. Inconsistent or missing operands yield unavailable net values. |
| FR-024 | Represent absent nutrient values as unknown, never zero; show known daily subtotals with incompleteness indicators per nutrient. Reject unverified records for numeric calculation and retain access to other verified foods. |
| FR-025 | Allow editing and deleting a saved food entry with explicit deletion confirmation; recalculate the affected day summary from remaining snapshots and persist atomically. |
| FR-026 | Validate all template meals and user meal edits against declared restrictions/allergies before saving or applying. Block known conflicts; unresolved ingredient/allergen metadata prevents automatic selection and displays the limitation, without claiming allergen-free safety. |
| FR-027 | Show calculated daily-plan calories/macros from verified portion data; persist meals, portions, configuration, and screening/template versions. Reload the same saved plan; if no eligible template exists, retain the previous plan as unapplied where eligibility changed, explain the failure, and offer basic logging without inventing a substitute restrictive plan. |
| FR-028 | Aggregate only matching ingredient IDs and compatible normalized units (g/kg, ml/l, or identical count units); require explicit verified density or item mappings for cross-dimension conversions. Show unresolved items separately instead of dropping them. |
| FR-029 | Allow local grocery quantity edits and purchased-status changes. On regeneration preview additions/removals/quantity changes, retain overrides/status for surviving ingredient IDs, flag overrides affected by plan changes, and require an explicit keep/reset decision before replacement; cancel preserves the entire old list. |
| FR-030 | Store local item prices with ingredient, currency BDT, unit, amount, date, and origin (bundled or user). Permit manual local price search/entry; reject negative/nonfinite prices and unsupported units, allow explicit zero, and retain dated prior values on validation failure. |
| FR-031 | Compute each known cost as normalized quantity multiplied by unit price, round line cost half-up to two BDT decimals, and sum displayed line costs. Include purchased items in the full-plan estimate; identify unpriced/unconvertible items and show a labeled partial subtotal or no-known-prices state. |
| FR-032 | Record weight with editable timestamp, retain history chronologically, and allow confirmed edit/delete. Store canonical kg; support kg/lb display and input using 1 lb = 0.45359237 kg, with two-decimal display and full-precision storage. Reject nonpositive/nonfinite values or invalid timestamps without losing prior records. |
| FR-033 | Plot recorded weight by timestamp with an accessible textual history; one point shows a point without an inferred trend, zero points shows an empty state, and two or more show chronological recorded points without predictions or promised outcomes. |
| FR-034 | Allow creation, editing, disabling, and rescheduling of meal, water, and activity reminders locally. Persist local-wall-time schedule and timezone, cancel superseded pending requests, and reconcile enabled schedules after restart/timezone changes using platform APIs; show permission/scheduling failures without claiming delivery. |
| FR-035 | Validate writes and foreign-key relationships; commit each logically related log/summary, plan/grocery replacement, or reminder-setting mutation as an atomic SQLite transaction. Interrupted writes expose either the prior committed state or the complete new state, never a partial success. |
| FR-036 | Version the schema and apply validated transactional migrations before normal writes; reject unsupported schema versions. On corruption/migration failure stop unsafe writes, preserve existing files, and offer retry/help; never silently reset or promise automatic recovery. Insufficient storage reports failure without reporting an uncommitted save as success. |
| FR-037 | Collect only user-provided data needed for stated functions. Provide local purpose-specific consent controls; optional telemetry/sharing defaults off and can be declined/withdrawn without losing core functions. Do not transmit data before consent or introduce an MVP online service. |
| FR-038 | Encrypt the local database at rest with the PRD AES-256 target; use platform-protected local keys and verify key creation, access, lifecycle, and integration before release. Exclude sensitive values/keys from logs and document unlocked/compromised-device limitations; this is not end-to-end cloud encryption. |
| FR-039 | Provide confirmed local deletion of profile-associated personal records and reminder schedules without login/internet; return to first-launch state only after successful deletion. Explain that deletion does not erase separately exported files or guarantee forensic erasure. |
| FR-040 | Ship only qualified-professional-reviewed template parameters, macro conventions, screening rules, age eligibility, and guidance. Record reviewer qualifications, reviewed versions, risk assessment, and approval; material changes require renewed review. Pending/unknown age or medical eligibility withholds restrictive automation and preserves basic logging. |
| FR-041 | Bundle only nutrition data with verified suitability, licensing/redistribution rights, source/version, units, and validation status; disclose composition uncertainty and review updates before distribution. AI output never supplies authoritative nutrient values or bypasses screening. |

Module allocation: FR-018 profile; FR-019 diet; FR-020–FR-025 nutrition; FR-026–FR-027 planner; FR-028–FR-031 grocery; FR-032–FR-033 weight; FR-034 notifications; FR-035–FR-036 persistence; FR-037–FR-039 privacy; FR-040–FR-041 safety/provenance. These refine the ten MVP capabilities, not additional roadmap products.

## 3. Offline-first system requirements

| ID | Requirement |
| --- | --- |
| SYS-001 | Use SQLite for local persistence and pure TypeScript for nutrition calculations. |
| SYS-002 | Bundle nutrition data, daily templates, local unit prices, and offline safety guidance needed for core flows. |
| SYS-003 | Require no account, login, internet, server, download, subscription, or telemetry for core use. |
| SYS-004 | Require no paid AI dependency; manual logging and core calculations must function without AI. |
| SYS-005 | Run every core feature on Android and iOS from fresh airplane-mode launch through restart. |
| SYS-006 | Keep local privacy and permission controls available offline; any future online service requires separate opt-in. |
| SYS-007 | Audit nutrition sources, units, and verification status and document actual dataset count/coverage before release. |
| SYS-008 | Measure core response times on documented release-build devices against a provisional under-2-second benchmark. |
| SYS-009 | Measure installed size and peak RAM against provisional below-200MB and below-300MB benchmarks. |
| SYS-010 | Measure crash rate against provisional below-0.1% and satisfaction against above-4/5 targets; document population, period where applicable, and method. |

Performance, size, RAM, and crash benchmarks are provisional and subject to device
validation and documented revision; they are not guaranteed results or hard release gates.
All three PRD acceptance milestones remain required without a fixed calendar deadline.

## 4. WF-001 — First-launch onboarding and safety screening

References: FR-001, FR-012–FR-017; SYS-002–SYS-006.
Precondition: fresh installation; airplane mode; no profile or downloaded content.

1. Open the app and access Bangla or English onboarding.
2. Enter the local profile information; save it on the device.
3. Complete local high-risk screening during onboarding.
4. Evaluate screening locally before applying a selected pattern or energy goal.
5. If screening triggers, block automated restrictive plans and show professional-advice guidance.
6. Keep basic food logging accessible regardless of a triggered screening result.
7. Configure optional reminders; request device permission where needed.
8. Persist profile, screening responses, and reminder settings for subsequent launches.

System behavior: validate and persist local inputs, evaluate bundled screening, and enforce permission and safety branches.
Expected result: one saved profile, stored screening state, accessible basic logging, and optional reminders.

Acceptance criteria:
- AC-A01: On each platform, fresh airplane-mode launch completes profile creation/editing in both languages without login or downloads.
- AC-A02: An approved high-risk fixture triggers the block and offline guidance; basic logging remains usable.
- AC-A03: Applying any pattern or energy goal invokes screening before application; a restricted result cannot activate an automated restrictive plan.
- AC-A04: Screening screens and results contain no diagnosis or medical-clearance claim.
- AC-A05: Denying notification permission leaves onboarding, logging, and other core functions usable.
- AC-A06: Restart in airplane mode restores saved profile, screening responses, and reminder settings.

Error/offline behavior:
- Missing or invalid required inputs receive localized correction guidance without falsely recording completion.
- An incomplete or failed screen cannot be treated as clearance for restrictive automation; basic logging remains available.
- A failed local save is reported and must not be represented as successfully persisted.
- Network unavailability causes no interruption to this workflow.

## 5. WF-002 — Manual food logging and nutrition calculation

References: FR-002, FR-003, FR-013, FR-015, FR-016; SYS-001–SYS-007.
Precondition: local profile available; verified nutrition dataset bundled.

1. Open food search and find a food in the bundled dataset.
2. Select the verified food record and enter its portion using supported units.
3. Validate the amount and its compatibility with the record's nutrition basis.
4. Calculate calories and macros locally by scaling verified values to the portion.
5. Save the entry to the selected day's log and update daily totals.
6. Reopen the log after restart to review persisted entries and totals.

System behavior: validate portions, calculate from versioned verified records, and commit entry/summary atomically.
Expected result: saved food entries and a daily summary with unknown-value indicators where applicable.

Acceptance criteria:
- AC-B01: Bundled search and logging work in airplane mode on both platforms and in both languages.
- AC-B02: A verified reference fixture and supported portion produce matching calorie/macro results under the agreed rounding rule.
- AC-B03: Multiple reference entries produce daily totals matching the sum of their calculated contributions.
- AC-B04: A triggered high-risk screen does not prevent searching, logging, or viewing totals.
- AC-B05: Restart preserves entries and reproduces the same daily totals without internet.
- AC-B06: Search timing is recorded on documented release-build devices against the provisional benchmark.

Error/offline behavior:
- No search match shows a localized empty result and permits another manual search.
- Invalid portions or unsupported conversions are rejected with correction guidance.
- Missing or unverified nutrition values are not fabricated or used as verified calculation inputs.
- Calculation/save failures are visible; an unsaved entry must not appear successfully persisted.
- No-match or data failures require no AI, cloud lookup, or paid fallback.

## 6. WF-003 — Daily plan to groceries and BDT cost

References: FR-004–FR-009, FR-012–FR-016; SYS-001–SYS-006.
Precondition: local profile, screening, bundled templates, ingredient mappings, and prices available.

1. Select Keto, Low-Carb, or Balanced and optionally select the separate Calorie Deficit goal.
2. Run local screening before applying the pattern or goal; enforce restrictive-plan blocking.
3. Create a daily plan and add, replace, or remove meals and adjust portions.
4. Generate groceries from the current plan's ingredient quantities.
5. Combine quantities for the same ingredient where units are compatible.
6. Apply bundled unit prices and calculate a BDT estimate locally.
7. Display price dates, estimate limitations, and unpriced items alongside any partial total.
8. After plan edits, regenerate groceries and costs to reflect the updated plan; persist results.

System behavior: validate safety/restrictions, aggregate compatible ingredients, and calculate dated BDT costs; regeneration uses FR-029 edit preservation.
Expected result: saved eligible daily plan and groceries with complete or explicitly partial estimates.

Acceptance criteria:
- AC-C01: Both platforms support all three patterns and a separate energy-goal selection offline, with screening enforced before application.
- AC-C02: A reference plan containing repeated ingredients yields the expected combined quantities for compatible units.
- AC-C03: Adding, replacing, removing meals, or changing portions produces expected groceries after regeneration.
- AC-C04: Known quantities/prices yield the expected BDT total under agreed conversion and rounding rules, with dates and limitations visible.
- AC-C05: An unknown price yields an identified unpriced item and labeled partial total; manual price search remains available offline.
- AC-C06: Triggered screening blocks restrictive automation and leaves basic logging available.
- AC-C07: Restart restores the saved daily plan and generated grocery list without connectivity.

Error/offline behavior:
- Missing ingredient mappings or incompatible units are identified instead of silently producing a complete list or estimate.
- Unknown prices are never silently treated as zero; partial estimates disclose their incompleteness.
- Bundled prices remain usable without live updates; dates and limitations remain visible.
- Generation/save failures are reported; outdated results must not be presented as reflecting unsaved or unprocessed edits.

## 7. Non-functional requirements

The following verification methods define acceptance, not measured results. P0 means safety/data/core blocker; P1 means required MVP quality check. Provisional benchmark misses require recorded investigation and disposition, not an invented performance pass.

| ID | Requirement and verification |
| --- | --- |
| NFR-001 | Offline reliability: execute every MVP functional test offline on Android and iOS, including fresh launch/restart; capture network activity and confirm no required network request or login prompt. |
| NFR-002 | Performance: measure launch, food search, log save, plan edit, grocery generation, and history load in release builds with documented device/OS/dataset and sample timings; compare to provisional under-2-second core-interaction target and document revisions. |
| NFR-003 | Resource efficiency: measure installed size and peak RAM across the core-flow suite against provisional below-200MB/below-300MB targets; record local database growth for a documented workload and explain revisions. No measured result is assumed. |
| NFR-004 | Compatibility: run the full acceptance suite on each supported Android/iOS version/device class; publish minimum OS versions and device matrix before release. Unsupported devices must not be claimed as tested. |
| NFR-005 | Localization: review every core, safety, validation, permission, and empty-state string in Bangla and English; no untranslated keys; Bangla uses left-to-right layout; switching language preserves saved values and units. |
| NFR-006 | Accessibility: complete all core flows with VoiceOver/TalkBack; controls expose names, roles, values, errors, logical focus order, and non-color status cues. At 200% text size no required action is clipped; charts provide equivalent readable history. |
| NFR-007 | Privacy: inspect default consent state and captured traffic/logs; optional sharing is off, withdrawal prevents subsequent optional collection/transmission, and offline features remain available. |
| NFR-008 | Protection: inspect copied database bytes and platform key handling on both platforms; personal values are not readable as plaintext in database files/logs. Verify missing/unavailable keys produce an error without destructive reset; document threat model and AES-256 integration evidence. |
| NFR-009 | Integrity: inject interruption/storage errors into each transactional mutation and supported schema migration; compare records/references to pre/post snapshots, require atomic results, and retain existing files on migration failure. |
| NFR-010 | Failure resilience: run the Section 9 fault cases; no uncaught crash or false save-success indication in those tests. Measure release-test crash rate against provisional below-0.1%, documenting denominator, population, period, and method; no universal crash-free guarantee. |
| NFR-011 | Maintainability: architecture review confirms independent pure TypeScript nutrition/cost rules, persistence adapters, safety rules, notifications, and localized UI; rule tests run without network, UI, or a live database. |
| NFR-012 | Testability: deterministic clock, food/price fixtures, screening-rule versions, and storage/notification failure injection are available in the test harness; each FR maps to an acceptance test below. |
| NFR-013 | Notification efficiency: use OS local scheduling, not network polling or a continuously running app timer; instrument schedule/edit/disable/restart and confirm no duplicate active request per reminder occurrence and no app-owned repeating background poll. OS delivery timing is not guaranteed. |
| NFR-014 | Online expansion: interface review confirms future cloud/AI/price adapters are optional and isolated; removing or failing adapters leaves the offline suite passing. Future online transmission requires consent and TLS 1.3 certificate validation; invalid certificates must be rejected before that feature ships. |
| NFR-015 | Release evidence: record all three PRD milestone outcomes plus satisfaction testing against above-4/5 with population/method, benchmark disposition, dataset audit, and professional review approvals. Missing evidence is not a verified result. |

## 8. Additional workflows

### WF-004 — Weight tracking and progress history
- Preconditions: local profile; zero or more weight entries; airplane mode allowed.
- User actions: enter weight/unit/time, save, view chart/history, edit an entry, confirm deletion.
- System behavior: validate, normalize to kg, commit mutation, reorder history and redraw recorded points/text.
- Expected result: history and chart reflect only saved entries; no inferred result for an empty/single-point history.
- Error conditions: invalid time/nonpositive/nonfinite weight shows field error; storage failure preserves previous committed history.
- Offline behavior: input, unit conversion, charts, edit/delete and reload require no connection.
- Acceptance criteria: AT-032 and AT-033 verify conversion, ordering, boundaries, edit/delete, and empty states; AT-015 verifies restart.

### WF-005 — Offline notification management
- Preconditions: local profile; platform notification capability; permission may be granted or denied.
- User actions: create each reminder type, allow/deny permission, edit time, disable, then re-enable.
- System behavior: save preferences, request permission when needed, schedule/cancel through OS, reconcile after restart or timezone change.
- Expected result: enabled permitted reminders have one current pending occurrence; disabled/superseded requests are canceled.
- Error conditions: permission denial/revocation or scheduling failure displays status/settings guidance; do not claim delivery.
- Offline behavior: no network scheduler or login; device power/OS restrictions can delay or suppress delivery.
- Acceptance criteria: AT-011, AT-017, AT-034 verify all types, denial, edit/disable/re-enable, reconciliation, and pending-request uniqueness.

### WF-006 — Application restart and data persistence
- Preconditions: saved examples of all FR-015 entities; schema version known.
- User actions: terminate and reopen app; retry after a reported failure if appropriate.
- System behavior: open protected SQLite, check schema/integrity, migrate transactionally if supported, reload committed state, reconcile reminders.
- Expected result: committed state reappears without login or download; interrupted mutations are entirely old or entirely new.
- Error conditions: corruption, unavailable keys, failed/unsupported migration, or storage exhaustion prevents unsafe writes and shows retry/help without silently resetting data.
- Offline behavior: restart and supported migrations use installed resources; no server recovery required or promised.
- Acceptance criteria: AT-015, AT-035, AT-036, and AT-038 verify restart, interruption, migration, storage, and key failures.

### WF-007 — High-risk user safety scenario
- Preconditions: bundled professionally approved rule fixtures; age/medical eligibility may be high-risk or unresolved.
- User actions: submit screening, request a restrictive automated plan or deficit goal, then log a verified food manually.
- System behavior: evaluate locally before application; block restrictive automation for triggered, incomplete, or unvalidated eligibility; invalidate eligibility after relevant profile changes.
- Expected result: offline professional-advice guidance and usable basic logging; no diagnosis, clearance, pediatric prescription, or promised outcome.
- Error conditions: missing/unapproved rules cannot authorize restrictive automation; previous plans remain unapplied when eligibility changes.
- Offline behavior: no consultation service or emergency-contact integration required to display guidance or enforce the block.
- Acceptance criteria: AT-012–AT-014, AT-019, AT-040 verify high-risk/unresolved branches and continued logging. This extends WF-001 without repeating onboarding.

### WF-008 — Grocery calculation with missing prices
- Preconditions: saved daily plan with compatible duplicate ingredients and at least one unpriced ingredient.
- User actions: generate list, inspect partial estimate, search/enter local price, edit quantity/status, change plan and regenerate.
- System behavior: aggregate compatible units; disclose missing prices; recalculate known line costs; preview regeneration and preserve or explicitly reset edits.
- Expected result: dated full or partial BDT total with no silent zero assumption and no discarded override on cancel.
- Error conditions: invalid price/incompatible units are identified; save failure retains previous committed list; all prices missing shows no-known-prices state.
- Offline behavior: uses bundled/user prices only; no live price request needed.
- Acceptance criteria: AT-009 and AT-028–AT-031 verify missing/all-missing prices, duplicate aggregation, manual entry, and edit preservation. This extends WF-003's normal path.

## 9. Edge cases and failure handling

| Condition | Required observable behavior | Verification |
| --- | --- | --- |
| Fresh install without internet | All ten core capabilities usable with bundled resources; no account/download gate. | AT-001, AT-042 |
| Empty/incomplete food bundle | Show empty/unavailable-data state, never invent nutrients; other stored data accessible. An empty bundle fails the release dataset gate, even if handled gracefully. | AT-002, AT-041 |
| Unknown nutrient | Unknown label and per-nutrient partial subtotal; never implicit zero. | AT-024 |
| Invalid serving quantity | Reject zero, negative, nonfinite, or unsupported serving conversion; keep previous log unchanged. | AT-020 |
| Missing prices | Show unpriced items and partial subtotal; all missing has no complete total. | AT-009, AT-031 |
| Duplicate ingredients | Combine identical IDs/compatible units; keep incompatible units separate with explanation. | AT-007, AT-028 |
| Permission denied | Store preferences/status but no false scheduled/delivered claim; core flows remain usable. | AT-017 |
| Terminated database write | Transaction leaves old or complete new state on reopen; no partial linked records. | AT-035 |
| Existing data on restart | Reload every FR-015 entity from committed local state. | AT-015 |
| Corruption/failed migration | Stop unsafe writes; retain files and show retry/help; validated backup recovery is future scope, not guaranteed MVP recovery. | AT-036 |
| Unsupported diet combination | Reject unsupported configuration without changing active one; offer valid selection/basic logging. | AT-019 |
| High-risk/unknown eligibility | Block restrictive automation and show offline professional guidance; manual logging remains. | AT-013, AT-040 |
| Storage exhaustion | Explicit save failure; no false success, prior committed records retained where technically possible; external/device corruption may prevent reading. | AT-036 |

## 10. Acceptance test matrix

These are test specifications, not executed application results. All rows are required MVP acceptance checks unless explicitly describing a future boundary. P0 = safety, core flow, or integrity blocker; P1 = required functional/quality check. Repeat applicable rows on Android/iOS, Bangla/English, and airplane mode; record device/OS/build/dataset/rule versions. Original AC-A/B/C criteria remain valid and are expanded by this matrix.

Calculation fixtures are synthetic arithmetic test inputs, not deployable nutrition sources or dietary recommendations. N1: verified test record per 100g = 200 kcal, 10g protein, 8g fat, 22g total carbohydrate, 2g fiber; one mapped serving = 50g. N2: same basis with fiber/protein unknown. Use production audited records separately to validate source ingestion. G1: ingredient R at 80 BDT/kg dated 2026-01-01; ingredient E at 12 BDT/piece with the same date. Rule fixtures must be professionally approved; no invented medical cutoff is implied.

| Test ID | Requirement ID | Scenario | Preconditions | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- |
| AT-001 | FR-001 | First launch/profile edit | Fresh airplane-mode install | Create/edit one local profile; restart retains edits; no login or second-profile creation. | P0 |
| AT-002 | FR-002 | Food search/empty bundle | Audited bundle, then injected empty bundle | Known food found locally; empty fixture shows unavailable state without fabricated matches. | P0 |
| AT-003 | FR-003 | Daily nutrition arithmetic | N1; log 50g then 100g | First entry 100 kcal/5g protein/4g fat/11g carbs; daily totals 300/15/12/33. | P0 |
| AT-004 | FR-004 | Supported patterns | Eligible approved rule fixture | Each Keto, Low-Carb, Balanced template opens an editable daily plan offline. | P0 |
| AT-005 | FR-005 | Separate deficit goal | Eligible fixture; each supported pattern | Goal toggles separately from pattern; no fourth Calorie Deficit pattern appears. | P0 |
| AT-006 | FR-006 | Plan mutations | Saved eligible daily plan | Add/replace/remove meal and change portion; reload reproduces the exact final meals/portions. | P0 |
| AT-007 | FR-007 | Duplicate groceries | Plan has R 500g and R 0.5kg | Generated list has one R quantity of 1kg; regeneration after removing 500g gives 0.5kg. | P0 |
| AT-008 | FR-008 | Dated BDT estimate | G1; R 1kg and E 2 pieces | Lines are 80.00 and 24.00 BDT; total 104.00; price dates and estimate limitations visible. | P0 |
| AT-009 | FR-009 | Unknown price/search | G1 R 1kg plus unknown item U | U marked unpriced, partial subtotal 80.00 BDT; local price search available; no implied zero price. | P0 |
| AT-010 | FR-010 | Weight history | Offline profile; two valid weights | Both saved weights appear by timestamp in history and chart after restart. | P1 |
| AT-011 | FR-011 | All reminder types | Permission granted; airplane mode | Meal/water/activity schedules appear in OS pending requests and fire in controlled platform test conditions. | P1 |
| AT-012 | FR-012 | Screening checkpoints | Fresh profile; approved rule fixtures | Onboarding and every pattern/goal application evaluate local rules before application. | P0 |
| AT-013 | FR-013 | Flagged user | Approved triggered fixture; airplane mode | Restrictive automatic plan blocked; guidance displayed; N1 manual entry saves and totals update. | P0 |
| AT-014 | FR-014 | Safety wording | All screening result branches | Content review finds no diagnosis, medical clearance, guaranteed safety, or outcome claim. | P0 |
| AT-015 | FR-015 | Restart all records | Save profile, screening, logs, plan, groceries, weights, reminder settings | Terminate/reopen offline; compare all saved values/IDs and calculated snapshots: no committed record lost. | P0 |
| AT-016 | FR-016 | Language coverage | Each core/error/safety flow in each language | Correct Bangla/English text appears without untranslated keys; saved data unchanged on switch. | P1 |
| AT-017 | FR-017 | Permission denial | Deny then revoke permission | Reminder status explains denial; no delivery claim; logging/planning/weight remain accessible. | P0 |
| AT-018 | FR-018 | Profile fields/boundaries | Enter all fields; then height 0, weight -1, invalid activity enum | Valid fields persist including allergies/goals; each invalid input rejected and prior saved profile retained. | P0 |
| AT-019 | FR-019 | Configuration invalidation | Saved plan/config; alter screening; request unknown pattern or two simultaneous patterns | Eligibility invalidated after relevant change; unsupported selection rejected without active-config overwrite. | P0 |
| AT-020 | FR-020 | Grams/serving boundaries | N1 mapped serving; quantities 1 serving, 0g, -1g, nonfinite; unmapped serving | One serving gives 100.00 kcal; invalid/unmapped values rejected without a new entry. | P0 |
| AT-021 | FR-021 | Provenance snapshots | N1 log; install revised test record | Entry retains old source/version/basis and original calculation; new entry uses new version. | P0 |
| AT-022 | FR-022 | Raw/cooked distinction | Two verified preparation-state records | Search labels both; selecting cooked uses cooked record only; absent yield conversion produces no inferred substitution. | P0 |
| AT-023 | FR-023 | Carbohydrate conventions | N1 100g; then missing fiber and fiber greater than total | Default total 22.00g; available net 20.00g labeled; missing/inconsistent net unavailable; no sugar-alcohol subtraction. | P0 |
| AT-024 | FR-024 | Missing nutrients | N1 100g plus N2 100g; unverified record | Known protein subtotal 10.00g labeled incomplete; unknown not zero; unverified record excluded from numeric calculations. | P0 |
| AT-025 | FR-025 | Edit/delete food | N1 100g saved | Edit to 50g yields 100 kcal; cancel deletion retains entry; confirm deletion removes it and known daily total becomes zero if no entries. | P0 |
| AT-026 | FR-026 | Restrictions/allergies | Declared allergen; conflicting or unknown-metadata meal | Known conflict blocks save/application; unknown metadata prevents automatic selection and shows limitation. | P0 |
| AT-027 | FR-027 | Plan totals/fallback | N1 100g plan; then no eligible templates | Plan shows 200 kcal and reloads versions/portions; failed generation explains reason and leaves logging available, no invented plan. | P0 |
| AT-028 | FR-028 | Unit boundaries | R 1000g + R 1kg; R 1l without density; different ingredient IDs | Mass combines to 2kg; volume is flagged separately; different IDs not merged. | P0 |
| AT-029 | FR-029 | Regeneration override | Override R quantity and mark purchased; change plan | Preview identifies changes; cancel retains old list; keep retains flagged override/status; reset explicitly replaces selected override; removed edited item requires decision. | P0 |
| AT-030 | FR-030 | Local prices | Airplane mode; enter dated 0 BDT, then -1/nonfinite price | Explicit zero persists with unit/date/origin; invalid prices rejected and last valid record retained/searchable. | P0 |
| AT-031 | FR-031 | Cost rounding/all unknown | G1 plus unpriced U; separate 0.333kg at 10 BDT/kg; all-unpriced list | Partial known total labeled; fractional line 3.33 BDT; all-unpriced list shows no-known-prices state; purchased status does not reduce full-plan cost. | P0 |
| AT-032 | FR-032 | Weight conversions/edit/delete | Enter 100lb; out-of-order timestamps; invalid 0/nonfinite/time | Canonical 45.359237kg, display 45.36kg; timestamp order correct; valid edit/delete persists; invalid values leave history unchanged. | P1 |
| AT-033 | FR-033 | Chart boundaries | Zero, one, then two recorded points | Empty message, single point without inferred trend, then chronological points with equivalent accessible text; no prediction. | P1 |
| AT-034 | FR-034 | Reminder lifecycle | Permitted reminder; change time, disable, re-enable, change timezone, restart | Old pending request canceled, disabled absent, one current occurrence when enabled; failures shown and preferences preserved. | P1 |
| AT-035 | FR-035 | Interrupted transactions | Inject termination before/during/after each logical commit | Reopen shows either entire old or entire new linked state; no orphan/partial summary or grocery replacement. | P0 |
| AT-036 | FR-036 | Migration/corruption/storage failure | Supported/unsupported schema; corrupt fixture; injected full disk | Supported migration preserves data; failures stop unsafe writes, retain files, display retry/help, never silent reset or false success. | P0 |
| AT-037 | FR-037 | Consent default/withdrawal | Fresh install; locally change optional consent choices | Default off; decline/withdraw preserved; no unconsented collection/transmission; all core flows available. | P0 |
| AT-038 | FR-038 | Encryption/key failure | Copied DB; inspect logs; key unavailable fixture | No plaintext personal DB values/keys in logs; AES-256/key integration evidence recorded; unavailable key reports failure without reset. | P0 |
| AT-039 | FR-039 | Local deletion | Populated local profile and reminders; cancel then confirm | Cancel retains all; confirm clears personal records and scheduled reminders and returns onboarding; injected failure reports incomplete deletion rather than success. | P0 |
| AT-040 | FR-040 | Professional safety gate | Approval records; triggered/unresolved age or medical fixture; material rule change | Only approved versions release; unresolved eligibility blocks restrictive automation with logging/guidance; changed rules require renewed approval. | P0 |
| AT-041 | FR-041 | Nutrition rights/source gate | Bundle manifest including unlicensed/unverified candidate | Candidate excluded until suitability/rights/validation approved; shipped records traceable/versioned; uncertainty disclosed and AI cannot replace authoritative values. | P0 |
| AT-042 | SYS-001, SYS-002, SYS-003, SYS-004, SYS-005, SYS-006, SYS-007, NFR-001 | Full offline architecture audit | Both platforms; fresh install through restart | All ten core capabilities pass offline with SQLite/local TypeScript, bundled assets, no login/server/telemetry/paid AI dependency; manifest and consent audit recorded. | P0 |
| AT-043 | SYS-008, SYS-009, SYS-010, NFR-002, NFR-003, NFR-004, NFR-010, NFR-015 | Release evidence | Documented supported device/OS matrix and release workload | Timing/size/RAM/crash/satisfaction measurements and population/method recorded; provisional misses have disposition; no fabricated pass. | P1 |
| AT-044 | NFR-005, NFR-006 | LTR/accessibility | Bangla/English; 200% text; VoiceOver/TalkBack | Bangla LTR; all core controls/errors announced and reachable; no required action clipped; charts have text equivalents. | P1 |
| AT-045 | NFR-007, NFR-008, NFR-009 | Security/fault suite | Consent, encryption, transaction and migration fixtures | AT-035 through AT-038 expected outcomes hold on each platform with captured evidence. | P0 |
| AT-046 | NFR-011, NFR-012, NFR-013, NFR-014 | Architecture/test/notification isolation | Adapters disabled/failed; instrument scheduling and inspect module boundaries | Pure rule tests run deterministically without UI/network/DB; offline suite passes without online adapters; no duplicate reminders or background polling; future TLS verification remains gated before online shipping. | P1 |

## 11. Roadmap boundaries and source traceability

All 24 PRD Section 6 capabilities remain on the roadmap. The table preserves their release classification; mixed-stage rows do not authorize future work in MVP.

| PRD capability | MVP allocation | Future boundary |
| --- | --- | --- |
| 1 Local profiles/onboarding | FR-001, FR-018 | One profile only. |
| 2 Patterns/energy goal | FR-004, FR-005, FR-019 | Professional safety review applies. |
| 3 Bangladeshi nutrition | FR-002, FR-041 | Coverage/count determined by audit. |
| 4 Calorie/macro tracking | FR-003, FR-020–FR-025 | Manual verified calculations only. |
| 5 Meal planning | FR-004, FR-006, FR-026–FR-027: daily | Weekly/monthly automation Post-MVP Offline. |
| 6 Recipes/substitutions | None | Post-MVP Offline recipe/substitution library; MVP ingredient mappings do not imply this library. |
| 7 Grocery generation | FR-007, FR-028–FR-029 | Daily-plan groceries only. |
| 8 Budget/cost | FR-008–FR-009, FR-030–FR-031: estimates | Expanded budgeting Post-MVP Offline. |
| 9 Couple/family/shared grocery | None | Post-MVP Offline; cross-device family sync Optional Online. |
| 10 Pantry/inventory/leftovers | None | Post-MVP Offline. |
| 11 Reminders | FR-011, FR-017, FR-034 | Local device scheduling only. |
| 12 Weight/activity/progress | FR-010, FR-032–FR-033: weight/history/trends | Expanded activity/progress Post-MVP Offline. |
| 13 Cached barcode | None | Post-MVP Offline lookup; cache updates Optional Online. |
| 14 Ramadan | None | Post-MVP Offline enhancements, safety restrictions retained. |
| 15 AI food photo | None | Optional Online, opt-in. |
| 16 Bangla voice AI/logging | None | Optional Online, opt-in. |
| 17 AI meal recommendations | None | Optional Online; cannot bypass screening or verified calculations. |
| 18 Market prices/cache | FR-008, FR-030: bundled dated prices | History/analysis Post-MVP Offline; live updates/vendor APIs Optional Online, source availability unverified. |
| 19 Cloud backup/sync | None | Optional Online; separate from local persistence and portable backup. |
| 20 Wearable/health integrations | None | Optional Online; permissions/platform/vendor connectivity applies. |
| 21 Nutritionist portal/services | None | Future Commercial; offline guidance needs no service connection. |
| 22 Subscriptions/premium | None | Future Commercial; MVP needs no subscription. |
| 23 Encrypted local backup/export/restore | None | Post-MVP Offline per PRD; portable passphrase/archive controls apply before shipping. |
| 24 Privacy/consent/safety | FR-012–FR-014, FR-037–FR-041 | Service-specific opt-in for future online features. |

PRD Section 10 trace: PR-001 → FR-037; PR-002 → FR-038; PR-003 → FR-039 plus future export/backup boundary; SR-001 → FR-001/SYS-003; SR-002 → FR-035–FR-036 for active data integrity, future restore staging deferred; SR-003 → NFR-014 future transport gate; SR-004 → Post-MVP portable backup.
PRD Section 11 trace: MSR-001–MSR-004 → FR-012–FR-014/FR-040; NSR-001 → FR-021/FR-041; NSR-002 → SYS-004/FR-041; NSR-003 → FR-004–FR-005/FR-040.
PRD Section 14 milestone trace: foundation/data → AT-001/002/012/040/041/042; tracking/planning/grocery/weight → AT-003–AT-010/020–AT-033; persistence/reminders/release readiness → AT-011/015/017/034–AT-046.

## 12. Dependencies, unresolved decisions, and release gates

Required offline inputs: audited licensed food bundle and serving/preparation mappings, dated BDT prices, ingredient/allergen metadata, reviewed daily templates and screening/guidance translations. Required platform capabilities: encrypted SQLite integration, protected keys, local storage, local scheduling, supported OS accessibility. No external API, AI provider, online price source, or live professional service is a runtime MVP dependency.

Engineering conventions in FR-020–FR-034 are explicit SRS decisions for arithmetic, units, provenance, and editing; they are not claims that PRD specified these details or that they were clinically verified. Qualified review must approve nutritional/template conventions before public release. The following decisions cannot be safely fabricated:

| Decision | Required resolution / release consequence |
| --- | --- |
| D-001 Clinical eligibility | Qualified reviewers approve age rules, questions, triggers, restrictions, deficit/energy calculations, template parameters, net-carb limitations, and guidance; record qualifications/version approvals. Unresolved eligibility withholds restrictive automation; all supported templates require approval before public release. |
| D-002 Food/data rights | Audit actual coverage/count, source suitability, licensing, redistribution rights, nutrient bases, preparation/serving mappings, uncertainty and allergen metadata before bundling. Candidate sources from PRD are not automatically approved. |
| D-003 Profile/day semantics | Approve activity/goal enumerations, permitted age/height/weight ranges, daily-log timezone/day-boundary behavior and handling of existing plans after profile changes; no invented clinical cutoffs. |
| D-004 Price/template coverage | Approve ingredient catalog, local price geography/dates/update policy, template ingredient mappings, unknown-metadata copy, and unit-mapping coverage; no live price availability assumption. |
| D-005 Security architecture | Verify SQLite AES-256 integration, key lifecycle/storage, platform backup exclusions and threat model; deletion failure/retry behavior must not silently discard data. Encryption is required, not deferred with portable backup. |
| D-006 Platform/release plan | Specify minimum Android/iOS versions/devices, reminder recurrence/DST behavior and platform limitations; record performance/resource/crash/satisfaction methods and benchmark dispositions. No device results currently verified. |
| D-007 Export scope ambiguity | PRD Section 10 PR-003 mentions readable JSON/CSV export but Section 6 capability 23 and Section 14 defer backup/export/restore. Keep export outside MVP pending product clarification; do not silently add export or conflate it with deletion/local encryption. This ambiguity remains open. |

## 13. Document quality and completion criteria

FR-001–FR-017 and SYS-001–SYS-010 retain their original wording/IDs; FR-018–FR-041 extend them sequentially. AT-001–AT-041 provide direct acceptance for every FR; AT-042–AT-046 cover cross-cutting/system/NFR checks. Workflow criteria AC-A/B/C remain preserved. Runtime acceptance requires actual recorded test results, not this specification alone.

Release review must confirm no mandatory login/network/AI service, no unsupported medical claims, no restrictive automation for triggered/unresolved eligibility, all required professional/data/security evidence, and all three PRD milestone outcomes. Future capabilities remain excluded from MVP acceptance. Open decisions above must be resolved by the named discipline before affected implementation or public release; v1.0 is not a claim that those decisions or tests are complete.

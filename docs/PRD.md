# DietMate BD - Product Requirements Document (PRD)

## Document Information
- **Document ID**: PRD-001
- **Version**: 1.0
- **Status**: Initial Planning Phase
- **Created**: November 12, 2026
- **Target Platform**: React Native + Expo + TypeScript mobile application
- **Target Markets**: Bangladesh (Bangladeshi diaspora included)

---

## 1. Product Vision and Objectives

### Vision Statement
DietMate BD empowers Bangladeshis to achieve optimal health through culturally relevant, accessible, and privacy-first nutrition management. We believe that everyone should have access to affordable, personalized nutrition tools that respect local food cultures and dietary preferences while maintaining medical safety standards.

### Core Objectives
1. **Cultural Relevance**: Deliver nutrition management tools specifically tailored to Bangladeshi food culture, dietary patterns, and health considerations
2. **Privacy Protection**: Ensure all core features work without requiring user accounts or cloud dependencies
3. **Accessibility**: Provide free, lightweight mobile solution accessible to all socioeconomic groups in Bangladesh
4. **Medical Safety**: Establish clear boundaries between informational nutrition tracking and professional medical advice
5. **Cost Awareness**: Integrate BDT currency and local market pricing to address Bangladesh's economic reality

### Success Objectives
- Support informed food logging and nutrition awareness without promising medical outcomes
- Increase nutrition awareness and food literacy in Bangladesh
- Provide culturally appropriate dietary guidance tools
- Establish privacy-first approach as industry standard for health apps

---

## 2. Problem Statement

### Primary Problems
1. **Cultural Gap**: Existing global nutrition apps lack Bangladeshi food database and cultural context
2. **Privacy Concerns**: Users hesitate to use health apps requiring mandatory accounts and cloud sync
3. **Cost Barriers**: Premium nutrition apps are unaffordable for many Bangladeshis
4. **Offline Limitations**: Lack of reliable internet connectivity in many regions
5. **Local Relevance**: Absence of Ramadan-aware meal planning and BDT-centric budgeting

### Secondary Problems
1. **Nutrition Knowledge Gap**: Limited awareness of proper portion sizes and nutritional values
2. **Meal Planning Difficulty**: Time constraints prevent effective weekly meal planning
3. **Grocery Waste**: Poor inventory management leads to food waste and financial loss
4. **Health Monitoring**: Lack of accessible tools for tracking weight and progress
5. **Dietary Compliance**: Difficulty maintaining specialized diets (Keto, Low-Carb) without guidance

---

## 3. Target Audience and Personas

### Primary Personas

#### 1. Noor - Urban Working Professional (Male, 30-45)
- **Background**: Software engineer, teacher, or business professional in Dhaka/Chittagong
- **Challenges**: Limited time for meal planning, desire for keto/low-carb results, need for cost-effective nutrition
- **Goals**: Maintain weight loss, track macros efficiently, manage family meals
- ** Pain Points**: Global apps lack local food database, subscription costs too high

#### 2. Fatima - Homemaker (Female, 28-40)
- **Background**: Manages household of 4-6, responsible for family nutrition
- **Challenges**: Ramadan meal planning, budget constraints, managing dietary restrictions
- **Goals**: Plan nutritious meals for family, track grocery expenses, reduce food waste
- ** Pain Points**: No local market pricing, no culturally appropriate meal planning

#### 3. Karim - College Student (Male, 18-25)
- **Background**: University student with limited budget, interested in fitness
- **Challenges**: Campus food options, budget-friendly nutrition, keto/low-carb curiosity
- **Goals**: Track daily calorie intake, plan cheap meals, maintain fitness
- ** Pain Points**: Expensive premium apps, lack of student-friendly features

#### 4. Ayesha - Rural Farmer/Small Business Owner (Female, 35-55)
- **Background**: Lives outside major cities, grows some food, sells produce
- **Challenges**: Seasonal availability, traditional cooking methods, health monitoring
- **Goals**: Utilize homegrown foods nutritionally, track health, manage inventory
- ** Pain Points**: No offline barcode lookup, limited local food database

### Secondary Personas

#### Tech-Savvy Early Adopters
- Interest in AI features, willing to experiment with new tech
- Primary users of optional features (AI analysis, voice logging)

#### Healthcare Professionals
- Future users of nutritionist dashboard
- Need secure patient data management

---

## 4. User Journeys

Journeys describe the full product lifecycle. Section 6 governs staging: MVP uses manual logging, editable daily plans and generated groceries; barcode, pantry, recipes, weekly/monthly automation and optional online inputs follow MVP.

### Core User Journey Map

#### Phase 1: Onboarding
**Time**: 5-10 minutes
**Touchpoints**: First launch, profile setup, dietary preference selection

1. **Launch App** → User sees welcome screen with Bangla/English options
2. **Setup Profile** → Enter basic info (age, gender, height, weight)
3. **Dietary Goal Selection** → Choose a Keto, Low-Carb or Balanced pattern and a separate energy goal such as Calorie Deficit, subject to screening
4. **Food Preferences** → Select liked/disliked Bangladeshi foods
5. **Lifestyle Setup** → Activity level, dietary restrictions, budget range
6. **Goal Setting** → Weekly target weight change, budget goals
7. **Complete Onboarding** → Welcome to DietMate BD

#### Phase 2: Daily Tracking
**Time**: 2-5 minutes per day
**Touchpoints**: Food logging, water intake, activity tracking

1. **Quick Log** → Capture photo or voice entry for meals
2. **Manual Entry** → Add foods from local database
3. **Nutrition Calculation** → Auto-calculate calories and macros
4. **Progress Update** → Record weight, measurements, energy levels
5. **Reminders** → Local notifications for meals, water, activity

#### Phase 3: Meal Planning
**Time**: 15-30 minutes per week
**Touchpoints**: Meal plan creation, grocery list generation

1. **Browse Recipes** → Select from Bangladeshi recipes database
2. **Create Plans** → Generate daily/weekly meal plans
3. **Nutritional Analysis** → Review macro balance, calorie distribution
4. **Generate List** → Automatic grocery list with quantities
5. **Budget Calculation** → Estimate costs in BDT

#### Phase 4: Grocery Management
**Time**: 10-15 minutes per shopping trip
**Touchpoints**: Inventory management, price comparison

1. **Check Pantry** → View current stock levels
2. **Shopping List** → Add items, scan barcodes offline
3. **Price Check** → Compare local market prices (offline cache)
4. **Purchase** → Mark items as bought, update inventory
5. **Storage** → Record shelf life, expiration dates

#### Phase 5: Progress Tracking
**Time**: 5-10 minutes per week
**Touchpoints**: Progress charts, goal review, adjustments

1. **View Metrics** → Weight trends, macro balance, budget spending
2. **Review Goals** → Assess progress toward weekly/monthly targets
3. **Adjust Plans** → Modify meal plans based on results
4. **Celebrate** → Achieve milestones, receive encouragement
5. **Professional Help** → Access nutritionist consultation when needed

---

## 5. Complete Feature Inventory

### Offline Feature Inventory (MVP and Post-MVP)

This is the long-term inventory, not an MVP checklist. Release stages follow Section 6; only Section 14 defines MVP. Optional AI/voice services require opt-in internet; all core calculations remain local.

#### 1. User Onboarding and Personalized Profiles
- Basic user profile setup (age, gender, height, weight)
- Diet pattern selection (Keto, Low-Carb, Balanced) with a separate Calorie Deficit energy goal, subject to screening
- Food preference and restriction management
- Lifestyle and activity level recording
- Goal setting for weight, macros, and budget

#### 2. Bangladeshi Food Nutrition Database
- Verified bundled Bangladeshi food records; dataset size unverified until audit and source redistribution rights verified
- Nutritional information (calories, protein, carbs, fats, vitamins, minerals)
- Portion size standards for local measurements
- Regional variations and preparation methods
- Historical and traditional food items

#### 3. Calorie and Macro Tracking
- Manual food entry (MVP); cached barcode scanning (Post-MVP Offline)
- Photo-based food logging (optional AI)
- Voice-based food logging in Bangla/English (optional)
- Real-time nutrition calculation and tracking
- Daily/weekly/monthly macro balance analysis
- Nutritional value comparison between foods

#### 4. Personalized Meal Plans
- Daily meal planning with nutritional balance
- Weekly meal rotation to prevent boredom
- Ramadan-specific meal planning
- Diet-specific meal templates (Keto, Low-Carb, etc.)
- Dietary restriction accommodation
- Seasonal meal recommendations

#### 5. Grocery Management
- Pantry, stock, and leftover tracking
- Automatic grocery list generation
- Local market price cache (BDT)
- Ingredient cost calculations
- Shopping list optimization
- Purchase history tracking

#### 6. Progress Tracking
- Weight, body measurements, and activity tracking
- Progress charts and trend analysis
- Goal achievement celebration
- Health metrics monitoring
- Activity level tracking
- Energy level and wellbeing ratings

#### 7. Reminders and Notifications
- Local meal, water, and activity reminders
- Custom reminder scheduling
- Ramadan-specific timing notifications
- Weekly plan reminders
- Grocery restocking alerts

#### 8. Food Substitution and Compatibility
- Meal substitution suggestions
- Alternative ingredient recommendations
- Dietary restriction compatibility checking
- Nutrient replacement suggestions
- Cultural meal pairing suggestions

### Optional Online Features

#### 9. AI Food Photo Analysis
- Upload food photos for nutritional analysis
- AI-based ingredient identification
- Nutritional value estimation
- Confidence scoring and human verification

#### 10. AI Meal Recommendations
- Personalized meal suggestions based on history
- Seasonal and regional recommendations
- Dietary restriction-aware suggestions
- Health-based meal optimization

#### 11. Bangla Voice-Based Food Logging
- Speech-to-text food recognition
- Bangla language support for logging
- Voice command integration
- Pronunciation assistance

#### 12. Cloud Backup and Synchronization
- Encrypted cloud storage for user data
- Cross-device synchronization
- Backup and restore functionality
- Privacy-focused sync protocols

#### 13. Wearable/Health Data Integrations
- Step and activity tracking integration
- Heart rate and sleep data import
- Health app compatibility
- Professional health data sharing

#### 14. Local Market Pricing APIs
- Real-time market price integration
- Price comparison between vendors
- Historical price tracking
- Seasonal price analysis

#### 15. Professional Consultation
- Nutritionist dashboard for healthcare providers
- Secure patient data sharing
- Professional consultation scheduling
- Medical report generation

#### 16. Premium Features and Subscriptions
- Advanced analytics and insights
- Priority customer support
- Advanced recipe database
- Custom meal planning templates

#### 17. Advanced Security Features
- Encrypted local backup/export
- Data encryption at rest and in transit
- Privacy consent management
- Data retention policies

### Additional Features

#### 18. Health Screening and Safety
- Risk assessment for high-risk diets
- Professional review for medical conditions
- Age and pregnancy considerations
- Contraindication warnings
- Emergency contact integration

#### 19. Accessibility and Localization
- Screen reader compatibility
- High contrast mode support
- Bangla script input methods
- Cultural sensitivity considerations
- Accessibility testing integration

#### 20. Analytics and Success Metrics
- Optional, consent-based usage pattern analysis; no mandatory telemetry
- Feature adoption tracking
- User satisfaction measurements
- Health outcome correlations
- Performance optimization feedback

---

## 6. Offline vs Optional Online Feature Matrix

| No. | Feature | Release Stage | Offline / Online Dependency | Requirement Reference |
| --- | --- | --- | --- | --- |
| 1 | Local profiles and onboarding | MVP | Offline: one local profile, no login; persistent device storage. | Section 14 — Core Features 1, 10 |
| 2 | Keto, Low-Carb, Balanced patterns + Calorie Deficit goal | MVP | Offline templates and calculations; Calorie Deficit is a separate energy goal, subject to screening. | Section 14 — Core Features 4, 9 |
| 3 | Bangladeshi food nutrition database | MVP | Offline bundled verified data; dataset size remains unverified until audit. | Section 14 — Core Feature 2; Milestone 1 |
| 4 | Calorie and macro tracking | MVP | Offline manual food/portion logging and local calculations; AI is never required. | Section 14 — Core Features 3, 10 |
| 5 | Daily, weekly and monthly meal planning | MVP (daily); Post-MVP Offline (weekly/monthly automation) | Offline editable daily plans; weekly/monthly automated planning follows MVP; screening restrictions apply. | Section 14 — Core Features 4, 9; Post-MVP Scope |
| 6 | Bangladeshi recipes and food substitutions | Post-MVP Offline | Offline bundled recipes and local substitution rules. | Section 14 — preserved long-term scope: recipes and substitutions |
| 7 | Automatic grocery list generation | MVP | Offline generation from daily plans; combine quantities and regenerate after edits. | Section 14 — Core Feature 5; Milestone 2 |
| 8 | BDT budget and grocery cost calculations | MVP (grocery estimates); Post-MVP Offline (expanded budgeting) | Offline bundled unit prices and local calculations; dated estimates, manual price search, partial totals for unknown prices; live updates optional. | Section 14 — Core Feature 6; Milestone 2; preserved long-term budgeting scope |
| 9 | Couple/family profiles and shared grocery | Post-MVP Offline; Optional Online (cross-device sync) | Multiple profiles and shared grocery work offline on one device; cross-device sync requires optional internet. | Section 14 — Post-MVP Scope: family profiles and sync |
| 10 | Pantry, inventory and leftovers | Post-MVP Offline | Offline local inventory, pantry and leftover management; advanced pantry is post-MVP. | Section 14 — Post-MVP Scope: advanced pantry and inventory; preserved leftovers scope |
| 11 | Local reminders and notifications | MVP | Offline device scheduler; permission denial must not block core use. | Section 14 — Core Feature 8; Milestone 3 |
| 12 | Weight, activity and progress tracking | MVP (weight/history/trends); Post-MVP Offline (expanded activity/progress) | Offline local logs and trends; expanded activity and progress tracking follows MVP. | Section 14 — Core Features 7, 10; preserved activity/progress scope |
| 13 | Cached barcode lookup | Post-MVP Offline; Optional Online (cache updates) | Offline lookup of cached barcode data and local price history; manual search on cache misses; optional internet to populate/update cache. | Section 14 — Post-MVP Scope: barcode scanning |
| 14 | Ramadan meal planning | Post-MVP Offline | Offline Ramadan templates and scheduling, subject to high-risk screening restrictions. | Section 14 — Core Feature 9; preserved long-term Ramadan scope |
| 15 | Optional AI food photo analysis | Optional Online | Opt-in internet/cloud AI; manual logging remains available offline. | Section 14 — Post-MVP Scope: AI features and cloud services |
| 16 | Optional Bangla voice logging | Optional Online | Opt-in internet-dependent voice service; manual logging remains available offline. | Section 14 — preserved long-term voice logging scope; no online dependency for core use |
| 17 | Optional AI meal recommendations | Optional Online | Opt-in internet/cloud AI; core nutrition, planning and cost calculations remain local; screening restrictions apply. | Section 14 — Core Feature 9; Post-MVP Scope: AI features and cloud services |
| 18 | Local market prices and offline cache | MVP (bundled prices); Post-MVP Offline (price history/analysis); Optional Online (live updates) | Offline dated local prices/cache; optional live market APIs, vendor comparison, historical and seasonal analysis; external source availability unverified. | Section 14 — Core Feature 6; preserved long-term market pricing scope |
| 19 | Optional cloud backup and sync | Optional Online | Opt-in internet/cloud service; separate from local encrypted backup/restore; never required for core persistence. | Section 14 — Core Feature 10; Post-MVP Scope: sync and cloud services |
| 20 | Wearable/health integrations | Optional Online | Optional device permissions and supported platform/vendor APIs; connectivity depends on integration; core tracking stays offline. | Section 14 — preserved long-term wearable/health integration scope |
| 21 | Nutritionist services and portal | Future Commercial | Optional internet-dependent professional consultation and portal; offline safety guidance remains available without this service. | Section 14 — Core Feature 9; preserved long-term professional services scope |
| 22 | Subscriptions and premium services | Future Commercial | Optional online purchase/entitlement services; no subscription required for MVP core use. | Section 14 — core-use requirements; preserved long-term commercial scope |
| 23 | Encrypted local backup/export/restore | Post-MVP Offline | Offline encrypted file export and restore using local storage; distinct from optional cloud backup and ordinary MVP persistence. | Section 14 — Core Feature 10; preserved long-term local backup/export/restore scope |
| 24 | Privacy, consent and health safety | MVP (local privacy, permissions and screening); Optional Online (service-specific consent) | Offline local data and consent controls; triggered screening blocks automated restrictive plans, preserves basic logging and shows offline professional-advice guidance without diagnosis; online services require separate opt-in. | Section 14 — Core Features 8–10; first-launch requirements; Milestones 1, 3 |

---


## 7. Functional Requirements

### Core Functional Requirements

#### FR-001: User Management
- **Requirement**: Create and manage one local profile without accounts in MVP; multiple/family profiles are Post-MVP Offline
- **Description**: Users can set up profiles locally with age, gender, height, weight, dietary goals
- **Acceptance Criteria**: Profile saved locally and persists after app restart; portable export/restore is Post-MVP Offline under SR-004

#### FR-002: Food Database Management
- **Requirement**: Access verified Bangladeshi food nutrition records offline.
- **Description**: Each record includes source and version, nutrients per 100g edible portion, raw/cooked preparation state, and a documented serving-to-gram conversion. Dataset size remains unverified until audit. The Food Composition Table for Bangladesh (Shaheen et al., 2013) remains a candidate source until licensing and redistribution rights are verified; do not bundle it before verification.
- **Acceptance Criteria**: Database is searchable by name and filterable by category; measure load time against the provisional NFR-001 benchmark on release-build test devices. Validate provenance, units, preparation state, conversions, and plausible values. Mark missing nutrients explicitly as unknown, never silently as zero; label affected totals as incomplete. Record whether source carbohydrate includes dietary fiber and normalize records to the FR-003 convention only when supported by source definitions; otherwise mark the relevant carbohydrate values unknown. Verification documents data quality and composition uncertainty; it does not guarantee exact nutrient content.


#### FR-003: Nutrition Tracking
- **Requirement**: Track daily calorie and macro intake using the verified food database and local TypeScript calculation engine.
- **Description**: Manual food and portion entry, with post-MVP barcode scanning and optional AI photo suggestions requiring user confirmation; BDT cost calculations use local unit prices. Scale nutrients from per-100g edible-portion values using documented serving-to-gram conversions and the matching raw/cooked record. Deterministic calculation correctness is separate from uncertainty in food composition and portion estimates.
- **Acceptance Criteria**: Support all macronutrients. Define total carbohydrate as including dietary fiber; net carbohydrate equals total carbohydrate minus dietary fiber, with no other deductions. For source values that exclude fiber, add fiber once to obtain total carbohydrate when both values are available and compatible; never subtract fiber again from an already fiber-excluding value. Unknown fiber leaves net carbohydrate unknown; missing nutrient contributions make affected totals explicitly incomplete. Test scaling, aggregation, serving conversions, carbohydrate normalization, missing values, and rounding against documented reference fixtures with inputs and expected outputs. Preserve full precision during calculations, round only displayed final totals to the nearest 1 kcal and 0.1g using round-half-up, and document numeric comparison tolerances for floating-point tests. No percentage accuracy guarantee applies to underlying food composition.


#### FR-004: Meal Planning
- **Requirement**: Generate personalized meal plans
- **Description**: Editable daily plans in MVP; weekly/monthly automated planning is Post-MVP Offline. Keto, Low-Carb and Balanced are patterns; Calorie Deficit is a separate energy goal.
- **Acceptance Criteria**: Reviewed templates use verified food records and respect restrictions; offline high-risk screening blocks automated restrictive plans while preserving basic logging and offline professional guidance

#### FR-005: Grocery Management
- **Requirement**: Generate shopping lists from daily plans in MVP; pantry/inventory/leftover tracking is Post-MVP Offline
- **Description**: Automatic list generation and offline BDT cost estimates with price source/date stamps; inventory integration follows MVP
- **Acceptance Criteria**: Generate and regenerate combined ingredient quantities from daily plans; calculate offline BDT estimates with partial totals for unknown prices; validate inventory tracking post-MVP

#### FR-006: Progress Tracking
- **Requirement**: Monitor weight/history/trends in MVP; expanded measurements, activity and health metrics are Post-MVP Offline
- **Description**: Daily tracking with historical data, trend analysis
- **Acceptance Criteria**: Accurate measurements, clear visual trends, goal achievement tracking

#### FR-007: Communication and Reminders
- **Requirement**: Local notifications for meals, water, activity
- **Description**: Customizable reminders with cultural consideration (Ramadan), works offline when permitted; permission denial does not block core use
- **Acceptance Criteria**: Reliable delivery, respects user preferences, culturally appropriate timing, graceful fallback when denied

### Optional Feature Requirements

#### OFR-008: AI Food Analysis
- **Requirement**: Optionally suggest food and portion matches from food photos.
- **Description**: With user consent, upload photos for AI suggestions; users must review and confirm food matches, preparation state, and portions before logging. AI estimates are uncertain and must not be treated as verified nutrient values.
- **Acceptance Criteria**: Allow users to correct or reject suggestions and use manual entry when no verified match exists. Final nutrition calculations use confirmed matches from the verified food database and the local TypeScript engine under FR-002 and FR-003. AI must not supply authoritative nutrient values or bypass confirmation; core logging and calculations remain available offline without AI.


#### OFR-009: Voice Input
- **Requirement**: Bangla/English voice-based food logging
- **Description**: Speech-to-text for adding foods, voice commands
- **Acceptance Criteria**: 90% speech recognition accuracy, supports Bangla language

#### OFR-010: Cloud Sync
- **Requirement**: Optional post-MVP cloud backup and synchronization, separate from SR-004 offline encrypted archives
- **Description**: Encrypted cloud storage, cross-device sync
- **Acceptance Criteria**: Explicit opt-in consent, user-controlled sync, and separately verified cloud encryption/key management under Section 10; no cloud dependency for core use

---

## 8. Non-Functional Requirements

### Performance Requirements (Provisional Release-Build Targets)

#### NFR-001: Response Time
- **Goal**: Core interactions target under 2 seconds as a provisional release-build benchmark, subject to device testing; not a guaranteed result or hard release gate
- **Specific**: Measure profile loading, food search, local nutrition calculations and daily plan editing against the same core-interaction benchmark; revise based on documented device results
- **Measurement**: Automated performance testing with dataset validation

#### NFR-002: Memory Usage
- **Goal**: Peak RAM below 300MB as a provisional release-build benchmark, subject to device testing, not a guaranteed result or hard release gate
- **Specific**: Optimized data structures, efficient SQLite indexing
- **Measurement**: Memory profiling tools during heavy operations

#### NFR-003: Storage Efficiency
- **Goal**: Installed app size below 200MB as a provisional release-build benchmark; measure database/runtime storage separately without an unvalidated size gate
- **Specific**: Optimized data compression, efficient indexing for Bangla/English content
- **Measurement**: App Store Connect metrics, device storage monitoring

### Reliability Requirements

#### NFR-004: Offline Operation
- **Goal**: All MVP core features must work without internet; acceptance requires offline testing
- **Specific**: Database transactions reliable, local notifications work with fallback
- **Measurement**: Fresh-install airplane-mode and restart testing against Section 14 milestones, with voluntary usability feedback

#### NFR-005: Crash Resistance
- **Goal**: Crash rate below 0.1% of observed launches as a provisional release-build benchmark; document sample size and observation period, not a guaranteed result or hard release gate
- **Specific**: Graceful handling of invalid data, memory corruption protection
- **Measurement**: Consent-based release-build test reports and local error logs; no mandatory production telemetry

### Security Requirements

#### NFR-006: Data Privacy
- **Goal**: No optional data sharing without explicit consent; separate local database, portable archive and future cloud security under Section 10
- **Specific**: No mandatory account creation, encrypted local storage
- **Measurement**: Privacy audits, security penetration testing

#### NFR-007: Data Integrity
- **Goal**: Deterministic nutrition calculations that follow documented arithmetic and rounding rules, with food composition uncertainty disclosed separately.
- **Specific**: Enforce FR-002 provenance, units, preparation state, serving conversions, missing nutrient handling, and source licensing checks. Validate source transcription through double-entry checks. Apply FR-003 total/net-carbohydrate conventions without double subtraction of fiber. Verified records are traceable and validated, not guaranteed to represent exact nutrient content for every food or portion.
- **Measurement**: Automated tests compare local TypeScript results with documented reference fixtures and expected outputs under FR-003 rounding rules and documented floating-point tolerances. Include missing nutrients and both fiber-inclusive and fiber-exclusive source cases. Manually review source transcription and composition limitations. Do not use 100% nutritional accuracy or an arbitrary percentage tolerance as a data-quality guarantee.

---


## 9. Performance and Usability Goals

### Performance Goals (Provisional Targets)

#### Consolidated Release-Build Benchmarks
- **Core Response Time**: Under 2 seconds; NFR-001 governs measurement.
- **Peak RAM / Installed Size / Crash Rate**: Below 300MB / below 200MB / below 0.1% of observed launches, as defined in NFR-002, NFR-003 and NFR-005.
- **Validation**: All numeric performance benchmarks are provisional, require real Android/iOS release-build testing on documented devices, and may be revised from results; they are not guaranteed results or arbitrary hard release gates. Measure CPU, battery, runtime storage and optional online sync separately before setting targets.

### Usability Goals

#### User Experience
- **First Launch**: < 5 minutes to complete initial setup
- **Daily Logging**: < 2 minutes per day
- **Weekly Planning**: Post-MVP usability study item; no MVP acceptance dependency
- **Learning Curve**: Basic functionality usable after 5 minutes of exploration

#### Accessibility
- **Screen Readers**: Native VoiceOver/TalkBack compatibility from first release
- **Language Support**: Complete Bangla and English support, left-to-right layout
- **Visual Design**: High contrast options, large text support, Bangla script rendering
- **Input Methods**: Native keyboard, accessible controls and supported gestures; optional internet-dependent voice food logging follows MVP

---

## 10. Security and Privacy Requirements

### Privacy Requirements

#### PR-001: Data Collection
- **Requirement**: Collect only data explicitly provided by users; no mandatory telemetry or login for core use.
- **Specific**: No data mining. Optional telemetry and data sharing require explicit, informed, purpose-specific consent before collection or transmission; cloud and AI sharing are opt-in.
- **Acceptance**: Users can decline or withdraw optional sharing without losing offline core functionality; consent choices are available locally.

#### PR-002: Data Storage
- **Requirement**: Encrypt the local database at rest; treat portable backup encryption and future cloud security as separate controls.
- **Specific**: AES-256 is the selected encryption target. Local key storage, key lifecycle, database encryption integration, and platform protections must be verified during architecture design. Portable archive keys follow SR-004; future cloud storage requires its own security design.
- **Acceptance**: Verify encryption and key management on supported platforms before shipping the applicable capability. Document threat-model limitations; no guarantee is made that data remains protected on a compromised or unlocked device. Do not describe local at-rest encryption as end-to-end cloud encryption.

#### PR-003: User Control
- **Requirement**: Provide user-controlled local data export, backup/restore, and deletion.
- **Specific**: JSON/CSV exports are readable interchange files, not restorable backup archives. Encrypted portable backup/restore follows SR-004 and is Post-MVP Offline; optional cloud backup is a separate post-MVP feature.
- **Acceptance**: Clearly distinguish readable JSON/CSV exports from encrypted restorable archives and explain that exported readable files need user protection. No account or internet is required for local export, backup, or restore.

### Security Requirements

#### SR-001: Authentication
- **Requirement**: No mandatory login for core features; authentication is optional for optional cloud features.
- **Specific**: Biometric, PIN, or password options may protect local access; cloud authentication is separate from local access and portable archive passphrases.
- **Acceptance**: Core use works offline without an account or cloud authentication.

#### SR-002: Data Integrity
- **Requirement**: Detect corruption and preserve valid existing data during failed imports or restores.
- **Specific**: Validate checksums, archive versions, schemas, and authenticated integrity where applicable; stage and validate restored data before an atomic replacement of the active database.
- **Acceptance**: Corruption produces a clear error and recovery options using a validated backup; do not promise automatic recovery for every failure. A failed restore leaves existing user data intact and usable.

#### SR-003: Secure Communications
- **Requirement**: Encrypt transmission for optional online features; cloud backup and sync remain optional and post-MVP.
- **Specific**: TLS 1.3 with certificate validation for online communications. Cloud storage encryption, access controls, and key management require separate architecture verification; sharing requires PR-001 consent.
- **Acceptance**: Verify certificate validation and rejection of invalid connections. Core features retain no mandatory online dependency; do not promise universal protection against interception or compromised endpoints.

#### SR-004: Encrypted Local Backup and Restore
- **Requirement**: Post-MVP Offline portable encrypted backup/export/restore for local data, independent of cloud backup.
- **Specific**: Create versioned encrypted restorable archives using the AES-256 target, authenticated integrity protection, and a user-managed passphrase. Key derivation, encryption mode, key lifecycle, and implementation must be verified during architecture design before this capability ships. Backup and restore must work entirely offline without login.
- **Acceptance**:
  - A backup creates an encrypted archive containing the supported local data and version/schema metadata; offline round-trip testing verifies restoration.
  - Restore validates the passphrase, authenticated integrity, checksum, supported version, and schema before applying data.
  - Incorrect passphrases, corrupt archives, and unsupported archives are rejected with a clear error; failed restore preserves existing data intact and usable.
  - Apply validated restored data atomically, including failure/interruption tests that prove existing data is preserved on failure.
  - JSON/CSV exports are readable interchange files, not encrypted restorable archives; the UI distinguishes them from backups.

---


## 11. Medical and Nutritional Safety Boundaries

### Medical Safety Requirements

#### MSR-001: Professional Review
- **Requirement**: Qualified professionals must review diet templates and screening rules before public release.
- **Specific**: Document reviewer qualifications, reviewed template/rule versions, risk assessment, and approval. Material changes require renewed review before release.
- **Acceptance**: Public release uses professionally reviewed templates and screening rules with clear limitations and guidance. Core use does not require an emergency-contact integration or a live professional connection.

#### MSR-002: Age Restrictions
- **Requirement**: Apply professionally validated age-related eligibility rules before offering restrictive automated plans.
- **Specific**: Age thresholds and pediatric eligibility remain pending qualified professional validation; do not prescribe pediatric diets or assume adult templates are appropriate for children.
- **Acceptance**: No unsupported pediatric prescriptions. Until eligibility is validated, withhold automated restrictive plans for unresolved age eligibility while retaining basic food logging and offline guidance to seek professional advice.

#### MSR-003: Medical Condition Screening
- **Requirement**: Screen locally for risks relevant to diet planning without diagnosing users.
- **Specific**: Qualified professionals must validate screening questions, rules, and medical eligibility thresholds, including considerations such as diabetes, pregnancy, and heart conditions. Eligibility thresholds remain pending that validation; do not invent cutoffs or treat screening as medical clearance.
- **Acceptance**: Reviewed screening rules ship with the app and work without internet. High-risk responses trigger MSR-004; unvalidated eligibility must not enable automated restrictive plans.

#### MSR-004: Offline High-Risk Screening Branch
- **Requirement**: Run high-risk screening offline without requiring a live consultation; professional validation before release remains mandatory under MSR-001.
- **Specific**: When screening is triggered, block automated restrictive meal plans, preserve basic food logging, and display bundled guidance to seek qualified professional advice.
- **Acceptance**: Airplane-mode tests verify screening, blocked restrictive automation, continued basic logging, and professional guidance. Guidance must not diagnose the user, promise safety, or require internet to be shown.

### Nutritional Safety Requirements

#### NSR-001: Source Verification
- **Requirement**: Use traceable, verified nutrition records under FR-002, with composition uncertainty disclosed.
- **Specific**: The Food Composition Table for Bangladesh (Shaheen et al., 2013), WHO, and local health organizations are candidate sources subject to suitability, licensing, and redistribution-rights verification. Do not bundle data before rights are verified.
- **Acceptance**: Record source/version and validation status; review updates before distribution. Do not equate source verification with guaranteed nutritional accuracy; bundled data remains usable offline.

#### NSR-002: AI Boundaries
- **Requirement**: AI is never the source of truth for nutrition and is not required for core calculations.
- **Specific**: AI may suggest food and portion matches; users must confirm or correct them before logging. Final calculations use the verified food database and local TypeScript engine under FR-002, FR-003, and OFR-008.
- **Acceptance**: Users can reject suggestions and log manually offline. AI cannot bypass screening restrictions or supply authoritative nutrient values; confidence scores do not establish medical eligibility.

#### NSR-003: Macro Balance
- **Requirement**: Qualified professionals must review template macro conventions and safety limitations before public release; no macro ratio is universally safe.
- **Specific**: Keto, Low-Carb, and Balanced are diet patterns; Calorie Deficit is a separate energy goal. Individualized prescriptions require qualified review; medical eligibility thresholds remain pending professional validation.
- **Acceptance**: Document reviewed template parameters and limitations, show offline professional-advice guidance, and enforce MSR-004 restrictions. Do not promise medical suitability or outcomes for every user.

---


## 12. Accessibility and Localization Requirements

### Accessibility Requirements

#### ASR-001: Screen Reader Support
- **Requirement**: Native VoiceOver/TalkBack compatibility from first release
- **Specific**: Native React Native accessibility labels, roles and hints, touch target sizes, Bangla left-to-right (LTR) layout
- **Acceptance**: WCAG 2.1 AA compliance, native platform accessibility APIs

#### ASR-002: Visual Accessibility
- **Requirement**: High contrast mode, large text support
- **Specific**: Dynamic type sizing, color blindness support, Bangla script rendering
- **Acceptance**: Apple Dynamic Type, Android Text Scale

#### ASR-003: Physical Accessibility
- **Requirement**: Large touch targets, alternative input methods
- **Specific**: Minimum 44x44 point targets, voice control integration
- **Acceptance**: Tested with various physical capabilities

---

## 13. Product Success Metrics

### Adoption Metrics

#### AM-001: User Growth
- Measure adoption and retention only through consent-based studies or optional analytics with documented cohorts and observation periods; no user-growth forecasts or account requirement.

#### AM-002: Engagement
- Measure completion of offline logging, daily planning and grocery workflows in usability tests; document the study method and observed results rather than unsupported adoption targets.

### Health Impact Metrics

#### HIM-001: Behavior Change
- Assess nutrition understanding and self-reported logging usefulness through voluntary studies; no prescribed weight-change or diet-compliance outcome target.

#### HIM-002: Health Outcomes
- No promised BMI, energy, cholesterol or blood-pressure improvement. Any future health-outcome evaluation requires qualified professional review, informed consent and a suitable study design; it is not an MVP release gate.

### Business Metrics

#### BM-001: Revenue
- Future commercial services may measure actual opt-in purchases and revenue after validation; no revenue, conversion or paid-user forecasts are assumed for MVP.

#### BM-002: Cost Efficiency
- Record actual development and operating costs by milestone; establish budgets from validated estimates. No unsupported development, acquisition or hosting-cost prediction; MVP requires no hosted server.

---

## 14. MVP Definition

### Minimum Viable Product Scope

The MVP is a complete offline experience for one local profile. Release readiness is determined by the milestones below, without an arbitrary 12-month deadline. No login or internet connection is required, including on first launch after installation.

#### Core Features (Must Have)
1. **Local Profile**: Onboarding and editing for one profile stored on the device.
2. **Bundled Food Data**: Verified Bangladeshi food nutrition data available for offline search. Dataset size is unverified; no item count is claimed or required until the bundled dataset is audited.
3. **Manual Nutrition Tracking**: Manual food and portion logging with calculated daily calorie and macro totals.
4. **Daily Meal Planner**: An editable daily plan with templates for the Keto, Low-Carb, and Balanced diet patterns. Calorie Deficit is a separate energy goal that can be applied to a diet pattern, subject to high-risk screening. Users can add, replace, and remove meals and adjust portions.
5. **Automatic Grocery Lists**: Generate and regenerate a grocery list from the daily plan, combining ingredient quantities and reflecting plan edits.
6. **Offline BDT Estimates**: Estimate grocery costs in BDT using bundled local price data, with price dates and estimate limitations shown; live prices are not required.
7. **Weight Tracking**: Record weight and view weight history and trends.
8. **Local Notifications**: Meal, water, and activity reminders where permitted by the device, with graceful behavior if permission is denied.
9. **High-Risk Diet Screening**: Screen locally during onboarding and before applying diet patterns or energy goals. If screening is triggered, block automated restrictive meal plans, keep basic food logging available, and show offline guidance to seek professional advice. Screening must not present a diagnosis or medical clearance.
10. **Local Data Persistence**: Persist profile, screening responses, logs, plans, grocery lists, weight history, and reminder settings across app restarts.

#### Required Technical Capabilities
1. **Offline Storage**: SQLite with local persistence.
2. **Nutrition Engine**: Pure TypeScript calculations.
3. **Cross-Platform**: Android and iOS support.
4. **Localization**: Bangla and English support.
5. **Performance**: Core interactions target under 2 seconds as a provisional release-build benchmark under NFR-001, subject to device testing rather than a hard release gate.

#### Post-MVP Scope (Preserved for Future Releases)
- Barcode scanning.
- Advanced pantry management and inventory tracking.
- Family profiles and sync.
- Weekly/monthly automated planning.
- AI features and cloud services.

These features remain part of the long-term product scope and are not prerequisites for MVP acceptance. The long-term roadmap remains preserved.

### First Launch - Airplane Mode Requirements

After installation, a fresh first launch in airplane mode must support all ten core features using bundled data and device capabilities. Profile setup, high-risk diet screening, food search, manual calorie/macro logging, daily plan editing, grocery generation with BDT estimates, and weight tracking must work without downloads. Local reminders must work when permission is granted; denial must not block other features. All saved data must remain available after restart.

Core use requires no account, login, internet, server, download, subscription, or telemetry.

### Milestone-Based Acceptance Criteria

MVP release requires completion of every milestone; milestones have no fixed calendar deadline.

#### Milestone 1: Offline Foundation and Verified Data
- [ ] On Android and iOS, a fresh installation in airplane mode supports creating and editing one local profile in Bangla and English.
- [ ] The bundled food dataset is audited for nutrition sources, units, and verification status; its actual item count and coverage are documented before release, with no assumed dataset size.
- [ ] Bundled food search works without a download; measure it against the provisional under-2-second benchmark on documented release-build test devices.
- [ ] High-risk diet screening runs locally during onboarding and before applying diet patterns or energy goals. Triggered screening blocks automated restrictive meal plans, preserves basic food logging, and shows offline guidance to seek professional advice without diagnosing the user.

#### Milestone 2: Daily Tracking, Planning, and Grocery Flow
- [ ] Manual food and portion entries produce calorie and macro totals matching verified reference calculations.
- [ ] Users can create and edit a daily plan, including meals and portions, using the supported diet patterns and separate energy goal, subject to high-risk screening restrictions.
- [ ] Grocery generation combines ingredient quantities and reflects daily plan edits when regenerated.
- [ ] Grocery costs are estimated offline in BDT from bundled prices, with dates and estimate limitations visible.
- [ ] Users can log weight and view history and trends offline.

#### Milestone 3: Persistence, Reminders, and Release Readiness
- [ ] All ten core features pass an end-to-end airplane-mode check from fresh first launch through app restart.
- [ ] Profile, screening responses, nutrition logs, daily plans, grocery lists, weight history, and reminder settings survive app restart without data loss.
- [ ] Local notifications work without internet when permitted; denied permission is handled gracefully and does not block core use.
- [ ] Android and iOS checks confirm Bangla/English support and record core interaction response times against the provisional under-2-second benchmark; document results and any benchmark revisions.
- [ ] Measure installed size and peak RAM usage in real release builds on documented test devices. Below 200MB installed size and below 300MB peak RAM are provisional benchmarks to validate and revise based on results, not guaranteed results or hard release gates.
- [ ] Measure crash rate in real release-build testing, documenting the test population, observation period, and measurement method. Below 0.1% is a provisional benchmark to validate and revise based on results, not a guaranteed result or hard release gate. Record user satisfaction above 4/5 in testing, with test population and measurement method documented.
- [ ] No post-MVP feature, login, internet connection, or cloud service is required to complete any acceptance milestone.

---

## 15. Long-term Feature Roadmap

### 24 Roadmap Capabilities — Release Stages and Dependencies

Section 6 is the canonical numbered map for all 24 capabilities and their release stages/dependencies. All remain in long-term scope; the milestones below do not add MVP requirements.

---

### Milestone 1: Core Foundation — Offline-First MVP
**Capabilities Delivered**: MVP portions of capabilities 1–5, 7–8, 11–12, 18 and 24, limited to Section 14 scope; completion requires its three acceptance milestones.
- **Offline Core**: One local profile, bundled verified Bangladeshi food data, manual calorie/macro logging, editable daily plans using reviewed diet patterns and a separate energy goal, automatic grocery lists, offline dated BDT estimates, local reminders, weight history/trends and local persistence; no login, server or internet required.
- **Medical Safety**: Privacy/consent/health safety — offline high-risk screening branch that withholds automated restrictive plans, preserves basic logging, directs to professional review
- **Local Dependencies**: SQLite + Drizzle ORM, pure TypeScript nutrition/planning engine, bundled food data, Expo Notifications
- **Requirements Met**: Complete Bangla/English support, left-to-right layout, VoiceOver/TalkBack compatibility, five primary navigation areas (Home, Planner, Food Log, Grocery, Progress)
- **Validation Items**: Dataset size, redistribution rights for Shaheen et al., encryption implementation, key management

### Milestone 2: Post-MVP Offline Extensions and Optional Online Features
**Capabilities Delivered**: Post-MVP portions of 5–6, 8–10, 12–14, 18 and 23; optional online capabilities 15–17 and 19–20. Each ships after its own safety, privacy and functional validation.
- **Offline Extensions**: Weekly/monthly automated planning, recipes/substitutions, expanded budgeting and activity tracking, couple/family profiles and shared grocery on one device, pantry/stock/leftovers, cached barcode lookup with manual fallback, Ramadan planning and encrypted local backup/export/restore under SR-004.
- **Optional Online Inputs**: AI photo suggestions and Bangla voice logging require opt-in internet; manual logging remains the offline fallback, with confirmed food/portion matches calculated by the local engine.
- **Online Features**: Cloud backup/sync (encrypted, opt-in), wearable integrations (HealthKit/Google Fit, opt-in), AI meal recommendations (cloud AI, local history, user confirmation), market price integration (optional external feeds, unverified availability)
- **Local Dependencies**: Enhanced nutrition engine with BDT cost calculations, multi-profile SQLite schema, Ramadan cultural rules engine

### Milestone 3: Future Commercial Services
**Capabilities Delivered**: 21–22, subject to service, consent and commercial validation; local backup and bundled prices do not depend on this milestone.
- **Pricing Dependencies**: Bundled dated prices are MVP; optional live market updates require validated feeds and do not block offline estimates.
- **Online Services**: Nutritionist dashboard (secure local sharing), healthcare provider integration, research data collection (opt-in), premium subscriptions (opt-in)
- **Offline Security Reference**: Post-MVP local encrypted archives follow SR-004; readable JSON/CSV exports are distinct from restorable archives.
- **Requirements**: Offline restore with invalid archive handling, preservation of existing data after failed restore

### Milestone 4: Validated Scale and Expansion
**Capabilities Delivered**: Regional and enterprise extensions
- **Regional Features**: Local market pricing refinements, regional customization (other South Asian markets)
- **Enterprise Features**: Enterprise wellness programs, insurance integration, hospital partnerships
- **Infrastructure**: Scalable architecture with offline-first design

---

## 16. Product Risks and Assumptions

### Key Assumptions

#### AS-001: Technology
- **Assumption**: React Native + Expo can deliver required performance
- **Risk**: Cross-platform compatibility issues
- **Mitigation**: Extensive testing on target devices

#### AS-002: User Behavior
- **Assumption**: Users will consistently log their food intake
- **Risk**: Low engagement and adoption
- **Mitigation**: Gamification and motivational features

#### AS-003: Cultural Fit
- **Assumption**: Local food database will be comprehensive
- **Risk**: Missing important regional foods
- **Mitigation**: Community contribution system

#### AS-004: Technical Skills
- **Assumption**: Solo developer can deliver full application
- **Risk**: Overambitious feature set
- **Mitigation**: Agile development with MVP focus

### Risk Management

#### RM-001: Development Risks
- **Risk**: Technical debt accumulation
- **Mitigation**: Code review process, automated testing

#### RM-002: Market Risks
- **Risk**: User acquisition challenges
- **Mitigation**: Community engagement, cultural relevance

#### RM-003: Compliance Risks
- **Risk**: Medical disclaimer non-compliance
- **Mitigation**: Legal review, professional consultation

---

## 17. Open Questions for Later Validation

### Technical Questions
1. What is the optimal database structure for the local food database?
2. How can we ensure 100% offline capability for all core features?
3. What is the best approach for nutrition calculation accuracy?
4. How can we optimize app size while maintaining features?
5. What are the performance requirements for different device classes?

### Market Questions
1. How much local market pricing data is available and reliable?
2. What are the cultural barriers to adopting digital nutrition tools?
3. How can we reach rural users with limited internet access?
4. What price points are acceptable in the Bangladeshi market?
5. How can we compete with existing global nutrition apps?

### Product Questions
1. What is the ideal user journey for different demographic groups?
2. How can we ensure cultural relevance across diverse Bangladeshi regions?
3. What are the key motivators for long-term user engagement?
4. How can we balance feature completeness with app simplicity?
5. What success metrics are most important for investor or user validation?

### User Experience Questions
1. How can we make nutrition tracking engaging rather than tedious?
2. What is the optimal frequency for meal planning and grocery generation?
3. How can we handle dietary restrictions within the Bangladeshi context?
4. What are the biggest user friction points in nutrition tracking?
5. How can we integrate with existing health and fitness habits?

---

## 18. Testable Acceptance Criteria for MVP Workflows

### Workflow 1: Daily Food Logging
**As**: User who wants to track daily nutrition
**I want**: To quickly log meals and see nutritional results
**Acceptance Criteria**:
- [ ] User can add a food item manually; record task time in usability testing
- [ ] Nutrition arithmetic matches documented FR-003 fixtures and rounding rules; food composition uncertainty is disclosed
- [ ] User can search bundled foods by name; barcode lookup is Post-MVP Offline
- [ ] Daily totals display clearly
- [ ] User can edit or delete entries
- [ ] Offline mode works without internet connectivity

### Workflow 2: Editable Daily Meal Planning
**As**: User who wants to plan meals
**I want**: To create and edit a daily plan; weekly/monthly automation is Post-MVP Offline
**Acceptance Criteria**:
- [ ] User can select Keto, Low-Carb or Balanced as a pattern, with a separate Calorie Deficit energy goal subject to screening
- [ ] Diet templates and screening rules have qualified professional review; high-risk screening blocks automated restrictive plans while preserving basic logging and offline guidance
- [ ] Plans include local Bangladeshi foods
- [ ] Grocery list is automatically generated
- [ ] User can customize individual meals
- [ ] User can adjust meals and portions; pantry-based automatic adjustments are Post-MVP Offline

### Workflow 3: Grocery Management
**As**: User who manages household shopping
**I want**: To generate shopping lists from my daily plan with offline BDT estimates
**Acceptance Criteria**:
- [ ] Regenerating a list reflects daily plan edits and combines ingredient quantities
- [ ] Offline BDT estimates show price dates, limitations and partial totals for missing prices
- [ ] Grocery list generation works automatically
- [ ] List can be marked as purchased
- [ ] Pantry, expiration and restocking automation remain Post-MVP Offline
- [ ] Works without internet connectivity

### Workflow 4: Progress Tracking
**As**: User who wants to monitor health progress
**I want**: To track and visualize health metrics
**Acceptance Criteria**:
- [ ] User can log weight; expanded measurement/activity tracking is Post-MVP Offline
- [ ] Historical data is stored and displayed
- [ ] Progress charts show trends clearly
- [ ] Goal achievement is tracked
- [ ] User can set weight and health goals
- [ ] Weight history persists after restart; portable export/restore is Post-MVP Offline under SR-004

### Workflow 5: User Onboarding
**As**: New user
**I want**: To set up my profile and dietary preferences
**Acceptance Criteria**:
- [ ] Profile setup takes less than 5 minutes
- [ ] User can select dietary goals (weight loss/gain/maintenance)
- [ ] Food preferences and restrictions are captured
- [ ] User understands all available features
- [ ] One local profile works offline from first use without login, server, download or telemetry
- [ ] User receives welcome guidance and tips

---

## 19. Implementation Navigation Areas

### Primary Mobile Navigation Areas

The application will be organized around 5 primary navigation areas. Descriptions include long-term features; Section 6 governs availability, and deferred features are not MVP dependencies:

#### 1. **Home Dashboard**
- **Purpose**: Central overview and quick access to core features
- **Content**: Daily nutrition summary, weight trends, recent meals, quick actions
- **Key Features**: Daily calorie counter, progress indicators, notification badges
- **User Journey**: Entry point for all major workflows

#### 2. **Planner**
- **Purpose**: Meal planning and scheduling
- **Content**: Daily/weekly meal plans, recipe browser, nutrition analysis
- **Key Features**: Diet-specific templates, grocery integration, nutritional balancing
- **User Journey**: Planning and preparation workflow

#### 3. **Food Log**
- **Purpose**: Food tracking and nutrition monitoring
- **Content**: Meal entries, barcode scanning, nutrition details, historical data
- **Key Features**: Quick entry options, AI assistance, nutritional analysis
- **User Journey**: Daily tracking and monitoring workflow

#### 4. **Grocery**
- **Purpose**: Inventory management and shopping
- **Content**: Pantry tracking, shopping lists, market prices, purchase history
- **Key Features**: Automatic list generation, price comparison, expiration tracking
- **User Journey**: Shopping and inventory management workflow

#### 5. **Progress**
- **Purpose**: Health metrics and goal tracking
- **Content**: Weight charts, body measurements, activity logs, health insights
- **Key Features**: Goal setting, achievement celebration, health recommendations
- **User Journey**: Monitoring and improvement workflow

---

## 20. Implementation Phases

### Milestone 1: Offline Foundation and Verified Data
**Completion**: Section 14 Milestone 1, plus architecture verification of encryption/key management under Section 10.
- Technical architecture and local database design (React Native + Expo + TypeScript); one local profile without authentication requirements.
- Audit bundled food records and redistribution rights; dataset size remains unverified until audit. Shaheen et al. (2013) is a candidate source only.
- Implement local nutrition arithmetic with FR-003 fixtures and rounding rules; obtain qualified review of templates and screening rules before public release.

### Milestone 2: Daily Tracking, Planning and Grocery Flow
**Completion**: Section 14 Milestone 2.
- Manual logging and food search; editable daily plans with Keto, Low-Carb and Balanced patterns plus a separate Calorie Deficit goal, subject to screening.
- Automatic groceries, offline BDT estimates and weight history/trends; no pantry or barcode dependency.

### Milestone 3: Offline Release Readiness
**Completion**: Section 14 Milestone 3; no fixed calendar deadline.
- Bangla/English localization with Bangla LTR layout, native VoiceOver/TalkBack, dynamic text and accessible controls before first public release.
- Local reminders with permission-denial handling; persistence, airplane-mode workflows, high-risk restrictions and bundled professional guidance.
- Security/privacy review, release-build device measurements against provisional performance benchmarks, and user acceptance testing.

### Milestone 4: Post-MVP Delivery
**Completion**: Feature-specific validation under Sections 6, 10–11 and 15; independent of MVP release.
- Offline: weekly/monthly automation, recipes/substitutions, family/shared groceries on one device, advanced pantry/leftovers, cached barcode lookup, Ramadan planning, expanded budgeting/progress, and encrypted local backup/export/restore.
- Optional online: AI photo/meal suggestions, Bangla voice logging, cloud backup/cross-device sync, wearables and live market feeds, with explicit consent and offline core fallback.
- Future commercial services: nutritionist portal, subscriptions and related expansion after their own validation.

---

## Appendix: Project Resources

### Document Control
- **Document**: PRD-001, Version 1.0
- **Date**: November 12, 2026
- **Approver**: TBD
- **Review Cycle**: Monthly

### References
1. Shaheen et al., *Food Composition Table for Bangladesh*, University of Dhaka, 2013 - Candidate nutrition source; licensing and redistribution rights pending verification
2. Bangladesh Food Composition Table - Ministry of Health
3. WHO Dietary Guidelines
4. React Native Documentation
5. SQLite Documentation
6. TypeScript Best Practices

### Contact Information
- **Product Owner**: TBD
- **Technical Lead**: TBD
- **Product Manager**: TBD
- **Engineering Team**: TBD

---

*Document created as part of DietMate BD product development initiative. This document is subject to revision based on user feedback, market research, and technical validation.*

---

**End of Document**

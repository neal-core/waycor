# Product Requirements Document: Waycor
**Course:** BU-COS209 Innovation in Web Design and Development  
**Team:** Quantum (Team 7)

## 1. Product Overview
**Waycor** is a campus directory and pedestrian walking guide built for newly admitted Babcock University students. It maps campus abbreviations and office names to their official buildings, provides step-by-step walking directions from widely recognized Primary Anchors, includes exact entrance descriptions and photos where useful, and uses anonymous student reporting with administrator verification to keep location data accurate.

## 2. Problem Statement
For many 100L students at Babcock, finding buildings and offices is a significant challenge. Directions are often given using abbreviations such as "meet me at BBS or WRA" or vague landmarks such as "near Babrite." A new student may not know what these abbreviations or landmarks mean, making it difficult to ask for or follow directions.
Most first-year students know only the Amphitheatre, the Cafeteria, their own hall, and a few other major locations. They may also know the office they need but not the building where it is located.
Based on team-member experience and interviews with other students, it took approximately 5–8 weeks for students to learn the basic campus abbreviations. Students reported arriving late to or missing approximately 3–5 classes and events in their first semester because they could not find the venue.
Venue changes caused by power issues or use of a location for another event are often communicated through WhatsApp class groups. Students who are not in the relevant groups may not receive the update until after the change takes effect.

## 3. Business Objectives
- **Reduce 100L navigation friction:** Cut down the time it takes new students to learn campus buildings and abbreviations (currently 5–8 weeks) and reduce late arrivals or missed classes caused by venue confusion.
- **Create a single trusted source of campus location data:** Replace unreliable workarounds (vague verbal directions, outdated Google Maps pins, and buried WhatsApp messages) with verified, campus-specific information.
- **Keep data accurate with low maintenance overhead:** Use anonymous student flagging paired with a prioritized administrator verification queue so moved offices and temporary venue notices stay up to date without manual daily audits.
- **Drive early-semester adoption:** Establish Waycor as a go-to reference during 100L orientation and the first four weeks of the semester.

## 4. Research Methodology and Findings

### 4.1 Research Methodology
The interviews were conducted over a single day and were mostly held in person. Five Babcock students were approached randomly, with no selection criteria other than their year level. The sample consisted of two 100L students and three 200L students.
Follow-up interviews were also conducted with some participants using targeted questions to confirm details such as:
- Campus landmarks that 100L students recognize
- How frequently lecture venues or offices change
- What would encourage students to report incorrect information
- How administrators should verify student reports before updating the system

### 4.2 Hard-to-Find Locations and Abbreviations
- **SCLT** – Silvanus Chioma Lecture Hall
- **CIT** – Chioma Ikeonne Theatre
- **BBS** – Babcock Business School
- **WRA** – Wilfred Riley Auditorium
- **SAT** – Science and Technology Building
- **Other high-friction locations:** Senate Building, Stadium, and Clinic

### 4.3 Real Failure Stories

**Case 1: Amphitheatre and Clinic**
Students have been directed to the Clinic as being "just by the Amphitheatre." The two small doors leading to the Clinic are easy to overlook, and there are few or no signs identifying them. As a result, students walk around the area without reaching the correct entrance.

**Case 2: Google Maps Mismatch**
Students sometimes rely on Google Maps when they are unfamiliar with a building or venue. In some cases, the route is unnecessarily long or does not match the campus layout. A map pin may also point to an earlier location for a venue that has moved.

## 5. Target Users
- **Primary users – 100L and new students:** Students who need to find lecture halls, administrative offices, event venues, and campus facilities without arriving late or missing an event. Their main pain points include unfamiliar abbreviations and landmarks, vague directions, outdated map pins, and limited knowledge of campus locations.
- **Secondary users – verified administrators:** Trusted campus administrators who receive reports of office relocations and temporary venue changes. They review reports, confirm changes using reliable sources, and update location information in the system.

The secondary users may include verified porters or other campus staff if they are granted administrator access.

## 6. Stakeholders

| Stakeholder | Role / Involvement | How They Are Affected |
| --- | --- | --- |
| **100L / New Students** | Primary end users | Rely on Waycor to find lecture halls, offices, and facilities without getting lost or arriving late |
| **Verified Administrators (Course Reps & Moderators)** | Secondary users / content maintainers | Review prioritized reports, verify changes, and publish location or route updates |
| **Hostel Porters & Campus Security** | Verification sources and potential admins | Fewer repetitive direction requests; act as trusted sources for confirming office or venue changes |
| **Academic & Facilities Staff** | Indirect stakeholders | Experience fewer late students and provide confirmation when lecture venues or offices relocate |
| **Student Affairs / Orientation Coordinators** | Distribution partners | Can share Waycor during fresher orientation to ease onboarding |
| **Team Quantum (Development Team)** | Product builders | Responsible for designing, building, and maintaining the MVP within course constraints |

---

## 7. Existing Solutions and Why They Fall Short

| Current workaround | How students use it | Why it fails |
| --- | --- | --- |
| Asking porters, security personnel, or other students | Students stop passersby and ask for directions to a hall or office | Directions may be vague or use abbreviations and landmarks that new students do not know |
| Following classmates | Students accompany classmates to the same destination | This depends on the classmate knowing the campus and is not useful when the classmate is also unfamiliar with the route |
| Google Maps | Students search for a building or venue and follow the suggested route | The route may direct students along unnecessary detours, omit campus shortcuts or buildings, or lead to a previous location |
| WhatsApp class groups | Students check class chats or ask classmates about venue updates | Messages may lack clear walking directions and may not reach students who are not members of the relevant groups |

---

## 8. Proposed Solution, Scope, and Priorities

Waycor solves campus navigation for 100L students by combining an alias-aware building/office directory with curated, landmark-based pedestrian routes and entrance notes. Rather than relying on static data that quickly goes stale, Waycor pairs zero-login student reporting with a verified administrator review workflow.

### 8.1 Primary Anchors
A **Primary Anchor** is a recognizable campus location that most 100L students already know. The MVP will use locations such as the Amphitheatre and selected student halls as route starting points.

### 8.2 Scope and Priorities

| Priority | Feature | Release Target | Rationale |
| --- | --- | --- | --- |
| **P0 (Must-Have)** | Alias and office-to-building search | MVP (v1) | Directly solves the 5–8 week abbreviation barrier |
| **P0 (Must-Have)** | Landmark-based walking directions from Primary Anchors | MVP (v1) | Solves vague verbal directions and Google Maps detours |
| **P0 (Must-Have)** | Entrance and door-level notes (+ optional photos) | MVP (v1) | Prevents walking in circles at hard-to-spot entrances (e.g., Clinic) |
| **P0 (Must-Have)** | Administrator relocation, temporary notice, and verification updates | MVP (v1) | Prevents location data from going stale |
| **P1 (Should-Have)** | Anonymous user reporting with prioritized moderation queue | MVP (v1) | Enables scalable accuracy updates with zero login friction |
| **P2 (Deferred / Out of Scope)** | Task-to-location search, offline mode, live GPS, indoor floor maps, user accounts/reviews, automatic route generation | v2+ | High data/engineering complexity; not required to validate core campus navigation |

### 8.3 In Scope for the MVP
- **Alias and Office-to-Building Search:** Search using campus abbreviations such as `SCLT`, `CIT`, `BBS`, `WRA`, and `SAT`, or using an office name, and return the official building and, for offices, the parent building.
- **Landmark-Based Walking Directions:** Display ordered, pedestrian steps from a selected Primary Anchor to the destination. The result will include an estimated walking time.
- **Entrance and Door-Level Notes:** Attach a text description and optional reference photo to each location so students know which entrance or door to use.
- **Administrator Relocation and Status Updates:** Allow verified administrators to update moved offices, add temporary venue notices, and refresh a visible Last Verified date.
- **Anonymous Reporting:** Allow students to flag an outdated location or incorrect direction without logging in. A report may include a short description and an optional photo.

### 8.4 Out of Scope for the MVP
- **Task-to-location search:** Mapping common tasks to specific offices is deferred because it requires significant upfront data entry.
- **Offline mode:** Full text and image caching is deferred until the core directory is stable.
- **Live turn-by-turn GPS:** The MVP will use landmark-based directions because GPS accuracy and pedestrian access may vary between buildings.
- **Indoor floor-by-floor maps:** Room-level navigation is deferred until building-level navigation is established.
- **User accounts and reviews:** The MVP will not require accounts or support social reviews.
- **Automatic route generation:** Routes must be reviewed and verified before publication.

## 9. User Stories

### 100L / New Students
- **US-1:** As a 100L student, I want to search using a campus abbreviation (like `BBS`, `WRA`, or `SCLT`) or an office name so that I can find the official building without already knowing what the abbreviation stands for.
- **US-2:** As a 100L student, I want step-by-step walking directions starting from a Primary Anchor I already know (such as the Amphitheatre or my hall) so that I do not get lost following unfamiliar landmarks or long road routes.
- **US-3:** As a 100L student, I want to see exact entrance notes and an optional photo of the door so that I do not walk in circles once I reach the right building.
- **US-4:** As a 100L student, I want to see a **Last Verified** date and any temporary venue notices on a location page so that I know whether I can trust the information.
- **US-5:** As a 100L student, I want to report a moved office, wrong direction, or unclear entrance in under 3 minutes without creating an account so that outdated information gets fixed quickly.

### Verified Administrators
- **US-6:** As a verified administrator, I want incoming student reports to be automatically prioritized when they include a photo or multiple independent submissions so that I can review high-confidence issues first.
- **US-7:** As a verified administrator, I want to edit location details, routes, and temporary notices—and record my verification source—so that public information stays accurate and auditable.
- **US-8:** As a verified administrator, I want to reject spam reports or remove photos containing sensitive information so that public pages remain safe and reliable.

## 10. Functional Requirements
- **FR-1 (Alias & Office Search):** The system must allow case-insensitive search by official building name, campus abbreviation/alias (`SCLT`, `CIT`, `BBS`, `WRA`, `SAT`), or office name, and return the matching location along with its parent building when applicable.
- **FR-2 (Search Fallback):** When no exact match is found, the system must return close spelling suggestions, related aliases, or a clear "no result found" state.
- **FR-3 (Location Details):** Each location page must display the official name, parent building (if an office), entrance note, optional compressed entrance photo, current status (including temporary venue notices), and Last Verified date.
- **FR-4 (Anchor-Based Directions):** The system must allow users to select a Primary Anchor and retrieve ordered, verified pedestrian walking steps and an estimated walking time to the chosen destination.
- **FR-5 (Anonymous Reporting):** The system must allow any user to submit an issue report (issue type, optional description up to 500 characters, optional photo up to 5 MB) without logging in, and return a submission confirmation.
- **FR-6 (Flagging & Queue Prioritization):** The system must store submitted reports as `Pending`, never auto-publish unverified edits, mark locations with repeated or high-priority reports as `Update Under Review`, and sort the administrator queue to surface reports with photos or three or more independent submissions first.
- **FR-7 (Admin Verification & Publishing):** Verified administrators must be able to review reports, update `Location` or `LandmarkRoute` records, record a verification source, set review states (`Pending`, `Needs More Information`, `Under Review`, `Verified`, `Rejected`), and automatically refresh `last_verified_at`.


## 11. Core User Flows

### 11.1 Flow 1: Search by Abbreviation or Office Name

**Preconditions:**
- Location and alias records are available.
- The student has internet access.

**Main steps:**
1. The student enters an abbreviation or office name into the search bar.
2. The system searches aliases and location records.
3. The system displays the official name, parent building when applicable, entrance notes, entrance photo, and Last Verified date.

**Success outcome:** The correct location is returned on the first search attempt.
**Failure outcome:** If no exact match exists, the system shows spelling suggestions, known aliases, or a clear "no result found" response. Search will be case-insensitive and will support common abbreviations and minor misspellings.

### 11.2 Flow 2: Get Landmark-Based Directions

**Preconditions:**
- The selected location has at least one verified route.
- A primary anchor is available.

**Main steps:**
1. The student opens a location page and selects **Get Directions**.
2. The student selects a Primary Anchor.
3. The system displays ordered walking steps and an estimated walking time.

**Success outcome:** The student follows the route to the correct entrance.
**Failure outcome:** If no route is available, the system explains the issue and offers the nearest available Primary Anchor or a reporting option.

### 11.3 Flow 3: Report Incorrect or Outdated Information

**Preconditions:**
- The student has viewed a location page.
- The student does not need to create an account.

**Main steps:**
1. The student selects **Report Wrong Info**.
2. The student chooses an issue type, such as moved office, wrong directions, or unclear entrance.
3. The student optionally enters a short description and uploads an optional photo.
4. The student submits the report.

**Success outcome:** The report is saved as pending and the student receives a submission confirmation. Repeated or high-priority reports mark the location as **Update Under Review**; they do not change public location data automatically.
**Failure outcome:** If submission fails, the system retains the entered text and photo when possible and allows the student to retry.

### 11.4 Flow 4: Verify and Update Location Information

**Preconditions:**
- The user is a verified administrator.
- A report is available in the moderation queue.

**Main steps:**
1. The administrator opens the moderation queue.
2. The system places reports with photos or multiple independent submissions near the top of the queue.
3. The administrator confirms the reported change using a reliable source, such as facilities staff, security personnel, porters, academic staff, or another verified administrator.
4. The administrator updates the location or route, records the verification source, and marks the report as verified.
5. The system updates the Last Verified date and public location status.

**Review states:** Pending, Needs More Information, Under Review, Verified, and Rejected.

## 12. Acceptance Criteria
- **Search (US-1 / FR-1, FR-2):**
  - Searching `wra`, `WRA`, or `Wilfred Riley` returns Wilfred Riley Auditorium with its entrance note and Last Verified date.
  - Searching an office name displays both the office details and its parent building.
  - Searching a misspelled or unknown term displays spelling suggestions or a clear "no result found" message without crashing.
- **Directions (US-2, US-3 / FR-3, FR-4):**
  - Selecting a Primary Anchor returns an ordered list of pedestrian steps, estimated walking time, and the route's Last Verified date.
  - If no route exists from the selected anchor, the system notifies the user and offers the nearest available Primary Anchor or a reporting option.
- **Anonymous Reporting (US-5 / FR-5, FR-6):**
  - A student can submit a report without logging in within 3 minutes.
  - Submissions exceeding 500 characters or 5 MB photo size are rejected with a clear validation message.
  - Submitting a report saves it as `Pending` and does **not** alter public location data immediately.
  - Rapid repeated submissions from the same source are rate-limited.
- **Admin Moderation (US-6, US-7, US-8 / FR-6, FR-7):**
  - Reports with photos or three or more independent submissions appear above standard text-only reports in the moderation queue.
  - An administrator cannot publish a verified update without recording a verification source.
  - Approving a report updates the public location/route and refreshes `last_verified_at` immediately.

## 13. Conceptual Data Model

| Entity | Key attributes | Purpose |
| --- | --- | --- |
| Location | id, official_name, category, parent_location_id, is_primary_anchor, entrance_note, entrance_photo_url, last_verified_at, last_verified_by, verification_source, status | Stores buildings, lecture halls, offices, facilities, and landmarks |
| Alias | id, location_id, alias_text | Maps abbreviations and nicknames to an official location |
| LandmarkRoute | id, start_anchor_id, destination_location_id, steps, estimated_walk_minutes, status, last_verified_at, last_verified_by | Stores a reviewed walking route between a primary anchor and a destination |
| UpdateReport | id, location_id, issue_type, description, photo_url, submitted_at, status, reviewed_by, resolved_at, rejection_reason | Logs student reports and administrator review results |
| Admin | id, name, role, credentials, is_active | Stores verified administrators and their permissions |

### 13.1 Key Relationships
- **Office parent location:** A `Location` can reference another `Location` through `parent_location_id`, allowing an office to identify the building in which it is located.
- **Alias to location:** Multiple aliases may reference one location.
- **Anchor to destination:** A `LandmarkRoute` connects one location marked as `is_primary_anchor = true` to a destination location.
- **Location to reports:** A location may have multiple update reports.
- **Administrator to reports:** An administrator may review and resolve multiple reports.

## 14. Non-Functional Requirements
- **Zero-friction reporting:** Report submission must require no login and must take no more than 3 minutes for a student using a standard phone.
- **Anonymous report abuse controls:** The system must allow anonymous reports but must limit rapid repeated submissions and retain only the minimum information required for moderation.
- **Data freshness and trust:** Public locations must display a Last Verified date. A location must show when it was most recently reviewed, and the administrator queue must prioritize reports with photos or three or more independent submissions.
- **Search tolerance:** Search must be case-insensitive and handle common abbreviations, known nicknames, and minor spelling mistakes.
- **Low-bandwidth performance:** Pages must prioritize text and load text content within 3 seconds on a slow 3G-equivalent connection. Entrance photos must be compressed and optional, with a clear text alternative.
- **Image and description limits:** Photos must use supported mobile image formats and be limited to 5 MB. Report descriptions must be limited to 500 characters.
- **Privacy:** Public location pages must not expose reporter identity or unnecessary personal information.

## 15. Success Metrics, Risks, and Mitigations

### 15.1 Success Metrics
- **Search success:** At least 80% of test searches return the correct building or office on the first attempt.
- **Search zero-result rate:** Fewer than 5% of tested campus searches return no usable result.
- **Navigation accuracy:** At least 85% of tested landmark routes lead to the correct destination in a small pilot test.
- **Reporting completion:** At least 90% of test report submissions are completed in under 3 minutes.
- **Reporting response:** High-priority reports receive an initial administrator review within 6 hours.
- **Report resolution:** 80% of reports are resolved within 24 hours during the pilot period.
- **Reduced navigation problems:** At least a 25% reduction in reported late arrivals or missed classes/events related to venue confusion among participating 100L students during a four-week pilot.

### 15.2 Risks and Mitigations
- **Fake or spam anonymous reports:** No edit goes live automatically. Only verified administrators may publish changes, and the queue prioritizes photos and multiple independent submissions. Rapid repeated submissions will be rate-limited.
- **Incorrect or disputed campus information:** Updates must include a verification source and reviewer before publication.
- **Low adoption by 100L students:** Promote Waycor during orientation and through 100L departmental WhatsApp groups.
- **Administrator bottleneck:** Assign multiple verified administrators across departments and escalate unresolved high-priority reports.
- **Unsafe or inaccessible pedestrian routes:** Administrators must verify pedestrian access and avoid suggesting restricted, unsafe, or inaccessible routes.
- **Privacy concerns:** Require no account for reporting and do not publish reporter identity or personal information.
- **Photos containing sensitive information:** Administrators must be allowed to reject or remove photographs that expose private areas or personal data.
- **Outdated routes:** Routes must show their own Last Verified date and status, not only the destination's verification date.

## 16. Assumptions and Open Questions

### 16.1 Assumptions
- Most 100L students have access to a smartphone with at least slow 3G mobile data or campus Wi-Fi when navigating campus.
- Course representatives, hostel porters, or designated student moderators are willing to verify and update location changes when notified.
- A curated set of Primary Anchors (such as the Amphitheatre, Main Gate, and major student halls) is recognizable enough to serve as starting points for most 100L students.
- Pedestrian shortcuts mapped in the MVP remain open and accessible during regular school hours.

### 16.2 Open Questions
- **Initial data seeding:** Who will physically walk and verify the initial set of buildings, entrance photos, and Primary Anchor routes before the pilot launch?
- **Admin onboarding and permissions:** What approval process will be used to verify and onboard course reps or porters as administrators?
- **Temporary venue notices:** How long should a temporary venue notice (e.g., due to power issues or an event clash) stay visible before expiring automatically?
- **Photo moderation policy:** Are there specific campus buildings or administrative areas where exterior/entrance photography is restricted by school security?
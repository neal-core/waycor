# Product Requirements Document: Waycor

**Course:** BU-COS209 Innovation in Web Design and Development  
**Team:** Quantum (Team 7)

## 1. Problem Statement

For many 100L students at Babcock, finding buildings and offices is a significant challenge. Directions are often given using abbreviations such as "meet me at BBS or WRA" or vague landmarks such as "near Babrite." A new student may not know what these abbreviations or landmarks mean, making it difficult to ask for or follow directions.

Most first-year students know only the Main Gate, the Amphitheatre, their own hall, and a few other major locations. They may also know the office they need but not the building where it is located.

Based on team-member experience and interviews with other students, it took approximately 5–8 weeks for students to learn the basic campus abbreviations. Students reported arriving late to or missing approximately 3–5 classes and events in their first semester because they could not find the venue.

Venue changes caused by power issues or use of a location for another event are often communicated through WhatsApp class groups. Students who are not in the relevant groups may not receive the update until after the change takes effect.

## 2. Research Methodology and Findings

### 2.1 Research Methodology

The interviews were conducted over a single day and were mostly held in person. I approached five Babcock students randomly, with no selection criteria other than their year level. The sample consisted of two 100L students and three 200L students.

I also followed up with some participants using targeted questions to confirm details such as:

- Campus landmarks that 100L students recognize
- How frequently lecture venues or offices change
- What would encourage students to report incorrect information
- How administrators should verify student reports before updating the system

### 2.2 Hard-to-Find Locations and Abbreviations

- **SCLT** – Silvanus Chioma Lecture Hall
- **CIT** – Chioma Ikeonne Theatre
- **BBS** – Babcock Business School
- **WRA** – Wilfred Riley Auditorium
- **SAT** – Science and Technology Building
- **Other high-friction locations:** Senate Building, Stadium, and Clinic

### 2.3 Real Failure Stories

**Case 1: Amphitheatre and Clinic**

Students have been directed to the Clinic as being "just by the Amphitheatre." The two small doors leading to the Clinic are easy to overlook, and there are few or no signs identifying them. As a result, students walk around the area without reaching the correct entrance.

**Case 2: Google Maps Mismatch**

Students sometimes rely on Google Maps when they are unfamiliar with a building or venue. In some cases, the route is unnecessarily long or does not match the campus layout. A map pin may also point to an earlier location for a venue that has moved.

## 3. Target Users

- **Primary users – 100L and new students:** Students who need to find lecture halls, administrative offices, event venues, and campus facilities without arriving late or missing an event. Their main pain points include unfamiliar abbreviations and landmarks, vague directions, outdated map pins, and limited knowledge of campus locations.
- **Secondary users – verified administrators:** Trusted campus administrators who receive reports of office relocations and temporary venue changes. They review reports, confirm changes using reliable sources, and update location information in the system.

The secondary users may include verified porters or other campus staff if they are granted administrator access.

## 4. Existing Solutions and Why They Fall Short

| Current workaround | How students use it | Why it fails |
| --- | --- | --- |
| Asking porters, security personnel, or other students | Students stop passersby and ask for directions to a hall or office | Directions may be vague or use abbreviations and landmarks that new students do not know |
| Following classmates | Students accompany classmates to the same destination | This depends on the classmate knowing the campus and is not useful when the classmate is also unfamiliar with the route |
| Google Maps | Students search for a building or venue and follow the suggested route | The route may direct students along unnecessary detours, omit campus shortcuts or buildings, or lead to a previous location |
| WhatsApp class groups | Students check class chats or ask classmates about venue updates | Messages may lack clear walking directions and may not reach students who are not members of the relevant groups |

## 5. Proposed Solution and MVP Scope

Waycor is a campus directory and pedestrian walking guide designed to help newly admitted Babcock students find classes, offices, event halls, and other facilities without relying on vague directions or outdated maps.

The application will map campus abbreviations and office names to their official buildings, provide step-by-step walking directions from widely recognized primary anchors, and include entrance descriptions and photos where useful. Anonymous reports will allow students to flag outdated or incorrect information for administrator review.

### 5.1 Primary Anchors

A **Primary Anchor** is a recognizable campus location that most 100L students already know. The MVP will use locations such as the Amphitheatre and selected student halls as route starting points.

### 5.2 In Scope for the MVP

- **Alias and Office-to-Building Search:** Search using campus abbreviations such as `SCLT`, `CIT`, `BBS`, `WRA`, and `SAT`, or using an office name, and return the official building and, for offices, the parent building.
- **Landmark-Based Walking Directions:** Display ordered, pedestrian steps from a selected Primary Anchor to the destination. The result will include an estimated walking time.
- **Entrance and Door-Level Notes:** Attach a text description and optional reference photo to each location so students know which entrance or door to use.
- **Administrator Relocation and Status Updates:** Allow verified administrators to update moved offices, add temporary venue notices, and refresh a visible Last Verified date.
- **Anonymous Reporting:** Allow students to flag an outdated location or incorrect direction without logging in. A report may include a short description and an optional photo.

### 5.3 Out of Scope for the MVP

- **Task-to-location search:** Mapping common tasks to specific offices is deferred because it requires significant upfront data entry.
- **Offline mode:** Full text and image caching is deferred until the core directory is stable.
- **Live turn-by-turn GPS:** The MVP will use landmark-based directions because GPS accuracy and pedestrian access may vary between buildings.
- **Indoor floor-by-floor maps:** Room-level navigation is deferred until building-level navigation is established.
- **User accounts and reviews:** The MVP will not require accounts or support social reviews.
- **Automatic route generation:** Routes must be reviewed and verified before publication.

## 6. Core User Flows

### 6.1 Flow 1: Search by Abbreviation or Office Name

**Preconditions:**

- Location and alias records are available.
- The student has internet access.

**Main steps:**

1. The student enters an abbreviation or office name into the search bar.
2. The system searches aliases and location records.
3. The system displays the official name, parent building when applicable, entrance notes, entrance photo, and Last Verified date.

**Success outcome:** The correct location is returned on the first search attempt.

**Failure outcome:** If no exact match exists, the system shows spelling suggestions, known aliases, or a clear “no result found” response. Search will be case-insensitive and will support common abbreviations and minor misspellings.

### 6.2 Flow 2: Get Landmark-Based Directions

**Preconditions:**

- The selected location has at least one verified route.
- A primary anchor is available.

**Main steps:**

1. The student opens a location page and selects **Get Directions**.
2. The student selects a Primary Anchor.
3. The system displays ordered walking steps and an estimated walking time.

**Success outcome:** The student follows the route to the correct entrance.

**Failure outcome:** If no route is available, the system explains the issue and offers the nearest available Primary Anchor or a reporting option.

### 6.3 Flow 3: Report Incorrect or Outdated Information

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

### 6.4 Flow 4: Verify and Update Location Information

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

## 7. Conceptual Data Model

| Entity | Key attributes | Purpose |
| --- | --- | --- |
| Location | id, official_name, category, parent_location_id, is_primary_anchor, entrance_note, entrance_photo_url, last_verified_at, last_verified_by, verification_source, status | Stores buildings, lecture halls, offices, facilities, and landmarks |
| Alias | id, location_id, alias_text | Maps abbreviations and nicknames to an official location |
| LandmarkRoute | id, start_anchor_id, destination_location_id, steps, estimated_walk_minutes, status, last_verified_at, last_verified_by | Stores a reviewed walking route between a primary anchor and a destination |
| UpdateReport | id, location_id, issue_type, description, photo_url, submitted_at, status, reviewed_by, resolved_at, rejection_reason | Logs student reports and administrator review results |
| Admin | id, name, role, credentials, is_active | Stores verified administrators and their permissions |

### 7.1 Key Relationships

- **Office parent location:** A `Location` can reference another `Location` through `parent_location_id`, allowing an office to identify the building in which it is located.
- **Alias to location:** Multiple aliases may reference one location.
- **Anchor to destination:** A `LandmarkRoute` connects one location marked as `is_primary_anchor = true` to a destination location.
- **Location to reports:** A location may have multiple update reports.
- **Administrator to reports:** An administrator may review and resolve multiple reports.

## 8. Non-Functional Requirements

- **Zero-friction reporting:** Report submission must require no login and must take no more than 3 minutes for a student using a standard phone.
- **Anonymous report abuse controls:** The system must allow anonymous reports but must limit rapid repeated submissions and retain only the minimum information required for moderation.
- **Data freshness and trust:** Public locations must display a Last Verified date. A location must show when it was most recently reviewed, and the administrator queue must prioritize reports with photos or three or more independent submissions.
- **Search tolerance:** Search must be case-insensitive and handle common abbreviations, known nicknames, and minor spelling mistakes.
- **Low-bandwidth performance:** Pages must prioritize text and load text content within 3 seconds on a slow 3G-equivalent connection. Entrance photos must be compressed and optional, with a clear text alternative.
- **Image and description limits:** Photos must use supported mobile image formats and be limited to 5 MB. Report descriptions must be limited to 500 characters.
- **Privacy:** Public location pages must not expose reporter identity or unnecessary personal information.

## 9. Success Metrics

### 9.1 Success Metrics

- **Search success:** At least 80% of test searches return the correct building or office on the first attempt.
- **Search zero-result rate:** Fewer than 5% of tested campus searches return no usable result.
- **Navigation accuracy:** At least 85% of tested landmark routes lead to the correct destination in a small pilot test.
- **Reporting completion:** At least 90% of test report submissions are completed in under 3 minutes.
- **Reporting response:** High-priority reports receive an initial administrator review within 6 hours.
- **Report resolution:** 80% of reports are resolved within 24 hours during the pilot period.
- **Reduced navigation problems:** At least a 25% reduction in reported late arrivals or missed classes/events related to venue confusion among participating 100L students during a four-week pilot.

### 9.2 Risks and Mitigations

- **Fake or spam anonymous reports:** No edit goes live automatically. Only verified administrators may publish changes, and the queue prioritizes photos and multiple independent submissions. Rapid repeated submissions will be rate-limited.
- **Incorrect or disputed campus information:** Updates must include a verification source and reviewer before publication.
- **Low adoption by 100L students:** Promote Waycor during orientation and through 100L departmental WhatsApp groups.
- **Administrator bottleneck:** Assign multiple verified administrators across departments and escalate unresolved high-priority reports.
- **Unsafe or inaccessible pedestrian routes:** Administrators must verify pedestrian access and avoid suggesting restricted, unsafe, or inaccessible routes.
- **Privacy concerns:** Require no account for reporting and do not publish reporter identity or personal information.
- **Photos containing sensitive information:** Administrators must be allowed to reject or remove photographs that expose private areas or personal data.
- **Outdated routes:** Routes must show their own Last Verified date and status, not only the destination's verification date.

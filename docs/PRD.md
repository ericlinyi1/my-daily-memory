# My Daily Memory - Product Requirements Document (PRD)

**Version:** 1.0  
**Last Updated:** April 26, 2026  
**Status:** Draft

---

## 1. Background

### 1.1 Context

Many users want a simple way to capture daily moments and emotions, but existing solutions often feel:

- **Too heavy** (too many steps, distracting UI)
- **Hard to review** (no structure, weak search)
- **Not private enough** (fear of data exposure)
- **Difficult to maintain as a habit** (no gentle routine support)

### 1.2 Goals

1. Enable users to create a meaningful daily entry in **under 30 seconds**
2. Help users review and understand **mood patterns over time**
3. Provide a **privacy-first experience** that builds trust and retention

### 1.3 Non-goals (v1.0)

- ❌ Social/community features
- ❌ Cross-device sync via accounts (can be v1.1+)
- ❌ AI writing/summaries (can be future iteration)

---

## 2. Product Positioning & Scope

### 2.1 Positioning

> **My Daily Memory** is a privacy-first, lightweight journaling and mood tracking app designed for fast daily entries, easy recall, and simple habit-building.

### 2.2 In-scope (v1.0)

- ✅ Create/edit/delete journal entries (text + mood + tags + date)
- ✅ Browse entries via list and calendar
- ✅ Search by keyword and filter by tag
- ✅ Optional reminders (notifications)
- ✅ Optional app lock (Face ID / Touch ID / passcode)
- ✅ App Store publishing essentials (privacy disclosures, permission messaging)

---

## 3. Target Users & Use Cases

### 3.1 Target users

| Segment | Age Range | Characteristics |
|---------|-----------|-----------------|
| **Light journalers** | 18–35 | Quick notes, occasional review |
| **Mood trackers** | 18–40 | Detect emotional patterns and triggers |
| **Habitual writers** | 25–45 | Organization, search, strong privacy |

### 3.2 Core scenarios

1. **Before bed:** Write a short reflection + pick a mood
2. **During stress:** Quickly log feelings and causes
3. **Weekly review:** Scan calendar and trends to reflect
4. **Memory lookup:** Search past entries by keyword/tag

---

## 4. Success Metrics (for validation)

| Metric | Target |
|--------|--------|
| First-day "created first entry" conversion | ≥ TBD% |
| Median time to complete an entry | ≤ TBD seconds |
| D7 retention | ≥ TBD% |
| Search usage within 7 days | ≥ TBD% |

---

## 5. Functional Requirements (v1.0)

### 5.1 Information Architecture

```
Home / New Entry
├── Calendar (Review)
├── Search
└── Settings
```

### 5.2 Requirements List

#### **FR-01: Create Entry** (P0)

**Description:**
- User can create a journal entry with:
  - Date (default: today; editable)
  - Text content (required or optional)
  - Mood (e.g., 1–5 scale or labeled levels)
  - Tags (optional; multi-select)
- User can save and see the entry immediately in list/calendar

**Acceptance Criteria:**
- ✅ Reach "New Entry" in ≤ 2 taps from app launch
- ✅ Saved entry persists after app restart
- ✅ Empty/error states are clear and non-blocking

---

#### **FR-02: Entries List** (P0)

**Description:**
- Show entries in reverse chronological order
- Tap to open entry details
- Empty state prompts user to create the first entry

**Acceptance Criteria:**
- ✅ Smooth scrolling with typical datasets (see performance requirements)
- ✅ Clear date grouping (optional)

---

#### **FR-03: Calendar View** (P0)

**Description:**
- Monthly calendar view showing days with entries
- Tap a day to view that day's entries or details
- Optional mood indicator on calendar cells

**Acceptance Criteria:**
- ✅ Calendar correctly reflects existing entries
- ✅ Navigation between months is responsive

---

#### **FR-04: Entry Detail + Edit/Delete** (P0)

**Description:**
- View entry detail (date, mood, tags, text)
- Edit and save changes
- Delete requires confirmation

**Acceptance Criteria:**
- ✅ Edit updates reflect immediately in list/calendar
- ✅ Delete is not accidental (confirmation modal)

---

#### **FR-05: Tags** (P1)

**Description:**
- Create/rename/delete tags
- Assign tags during entry creation/editing
- Filter entries by tag

**Acceptance Criteria:**
- ✅ Tag changes apply consistently across all views
- ✅ Filtering is fast and reversible

---

#### **FR-06: Search** (P1)

**Description:**
- Keyword search across entry text
- Optional combination with tag filter
- No-results state provides guidance (clear filters, try another keyword)

**Acceptance Criteria:**
- ✅ Search results are relevant and update quickly
- ✅ Searching does not crash with large datasets

---

#### **FR-07: Reminders** (P1)

**Description:**
- User can enable a daily reminder
- User can set reminder time
- User can disable reminders

**Acceptance Criteria:**
- ✅ Notification permission request is shown at the right moment (when enabling)
- ✅ Reminder time change takes effect the next scheduled notification

---

#### **FR-08: Privacy / App Lock** (P1 or P0 depending on positioning)

**Description:**
- Optional biometric/passcode lock for app access
- Optional auto-lock when app goes background

**Acceptance Criteria:**
- ✅ Lock reliably protects entry access
- ✅ Lock settings are clearly explained to the user

---

## 6. Non-Functional Requirements

### 6.1 Performance

- Cold start "usable" time ≤ **TBD seconds** on supported devices
- List view remains responsive with **1,000+ entries**

### 6.2 Reliability & Data Safety

- Data stored **locally by default**
- No unintended data loss during normal use
- No collection of journal text for analytics (unless explicitly required and disclosed)

### 6.3 Security & Privacy

- Do not log sensitive user content
- Follow Apple privacy guidelines and disclose SDK usage
- Only request permissions when needed (**just-in-time**)

### 6.4 Compliance (App Store)

- Complete App Privacy details in App Store Connect
- Provide review notes/test account if login exists (otherwise N/A)
- Encryption/export compliance questions answered appropriately

---

## 7. Analytics (Optional, privacy-safe)

If analytics are used, track **behavior only** (no entry text):

**Events:**
- First open
- Create entry
- Enable reminder
- Search
- Filter by tag
- Edit entry
- Delete entry

**Funnel:**
```
Open → New Entry → Save Success
```

---

## 8. Risks & Mitigations

| Risk | Mitigation |
|------|-----------|
| **Privacy concerns reduce usage** | Clear privacy messaging, local storage, optional app lock |
| **Reminders feel intrusive** | Default off, user-controlled timing, respectful copy |
| **Low habit formation** | Minimal friction entry flow, gentle streak/insights (optional future) |

---

## Appendix A: Feature Priority Matrix

| Feature | Priority | Complexity | Impact | Status |
|---------|----------|------------|--------|--------|
| Create Entry | P0 | Low | High | Not Started |
| Entries List | P0 | Low | High | Not Started |
| Calendar View | P0 | Medium | High | Not Started |
| Edit/Delete | P0 | Low | High | Not Started |
| Tags | P1 | Medium | Medium | Not Started |
| Search | P1 | Medium | Medium | Not Started |
| Reminders | P1 | Low | Medium | Not Started |
| App Lock | P1 | Low | Medium | Not Started |

---

## Appendix B: Open Questions

1. **Mood scale:** 1-5 numeric vs emoji-based vs text labels?
2. **Export format:** Should v1.0 include PDF/Markdown export?
3. **Success metrics:** Define specific target percentages for retention/conversion
4. **Performance targets:** Define specific cold start and list scroll thresholds

---

**Next Steps:**
1. Review and approve PRD
2. Create technical design document
3. Set up Xcode project with SwiftUI + SwiftData
4. Implement FR-01 through FR-04 (P0 features)
5. Internal testing & iteration
6. Implement P1 features
7. App Store submission preparation

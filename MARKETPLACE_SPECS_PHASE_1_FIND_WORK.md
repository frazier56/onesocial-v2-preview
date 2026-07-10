# OneSocial Marketplace Specifications - PHASE 1: Find Work

**Version:** 1.0  
**Date:** March 31, 2026  
**Status:** Phase 1 - Find Work (Job Discovery)  
**Dependencies:** Dashboard Framework (colors, typography, spacing)  
**Next:** Phase 2 - Hire Talent, Phase 3 - Discover Events

---

## 📑 Phase 1 Contents

This document details the **Find Work** marketplace page where professionals browse and apply for jobs.

### Covered in This Phase:
1. Find Work Page Layout
2. Search & Filter System
3. Job Card Specifications (Grid & List Views)
4. Filter Drawer
5. Sort Options
6. Job Detail View
7. Empty States

---

# SECTION 1: FIND WORK PAGE

**Route:** Global Header → Find Work  
**View Mode:** `'findJobs'`  
**Component:** `FindJobs`  
**Access:** Public (no sign-in required to browse)

---

## Page Structure

```
┌──────────────────────────────────────────────────┐
│ Global Header (Fixed)                            │
├──────────────────────────────────────────────────┤
│ Page Title: "Find Work"                          │
│ Subtitle: "Discover paid opportunities..."       │
├──────────────────────────────────────────────────┤
│ Search Bar + Location + Filters (Desktop)        │
│ OR                                               │
│ Chips Filter + Sort Pills (Mobile)               │
├──────────────────────────────────────────────────┤
│ Sort + View Toggle (Right aligned)               │
├──────────────────────────────────────────────────┤
│                                                  │
│ Jobs Grid (3 columns desktop, 1 mobile)         │
│ [Job Card] [Job Card] [Job Card]                │
│                                                  │
└──────────────────────────────────────────────────┘
```

---

## 1.1: Page Layout

**Container:**
```css
.find-work-page {
  min-height: 100vh;
  padding-top: 96px; /* Global header height */
  background: var(--bg-primary); /* #0B0F1A */
  position: relative;
}
```

**Content Container:**
```css
.find-work-content {
  max-width: 1400px;
  margin: 0 auto;
  padding: 16px 24px; /* Desktop */
  padding: 16px 16px; /* Mobile */
  position: relative;
  z-index: 10;
}
```

---

## 1.2: Page Header

**Title:**
```css
.find-work-title {
  /* Typography: display-large (48px desktop, 30px mobile, 700 weight) */
  font-size: 48px; /* Desktop */
  font-size: 30px; /* Mobile */
  font-weight: 700;
  color: var(--text-100);
  margin-bottom: var(--space-4); /* 16px */
}
```
- **Content:** "Find Work" [STATIC TEXT]

**Subtitle:**
```css
.find-work-subtitle {
  /* Typography: body-large (16px, 400 weight) */
  font-size: 16px;
  color: var(--text-60); /* rgba(255,255,255,0.6) */
  margin-bottom: var(--space-6); /* 24px */
}
```
- **Content:** "Discover paid opportunities at verified events." [STATIC TEXT]

---

## 1.3: Search & Filter Bar (Desktop)

**Container:**
```css
.search-bar-desktop {
  display: none; /* Mobile */
  display: flex; /* Desktop (lg breakpoint: 1024px+) */
  align-items: center;
  gap: var(--space-3); /* 12px */
  margin-bottom: var(--space-3); /* 12px */
}
```

---

### Search Input

**Container:**
```css
.search-input-wrapper {
  flex: 1;
  height: 48px;
  display: flex;
  align-items: center;
  gap: var(--space-3); /* 12px */
  padding: 0 16px;
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: 12px;
  transition: all 200ms ease;
}

.search-input-wrapper:focus-within {
  border-color: var(--primary-teal);
  background: rgba(255, 255, 255, 0.08);
}
```

**Icon:**
```css
.search-icon {
  width: 20px;
  height: 20px;
  color: rgba(255, 255, 255, 0.48);
  flex-shrink: 0;
}
```
- **Icon:** Search

**Input Field:**
```css
.search-input {
  flex: 1;
  background: transparent;
  border: none;
  outline: none;
  color: var(--text-100);
  font-size: 15px;
  font-family: 'Inter', sans-serif;
}

.search-input::placeholder {
  color: rgba(255, 255, 255, 0.48);
}
```
- **Placeholder:** "Role or keyword..." [STATIC TEXT]

---

### Location Input

**Container:**
```css
.location-input-wrapper {
  width: 220px;
  height: 48px;
  display: flex;
  align-items: center;
  gap: var(--space-3);
  padding: 0 16px;
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: 12px;
  flex-shrink: 0;
}
```

**Icon:**
```css
.location-icon {
  width: 20px;
  height: 20px;
  color: rgba(255, 255, 255, 0.48);
}
```
- **Icon:** MapPin

**Input Field:**
```css
/* Same as search input */
```
- **Placeholder:** "Location" [STATIC TEXT]

---

### Filters Button

**Specifications:**
```css
.filters-button {
  height: 48px;
  padding: 0 16px;
  display: flex;
  align-items: center;
  gap: var(--space-2); /* 8px */
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: 12px;
  color: var(--text-100);
  font-size: 15px;
  font-weight: 500;
  cursor: pointer;
  transition: all 200ms ease;
}

.filters-button:hover {
  background: rgba(255, 255, 255, 0.08);
}
```

**Icon:**
```css
.filters-icon {
  width: 18px;
  height: 18px;
}
```
- **Icon:** SlidersHorizontal

**Text:** "Filters" [STATIC TEXT]

**Action:** Opens filter drawer modal

---

### Sort Dropdown

**Button:**
```css
.sort-button {
  height: 48px;
  min-width: 120px;
  padding: 0 16px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: var(--space-2);
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: 12px;
  color: var(--text-100);
  font-size: 15px;
  font-weight: 500;
  cursor: pointer;
  transition: all 200ms ease;
}

.sort-button:hover {
  background: rgba(255, 255, 255, 0.08);
}
```

**Text:** "Sort by" [STATIC TEXT]

**Icon:**
```css
.sort-chevron {
  width: 16px;
  height: 16px;
  transition: transform 200ms ease;
}

.sort-button.open .sort-chevron {
  transform: rotate(180deg);
}
```
- **Icon:** ChevronDown

---

**Dropdown Menu:**
```css
.sort-dropdown-menu {
  position: absolute;
  top: calc(100% + 8px);
  right: 0;
  min-width: 200px;
  background: rgba(11, 15, 26, 0.95);
  backdrop-filter: blur(16px);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 12px;
  padding: var(--space-2); /* 8px */
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.4);
  z-index: 100;
}

.sort-dropdown-item {
  padding: 10px 12px;
  border-radius: 8px;
  color: var(--text-80);
  font-size: 14px;
  cursor: pointer;
  transition: all 150ms ease;
}

.sort-dropdown-item:hover {
  background: rgba(255, 255, 255, 0.06);
}

.sort-dropdown-item.active {
  background: rgba(46, 230, 214, 0.1);
  color: var(--primary-teal);
}
```

**Four Sort Options:**
1. "Newest" (Default) [STATIC TEXT]
2. "Highest Pay" [STATIC TEXT]
3. "Highest Score" (OneScore required) [STATIC TEXT]
4. "Soonest" (By event date) [STATIC TEXT]

---

### View Mode Toggle

**Container:**
```css
.view-mode-toggle {
  display: flex;
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 10px;
  padding: 4px;
  gap: 4px;
}
```

**Button:**
```css
.view-mode-button {
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 6px;
  background: transparent;
  border: none;
  cursor: pointer;
  transition: all 200ms ease;
}

.view-mode-button.active {
  background: var(--primary-teal);
  color: var(--bg-primary);
}

.view-mode-button.inactive {
  color: var(--text-60);
}

.view-mode-button.inactive:hover {
  background: rgba(255, 255, 255, 0.08);
}
```

**Two Buttons:**
1. **Grid View**
   - Icon: Grid3x3 (20px)
   - Action: `setViewMode('grid')`

2. **List View**
   - Icon: List (20px)
   - Action: `setViewMode('list')`

---

## 1.4: Mobile Filter Chips

**Container:**
```css
.mobile-filter-chips {
  display: flex; /* Mobile */
  display: none; /* Desktop (lg+) */
  align-items: center;
  gap: var(--space-2); /* 8px */
  overflow-x: auto;
  padding-bottom: var(--space-2);
  margin-bottom: var(--space-3);
  scrollbar-width: none;
  -ms-overflow-style: none;
}

.mobile-filter-chips::-webkit-scrollbar {
  display: none;
}
```

---

### Filter Chip Pattern

**Container:**
```css
.mobile-filter-chip {
  height: 44px;
  padding: 0 16px;
  display: flex;
  align-items: center;
  gap: var(--space-2);
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 999px; /* Pill shape */
  white-space: nowrap;
  flex-shrink: 0;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: all 200ms ease;
}

.mobile-filter-chip.active {
  background: rgba(46, 230, 214, 0.2);
  border-color: rgba(46, 230, 214, 0.3);
  color: var(--primary-teal);
}

.mobile-filter-chip.inactive {
  color: rgba(255, 255, 255, 0.72);
}
```

**Five Chips:**
1. **Filters** (Opens drawer)
   - Icon: SlidersHorizontal (16px)
   - Text: "Filters" [STATIC TEXT]

2. **Newest** (Sort option)
   - Text: "Newest" [STATIC TEXT]
   - Action: `setSortBy('newest')`

3. **Highest Pay** (Sort option)
   - Text: "Highest Pay" [STATIC TEXT]
   - Action: `setSortBy('highestPay')`

4. **Top Rated** (Sort option)
   - Text: "Top Rated" [STATIC TEXT]
   - Action: `setSortBy('highestScore')`

---

## 1.5: Jobs Grid (Grid View)

**Container:**
```css
.jobs-grid {
  display: grid;
  grid-template-columns: 1fr; /* Mobile: 1 col */
  grid-template-columns: repeat(2, 1fr); /* Tablet: 2 cols */
  grid-template-columns: repeat(3, 1fr); /* Desktop: 3 cols */
  gap: var(--space-5); /* 20px */
  padding: var(--space-6) 0; /* 24px vertical */
}

/* Responsive breakpoints */
@media (min-width: 768px) {
  .jobs-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .jobs-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}
```

---

## 1.6: Job Card Specifications (Grid View)

**Container:**
```css
.job-card {
  background: linear-gradient(135deg, rgba(255,255,255,0.12) 0%, rgba(255,255,255,0.06) 100%);
  border: 1px solid rgba(255, 255, 255, 0.16);
  border-radius: 20px;
  overflow: hidden;
  cursor: pointer;
  transition: all 300ms ease;
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.4), inset 0 1px 0 rgba(255,255,255,0.15);
}

.job-card:hover {
  transform: translateY(-4px);
  border-color: rgba(46, 230, 214, 0.3);
  box-shadow: 0 16px 40px rgba(0, 0, 0, 0.5), inset 0 1px 0 rgba(255,255,255,0.2);
}
```

---

### Card Structure

```
┌──────────────────────────────┐
│ [Cover Image - 16:9 ratio]   │ ← Event/venue image
│                              │
│ [OneScore Badge - overlay]   │ ← Required OneScore
├──────────────────────────────┤
│ Sound Engineer               │ ← Job title (h3)
│ Tech Summit 2025             │ ← Event name
│                              │
│ 📍 San Francisco, CA         │ ← Location
│ 📅 Jan 15-16, 2025           │ ← Date
│ 💰 $2,500                    │ ← Pay
│                              │
│ Audio • Conference           │ ← Category + Type tags
│                              │
│ Posted 2 days ago            │ ← Time posted
└──────────────────────────────┘
```

---

### Cover Image

**Container:**
```css
.job-card-image-container {
  position: relative;
  width: 100%;
  aspect-ratio: 16 / 9;
  overflow: hidden;
}

.job-card-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 400ms ease;
}

.job-card:hover .job-card-image {
  transform: scale(1.05);
}

.job-card-image-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(11, 15, 26, 0.8) 0%, transparent 60%);
}
```

**Image Source:** [SAMPLE DATA: `job.image`]
- Example: `'https://images.unsplash.com/photo-1540575467063-178a50c2df87?w=800'`

---

### OneScore Badge (Overlaid)

**Position:**
```css
.job-onescore-badge {
  position: absolute;
  top: 12px;
  right: 12px;
  padding: 6px 12px;
  border-radius: 8px;
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  display: flex;
  align-items: center;
  gap: var(--space-1); /* 4px */
  z-index: 10;
}
```

**Variants by Score:**

**High Score (90+):**
```css
background: linear-gradient(135deg, rgba(255, 215, 0, 0.25), rgba(255, 215, 0, 0.15));
border: 1px solid rgba(255, 215, 0, 0.4);
```

**Medium Score (80-89):**
```css
background: linear-gradient(135deg, rgba(46, 230, 214, 0.25), rgba(46, 230, 214, 0.15));
border: 1px solid rgba(46, 230, 214, 0.4);
```

**Lower Score (<80):**
```css
background: linear-gradient(135deg, rgba(255, 255, 255, 0.2), rgba(255, 255, 255, 0.1));
border: 1px solid rgba(255, 255, 255, 0.3);
```

**Badge Content:**
```css
.onescore-badge-icon {
  /* Icon: Shield, size: 14px */
  color: inherit;
}

.onescore-badge-text {
  /* Typography: label-small (12px, 600 weight) */
  color: inherit;
  display: flex;
  align-items: center;
  gap: 2px;
}

.onescore-badge-number {
  font-weight: 700;
}
```

**Content:** "85 OS" [SAMPLE DATA: `job.oneScoreRequired`]

---

### Card Content Section

**Container:**
```css
.job-card-content {
  padding: var(--space-5); /* 20px */
}
```

---

### Job Title

**Specifications:**
```css
.job-card-title {
  /* Typography: heading-4 (16px, 700 weight) */
  font-size: 16px;
  font-weight: 700;
  color: var(--text-100);
  margin-bottom: var(--space-1); /* 4px */
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}
```

**Content:** [SAMPLE DATA: `job.title`]
- Example: "Sound Engineer"

---

### Event Name

**Specifications:**
```css
.job-card-event-name {
  /* Typography: body-regular (14px, 400 weight) */
  font-size: 14px;
  color: var(--text-60);
  margin-bottom: var(--space-3); /* 12px */
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```

**Content:** [SAMPLE DATA: `job.eventName`]
- Example: "Tech Summit 2025"

---

### Job Details List

**Container:**
```css
.job-card-details-list {
  display: flex;
  flex-direction: column;
  gap: var(--space-2); /* 8px */
  margin-bottom: var(--space-4); /* 16px */
  padding-bottom: var(--space-4);
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}
```

**Detail Item Pattern:**
```css
.job-card-detail-item {
  display: flex;
  align-items: center;
  gap: var(--space-2); /* 8px */
}

.job-card-detail-icon {
  width: 16px;
  height: 16px;
  color: var(--text-60);
  flex-shrink: 0;
}

.job-card-detail-text {
  /* Typography: body-small (12px, 400 weight) */
  font-size: 12px;
  color: var(--text-72);
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```

**Three Detail Items:**

1. **Location**
   - Icon: MapPin (16px)
   - Text: [SAMPLE DATA: `job.location`]
   - Example: "San Francisco, CA"

2. **Date**
   - Icon: Calendar (16px)
   - Text: [SAMPLE DATA: `job.date`]
   - Example: "Jan 15-16, 2025"

3. **Pay**
   - Icon: DollarSign (16px)
   - Text: [SAMPLE DATA: `job.pay`]
   - Example: "$2,500"

---

### Tags Section

**Container:**
```css
.job-card-tags {
  display: flex;
  align-items: center;
  gap: var(--space-2); /* 8px */
  margin-bottom: var(--space-3);
  flex-wrap: wrap;
}

.job-card-tag {
  padding: 4px 10px;
  border-radius: 6px;
  background: rgba(46, 230, 214, 0.1);
  border: 1px solid rgba(46, 230, 214, 0.2);
  color: var(--primary-teal);
  /* Typography: body-tiny (10px, 500 weight) */
  font-size: 10px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
```

**Two Tags:**
1. **Category:** [SAMPLE DATA: `job.category`] - Example: "Audio"
2. **Event Type:** [SAMPLE DATA: `job.eventType`] - Example: "Conference"

---

### Posted Time

**Specifications:**
```css
.job-card-posted-time {
  /* Typography: body-tiny (10px, 400 weight) */
  font-size: 10px;
  color: var(--text-48);
}
```

**Content:** [SAMPLE DATA: `job.posted`]
- Example: "Posted 2 days ago"

---

## 1.7: Job Card Specifications (List View)

**Container:**
```css
.job-card-list {
  background: linear-gradient(135deg, rgba(255,255,255,0.12) 0%, rgba(255,255,255,0.06) 100%);
  border: 1px solid rgba(255, 255, 255, 0.16);
  border-radius: 16px;
  padding: var(--space-5); /* 20px */
  cursor: pointer;
  transition: all 300ms ease;
  margin-bottom: var(--space-4);
}

.job-card-list:hover {
  border-color: rgba(46, 230, 214, 0.3);
  background: linear-gradient(135deg, rgba(255,255,255,0.14) 0%, rgba(255,255,255,0.08) 100%);
}
```

---

### List View Layout

**Grid Structure:**
```css
.job-card-list-content {
  display: grid;
  grid-template-columns: 120px 1fr auto; /* Image, Content, Actions */
  gap: var(--space-4); /* 16px */
  align-items: center;
}

/* Mobile: Stack vertically */
@media (max-width: 768px) {
  .job-card-list-content {
    grid-template-columns: 1fr;
  }
}
```

---

**Left: Thumbnail Image**
```css
.job-card-list-thumbnail {
  width: 120px;
  height: 80px;
  border-radius: 12px;
  overflow: hidden;
  position: relative;
  flex-shrink: 0;
}

.job-card-list-thumbnail-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
```

---

**Center: Job Information**
```css
.job-card-list-info {
  flex: 1;
  min-width: 0;
}

.job-card-list-title {
  /* Typography: heading-4 (16px, 700 weight) */
  color: var(--text-100);
  margin-bottom: var(--space-1);
}

.job-card-list-event {
  /* Typography: body-regular (14px, 400 weight) */
  color: var(--text-60);
  margin-bottom: var(--space-2);
}

.job-card-list-details {
  display: flex;
  align-items: center;
  gap: var(--space-4);
  flex-wrap: wrap;
}

.job-card-list-detail {
  display: flex;
  align-items: center;
  gap: var(--space-1);
  /* Typography: body-small (12px, 400 weight) */
  color: var(--text-72);
}
```

---

**Right: OneScore Badge + Arrow**
```css
.job-card-list-actions {
  display: flex;
  align-items: center;
  gap: var(--space-3);
  flex-shrink: 0;
}

.job-card-list-onescore {
  /* Same badge as grid view but slightly smaller */
  padding: 4px 10px;
  border-radius: 6px;
}

.job-card-list-arrow {
  width: 20px;
  height: 20px;
  color: var(--primary-teal);
}
```
- Icon: ArrowRight

---

## 1.8: Filter Drawer (Modal)

**Overlay:**
```css
.filter-drawer-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.7);
  backdrop-filter: blur(4px);
  z-index: 9998;
  animation: fadeIn 200ms ease;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}
```

---

**Drawer Container:**
```css
.filter-drawer {
  position: fixed;
  right: 0;
  top: 0;
  bottom: 0;
  width: 400px; /* Desktop */
  width: 100%; /* Mobile */
  max-width: 400px;
  background: rgba(11, 15, 26, 0.98);
  backdrop-filter: blur(24px);
  border-left: 1px solid rgba(255, 255, 255, 0.12);
  box-shadow: -8px 0 32px rgba(0, 0, 0, 0.6);
  z-index: 9999;
  overflow-y: auto;
  animation: slideInRight 250ms ease;
}

@keyframes slideInRight {
  from {
    transform: translateX(100%);
  }
  to {
    transform: translateX(0);
  }
}
```

---

### Drawer Header

**Container:**
```css
.filter-drawer-header {
  padding: var(--space-6); /* 24px */
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: sticky;
  top: 0;
  background: rgba(11, 15, 26, 0.98);
  backdrop-filter: blur(24px);
  z-index: 10;
}

.filter-drawer-title {
  /* Typography: heading-3 (20px, 600 weight) */
  color: var(--text-100);
}

.filter-drawer-close {
  width: 36px;
  height: 36px;
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid rgba(255, 255, 255, 0.12);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 200ms ease;
}

.filter-drawer-close:hover {
  background: rgba(255, 255, 255, 0.10);
}

.filter-drawer-close-icon {
  width: 20px;
  height: 20px;
  color: var(--text-80);
}
```
- **Close Icon:** X

---

### Drawer Content

**Container:**
```css
.filter-drawer-content {
  padding: var(--space-6);
}
```

---

### Filter Section Pattern

**Section Container:**
```css
.filter-section {
  margin-bottom: var(--space-6); /* 24px */
}

.filter-section-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: var(--space-3) 0;
  cursor: pointer;
  user-select: none;
}

.filter-section-title {
  /* Typography: label-medium (14px, 600 weight) */
  color: var(--text-100);
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.filter-section-chevron {
  width: 16px;
  height: 16px;
  color: var(--text-60);
  transition: transform 200ms ease;
}

.filter-section-header.expanded .filter-section-chevron {
  transform: rotate(180deg);
}
```
- **Icon:** ChevronDown

---

**Section Content:**
```css
.filter-section-content {
  padding: var(--space-3) 0;
  display: none; /* Collapsed */
  display: block; /* Expanded */
  animation: expandDown 200ms ease;
}

@keyframes expandDown {
  from {
    opacity: 0;
    max-height: 0;
  }
  to {
    opacity: 1;
    max-height: 500px;
  }
}
```

---

### Filter 1: Category

**Checkboxes:**
```css
.filter-checkbox-list {
  display: flex;
  flex-direction: column;
  gap: var(--space-2);
}

.filter-checkbox-item {
  display: flex;
  align-items: center;
  gap: var(--space-2);
  padding: var(--space-2);
  border-radius: 8px;
  cursor: pointer;
  transition: background 150ms ease;
}

.filter-checkbox-item:hover {
  background: rgba(255, 255, 255, 0.03);
}

.filter-checkbox {
  width: 18px;
  height: 18px;
  border-radius: 4px;
  border: 2px solid rgba(255, 255, 255, 0.3);
  background: transparent;
  transition: all 200ms ease;
  flex-shrink: 0;
}

.filter-checkbox.checked {
  background: var(--primary-teal);
  border-color: var(--primary-teal);
}

.filter-checkbox-icon {
  /* Icon: Check, size: 14px */
  color: var(--bg-primary);
  display: none;
}

.filter-checkbox.checked .filter-checkbox-icon {
  display: block;
}

.filter-checkbox-label {
  /* Typography: body-regular (14px, 400 weight) */
  color: var(--text-80);
}
```

**Categories:**
- "Audio" [CHECKBOX]
- "Management" [CHECKBOX]
- "Lighting" [CHECKBOX]
- "Photography" [CHECKBOX]
- "DJ" [CHECKBOX]
- "Catering" [CHECKBOX]
- "Security" [CHECKBOX]
- "Floral" [CHECKBOX]

---

### Filter 2: Event Type

**Same checkbox pattern as Category**

**Event Types:**
- "Conference" [CHECKBOX]
- "Corporate" [CHECKBOX]
- "Entertainment" [CHECKBOX]
- "Wedding" [CHECKBOX]
- "Festival" [CHECKBOX]
- "Concert" [CHECKBOX]
- "Charity" [CHECKBOX]

---

### Filter 3: Pay Range

**Slider Component:**
```css
.filter-pay-range {
  padding: var(--space-4) var(--space-2);
}

.filter-pay-range-labels {
  display: flex;
  justify-content: space-between;
  margin-bottom: var(--space-2);
}

.filter-pay-range-label {
  /* Typography: body-small (12px, 500 weight) */
  color: var(--text-80);
}

.filter-pay-range-slider {
  width: 100%;
  height: 6px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 3px;
  position: relative;
}

.filter-pay-range-track {
  height: 100%;
  background: var(--primary-teal);
  border-radius: 3px;
}

.filter-pay-range-thumb {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: var(--primary-teal);
  border: 3px solid var(--bg-primary);
  position: absolute;
  top: 50%;
  transform: translate(-50%, -50%);
  cursor: grab;
}

.filter-pay-range-thumb:active {
  cursor: grabbing;
}
```

**Range:** $0 - $10,000+

---

### Filter 4: OneScore Required

**OneScore Slider with Visual Instrument:**

Uses component: `OneScoreInstrumentSlider`

```css
.filter-onescore-slider {
  padding: var(--space-4) 0;
}

.filter-onescore-value {
  /* Typography: display-small (20px, 700 weight) */
  color: var(--primary-teal);
  margin-bottom: var(--space-2);
  text-align: center;
}

.filter-onescore-description {
  /* Typography: body-small (12px, 400 weight) */
  color: var(--text-60);
  text-align: center;
  margin-bottom: var(--space-4);
}
```

**Slider Range:** 0 - 100
- 0 = No minimum requirement
- 100 = Highest OneScore jobs only

**Visual Feedback:**
- Color changes based on value (green → yellow → red gradient)
- "Thermometer" style visual indicator

---

### Drawer Footer

**Container:**
```css
.filter-drawer-footer {
  position: sticky;
  bottom: 0;
  padding: var(--space-6);
  background: rgba(11, 15, 26, 0.98);
  backdrop-filter: blur(24px);
  border-top: 1px solid rgba(255, 255, 255, 0.08);
  display: flex;
  gap: var(--space-3);
}
```

**Two Buttons:**

1. **Clear All**
   ```css
   /* Uses: btn-secondary pattern */
   flex: 1;
   padding: 12px 20px;
   border-radius: 10px;
   background: transparent;
   border: 1px solid rgba(255, 255, 255, 0.12);
   color: var(--text-80);
   font-size: 15px;
   font-weight: 600;
   ```
   - Text: "Clear All" [STATIC TEXT]
   - Action: Resets all filters to default

2. **Apply Filters**
   ```css
   /* Uses: btn-primary pattern */
   flex: 1;
   padding: 12px 20px;
   border-radius: 10px;
   background: var(--primary-teal);
   color: var(--bg-primary);
   font-size: 15px;
   font-weight: 600;
   ```
   - Text: "Apply Filters" [STATIC TEXT]
   - Action: Applies filters and closes drawer

---

## 1.9: Sample Job Data

```javascript
[SAMPLE DATA: Job object]
{
  id: 'j1',
  title: 'Sound Engineer',
  eventName: 'Tech Summit 2025',
  location: 'San Francisco, CA',
  date: 'Jan 15-16, 2025',
  pay: '$2,500',
  oneScoreRequired: 85,
  category: 'Audio',
  eventType: 'Conference',
  posted: '2 days ago',
  image: 'https://images.unsplash.com/photo-1540575467063-178a50c2df87?w=800'
}
```

**9 Sample Jobs Available** (as shown in code)

---

## 1.10: Empty State

**When no jobs match filters:**

```css
.jobs-empty-state {
  padding: var(--space-12); /* 48px */
  text-align: center;
  background: linear-gradient(135deg, rgba(255,255,255,0.12) 0%, rgba(255,255,255,0.06) 100%);
  border: 1px solid rgba(255, 255, 255, 0.16);
  border-radius: 20px;
  margin: var(--space-8) 0;
}

.jobs-empty-state-icon {
  width: 64px;
  height: 64px;
  margin: 0 auto var(--space-4) auto;
  color: var(--text-48);
}

.jobs-empty-state-title {
  /* Typography: heading-2-mobile (24px, 700 weight) */
  color: var(--text-100);
  margin-bottom: var(--space-2);
}

.jobs-empty-state-description {
  /* Typography: body-regular (14px, 400 weight) */
  color: var(--text-60);
  max-width: 400px;
  margin: 0 auto var(--space-6) auto;
}

.jobs-empty-state-action {
  /* Uses: btn-primary pattern */
}
```

**Content:**
- Icon: Briefcase (64px)
- Title: "No jobs found" [STATIC TEXT]
- Description: "Try adjusting your filters or check back later for new opportunities." [STATIC TEXT]
- Action: "Clear Filters" button

---

## 1.11: Trust Features Carousel (Optional Footer)

**Component:** `TrustFeaturesCarousel`

Shows rotating trust signals like:
- "Verified Events Only"
- "Secure Payments"
- "OneScore Protection"

**Specifications:**
```css
.trust-carousel {
  margin-top: var(--space-12);
  padding: var(--space-8) 0;
  border-top: 1px solid rgba(255, 255, 255, 0.08);
}
```

---

# END OF PHASE 1 - FIND WORK

**Status:** ✅ Complete  
**Covered:**
- Page layout and header
- Desktop search bar + filters
- Mobile filter chips
- Job cards (grid + list views)
- Filter drawer with 4 filter sections
- Sort dropdown
- View mode toggle
- Empty states
- Sample data structure

**Next Phase:** Phase 2 - Hire Talent

---

## Navigation & Actions

```javascript
// Card Actions
onViewJob(jobId) → Navigate to Job Detail view

// Filter Actions
setSearchQuery(query) → Updates search
setLocationQuery(location) → Updates location filter
setIsFilterOpen(true) → Opens filter drawer
setSortBy(sortType) → Changes sort order
setViewMode(mode) → Toggles grid/list view
setMinOneScore(score) → Filters by OneScore requirement

// Mobile Actions
ESC key → Closes filter drawer
```

---

## Responsive Breakpoints

- **Mobile:** < 768px
  - 1 column grid
  - Chip-based filters
  - Full-width search
  - Stacked card layout

- **Tablet:** 768px - 1023px
  - 2 column grid
  - Chip-based filters
  - Responsive spacing

- **Desktop:** 1024px+
  - 3 column grid
  - Full command bar
  - Side filter drawer
  - Optimal spacing

---

**File Location:** `/public/MARKETPLACE_SPECS_PHASE_1_FIND_WORK.md`

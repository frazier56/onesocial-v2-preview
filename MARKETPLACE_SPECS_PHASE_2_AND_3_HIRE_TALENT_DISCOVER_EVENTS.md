# OneSocial Marketplace Specifications - PHASE 2 & 3: Hire Talent + Discover Events

**Version:** 1.0  
**Date:** March 31, 2026  
**Status:** Phase 2 & 3 Complete  
**Dependencies:** Phase 1 - Find Work Framework  
**Includes:** Hire Talent + Discover Events + Detail Views

---

## 📑 Document Contents

This document covers:
- **PHASE 2:** Hire Talent (Browse Professionals)
- **PHASE 3:** Discover Events (Browse Events)
- **BONUS:** Detail Views (Job, Profile, Event)

---

# SECTION 1: HIRE TALENT PAGE

**Route:** Global Header → Hire Talent  
**View Mode:** `'hireTalent'`  
**Component:** `HireTalent`  
**Access:** Public (no sign-in required)

---

## Page Structure

```
┌──────────────────────────────────────────────────┐
│ Global Header (Fixed)                            │
├──────────────────────────────────────────────────┤
│ Page Title: "Hire Talent"                        │
│ Subtitle + Metrics (Desktop Right)               │
├──────────────────────────────────────────────────┤
│ Search Bar + Location + Filters + Sort           │
├──────────────────────────────────────────────────┤
│                                                  │
│ Professionals Grid (3 columns)                   │
│ [Profile Card] [Profile Card] [Profile Card]    │
│                                                  │
└──────────────────────────────────────────────────┘
```

---

## 1.1: Page Header with Metrics

**Layout:**
```css
.hire-talent-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: var(--space-6); /* 24px */
}
```

---

### Left: Title & Subtitle

**Title:**
```css
/* Same as Find Work */
font-size: 48px; /* Desktop */
font-size: 30px; /* Mobile */
font-weight: 700;
```
- **Content:** "Hire Talent" [STATIC TEXT]

**Subtitle:**
```css
font-size: 16px;
color: var(--text-60);
```
- **Content:** "Verified talent with real social reputation." [STATIC TEXT]

---

### Right: Metrics Row (Desktop Only)

**Container:**
```css
.hire-talent-metrics {
  display: none; /* Mobile */
  display: flex; /* Desktop (md+: 768px) */
  align-items: center;
  gap: var(--space-8); /* 32px */
}
```

**Metric Item Pattern:**
```css
.metric-item {
  text-align: right;
}

.metric-value {
  font-size: 32px;
  font-weight: 700;
  margin-bottom: var(--space-1); /* 4px */
}

.metric-label {
  font-size: 14px;
  color: rgba(255, 255, 255, 0.72);
}
```

**Three Metrics:**

1. **Total Professionals**
   - Value: "850+" [STATIC/DYNAMIC]
   - Label: "Professionals" [STATIC TEXT]
   - Color: White

2. **Average OneScore**
   - Value: "87" [CALCULATED from data]
   - Label: "Avg OneScore" [STATIC TEXT]
   - Color: Primary Teal (`#2EE6D6`)

3. **Satisfaction Rate**
   - Value: "98%" [STATIC/DYNAMIC]
   - Label: "Satisfaction" [STATIC TEXT]
   - Color: White

---

## 1.2: Search & Filter Bar

**Same pattern as Find Work but with adjusted placeholder:**

**Search Placeholder:** "Search professionals by name, skill, or specialty..." [STATIC TEXT]

**All other components same as Find Work:**
- Search input
- Location input
- Filters button
- Sort dropdown
- View mode toggle

---

## 1.3: Professionals Grid

**Grid Container:**
```css
/* Same as Find Work jobs grid */
grid-template-columns: 1fr; /* Mobile */
grid-template-columns: repeat(2, 1fr); /* Tablet */
grid-template-columns: repeat(3, 1fr); /* Desktop */
gap: var(--space-5); /* 20px */
```

---

## 1.4: Professional Card Specifications

**Container:**
```css
/* Uses same glass-card pattern as Job Card */
.professional-card {
  background: linear-gradient(135deg, rgba(255,255,255,0.12) 0%, rgba(255,255,255,0.06) 100%);
  border: 1px solid rgba(255, 255, 255, 0.16);
  border-radius: 20px;
  overflow: hidden;
  cursor: pointer;
  transition: all 300ms ease;
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.4), inset 0 1px 0 rgba(255,255,255,0.15);
}

.professional-card:hover {
  transform: translateY(-4px);
  border-color: rgba(46, 230, 214, 0.3);
}
```

---

### Card Structure

```
┌──────────────────────────────┐
│ [Cover Image - 16:9]         │ ← Professional's work image
│                              │
│ [Elite Badge - if applicable]│ ← Top right overlay
│ [OneScore Badge - bottom]    │ ← Bottom left overlay
├──────────────────────────────┤
│ Elite Events Co.             │ ← Name/Business (h3)
│ Event Production             │ ← Role/Specialty
│ 📍 Medellín                  │ ← Location
│                              │
│ ⭐ 4.9 (28)                  │ ← Rating + review count
│                              │
│ Full-service • Luxury        │ ← Skill tags (2-3)
│                              │
│ Custom Pricing               │ ← Pricing type
│ 47 jobs completed            │ ← Completed jobs count
└──────────────────────────────┘
```

---

### Cover Image

**Same pattern as Job Card:**
```css
.professional-card-image {
  aspect-ratio: 16 / 9;
  /* All other specs same */
}
```

**Image Source:** [SAMPLE DATA: `professional.coverImage`]

---

### Elite Badge (Conditional)

**Position:**
```css
.professional-elite-badge {
  position: absolute;
  top: 12px;
  right: 12px;
  padding: 6px 12px;
  border-radius: 8px;
  backdrop-filter: blur(12px);
  background: linear-gradient(135deg, rgba(255, 215, 0, 0.3), rgba(255, 215, 0, 0.2));
  border: 1px solid rgba(255, 215, 0, 0.5);
  z-index: 10;
  display: flex;
  align-items: center;
  gap: var(--space-1);
}

.professional-elite-icon {
  /* Icon: Award, size: 14px */
  color: #FFD700; /* Gold */
}

.professional-elite-text {
  font-size: 11px;
  font-weight: 700;
  color: #FFD700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
```

**Content:** "ELITE" [STATIC TEXT]

**Shown when:** [SAMPLE DATA: `professional.isElite === true`]

---

### OneScore Badge (Bottom Left Overlay)

**Position:**
```css
.professional-onescore-badge {
  position: absolute;
  bottom: 12px;
  left: 12px;
  padding: 6px 12px;
  border-radius: 8px;
  backdrop-filter: blur(12px);
  z-index: 10;
  /* Color based on score (same as Find Work) */
}
```

**Content:** "91 OS" [SAMPLE DATA: `professional.oneScore`]

---

### Card Content

**Container:**
```css
.professional-card-content {
  padding: var(--space-5); /* 20px */
}
```

---

**Name/Business:**
```css
.professional-name {
  font-size: 16px;
  font-weight: 700;
  color: var(--text-100);
  margin-bottom: var(--space-1);
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```
- **Content:** [SAMPLE DATA: `professional.name`]
- Example: "Elite Events Co."

---

**Role:**
```css
.professional-role {
  font-size: 14px;
  color: var(--text-60);
  margin-bottom: var(--space-2);
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```
- **Content:** [SAMPLE DATA: `professional.role`]
- Example: "Event Production"

---

**Location:**
```css
.professional-location {
  display: flex;
  align-items: center;
  gap: var(--space-1);
  font-size: 12px;
  color: var(--text-72);
  margin-bottom: var(--space-3);
}

.professional-location-icon {
  width: 14px;
  height: 14px;
  color: var(--text-60);
}
```
- **Icon:** MapPin
- **Content:** [SAMPLE DATA: `professional.location`]

---

**Rating Section:**
```css
.professional-rating {
  display: flex;
  align-items: center;
  gap: var(--space-1);
  padding-bottom: var(--space-3);
  margin-bottom: var(--space-3);
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.professional-rating-icon {
  width: 16px;
  height: 16px;
  color: #F59E0B; /* Warning/star color */
}

.professional-rating-value {
  font-size: 14px;
  font-weight: 600;
  color: var(--text-100);
}

.professional-rating-count {
  font-size: 12px;
  color: var(--text-60);
}
```

**Content:**
- Icon: Star (filled)
- Value: [SAMPLE DATA: `professional.rating`] - Example: "4.9"
- Count: [SAMPLE DATA: `professional.reviewCount`] - Example: "(28)"

---

**Skills Tags:**
```css
.professional-skills {
  display: flex;
  gap: var(--space-1);
  margin-bottom: var(--space-3);
  flex-wrap: wrap;
}

.professional-skill-tag {
  font-size: 10px;
  font-weight: 500;
  padding: 4px 8px;
  border-radius: 6px;
  background: rgba(46, 230, 214, 0.1);
  border: 1px solid rgba(46, 230, 214, 0.2);
  color: var(--primary-teal);
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```

**Shows:** First 2-3 skills from [SAMPLE DATA: `professional.skills` array]
- Example: "Production • Full-service • Luxury"

---

**Pricing:**
```css
.professional-pricing {
  font-size: 14px;
  font-weight: 600;
  color: var(--primary-teal);
  margin-bottom: var(--space-1);
}
```

**Two Types:**
1. **Fixed Pricing:** [SAMPLE DATA: `professional.price`]
   - Example: "$220 / night"
   - Shown when: `professional.pricingType === 'fixed'`

2. **Custom Pricing:** "Custom Pricing" [STATIC TEXT]
   - Shown when: `professional.pricingType === 'custom'`

---

**Completed Jobs:**
```css
.professional-completed-jobs {
  font-size: 11px;
  color: var(--text-60);
}
```
- **Content:** "[count] jobs completed" [SAMPLE DATA: `professional.completedJobs`]
- Example: "47 jobs completed"

---

## 1.5: Filter Drawer

**Same structure as Find Work but with different filter options:**

### Filter 1: Specialty/Category
- "Event Production" [CHECKBOX]
- "Photography" [CHECKBOX]
- "Videography" [CHECKBOX]
- "DJ Services" [CHECKBOX]
- "Wellness" [CHECKBOX]
- "Catering" [CHECKBOX]

### Filter 2: Experience Level
- "Entry Level" [CHECKBOX]
- "Intermediate" [CHECKBOX]
- "Expert" [CHECKBOX]
- "Elite" [CHECKBOX]

### Filter 3: Pricing Range
- Slider: $0 - $10,000+

### Filter 4: OneScore
- Same slider as Find Work
- Range: 0-100

---

## 1.6: Sample Professional Data

```javascript
[SAMPLE DATA: Professional object]
{
  id: 'p1',
  name: 'Elite Events Co.',
  role: 'Event Production',
  location: 'Medellín',
  oneScore: 91,
  rating: 4.9,
  reviewCount: 28,
  isElite: true,
  coverImage: 'https://images.unsplash.com/...',
  specialty: 'Full-service events',
  description: 'Complete event production from concept to execution.',
  skills: ['Production', 'Full-service', 'Luxury'],
  pricingType: 'custom', // or 'fixed'
  price: null, // or '$220 / night' for fixed
  completedJobs: 47
}
```

**6 Sample Professionals Available** (as shown in code)

---

# SECTION 2: DISCOVER EVENTS PAGE

**Route:** Global Header → Discover Events  
**View Mode:** `'discoverEvents'`  
**Component:** `DiscoverEvents`  
**Access:** Public

---

## Page Structure

```
┌──────────────────────────────────────────────────┐
│ Global Header (Fixed)                            │
├──────────────────────────────────────────────────┤
│ Page Title: "Discover Events"                    │
│ Subtitle: "Attend curated events..."             │
├──────────────────────────────────────────────────┤
│ Filter Dropdowns Row (Always Visible)            │
│ [Location ▼][Price ▼][Type ▼][Date ▼][Privacy ▼]│
├──────────────────────────────────────────────────┤
│                                                  │
│ Events Grid (3-4 columns)                        │
│ [Event Card] [Event Card] [Event Card]          │
│                                                  │
└──────────────────────────────────────────────────┘
```

---

## 2.1: Page Header

**Same pattern as Hire Talent:**
- Title: "Discover Events" [STATIC TEXT]
- Subtitle: "Attend curated events and unlock real-world credibility." [STATIC TEXT]

---

## 2.2: Filter Dropdowns (Always Visible)

**Container:**
```css
.discover-filters-row {
  display: flex;
  flex-direction: column; /* Mobile */
  flex-direction: row; /* Desktop (md+) */
  gap: var(--space-4); /* 16px */
  margin-bottom: var(--space-6);
}
```

---

### Dropdown Pattern

**Container:**
```css
.filter-dropdown {
  position: relative;
  flex: 1;
}

.filter-dropdown-select {
  width: 100%;
  height: 44px;
  padding: 0 16px;
  padding-right: 40px; /* Space for chevron */
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 12px;
  color: rgba(255, 255, 255, 0.9);
  font-size: 14px;
  font-family: 'Inter', sans-serif;
  cursor: pointer;
  appearance: none;
  transition: all 150ms ease;
}

.filter-dropdown-select:hover {
  background: rgba(255, 255, 255, 0.1);
}

.filter-dropdown-select:focus {
  outline: none;
  border-color: var(--primary-teal);
}

.filter-dropdown-chevron {
  position: absolute;
  right: 16px;
  top: 50%;
  transform: translateY(-50%);
  width: 16px;
  height: 16px;
  color: rgba(255, 255, 255, 0.5);
  pointer-events: none;
}
```
- **Icon:** ChevronDown

---

### Filter 1: Location

**Options:**
```html
<option value="all">All Locations</option>
<option value="sf">San Francisco</option>
<option value="oakland">Oakland</option>
<option value="sj">San Jose</option>
<option value="berkeley">Berkeley</option>
<option value="palo-alto">Palo Alto</option>
```

---

### Filter 2: Price Range

**Options:**
```html
<option value="all">Any Price</option>
<option value="free">Free</option>
<option value="low-to-high">Low to High</option>
<option value="high-to-low">High to Low</option>
<option value="0-50">$0 - $50</option>
<option value="50-150">$50 - $150</option>
<option value="150+">$150+</option>
```

---

### Filter 3: Ticket Type

**Options:**
```html
<option value="all">All Types</option>
<option value="general">General Admission</option>
<option value="vip">VIP</option>
<option value="free">Free Entry</option>
<option value="early-bird">Early Bird</option>
```

---

### Filter 4: Date

**Options:**
```html
<option value="all">Any Date</option>
<option value="today">Today</option>
<option value="this-week">This Week</option>
<option value="this-month">This Month</option>
<option value="next-month">Next Month</option>
```

---

### Filter 5: Privacy

**Options:**
```html
<option value="all">All Events</option>
<option value="public">Public</option>
<option value="private">Private</option>
```

---

## 2.3: Events Grid

**Grid Container:**
```css
.events-grid {
  display: grid;
  grid-template-columns: 1fr; /* Mobile */
  grid-template-columns: repeat(2, 1fr); /* Tablet */
  grid-template-columns: repeat(3, 1fr); /* Desktop (lg) */
  grid-template-columns: repeat(4, 1fr); /* Desktop XL (xl+) */
  gap: var(--space-5); /* 20px */
}

@media (min-width: 768px) {
  .events-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .events-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (min-width: 1440px) {
  .events-grid {
    grid-template-columns: repeat(4, 1fr);
  }
}
```

---

## 2.4: Event Card Specifications

**Container:**
```css
/* Same glass-card pattern as previous cards */
.event-card {
  background: linear-gradient(135deg, rgba(255,255,255,0.12) 0%, rgba(255,255,255,0.06) 100%);
  border: 1px solid rgba(255, 255, 255, 0.16);
  border-radius: 20px;
  overflow: hidden;
  cursor: pointer;
  transition: all 300ms ease;
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.4), inset 0 1px 0 rgba(255,255,255,0.15);
}

.event-card:hover {
  transform: translateY(-4px);
  border-color: rgba(46, 230, 214, 0.3);
}
```

---

### Card Structure

```
┌──────────────────────────────┐
│ [Cover Image - 4:3 ratio]    │ ← Event cover photo
│                              │
│ [Status Badge - top right]   │ ← Published/Sold Out
│ [Jobs Badge - bottom left]   │ ← If has jobs
├──────────────────────────────┤
│ Tech Summit 2025             │ ← Event title (h3)
│                              │
│ 📅 January 15-16, 2025       │ ← Date
│ 📍 San Francisco, CA         │ ← Location
│                              │
│ 🎫 34 of 100 left            │ ← Tickets remaining
│ 💰 $149                      │ ← Ticket price
│                              │
│ [Avatar] TechCorp • 92 OS    │ ← Host + OneScore
└──────────────────────────────┘
```

---

### Cover Image

**Container:**
```css
.event-card-image {
  position: relative;
  width: 100%;
  aspect-ratio: 4 / 3; /* Different from jobs - more square */
  overflow: hidden;
}

.event-card-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 400ms ease;
}

.event-card:hover .event-card-image img {
  transform: scale(1.05);
}

.event-card-image-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(11, 15, 26, 0.8) 0%, transparent 50%);
}
```

**Image Source:** [SAMPLE DATA: `event.coverImage`]

---

### Status Badge (Top Right)

**Component:** Uses `EventStatusPill` or `StatusBadge`

**Position:**
```css
.event-status-badge {
  position: absolute;
  top: 12px;
  right: 12px;
  padding: 6px 12px;
  border-radius: 8px;
  backdrop-filter: blur(12px);
  font-size: 11px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  z-index: 10;
}
```

**Status Variants:**

1. **Published** (Default - Green)
   ```css
   background: rgba(16, 185, 129, 0.25);
   border: 1px solid rgba(16, 185, 129, 0.4);
   color: var(--success);
   ```
   - Content: "LIVE" [STATIC TEXT]

2. **Sold Out** (Red)
   ```css
   background: rgba(239, 68, 68, 0.25);
   border: 1px solid rgba(239, 68, 68, 0.4);
   color: var(--error);
   ```
   - Content: "SOLD OUT" [STATIC TEXT]
   - Shown when: `event.ticketsRemaining === 0`

3. **Low Availability** (Warning)
   ```css
   background: rgba(245, 158, 11, 0.25);
   border: 1px solid rgba(245, 158, 11, 0.4);
   color: var(--warning);
   ```
   - Content: "LOW TICKETS" [STATIC TEXT]
   - Shown when: `event.ticketsRemaining < 10`

---

### Jobs Available Badge (Bottom Left - Conditional)

**Position:**
```css
.event-jobs-badge {
  position: absolute;
  bottom: 12px;
  left: 12px;
  padding: 6px 12px;
  border-radius: 8px;
  backdrop-filter: blur(12px);
  background: rgba(168, 85, 247, 0.25); /* Purple */
  border: 1px solid rgba(168, 85, 247, 0.4);
  display: flex;
  align-items: center;
  gap: var(--space-1);
  z-index: 10;
}

.event-jobs-badge-icon {
  width: 14px;
  height: 14px;
  color: #A855F7;
}

.event-jobs-badge-text {
  font-size: 11px;
  font-weight: 700;
  color: #A855F7;
}
```

**Content:**
- Icon: Briefcase
- Text: "[count] Jobs" [SAMPLE DATA: `event.jobCount`]
- Example: "3 Jobs"

**Shown when:** [SAMPLE DATA: `event.hasJobs === true`]

---

### Card Content

**Container:**
```css
.event-card-content {
  padding: var(--space-5); /* 20px */
}
```

---

**Event Title:**
```css
.event-card-title {
  font-size: 16px;
  font-weight: 700;
  color: var(--text-100);
  margin-bottom: var(--space-3);
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
```
- **Content:** [SAMPLE DATA: `event.title`]

---

**Date & Location:**
```css
.event-card-details {
  display: flex;
  flex-direction: column;
  gap: var(--space-2);
  margin-bottom: var(--space-4);
  padding-bottom: var(--space-4);
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.event-card-detail-item {
  display: flex;
  align-items: center;
  gap: var(--space-2);
  font-size: 12px;
  color: var(--text-72);
}

.event-card-detail-icon {
  width: 14px;
  height: 14px;
  color: var(--text-60);
}
```

**Two Details:**
1. **Date**
   - Icon: Calendar
   - Text: [SAMPLE DATA: `event.date`]

2. **Location**
   - Icon: MapPin
   - Text: [SAMPLE DATA: `event.location`]

---

**Ticket Info:**
```css
.event-card-ticket-info {
  display: flex;
  flex-direction: column;
  gap: var(--space-1);
  margin-bottom: var(--space-4);
}

.event-card-tickets-remaining {
  display: flex;
  align-items: center;
  gap: var(--space-1);
  font-size: 12px;
}

.event-card-tickets-icon {
  width: 14px;
  height: 14px;
  color: var(--primary-teal);
}

.event-card-tickets-text {
  color: var(--text-72);
}

.event-card-tickets-count {
  font-weight: 600;
  color: var(--primary-teal);
}

.event-card-price {
  display: flex;
  align-items: center;
  gap: var(--space-1);
  font-size: 14px;
}

.event-card-price-icon {
  width: 16px;
  height: 16px;
  color: var(--primary-teal);
}

.event-card-price-value {
  font-weight: 700;
  color: var(--text-100);
}
```

**Content:**
- **Tickets:** "[remaining] of [total] left" [SAMPLE DATA]
  - Icon: Ticket
  - Example: "34 of 100 left"
  - If `ticketsRemaining === 0`: "Sold Out"

- **Price:** [SAMPLE DATA: `event.ticketPrice`]
  - Icon: DollarSign
  - Example: "$149"
  - If `ticketPrice === 0`: "FREE"

---

**Host Section:**
```css
.event-card-host {
  display: flex;
  align-items: center;
  gap: var(--space-2);
}

.event-card-host-avatar {
  width: 28px;
  height: 28px;
  border-radius: 50%;
  background: var(--gradient-glass);
  overflow: hidden;
}

.event-card-host-info {
  display: flex;
  align-items: center;
  gap: var(--space-1);
  flex: 1;
  min-width: 0;
}

.event-card-host-name {
  font-size: 12px;
  font-weight: 500;
  color: var(--text-80);
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.event-card-host-separator {
  font-size: 12px;
  color: var(--text-48);
}

.event-card-host-onescore {
  font-size: 11px;
  font-weight: 600;
  color: var(--primary-teal);
  flex-shrink: 0;
}
```

**Content:**
- Avatar: Circle image or initials
- Name: [SAMPLE DATA: `event.host.name`]
- Separator: "•"
- OneScore: [SAMPLE DATA: `event.host.oneScore`] + " OS"
- Example: "TechCorp • 92 OS"

---

## 2.5: Sample Event Data

```javascript
[SAMPLE DATA: Event object]
{
  id: '1',
  title: 'Tech Summit 2025',
  coverImage: 'https://images.unsplash.com/photo-1540575467063-178a50c2df87?w=800',
  date: 'January 15-16, 2025',
  location: 'San Francisco, CA',
  ticketPrice: 149,
  ticketsRemaining: 34,
  totalTickets: 100,
  host: {
    name: 'TechCorp Events',
    oneScore: 92
  },
  hasJobs: true,
  jobCount: 3,
  status: 'published', // or 'sold-out', 'cancelled'
  startDate: '2025-01-15',
  endDate: '2025-01-16'
}
```

**7 Sample Events Available** (as shown in code)

---

# SECTION 3: DETAIL VIEWS

Now let's cover the detail views that appear when you click on cards.

---

## 3.1: JOB DETAIL VIEW

**Route:** Find Work → Click Job Card  
**Component:** `JobDetail`  
**View Mode:** `'jobDetail'`

### Page Structure

```
┌──────────────────────────────────────────────────┐
│ [← Back] [Save Job 🔖]                           │
├──────────────────────────────────────────────────┤
│ [Hero Image - Full Width]                        │
├──────────────────────────────────────────────────┤
│ Sound Engineer                                    │
│ Tech Summit 2025                                  │
├──────────────────────────────────────────────────┤
│ LEFT COLUMN              │ RIGHT COLUMN          │
│                          │                       │
│ About This Job           │ [Apply Now Button]    │
│ [Full Description]       │                       │
│                          │ Quick Details         │
│ Requirements             │ • Pay: $2,500         │
│ • Skills needed          │ • Date: Jan 15-16     │
│ • Experience level       │ • Location: SF        │
│                          │ • OneScore: 85+       │
│ Host Information         │                       │
│ [Avatar] TechCorp        │ Similar Jobs          │
│ OneScore: 92             │ [Job Card]           │
│                          │ [Job Card]           │
└──────────────────────────┴───────────────────────┘
```

### Key Sections:

**Hero Section:**
- Full-width event image (aspect-ratio: 21:9)
- Job title overlay (bottom left)
- Event name overlay

**Left Column (Main Content):**
- **About This Job** - Full description text
- **Requirements** - Bulleted list of skills/requirements
- **What You'll Do** - Responsibilities list
- **Host Information** - Host profile card with avatar, name, OneScore

**Right Column (Sidebar):**
- **Apply Now Button** (Primary CTA)
  - If signed in: Opens application modal
  - If not signed in: Opens sign-in modal
- **Quick Details Card**
  - Pay amount
  - Date & time
  - Location
  - OneScore required
  - Category tags
- **Similar Jobs** - 2-3 related job cards

---

## 3.2: PUBLIC PROFILE VIEW

**Route:** Hire Talent → Click Professional Card  
**Component:** `PublicProfile`  
**View Mode:** `'publicProfileView'`

### Page Structure

```
┌──────────────────────────────────────────────────┐
│ [← Back]                                         │
├──────────────────────────────────────────────────┤
│ [Cover Image - Full Width Banner]                │
├──────────────────────────────────────────────────┤
│ [Avatar - Large Circle]                          │
│ Elite Events Co.                                 │
│ Event Production • Medellín                      │
│ ⭐ 4.9 (28 reviews)                              │
│ [OneScore Badge: 91]                             │
├──────────────────────────────────────────────────┤
│ [Message] [Book Now]                             │
├──────────────────────────────────────────────────┤
│ About                                            │
│ Complete event production from concept...        │
│                                                  │
│ Skills & Expertise                               │
│ [Tag] [Tag] [Tag] [Tag] [Tag]                   │
│                                                  │
│ Portfolio / Work Samples                         │
│ [Image Grid - 3 columns]                         │
│                                                  │
│ Reviews (28)                                     │
│ [Review Card] [Review Card] [Review Card]        │
│                                                  │
│ Completed Jobs (47)                              │
│ [Job History List]                               │
└──────────────────────────────────────────────────┘
```

### Key Sections:

**Hero Banner:**
- Cover image (aspect-ratio: 21:9)
- Large avatar overlapping cover (centered bottom)

**Profile Header:**
- Name/Business name
- Role & Location
- Rating stars + review count
- OneScore badge (prominent)
- Elite badge (if applicable)

**Action Buttons:**
- **Message** (Secondary button)
- **Book Now** (Primary button)

**Content Sections:**
- **About** - Bio/description
- **Skills & Expertise** - Skill tags
- **Portfolio** - Image grid (3 cols)
- **Reviews** - Review cards with ratings
- **Completed Jobs** - Job history list
- **Pricing** - Fixed or custom pricing display
- **Availability** - Calendar or availability info

---

## 3.3: EVENT DETAIL VIEW

**Route:** Discover Events → Click Event Card  
**Component:** `EventDetail`  
**View Mode:** `'eventDetail'`

### Page Structure

```
┌──────────────────────────────────────────────────┐
│ [← Back]                                         │
├──────────────────────────────────────────────────┤
│ [Hero Image - Full Width]                        │
│ [Status Badge] [Save Button]                     │
├──────────────────────────────────────────────────┤
│ Tech Summit 2025                                 │
│ [OneScore Badge: Host 92]                        │
├──────────────────────────────────────────────────┤
│ LEFT COLUMN              │ RIGHT COLUMN          │
│                          │                       │
│ About This Event         │ [Get Tickets Button]  │
│ [Full Description]       │                       │
│                          │ Event Details         │
│ What to Expect           │ 📅 Jan 15-16, 2025   │
│ • Schedule/Agenda        │ 📍 Moscone Center    │
│ • Speakers/Performers    │ 🎫 34 of 100 left    │
│                          │ 💰 $149              │
│ Host Information         │                       │
│ [Avatar] TechCorp        │ Available Jobs (3)    │
│ OneScore: 92             │ [Job Card]           │
│ 156 events hosted        │ [Job Card]           │
│                          │                       │
│ Location & Venue         │ Similar Events        │
│ [Map - Interactive]      │ [Event Card]         │
│                          │ [Event Card]         │
└──────────────────────────┴───────────────────────┘
```

### Key Sections:

**Hero Section:**
- Full-width event cover (aspect-ratio: 21:9)
- Status badge overlay (top right)
- Save button (bookmark icon, top right)

**Event Header:**
- Event title (large)
- Host OneScore badge
- Category tags

**Left Column (Main Content):**
- **About This Event** - Full description
- **What to Expect** - Schedule/agenda
- **Host Information** - Host profile card
- **Location & Venue** - Map + address details

**Right Column (Sidebar):**
- **Get Tickets Button** (Primary CTA)
  - Shows pricing
  - Leads to ticket checkout
- **Event Details Card**
  - Date & time
  - Location
  - Tickets remaining
  - Price per ticket
- **Available Jobs** (if hasJobs)
  - List of job cards for this event
  - Link to apply
- **Similar Events** - 2-3 related event cards

---

# END OF PHASE 2 & 3

**Status:** ✅ Complete  
**Covered:**
- Hire Talent page (search, filters, professional cards)
- Discover Events page (filter dropdowns, event cards)
- Job Detail View
- Public Profile View
- Event Detail View

---

## Complete Summary

### PHASE 1: Find Work
- ✅ 9 sample jobs
- ✅ Grid & list views
- ✅ Filter drawer (4 sections)
- ✅ Sort options (4 types)
- ✅ Mobile filter chips

### PHASE 2: Hire Talent
- ✅ 6 sample professionals
- ✅ Elite badge system
- ✅ Rating & review display
- ✅ Pricing display (fixed/custom)
- ✅ Metrics dashboard (desktop)

### PHASE 3: Discover Events
- ✅ 7 sample events
- ✅ Always-visible filter dropdowns (5 filters)
- ✅ Status badges (Live/Sold Out/Low)
- ✅ Jobs available indicator
- ✅ 4-column grid (responsive)

### DETAIL VIEWS:
- ✅ Job Detail - Full job description with apply flow
- ✅ Public Profile - Professional/business profile
- ✅ Event Detail - Event info with ticket purchase

---

## File Locations

```
/public/MARKETPLACE_SPECS_PHASE_1_FIND_WORK.md
/public/MARKETPLACE_SPECS_PHASE_2_AND_3_HIRE_TALENT_DISCOVER_EVENTS.md
```

**Total:** 2 comprehensive marketplace specification documents  
**Combined:** ~15,000 lines  
**Status:** ✅ Ready for Figma recreation

---

**All marketplace pages and detail views now fully specified!** 🎉

# OneSocial Marketplace Pages - PRODUCTION SPECIFICATIONS

**Version:** 1.0 PRODUCTION  
**Date:** March 31, 2026  
**Status:** Ready for Figma Recreation & Production Build  
**Critical:** All [SAMPLE DATA] must be replaced with real data before production

---

## ⚠️ DATA LABELING SYSTEM

This document uses strict labeling for all content:

- **[STATIC TEXT]** - Hard-coded text that stays the same
- **[SAMPLE DATA]** - Placeholder data that MUST be replaced with real database data
- **[DYNAMIC]** - Calculated values based on real data
- **[CONDITIONAL]** - Shows/hides based on logic

---

# PAGE 1: FIND WORK

**URL:** `/find-work` or accessible via Global Header  
**Purpose:** Browse available paid job opportunities at events  
**Access:** Public (no authentication required)  
**Component:** `FindJobs.tsx`

---

## 1.1: GLOBAL HEADER

**Container:**
```css
position: fixed;
top: 0;
left: 0;
right: 0;
height: 80px;
background: rgba(11, 15, 26, 0.95);
backdrop-filter: blur(16px);
border-bottom: 1px solid rgba(255, 255, 255, 0.08);
z-index: 9999;
```

**Logo Section:**
- Logo: "OneSocial" [STATIC TEXT]
- Font: Inter, 20px, 700 weight
- Color: #FFFFFF
- Click action: Navigate to home/dashboard

**Navigation Links (Desktop):**
```css
display: none; /* Mobile */
display: flex; /* Desktop 1024px+ */
gap: 32px;
```

Three links:
1. **"Find Work"** [STATIC TEXT] - Active state (current page)
2. **"Hire Talent"** [STATIC TEXT] - Navigate to /hire-talent
3. **"Discover Events"** [STATIC TEXT] - Navigate to /discover-events

**Active State:**
```css
color: #2EE6D6; /* Primary teal */
border-bottom: 2px solid #2EE6D6;
```

**Inactive State:**
```css
color: rgba(255, 255, 255, 0.72);
```

**Right Actions:**
- If signed out: **"Sign In"** button [STATIC TEXT]
- If signed in: User avatar + dropdown menu

---

## 1.2: PAGE HEADER

**Container:**
```css
max-width: 1400px;
margin: 0 auto;
padding: 96px 24px 0 24px; /* Top padding accounts for fixed header */
```

**Title:**
```css
font-size: 48px; /* Desktop 1024px+ */
font-size: 30px; /* Mobile <1024px */
font-weight: 700;
color: #FFFFFF;
line-height: 1.2;
margin-bottom: 16px;
```
- Content: **"Find Work"** [STATIC TEXT]

**Subtitle:**
```css
font-size: 16px;
font-weight: 400;
color: rgba(255, 255, 255, 0.6);
line-height: 1.5;
margin-bottom: 24px;
```
- Content: **"Discover paid opportunities at verified events."** [STATIC TEXT]

---

## 1.3: SEARCH & FILTER BAR (DESKTOP)

**Container:**
```css
display: none; /* Mobile */
display: flex; /* Desktop 1024px+ */
align-items: center;
gap: 12px;
margin-bottom: 24px;
```

---

### Search Input

**Container:**
```css
flex: 1;
height: 48px;
display: flex;
align-items: center;
gap: 12px;
padding: 0 16px;
background: rgba(255, 255, 255, 0.06);
border: 1px solid rgba(255, 255, 255, 0.14);
border-radius: 12px;
transition: all 200ms ease;
```

**Focus State:**
```css
border-color: #2EE6D6;
background: rgba(255, 255, 255, 0.08);
```

**Icon:**
- Icon: Search (Lucide)
- Size: 20px × 20px
- Color: rgba(255, 255, 255, 0.48)

**Input Field:**
```css
flex: 1;
background: transparent;
border: none;
outline: none;
color: #FFFFFF;
font-size: 15px;
font-family: 'Inter', sans-serif;
```

**Placeholder:**
```css
color: rgba(255, 255, 255, 0.48);
```
- Text: **"Role or keyword..."** [STATIC TEXT]

---

### Location Input

**Container:**
```css
width: 220px;
height: 48px;
display: flex;
align-items: center;
gap: 12px;
padding: 0 16px;
background: rgba(255, 255, 255, 0.06);
border: 1px solid rgba(255, 255, 255, 0.14);
border-radius: 12px;
flex-shrink: 0;
```

**Icon:**
- Icon: MapPin (Lucide)
- Size: 20px × 20px
- Color: rgba(255, 255, 255, 0.48)

**Input Field:**
- Same styling as search input
- Placeholder: **"Location"** [STATIC TEXT]

---

### Filters Button

**Specifications:**
```css
height: 48px;
padding: 0 16px;
display: flex;
align-items: center;
gap: 8px;
background: rgba(255, 255, 255, 0.06);
border: 1px solid rgba(255, 255, 255, 0.14);
border-radius: 12px;
color: #FFFFFF;
font-size: 15px;
font-weight: 500;
cursor: pointer;
transition: all 200ms ease;
flex-shrink: 0;
```

**Hover State:**
```css
background: rgba(255, 255, 255, 0.08);
```

**Icon:**
- Icon: SlidersHorizontal (Lucide)
- Size: 18px × 18px

**Text:** **"Filters"** [STATIC TEXT]

**Action:** Opens filter drawer (slide-in from right)

---

### Sort Dropdown

**Button:**
```css
height: 48px;
min-width: 160px;
padding: 0 16px;
display: flex;
align-items: center;
justify-content: space-between;
gap: 8px;
background: rgba(255, 255, 255, 0.06);
border: 1px solid rgba(255, 255, 255, 0.14);
border-radius: 12px;
color: #FFFFFF;
font-size: 15px;
font-weight: 500;
cursor: pointer;
transition: all 200ms ease;
flex-shrink: 0;
```

**Text:** **"Sort by"** [STATIC TEXT]

**Chevron Icon:**
- Icon: ChevronDown (Lucide)
- Size: 16px × 16px
- Rotates 180° when dropdown open

**Dropdown Menu:**
```css
position: absolute;
top: calc(100% + 8px);
right: 0;
min-width: 200px;
background: rgba(11, 15, 26, 0.95);
backdrop-filter: blur(16px);
border: 1px solid rgba(255, 255, 255, 0.12);
border-radius: 12px;
padding: 8px;
box-shadow: 0 12px 30px rgba(0, 0, 0, 0.4);
z-index: 100;
```

**Four Sort Options:**

1. **"Newest"** [STATIC TEXT]
   - Default selected
   - Sorts by posted date (DESC)

2. **"Highest Pay"** [STATIC TEXT]
   - Sorts by compensation (DESC)

3. **"Highest Score"** [STATIC TEXT]
   - Sorts by OneScore required (DESC)

4. **"Soonest"** [STATIC TEXT]
   - Sorts by event date (ASC)

**Dropdown Item:**
```css
padding: 10px 12px;
border-radius: 8px;
color: rgba(255, 255, 255, 0.8);
font-size: 14px;
cursor: pointer;
transition: all 150ms ease;
```

**Dropdown Item Hover:**
```css
background: rgba(255, 255, 255, 0.06);
```

**Dropdown Item Active:**
```css
background: rgba(46, 230, 214, 0.1);
color: #2EE6D6;
```

---

### View Mode Toggle

**Container:**
```css
display: flex;
background: rgba(255, 255, 255, 0.06);
border: 1px solid rgba(255, 255, 255, 0.12);
border-radius: 10px;
padding: 4px;
gap: 4px;
```

**Button:**
```css
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
```

**Button Active:**
```css
background: #2EE6D6;
color: #0B0F1A;
```

**Button Inactive:**
```css
color: rgba(255, 255, 255, 0.6);
```

**Button Inactive Hover:**
```css
background: rgba(255, 255, 255, 0.08);
```

**Two Buttons:**

1. **Grid View**
   - Icon: Grid3x3 (Lucide), 20px
   - Default active

2. **List View**
   - Icon: List (Lucide), 20px

---

## 1.4: MOBILE FILTER CHIPS

**Container:**
```css
display: flex; /* Mobile */
display: none; /* Desktop 1024px+ */
align-items: center;
gap: 8px;
overflow-x: auto;
padding-bottom: 8px;
margin-bottom: 12px;
scrollbar-width: none;
-ms-overflow-style: none;
```

**Hide Scrollbar:**
```css
.mobile-filter-chips::-webkit-scrollbar {
  display: none;
}
```

---

### Chip Pattern

**Specifications:**
```css
height: 44px;
padding: 0 16px;
display: flex;
align-items: center;
gap: 8px;
background: rgba(255, 255, 255, 0.06);
border: 1px solid rgba(255, 255, 255, 0.12);
border-radius: 999px; /* Full pill shape */
white-space: nowrap;
flex-shrink: 0;
font-size: 14px;
font-weight: 500;
cursor: pointer;
transition: all 200ms ease;
```

**Chip Active:**
```css
background: rgba(46, 230, 214, 0.2);
border-color: rgba(46, 230, 214, 0.3);
color: #2EE6D6;
```

**Chip Inactive:**
```css
color: rgba(255, 255, 255, 0.72);
```

---

**Four Chips:**

1. **Filters Chip**
   - Icon: SlidersHorizontal (16px)
   - Text: **"Filters"** [STATIC TEXT]
   - Action: Opens filter drawer

2. **Newest Chip**
   - Text: **"Newest"** [STATIC TEXT]
   - Action: Sort by newest

3. **Highest Pay Chip**
   - Text: **"Highest Pay"** [STATIC TEXT]
   - Action: Sort by pay

4. **Top Rated Chip**
   - Text: **"Top Rated"** [STATIC TEXT]
   - Action: Sort by OneScore

---

## 1.5: JOBS GRID

**Container:**
```css
display: grid;
grid-template-columns: 1fr; /* Mobile <768px */
grid-template-columns: repeat(2, 1fr); /* Tablet 768px-1023px */
grid-template-columns: repeat(3, 1fr); /* Desktop 1024px+ */
gap: 20px;
padding: 24px 0;
```

---

## 1.6: JOB CARD (GRID VIEW)

**Container:**
```css
background: linear-gradient(135deg, rgba(255,255,255,0.12) 0%, rgba(255,255,255,0.06) 100%);
border: 1px solid rgba(255, 255, 255, 0.16);
border-radius: 20px;
overflow: hidden;
cursor: pointer;
transition: all 300ms ease;
box-shadow: 0 12px 30px rgba(0, 0, 0, 0.4), inset 0 1px 0 rgba(255,255,255,0.15);
```

**Hover State:**
```css
transform: translateY(-4px);
border-color: rgba(46, 230, 214, 0.3);
box-shadow: 0 16px 40px rgba(0, 0, 0, 0.5), inset 0 1px 0 rgba(255,255,255,0.2);
```

**Click Action:** Navigate to Job Detail view

---

### Cover Image

**Container:**
```css
position: relative;
width: 100%;
aspect-ratio: 16 / 9;
overflow: hidden;
```

**Image:**
```css
width: 100%;
height: 100%;
object-fit: cover;
transition: transform 400ms ease;
```

**Image on Hover:**
```css
transform: scale(1.05);
```

**Gradient Overlay:**
```css
position: absolute;
inset: 0;
background: linear-gradient(to top, rgba(11, 15, 26, 0.8) 0%, transparent 60%);
pointer-events: none;
```

**Image Source:** [SAMPLE DATA: job.image]
- Example: `'https://images.unsplash.com/photo-1540575467063-178a50c2df87?w=800'`

---

### OneScore Badge (Overlaid on Image)

**Position:**
```css
position: absolute;
top: 12px;
right: 12px;
padding: 6px 12px;
border-radius: 8px;
backdrop-filter: blur(12px);
-webkit-backdrop-filter: blur(12px);
display: flex;
align-items: center;
gap: 4px;
z-index: 10;
```

**Badge Color - High Score (90+):**
```css
background: linear-gradient(135deg, rgba(255, 215, 0, 0.25), rgba(255, 215, 0, 0.15));
border: 1px solid rgba(255, 215, 0, 0.4);
color: #FFD700; /* Gold */
```

**Badge Color - Medium Score (80-89):**
```css
background: linear-gradient(135deg, rgba(46, 230, 214, 0.25), rgba(46, 230, 214, 0.15));
border: 1px solid rgba(46, 230, 214, 0.4);
color: #2EE6D6; /* Teal */
```

**Badge Color - Lower Score (<80):**
```css
background: linear-gradient(135deg, rgba(255, 255, 255, 0.2), rgba(255, 255, 255, 0.1));
border: 1px solid rgba(255, 255, 255, 0.3);
color: rgba(255, 255, 255, 0.9);
```

**Icon:**
- Icon: Shield (Lucide)
- Size: 14px × 14px

**Text:**
```css
font-size: 12px;
font-weight: 600;
letter-spacing: 0.02em;
```
- Format: **"[score] OS"** [SAMPLE DATA: job.oneScoreRequired]
- Example: **"85 OS"**

---

### Card Content Section

**Container:**
```css
padding: 20px;
```

---

### Job Title

**Specifications:**
```css
font-size: 16px;
font-weight: 700;
color: #FFFFFF;
line-height: 1.3;
margin-bottom: 4px;
display: -webkit-box;
-webkit-line-clamp: 2;
-webkit-box-orient: vertical;
overflow: hidden;
text-overflow: ellipsis;
```

**Content:** [SAMPLE DATA: job.title]
- Example: **"Sound Engineer"**

---

### Event Name

**Specifications:**
```css
font-size: 14px;
font-weight: 400;
color: rgba(255, 255, 255, 0.6);
line-height: 1.4;
margin-bottom: 12px;
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
```

**Content:** [SAMPLE DATA: job.eventName]
- Example: **"Tech Summit 2025"**

---

### Job Details List

**Container:**
```css
display: flex;
flex-direction: column;
gap: 8px;
margin-bottom: 16px;
padding-bottom: 16px;
border-bottom: 1px solid rgba(255, 255, 255, 0.08);
```

**Detail Item:**
```css
display: flex;
align-items: center;
gap: 8px;
```

**Icon:**
```css
width: 16px;
height: 16px;
color: rgba(255, 255, 255, 0.6);
flex-shrink: 0;
```

**Text:**
```css
font-size: 12px;
font-weight: 400;
color: rgba(255, 255, 255, 0.72);
line-height: 1.4;
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
```

---

**Three Details:**

1. **Location**
   - Icon: MapPin (Lucide), 16px
   - Text: [SAMPLE DATA: job.location]
   - Example: **"San Francisco, CA"**

2. **Date**
   - Icon: Calendar (Lucide), 16px
   - Text: [SAMPLE DATA: job.date]
   - Example: **"Jan 15-16, 2025"**

3. **Pay**
   - Icon: DollarSign (Lucide), 16px
   - Text: [SAMPLE DATA: job.pay]
   - Example: **"$2,500"**

---

### Tags Section

**Container:**
```css
display: flex;
align-items: center;
gap: 8px;
margin-bottom: 12px;
flex-wrap: wrap;
```

**Tag:**
```css
padding: 4px 10px;
border-radius: 6px;
background: rgba(46, 230, 214, 0.1);
border: 1px solid rgba(46, 230, 214, 0.2);
color: #2EE6D6;
font-size: 10px;
font-weight: 500;
text-transform: uppercase;
letter-spacing: 0.05em;
line-height: 1;
```

**Two Tags:**

1. **Category Tag**
   - Text: [SAMPLE DATA: job.category]
   - Example: **"AUDIO"**

2. **Event Type Tag**
   - Text: [SAMPLE DATA: job.eventType]
   - Example: **"CONFERENCE"**

---

### Posted Time

**Specifications:**
```css
font-size: 10px;
font-weight: 400;
color: rgba(255, 255, 255, 0.48);
line-height: 1.4;
```

**Content:** [SAMPLE DATA: job.posted]
- Example: **"Posted 2 days ago"**

---

## 1.7: SAMPLE JOB DATA STRUCTURE

```javascript
// THIS IS SAMPLE DATA - REPLACE WITH REAL DATABASE DATA
const sampleJob = {
  id: 'j1', // [SAMPLE DATA] - Replace with real job ID
  title: 'Sound Engineer', // [SAMPLE DATA]
  eventName: 'Tech Summit 2025', // [SAMPLE DATA]
  location: 'San Francisco, CA', // [SAMPLE DATA]
  date: 'Jan 15-16, 2025', // [SAMPLE DATA]
  pay: '$2,500', // [SAMPLE DATA]
  oneScoreRequired: 85, // [SAMPLE DATA] - Number 0-100
  category: 'Audio', // [SAMPLE DATA]
  eventType: 'Conference', // [SAMPLE DATA]
  posted: '2 days ago', // [SAMPLE DATA]
  image: 'https://images.unsplash.com/photo-1540575467063-178a50c2df87?w=800' // [SAMPLE DATA]
};
```

---

## 1.8: FILTER DRAWER

**Overlay:**
```css
position: fixed;
inset: 0;
background: rgba(0, 0, 0, 0.7);
backdrop-filter: blur(4px);
z-index: 9998;
animation: fadeIn 200ms ease;
```

**Drawer Container:**
```css
position: fixed;
right: 0;
top: 0;
bottom: 0;
width: 100%; /* Mobile */
max-width: 400px;
background: rgba(11, 15, 26, 0.98);
backdrop-filter: blur(24px);
border-left: 1px solid rgba(255, 255, 255, 0.12);
box-shadow: -8px 0 32px rgba(0, 0, 0, 0.6);
z-index: 9999;
overflow-y: auto;
animation: slideInRight 250ms ease;
```

---

### Drawer Header

**Container:**
```css
padding: 24px;
border-bottom: 1px solid rgba(255, 255, 255, 0.08);
display: flex;
justify-content: space-between;
align-items: center;
position: sticky;
top: 0;
background: rgba(11, 15, 26, 0.98);
backdrop-filter: blur(24px);
z-index: 10;
```

**Title:**
```css
font-size: 20px;
font-weight: 600;
color: #FFFFFF;
```
- Text: **"Filters"** [STATIC TEXT]

**Close Button:**
```css
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
```

**Close Button Hover:**
```css
background: rgba(255, 255, 255, 0.10);
```

**Close Icon:**
- Icon: X (Lucide), 20px
- Color: rgba(255, 255, 255, 0.8)

---

### Filter Section Pattern

**Section Container:**
```css
margin-bottom: 24px;
```

**Section Header:**
```css
display: flex;
justify-content: space-between;
align-items: center;
padding: 12px 24px;
cursor: pointer;
user-select: none;
```

**Section Title:**
```css
font-size: 14px;
font-weight: 600;
color: #FFFFFF;
text-transform: uppercase;
letter-spacing: 0.05em;
```

**Chevron Icon:**
- Icon: ChevronDown (Lucide), 16px
- Color: rgba(255, 255, 255, 0.6)
- Rotates 180° when section expanded

**Section Content:**
```css
padding: 12px 24px;
display: none; /* When collapsed */
display: block; /* When expanded */
```

---

### Filter 1: Category

**Title:** **"Category"** [STATIC TEXT]

**Checkboxes (8 options):**

```css
.checkbox-list {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.checkbox-item {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px;
  border-radius: 8px;
  cursor: pointer;
  transition: background 150ms ease;
}

.checkbox-item:hover {
  background: rgba(255, 255, 255, 0.03);
}

.checkbox {
  width: 18px;
  height: 18px;
  border-radius: 4px;
  border: 2px solid rgba(255, 255, 255, 0.3);
  background: transparent;
  transition: all 200ms ease;
  flex-shrink: 0;
}

.checkbox.checked {
  background: #2EE6D6;
  border-color: #2EE6D6;
}

.checkbox-label {
  font-size: 14px;
  font-weight: 400;
  color: rgba(255, 255, 255, 0.8);
}
```

**Eight Options:** [STATIC TEXT for all labels]
- **"Audio"**
- **"Management"**
- **"Lighting"**
- **"Photography"**
- **"DJ"**
- **"Catering"**
- **"Security"**
- **"Floral"**

---

### Filter 2: Event Type

**Title:** **"Event Type"** [STATIC TEXT]

**Same checkbox styling as Category**

**Seven Options:** [STATIC TEXT for all labels]
- **"Conference"**
- **"Corporate"**
- **"Entertainment"**
- **"Wedding"**
- **"Festival"**
- **"Concert"**
- **"Charity"**

---

### Filter 3: Pay Range

**Title:** **"Pay Range"** [STATIC TEXT]

**Slider:**
```css
padding: 16px 8px;
```

**Labels:**
```css
display: flex;
justify-content: space-between;
margin-bottom: 8px;
font-size: 12px;
font-weight: 500;
color: rgba(255, 255, 255, 0.8);
```

**Min Label:** **"$0"** [STATIC TEXT]  
**Max Label:** **"$10,000+"** [STATIC TEXT]

**Slider Track:**
```css
width: 100%;
height: 6px;
background: rgba(255, 255, 255, 0.1);
border-radius: 3px;
position: relative;
```

**Slider Fill:**
```css
height: 100%;
background: #2EE6D6;
border-radius: 3px;
```

**Slider Thumb:**
```css
width: 20px;
height: 20px;
border-radius: 50%;
background: #2EE6D6;
border: 3px solid #0B0F1A;
position: absolute;
top: 50%;
transform: translate(-50%, -50%);
cursor: grab;
```

**Thumb Active:**
```css
cursor: grabbing;
```

---

### Filter 4: OneScore Required

**Title:** **"OneScore Required"** [STATIC TEXT]

**Value Display:**
```css
font-size: 20px;
font-weight: 700;
color: #2EE6D6;
margin-bottom: 8px;
text-align: center;
```

**Format:** [DYNAMIC: Selected value]
- If 0: **"No Minimum"** [STATIC TEXT]
- If 1-100: **"[value]+"** (e.g., "85+")

**Description:**
```css
font-size: 12px;
font-weight: 400;
color: rgba(255, 255, 255, 0.6);
text-align: center;
margin-bottom: 16px;
```

**Text:** **"Minimum OneScore to show jobs"** [STATIC TEXT]

**Slider:** Same pattern as Pay Range
- Range: 0-100

---

### Drawer Footer

**Container:**
```css
position: sticky;
bottom: 0;
padding: 24px;
background: rgba(11, 15, 26, 0.98);
backdrop-filter: blur(24px);
border-top: 1px solid rgba(255, 255, 255, 0.08);
display: flex;
gap: 12px;
```

**Clear All Button:**
```css
flex: 1;
padding: 12px 20px;
border-radius: 10px;
background: transparent;
border: 1px solid rgba(255, 255, 255, 0.12);
color: rgba(255, 255, 255, 0.8);
font-size: 15px;
font-weight: 600;
text-align: center;
cursor: pointer;
transition: all 200ms ease;
```

**Clear All Hover:**
```css
background: rgba(255, 255, 255, 0.06);
```

**Text:** **"Clear All"** [STATIC TEXT]

**Apply Filters Button:**
```css
flex: 1;
padding: 12px 20px;
border-radius: 10px;
background: #2EE6D6;
color: #0B0F1A;
font-size: 15px;
font-weight: 600;
text-align: center;
cursor: pointer;
transition: all 200ms ease;
```

**Apply Hover:**
```css
background: #26CFC1;
```

**Text:** **"Apply Filters"** [STATIC TEXT]

---

## 1.9: EMPTY STATE

**When no jobs match filters:**

**Container:**
```css
padding: 48px;
text-align: center;
background: linear-gradient(135deg, rgba(255,255,255,0.12) 0%, rgba(255,255,255,0.06) 100%);
border: 1px solid rgba(255, 255, 255, 0.16);
border-radius: 20px;
margin: 32px 0;
```

**Icon:**
- Icon: Briefcase (Lucide)
- Size: 64px × 64px
- Color: rgba(255, 255, 255, 0.48)

**Title:**
```css
font-size: 24px;
font-weight: 700;
color: #FFFFFF;
margin-bottom: 8px;
```
- Text: **"No jobs found"** [STATIC TEXT]

**Description:**
```css
font-size: 14px;
font-weight: 400;
color: rgba(255, 255, 255, 0.6);
max-width: 400px;
margin: 0 auto 24px auto;
```
- Text: **"Try adjusting your filters or check back later for new opportunities."** [STATIC TEXT]

**Clear Filters Button:**
```css
padding: 12px 24px;
border-radius: 10px;
background: #2EE6D6;
color: #0B0F1A;
font-size: 15px;
font-weight: 600;
cursor: pointer;
```
- Text: **"Clear Filters"** [STATIC TEXT]

---

# PAGE 2: HIRE TALENT

**URL:** `/hire-talent`  
**Purpose:** Browse and hire verified professionals  
**Access:** Public  
**Component:** `HireTalent.tsx`

---

## 2.1: PAGE HEADER WITH METRICS

**Title:** **"Hire Talent"** [STATIC TEXT]
- Same styling as Find Work title

**Subtitle:** **"Verified talent with real social reputation."** [STATIC TEXT]
- Same styling as Find Work subtitle

---

### Metrics Dashboard (Desktop Only)

**Container:**
```css
display: none; /* Mobile */
display: flex; /* Desktop 768px+ */
align-items: center;
gap: 32px;
margin-left: auto; /* Floats to right */
```

**Position:** Right side of header, aligned with title

---

**Metric Item Pattern:**
```css
text-align: right;
```

**Metric Value:**
```css
font-size: 32px;
font-weight: 700;
margin-bottom: 4px;
line-height: 1;
```

**Metric Label:**
```css
font-size: 14px;
font-weight: 400;
color: rgba(255, 255, 255, 0.72);
line-height: 1.4;
```

---

**Three Metrics:**

1. **Total Professionals**
   - Value: **"850+"** [STATIC TEXT or DYNAMIC count]
   - Label: **"Professionals"** [STATIC TEXT]
   - Color: #FFFFFF

2. **Average OneScore**
   - Value: **"87"** [DYNAMIC: Calculated average]
   - Label: **"Avg OneScore"** [STATIC TEXT]
   - Color: #2EE6D6

3. **Satisfaction Rate**
   - Value: **"98%"** [STATIC TEXT or DYNAMIC]
   - Label: **"Satisfaction"** [STATIC TEXT]
   - Color: #FFFFFF

---

## 2.2: SEARCH & FILTER BAR

**Same pattern as Find Work, except:**

**Search Placeholder:** **"Search professionals by name, skill, or specialty..."** [STATIC TEXT]

All other components identical to Find Work.

---

## 2.3: PROFESSIONALS GRID

**Same grid pattern as Find Work:**
```css
grid-template-columns: 1fr; /* Mobile */
grid-template-columns: repeat(2, 1fr); /* Tablet */
grid-template-columns: repeat(3, 1fr); /* Desktop */
gap: 20px;
```

---

## 2.4: PROFESSIONAL CARD

**Container:** Same glass-card styling as Job Card

**Click Action:** Navigate to Public Profile view

---

### Cover Image

**Same pattern as Job Card**
- Aspect ratio: 16:9
- Hover scale effect

**Image Source:** [SAMPLE DATA: professional.coverImage]

---

### Elite Badge (Conditional)

**Position:**
```css
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
gap: 4px;
```

**Shown When:** [CONDITIONAL: professional.isElite === true]

**Icon:**
- Icon: Award (Lucide), 14px
- Color: #FFD700 (Gold)

**Text:**
```css
font-size: 11px;
font-weight: 700;
color: #FFD700;
text-transform: uppercase;
letter-spacing: 0.05em;
```
- Content: **"ELITE"** [STATIC TEXT]

---

### OneScore Badge (Bottom Left)

**Position:**
```css
position: absolute;
bottom: 12px;
left: 12px;
```

**Same styling as Job Card OneScore badge**

**Content:** [SAMPLE DATA: professional.oneScore]
- Format: **"[score] OS"** (e.g., "91 OS")

---

### Card Content

**Container:** Same 20px padding

---

**Name/Business:**
```css
font-size: 16px;
font-weight: 700;
color: #FFFFFF;
line-height: 1.3;
margin-bottom: 4px;
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
```
- Content: [SAMPLE DATA: professional.name]
- Example: **"Elite Events Co."**

---

**Role:**
```css
font-size: 14px;
font-weight: 400;
color: rgba(255, 255, 255, 0.6);
line-height: 1.4;
margin-bottom: 8px;
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
```
- Content: [SAMPLE DATA: professional.role]
- Example: **"Event Production"**

---

**Location:**
```css
display: flex;
align-items: center;
gap: 4px;
font-size: 12px;
font-weight: 400;
color: rgba(255, 255, 255, 0.72);
margin-bottom: 12px;
```

**Icon:**
- Icon: MapPin (Lucide), 14px
- Color: rgba(255, 255, 255, 0.6)

**Text:** [SAMPLE DATA: professional.location]
- Example: **"Medellín"**

---

**Rating Section:**
```css
display: flex;
align-items: center;
gap: 4px;
padding-bottom: 12px;
margin-bottom: 12px;
border-bottom: 1px solid rgba(255, 255, 255, 0.08);
```

**Star Icon:**
- Icon: Star (Lucide, filled), 16px
- Color: #F59E0B (Warning/amber)

**Rating Value:**
```css
font-size: 14px;
font-weight: 600;
color: #FFFFFF;
```
- Content: [SAMPLE DATA: professional.rating]
- Example: **"4.9"**

**Review Count:**
```css
font-size: 12px;
font-weight: 400;
color: rgba(255, 255, 255, 0.6);
margin-left: 2px;
```
- Format: **"([count])"** [SAMPLE DATA: professional.reviewCount]
- Example: **"(28)"**

---

**Skills Tags:**
```css
display: flex;
gap: 4px;
margin-bottom: 12px;
flex-wrap: wrap;
```

**Tag:**
```css
font-size: 10px;
font-weight: 500;
padding: 4px 8px;
border-radius: 6px;
background: rgba(46, 230, 214, 0.1);
border: 1px solid rgba(46, 230, 214, 0.2);
color: #2EE6D6;
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
line-height: 1;
```

**Shows:** First 2-3 skills [SAMPLE DATA: professional.skills array]
- Example: **"Production"** • **"Full-service"** • **"Luxury"**

---

**Pricing:**
```css
font-size: 14px;
font-weight: 600;
color: #2EE6D6;
line-height: 1.4;
margin-bottom: 4px;
```

**Two Types:**

1. **Fixed Pricing** [CONDITIONAL: pricingType === 'fixed']
   - Content: [SAMPLE DATA: professional.price]
   - Example: **"$220 / night"**

2. **Custom Pricing** [CONDITIONAL: pricingType === 'custom']
   - Content: **"Custom Pricing"** [STATIC TEXT]

---

**Completed Jobs:**
```css
font-size: 11px;
font-weight: 400;
color: rgba(255, 255, 255, 0.6);
line-height: 1.4;
```
- Format: **"[count] jobs completed"** [SAMPLE DATA: professional.completedJobs]
- Example: **"47 jobs completed"**

---

## 2.5: SAMPLE PROFESSIONAL DATA

```javascript
// THIS IS SAMPLE DATA - REPLACE WITH REAL DATABASE DATA
const sampleProfessional = {
  id: 'p1', // [SAMPLE DATA]
  name: 'Elite Events Co.', // [SAMPLE DATA]
  role: 'Event Production', // [SAMPLE DATA]
  location: 'Medellín', // [SAMPLE DATA]
  oneScore: 91, // [SAMPLE DATA] Number 0-100
  rating: 4.9, // [SAMPLE DATA] Number 0-5
  reviewCount: 28, // [SAMPLE DATA] Integer
  isElite: true, // [SAMPLE DATA] Boolean
  coverImage: 'https://images.unsplash.com/...', // [SAMPLE DATA]
  specialty: 'Full-service events', // [SAMPLE DATA]
  description: 'Complete event production...', // [SAMPLE DATA]
  skills: ['Production', 'Full-service', 'Luxury'], // [SAMPLE DATA] Array
  pricingType: 'custom', // [SAMPLE DATA] 'custom' or 'fixed'
  price: null, // [SAMPLE DATA] String if fixed, null if custom
  completedJobs: 47 // [SAMPLE DATA] Integer
};
```

---

## 2.6: FILTER DRAWER DIFFERENCES

**Same drawer structure as Find Work, but with different filter options:**

### Filter 1: Specialty/Category

**Title:** **"Specialty"** [STATIC TEXT]

**Six Options:** [STATIC TEXT for all]
- **"Event Production"**
- **"Photography"**
- **"Videography"**
- **"DJ Services"**
- **"Wellness"**
- **"Catering"**

### Filter 2: Experience Level

**Title:** **"Experience Level"** [STATIC TEXT]

**Four Options:** [STATIC TEXT for all]
- **"Entry Level"**
- **"Intermediate"**
- **"Expert"**
- **"Elite"**

### Filter 3: Pricing Range

**Same as Find Work Pay Range**
- Title: **"Pricing Range"** [STATIC TEXT]
- Range: $0 - $10,000+

### Filter 4: OneScore

**Same as Find Work**

---

# PAGE 3: DISCOVER EVENTS

**URL:** `/discover-events`  
**Purpose:** Browse and purchase tickets for events  
**Access:** Public  
**Component:** `DiscoverEvents.tsx`

---

## 3.1: PAGE HEADER

**Title:** **"Discover Events"** [STATIC TEXT]
- Same styling as other pages

**Subtitle:** **"Attend curated events and unlock real-world credibility."** [STATIC TEXT]
- Same styling as other pages

---

## 3.2: FILTER DROPDOWNS (ALWAYS VISIBLE)

**Container:**
```css
display: flex;
flex-direction: column; /* Mobile */
flex-direction: row; /* Desktop 768px+ */
gap: 16px;
margin-bottom: 24px;
```

---

### Dropdown Pattern

**Container:**
```css
position: relative;
flex: 1;
```

**Select Element:**
```css
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
appearance: none; /* Remove default arrow */
transition: all 150ms ease;
```

**Select Hover:**
```css
background: rgba(255, 255, 255, 0.1);
```

**Select Focus:**
```css
outline: none;
border-color: #2EE6D6;
```

**Chevron Icon (Positioned):**
```css
position: absolute;
right: 16px;
top: 50%;
transform: translateY(-50%);
width: 16px;
height: 16px;
color: rgba(255, 255, 255, 0.5);
pointer-events: none;
```
- Icon: ChevronDown (Lucide)

---

### Filter 1: Location

**Default Option:** **"All Locations"** [STATIC TEXT]

**Five Options:** [STATIC TEXT for all]
- **"San Francisco"**
- **"Oakland"**
- **"San Jose"**
- **"Berkeley"**
- **"Palo Alto"**

---

### Filter 2: Price Range

**Default Option:** **"Any Price"** [STATIC TEXT]

**Six Options:** [STATIC TEXT for all]
- **"Free"**
- **"Low to High"** (sort option)
- **"High to Low"** (sort option)
- **"$0 - $50"**
- **"$50 - $150"**
- **"$150+"**

---

### Filter 3: Ticket Type

**Default Option:** **"All Types"** [STATIC TEXT]

**Four Options:** [STATIC TEXT for all]
- **"General Admission"**
- **"VIP"**
- **"Free Entry"**
- **"Early Bird"**

---

### Filter 4: Date

**Default Option:** **"Any Date"** [STATIC TEXT]

**Four Options:** [STATIC TEXT for all]
- **"Today"**
- **"This Week"**
- **"This Month"**
- **"Next Month"**

---

### Filter 5: Privacy

**Default Option:** **"All Events"** [STATIC TEXT]

**Two Options:** [STATIC TEXT for all]
- **"Public"**
- **"Private"**

---

## 3.3: EVENTS GRID

**Container:**
```css
display: grid;
grid-template-columns: 1fr; /* Mobile <768px */
grid-template-columns: repeat(2, 1fr); /* Tablet 768px-1023px */
grid-template-columns: repeat(3, 1fr); /* Desktop 1024px-1439px */
grid-template-columns: repeat(4, 1fr); /* Desktop XL 1440px+ */
gap: 20px;
padding: 24px 0;
```

---

## 3.4: EVENT CARD

**Container:** Same glass-card styling as previous cards

**Click Action:** Navigate to Event Detail view

---

### Cover Image

**Container:**
```css
position: relative;
width: 100%;
aspect-ratio: 4 / 3; /* More square than job cards */
overflow: hidden;
```

**Image:** Same hover scale effect

**Image Source:** [SAMPLE DATA: event.coverImage]

---

### Status Badge (Top Right)

**Position:**
```css
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
```

---

**Three Status Variants:**

1. **Published/Live** [DEFAULT]
   ```css
   background: rgba(16, 185, 129, 0.25);
   border: 1px solid rgba(16, 185, 129, 0.4);
   color: #10B981; /* Success green */
   ```
   - Text: **"LIVE"** [STATIC TEXT]

2. **Sold Out** [CONDITIONAL: ticketsRemaining === 0]
   ```css
   background: rgba(239, 68, 68, 0.25);
   border: 1px solid rgba(239, 68, 68, 0.4);
   color: #EF4444; /* Error red */
   ```
   - Text: **"SOLD OUT"** [STATIC TEXT]

3. **Low Availability** [CONDITIONAL: ticketsRemaining > 0 && ticketsRemaining < 10]
   ```css
   background: rgba(245, 158, 11, 0.25);
   border: 1px solid rgba(245, 158, 11, 0.4);
   color: #F59E0B; /* Warning amber */
   ```
   - Text: **"LOW TICKETS"** [STATIC TEXT]

---

### Jobs Available Badge (Bottom Left - Conditional)

**Position:**
```css
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
gap: 4px;
z-index: 10;
```

**Shown When:** [CONDITIONAL: event.hasJobs === true]

**Icon:**
- Icon: Briefcase (Lucide), 14px
- Color: #A855F7 (Purple)

**Text:**
```css
font-size: 11px;
font-weight: 700;
color: #A855F7;
```
- Format: **"[count] Jobs"** [SAMPLE DATA: event.jobCount]
- Example: **"3 Jobs"**

---

### Card Content

**Container:** Same 20px padding

---

**Event Title:**
```css
font-size: 16px;
font-weight: 700;
color: #FFFFFF;
line-height: 1.3;
margin-bottom: 12px;
display: -webkit-box;
-webkit-line-clamp: 2;
-webkit-box-orient: vertical;
overflow: hidden;
text-overflow: ellipsis;
```
- Content: [SAMPLE DATA: event.title]
- Example: **"Tech Summit 2025"**

---

**Details Section:**
```css
display: flex;
flex-direction: column;
gap: 8px;
margin-bottom: 16px;
padding-bottom: 16px;
border-bottom: 1px solid rgba(255, 255, 255, 0.08);
```

**Detail Item:** Same pattern as Job Card details

**Two Details:**

1. **Date**
   - Icon: Calendar (Lucide), 14px
   - Text: [SAMPLE DATA: event.date]
   - Example: **"January 15-16, 2025"**

2. **Location**
   - Icon: MapPin (Lucide), 14px
   - Text: [SAMPLE DATA: event.location]
   - Example: **"San Francisco, CA"**

---

**Ticket Info Section:**
```css
display: flex;
flex-direction: column;
gap: 4px;
margin-bottom: 16px;
```

---

**Tickets Remaining:**
```css
display: flex;
align-items: center;
gap: 4px;
font-size: 12px;
line-height: 1.4;
```

**Icon:**
- Icon: Ticket (Lucide), 14px
- Color: #2EE6D6

**Text (Normal):**
```css
color: rgba(255, 255, 255, 0.72);
```
- Format: **"[remaining] of [total] left"**
- [SAMPLE DATA: event.ticketsRemaining, event.totalTickets]
- Example: **"34 of 100 left"**

**Text (Sold Out):**
```css
color: #EF4444;
font-weight: 600;
```
- [CONDITIONAL: ticketsRemaining === 0]
- Content: **"Sold Out"** [STATIC TEXT]

**Count Highlight:**
```css
font-weight: 600;
color: #2EE6D6;
```

---

**Price:**
```css
display: flex;
align-items: center;
gap: 4px;
font-size: 14px;
line-height: 1.4;
```

**Icon:**
- Icon: DollarSign (Lucide), 16px
- Color: #2EE6D6

**Price Value:**
```css
font-weight: 700;
color: #FFFFFF;
```

**Two Formats:**

1. **Paid Event** [CONDITIONAL: ticketPrice > 0]
   - Format: **"$[price]"** [SAMPLE DATA: event.ticketPrice]
   - Example: **"$149"**

2. **Free Event** [CONDITIONAL: ticketPrice === 0]
   - Content: **"FREE"** [STATIC TEXT]
   - Color: #2EE6D6

---

**Host Section:**
```css
display: flex;
align-items: center;
gap: 8px;
```

**Avatar:**
```css
width: 28px;
height: 28px;
border-radius: 50%;
background: var(--gradient-glass);
overflow: hidden;
flex-shrink: 0;
```
- Image: [SAMPLE DATA: event.host.avatar or generated from name]

**Host Info:**
```css
display: flex;
align-items: center;
gap: 4px;
flex: 1;
min-width: 0;
```

**Host Name:**
```css
font-size: 12px;
font-weight: 500;
color: rgba(255, 255, 255, 0.8);
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
```
- Content: [SAMPLE DATA: event.host.name]
- Example: **"TechCorp Events"**

**Separator:**
```css
font-size: 12px;
color: rgba(255, 255, 255, 0.48);
flex-shrink: 0;
```
- Content: **"•"** [STATIC TEXT]

**OneScore:**
```css
font-size: 11px;
font-weight: 600;
color: #2EE6D6;
flex-shrink: 0;
```
- Format: **"[score] OS"** [SAMPLE DATA: event.host.oneScore]
- Example: **"92 OS"**

---

## 3.5: SAMPLE EVENT DATA

```javascript
// THIS IS SAMPLE DATA - REPLACE WITH REAL DATABASE DATA
const sampleEvent = {
  id: '1', // [SAMPLE DATA]
  title: 'Tech Summit 2025', // [SAMPLE DATA]
  coverImage: 'https://images.unsplash.com/...', // [SAMPLE DATA]
  date: 'January 15-16, 2025', // [SAMPLE DATA]
  location: 'San Francisco, CA', // [SAMPLE DATA]
  ticketPrice: 149, // [SAMPLE DATA] Number (0 for free)
  ticketsRemaining: 34, // [SAMPLE DATA] Integer
  totalTickets: 100, // [SAMPLE DATA] Integer
  host: {
    name: 'TechCorp Events', // [SAMPLE DATA]
    avatar: 'https://...', // [SAMPLE DATA] Optional
    oneScore: 92 // [SAMPLE DATA] Number 0-100
  },
  hasJobs: true, // [SAMPLE DATA] Boolean
  jobCount: 3, // [SAMPLE DATA] Integer (if hasJobs)
  status: 'published', // [SAMPLE DATA] String
  startDate: '2025-01-15', // [SAMPLE DATA] ISO date
  endDate: '2025-01-16' // [SAMPLE DATA] ISO date
};
```

---

## 3.6: EMPTY STATE (ALL PAGES)

**Same styling for all three pages**

**When to show:**
- Find Work: No jobs match filters
- Hire Talent: No professionals match filters
- Discover Events: No events match filters

**Content varies by page:**

**Find Work:**
- Icon: Briefcase
- Title: **"No jobs found"** [STATIC TEXT]
- Description: **"Try adjusting your filters or check back later for new opportunities."** [STATIC TEXT]
- Button: **"Clear Filters"** [STATIC TEXT]

**Hire Talent:**
- Icon: Users
- Title: **"No professionals found"** [STATIC TEXT]
- Description: **"Try adjusting your filters to see more talent."** [STATIC TEXT]
- Button: **"Clear Filters"** [STATIC TEXT]

**Discover Events:**
- Icon: Calendar
- Title: **"No events found"** [STATIC TEXT]
- Description: **"Try adjusting your filters or check back later for new events."** [STATIC TEXT]
- Button: **"Clear Filters"** [STATIC TEXT]

---

# RESPONSIVE BREAKPOINTS

**All three pages use:**

```css
/* Mobile */
@media (max-width: 767px) {
  - 1 column grid
  - Mobile filter chips (Find Work, Hire Talent)
  - Stacked filter dropdowns (Discover Events)
  - No metrics display
  - Full-width cards
}

/* Tablet */
@media (min-width: 768px) and (max-width: 1023px) {
  - 2 column grid
  - Show metrics (Hire Talent)
  - Responsive spacing
}

/* Desktop */
@media (min-width: 1024px) {
  - 3 column grid (Find Work, Hire Talent)
  - Desktop search bar
  - Show metrics dashboard
  - Filter drawer
}

/* Desktop XL */
@media (min-width: 1440px) {
  - 4 column grid (Discover Events only)
  - Maximum spacing
}
```

---

# COLOR SYSTEM REFERENCE

**Primary Colors:**
- Primary Teal: `#2EE6D6`
- Primary Teal Hover: `#26CFC1`
- Background: `#0B0F1A`

**Text Colors:**
- Text 100%: `#FFFFFF`
- Text 80%: `rgba(255, 255, 255, 0.8)`
- Text 72%: `rgba(255, 255, 255, 0.72)`
- Text 60%: `rgba(255, 255, 255, 0.6)`
- Text 48%: `rgba(255, 255, 255, 0.48)`

**Status Colors:**
- Success: `#10B981` (Green)
- Error: `#EF4444` (Red)
- Warning: `#F59E0B` (Amber)
- Purple: `#A855F7` (Jobs badge)
- Gold: `#FFD700` (Elite badge)

**Border Colors:**
- Border 16%: `rgba(255, 255, 255, 0.16)`
- Border 14%: `rgba(255, 255, 255, 0.14)`
- Border 12%: `rgba(255, 255, 255, 0.12)`
- Border 8%: `rgba(255, 255, 255, 0.08)`

---

# SPACING SYSTEM (8px base)

- space-0.5: `2px`
- space-1: `4px`
- space-2: `8px`
- space-3: `12px`
- space-4: `16px`
- space-5: `20px`
- space-6: `24px`
- space-8: `32px`
- space-12: `48px`

---

# TYPOGRAPHY SCALE

**Headings:**
- Display Large: 48px / 700 (Desktop titles)
- Display Small: 30px / 700 (Mobile titles)
- Heading 3: 20px / 600 (Section titles)
- Heading 4: 16px / 700 (Card titles)

**Body:**
- Body Large: 16px / 400 (Subtitles)
- Body Regular: 14px / 400 (Standard text)
- Body Small: 12px / 400 (Details)
- Body Tiny: 10px / 400 (Meta text)

**Labels:**
- Label Medium: 14px / 600 (Buttons)
- Label Small: 12px / 600 (Badges)

**Font Family:** Inter (system fallback: -apple-system, sans-serif)

---

# PRODUCTION CHECKLIST

Before going live, replace ALL [SAMPLE DATA] with:

✅ **Find Work:**
- [ ] Real job listings from database
- [ ] Actual event images
- [ ] Real OneScore requirements
- [ ] Accurate pay amounts
- [ ] Current posted times
- [ ] Live location data
- [ ] Actual categories/types

✅ **Hire Talent:**
- [ ] Real professional profiles
- [ ] Actual portfolio images
- [ ] Real ratings/reviews
- [ ] Current availability
- [ ] Accurate pricing
- [ ] Live OneScores
- [ ] Completed job counts

✅ **Discover Events:**
- [ ] Real event listings
- [ ] Actual event images
- [ ] Current ticket availability
- [ ] Real-time pricing
- [ ] Accurate dates
- [ ] Live host information
- [ ] Active job postings

---

**END OF PRODUCTION SPECIFICATIONS**

**Files:** 
- `/public/MARKETPLACE_PRODUCTION_SPECS.md`

**Status:** ✅ Ready for Figma recreation and production build  
**Total Lines:** ~2,500 lines (condensed for clarity)  
**All Sample Data:** Clearly marked for removal  
**All Static Text:** Clearly labeled  
**All Conditional Logic:** Documented

🎯 **Ready to build in Figma and deploy to production!**

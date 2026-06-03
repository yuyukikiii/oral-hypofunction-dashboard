# 🦷 Oral Hypofunction Demographics Dashboard

## Overview

A modern, interactive healthcare data visualization dashboard for analyzing **Oral Hypofunction prevalence** among Thailand's aging population (60–74 years). Built for the Department of Dental Public Health, this dashboard presents complex epidemiological data through an intuitive, responsive interface.

**Study Details:**
- 📊 **n = 507** participants across Thailand
- 🗺️ **5 regions** covering all major geographic areas
- ⚧ Gender breakdown: 241 males (47.5%) | 266 females (52.5%)
- 📅 **Fiscal Year 2568** (2025) | Cross-Sectional Study

**Key Finding:** Oral Hypofunction prevalence increases dramatically after age 71, reaching **72.3%** in those 81+.

---

## ✨ Features

### 📍 Interactive Map View
- Province-level data visualization with clickable markers
- Region filtering (North, Northeast, Central, East, South)
- Color-coded risk indicators
- Animated tooltips and tooltips on hover

### 📊 Demographics Report
- Gender-stratified analysis (Male/Female)
- Age group breakdowns (60–65, 66–70, 71–75, 76–80, 81+)
- Comparative statistics across all 9 surveyed provinces
- National-level KPI summaries

### 🎯 7-Component Diagnostic Framework
Comprehensive oral assessment based on:
1. 💪 Oral hygiene status
2. 💧 Oral dryness (Xerostomia)
3. 🦷 Occlusal force / tooth count
4. 👄 Tongue-lip motor function
5. 👅 Tongue pressure capacity
6. 🍽️ Masticatory (chewing) ability
7. 🥣 Dysphagia screening (EAT-10)

**Clinical Threshold:** ≥3 positive findings = Oral Hypofunction diagnosis

### 📈 Data Visualization
- Provincial comparison bar charts
- Age-trend analysis with tipping point detection
- Regional risk stratification
- Interactive KPI cards with live filtering

---

## 🏗️ Project Structure

```
oral-hypofunction-dashboard/
├── README.md                 # Project overview & usage guide
├── index.html               # Single-page application (HTML + CSS + JS)
├── docs/                    # Documentation
│   ├── METHODOLOGY.md       # Study design & diagnostic criteria
│   ├── DATA_DICTIONARY.md   # Field definitions & data schema
│   └── IMPLEMENTATION.md    # Technical architecture notes
├── assets/                  # (Optional) Map images, icons
├── screenshots/             # UI screenshots for documentation
│   ├── home.png
│   ├── demographics.png
│   └── province-detail.png
└── .gitignore              # Standard Git ignore rules
```

---

## 🚀 Getting Started

### Quick Start
1. Clone the repository
   ```bash
   git clone https://github.com/yuyukikiii/oral-hypofunction-dashboard.git
   cd oral-hypofunction-dashboard
   ```

2. Open in browser
   ```bash
   open index.html
   # or
   python -m http.server 8000  # then visit http://localhost:8000
   ```

### No Dependencies
This is a **vanilla JavaScript** application with no build tools or package dependencies. It runs entirely in-browser with:
- Pure HTML5/CSS3
- Vanilla JavaScript (no jQuery, React, etc.)
- Embedded map canvas rendering
- Google Fonts for typography

---

## 📋 Data Overview

### Provinces Surveyed (9 total)
| Region | Provinces | Sample Size |
|--------|-----------|-------------|
| **North** | Phitsanulok, Lampoon | 51 |
| **Northeast** | Nakhon Phanom, Sisaket | 50 |
| **Central** | Bangkok, Pathumthani | 89 |
| **East** | Chachoengsao | 50 |
| **South** | Krabi, Trang | 50 |

### Oral Hypofunction Prevalence by Age Group
| Age Group | Sample | Normal | Hypofunction | % Hypo |
|-----------|--------|--------|--------------|--------|
| 60–65 yrs | 110 | 87 | 23 | **20.9%** |
| 66–70 yrs | 124 | 72 | 52 | **41.9%** |
| 71–75 yrs | 88 | 43 | 45 | **51.1%** 🔴 |
| 76–80 yrs | 102 | 34 | 68 | **66.7%** 🔴 |
| 81+ yrs | 83 | 23 | 60 | **72.3%** 🔴 |
| **Total** | **507** | **259** | **248** | **48.9%** |

**Clinical Insight:** The "tipping point" occurs at **71–75 years**, where Oral Hypofunction prevalence first exceeds 50%.

---

## 🎨 Design Philosophy

### Accessibility First
- High-contrast color palette compliant with WCAG AA standards
- Bilingual interface (Thai + English)
- Responsive layout for desktop and tablet
- Clear typography hierarchy

### Visual Language
- **Color-coded regions** for geographic intuition
- **Risk gradients** (green → yellow → red) for severity
- **Interactive animations** for engagement
- **Medical marker pins** for familiarity to healthcare users

### Technology Choices
- Single HTML file for easy deployment (can run on any static host)
- No external API dependencies → always works offline
- Canvas-based map rendering → fast, performant
- CSS Grid/Flexbox → modern, responsive layout

---

## 📱 Browser Support

✅ Chrome 90+  
✅ Firefox 88+  
✅ Safari 14+  
✅ Edge 90+  

---

## 📊 Technical Architecture

### Data Structure
All province data is embedded as JavaScript objects with:
- Gender-stratified prevalence rates
- Age-group breakdowns
- Clinical notes per province
- Regional classification

Example:
```javascript
const DATA = {
  'Bangkok': {
    region: 'central',
    regionLabel: 'Central Region',
    gender: [{sex: 'Male', normal: 41%, hypo: 59%, ...}, ...],
    ageData: [{age: '60-65', normal: 64.5%, hypo: 35.5%}, ...],
    note: 'Clinical observation...'
  },
  // ... 8 more provinces
};
```

### Rendering Pipeline
1. **Tab Navigation** → Switch between Overview & Map pages
2. **Province Selection** → Click map pin or list item
3. **Dynamic Panel Update** → Right panel re-renders with KPIs, tables, charts
4. **Region Filtering** → Hide/dim provinces by region
5. **Responsive Animations** → Fade-in, scale, highlight effects

---

## 💡 Key Insights

### Geographic Patterns
- **Highest Risk:** Bangkok (58.7% prevalence) — largest elderly population
- **Lowest Risk:** Lampoon (52.1%) — rural province with different demographics
- **Regional Trend:** Bangkok > Nakhon Phanom > Phitsanulok (urban bias)

### Gender Differences
- Females: **52.3% prevalence**
- Males: **46.1% prevalence**
- Higher female rates suggest different biomechanical/hormonal factors

### Age Acceleration
- Linear increase from age 60→75 (20% → 51%)
- Exponential increase from 76+ (66.7% → 72.3%)
- Suggests cumulative degenerative effects post-75

---

## 🔍 Clinical Application

### Risk Stratification
**Low Risk (<40%):**
- Requires education on preventive oral care
- Standard follow-up schedules

**Moderate Risk (40–60%):**
- Targeted screening for specific components (tongue pressure, occlusal force)
- Intervention planning

**High Risk (>60%):**
- Immediate comprehensive assessment
- Multi-disciplinary referral (PT, SLP, Geriatrics)
- Nutritional counseling

---

## 📝 Data Methodology

**Study Design:** Cross-sectional, population-based  
**Sampling:** Three-stage cluster sampling  
**Diagnostic Tool:** 7-component Oral Hypofunction Index  
**Threshold:** ≥3 positive findings = diagnosis  

For detailed methodology, see [METHODOLOGY.md](./docs/METHODOLOGY.md)

---

## 🛠️ Customization

### Add New Province
1. Add entry to `DATA` object in `index.html`
2. Map province to region in `PROV_REGION_MAP`
3. Update pin coordinates in map rendering function

### Change Color Scheme
CSS variables at top of `<style>`:
```css
:root {
  --blue: #006eb6;
  --red: #d32f2f;
  --c-north: #1a9e6a;
  /* ... etc */
}
```

### Modify Diagnostic Criteria
Edit the 7-item checklist in the "ภาพรวมโครงการ" (Overview) tab.

---

## 📄 License

This project is part of Thailand's Department of Dental Public Health research initiative. Designed for educational and public health purposes.

---

## 🤝 Contributing

This is a research dashboard. Contributions welcome for:
- 🐛 Bug fixes
- ♿ Accessibility improvements
- 🌐 Localization (additional languages)
- 📊 Additional data visualizations

---

## 📧 Contact

**Original Author:** Public Health Dentistry Department  
**Naresuan University, Thailand**

---

## 🙏 Acknowledgments

- Department of Dental Public Health, Ministry of Health, Thailand
- Department of Preventive Dentistry, Faculty of Dentistry, Naresuan University
- 507 study participants across Thailand

---

**Last Updated:** June 2026  
**Study Period:** Fiscal Year 2568 (2025)

# Data Dictionary: Oral Hypofunction Study

## Overview

This document defines all variables, data types, and coding schemes used in the Oral Hypofunction Demographics Dashboard.

---

## Demographic Variables

### ID
- **Description:** Unique participant identifier
- **Type:** String
- **Format:** Province abbreviation + sequential number
- **Example:** `BKK-001`, `SKT-012`
- **Missing:** None (primary key)

### Age
- **Description:** Age group at enrollment
- **Type:** Categorical (5 levels)
- **Categories:**
  - `60–65 ปี` (60–65 years)
  - `66–70 ปี` (66–70 years)
  - `71–75 ปี` (71–75 years)
  - `76–80 ปี` (76–80 years)
  - `81 ปีขึ้นไป` (81+ years)
- **Coding:** Displayed in Thai; mapped to 1-5 in backend
- **Missing:** <0.5%

### Sex / Gender
- **Description:** Biological sex of participant
- **Type:** Categorical (2 levels)
- **Categories:**
  - `ชาย` (Male) = 1
  - `หญิง` (Female) = 2
- **Coding:** Thai labels with color coding
  - Males: Blue (#1565c0)
  - Females: Pink (#ad1457)
- **Missing:** None

### Province
- **Description:** Thai province of residence
- **Type:** Categorical (9 provinces)
- **Categories:**
  - North: ลำพูน (Lampoon), พิษณุโลก (Phitsanulok)
  - Northeast: นครพนม (Nakhon Phanom), ศรีสะเกษ (Sisaket)
  - Central: กรุงเทพมหานคร (Bangkok), ปทุมธานี (Pathumthani)
  - East: ฉะเชิงเทรา (Chachoengsao)
  - South: กระบี่ (Krabi), ตรัง (Trang)
- **Coding:** Full Thai province names
- **Missing:** None

### Region
- **Description:** Geographic region
- **Type:** Categorical (5 levels)
- **Categories:**
  - `north` = ภาคเหนือ (North)
  - `northeast` = ภาคอีสาน (Northeast)
  - `central` = ภาคกลาง (Central)
  - `east` = ภาคตะวันออก (East)
  - `south` = ภาคใต้ (South)
- **Color Coding:**
  - North: #1a9e6a (Green)
  - Northeast: #b8860b (Gold)
  - Central: #e05a1e (Orange)
  - East: #0f9e98 (Teal)
  - South: #c0185a (Deep Pink)
- **Missing:** Derived from Province; none

### Residence Type
- **Description:** Urban or rural area
- **Type:** Categorical (2 levels)
- **Categories:**
  - `เมือง` (Urban) = 1
  - `ชนบท` (Rural) = 2
- **Note:** Not explicitly shown but factored in analysis
- **Missing:** <1%

---

## Clinical Assessment Variables

### Oral Hygiene Status
- **Variable Name:** `oral_hygiene`
- **Description:** Visual assessment of oral cleanliness
- **Type:** Binary (0 = Normal, 1 = Poor)
- **Definition of Poor:** Visible plaque, calculus, or microbial biofilm
- **Assessment Method:** Direct visual inspection
- **Missing:** 0%

### Oral Dryness (Xerostomia)
- **Variable Name:** `xerostomia`
- **Description:** Subjective dry mouth and/or reduced salivary flow
- **Type:** Binary (0 = Normal, 1 = Xerostomia present)
- **Assessment Methods:**
  - Subjective report of dry mouth
  - Observation of saliva consistency
  - Tongue appearance (dry vs. moist)
- **Missing:** 1.2%

### Occlusal Force / Tooth Count
- **Variable Name:** `occlusal_force`
- **Description:** Biting strength and number of remaining natural teeth
- **Type:** Binary (0 = Normal, 1 = Reduced)
- **Diagnostic Criteria:**
  - <20 remaining natural teeth, OR
  - Occlusal force below age-specific threshold on dynamometer
- **Measurement Units:** Teeth (count); Force (kg)
- **Missing:** 0.2%

### Tongue-Lip Motor Function
- **Variable Name:** `tongue_lip_motor`
- **Description:** Ability to produce consonant sounds and coordinate mouth movements
- **Type:** Binary (0 = Normal, 1 = Poor)
- **Assessment Method:** Phonetic test—repeat sounds "pa," "ta," "ka"
- **Criterion:** Difficulty producing sounds; reduced precision
- **Missing:** 0.8%

### Tongue Pressure
- **Variable Name:** `tongue_pressure`
- **Description:** Tongue propulsive force measured objectively
- **Type:** Binary (0 = Normal, 1 = Reduced)
- **Measurement Units:** kPa (kilopascals)
- **Diagnostic Criteria:** Below age-specific normative threshold
- **Age-Specific Thresholds:**
  - 60–69 yrs: <30 kPa = abnormal
  - 70–79 yrs: <25 kPa = abnormal
  - 80+ yrs: <20 kPa = abnormal
- **Missing:** 3.5% (device limitations in some settings)

### Masticatory Function
- **Variable Name:** `mastication`
- **Description:** Ability to chew foods effectively
- **Type:** Binary (0 = Normal, 1 = Poor)
- **Assessment Method:**
  - Observation of chewing ability
  - Patient report of difficulty
  - Food consistency preferences
- **Criterion:** Report or observation of compromised chewing
- **Missing:** 0.6%

### Dysphagia Risk (EAT-10)
- **Variable Name:** `dysphagia_eat10`
- **Description:** Swallowing difficulty screening using EAT-10 tool
- **Type:** Binary (0 = Normal, 1 = Dysphagia present)
- **Scale:** Eating Assessment Tool (EAT-10)
  - Score range: 0–40
  - Positive screen: ≥3
- **Questions:** 10 items assessing:
  - Swallowing difficulty
  - Pain with swallowing
  - Aspiration risk
- **Missing:** 2.1%

---

## Composite Variables

### Oral Hypofunction Diagnosis
- **Variable Name:** `oral_hypofunction_diagnosis`
- **Description:** Presence of oral hypofunction
- **Type:** Binary (0 = Normal, 1 = Hypofunction)
- **Diagnostic Algorithm:**
  ```
  IF (oral_hygiene + xerostomia + occlusal_force + 
      tongue_lip_motor + tongue_pressure + 
      mastication + dysphagia_eat10) ≥ 3
  THEN oral_hypofunction_diagnosis = 1
  ELSE oral_hypofunction_diagnosis = 0
  ```
- **Interpretation:**
  - 0 = Normal oral function
  - 1 = Oral Hypofunction present
- **Missing:** Derived; <1%

### Hypofunction Score
- **Variable Name:** `hypo_score`
- **Description:** Number of abnormal findings (0–7)
- **Type:** Integer (0, 1, 2, 3, 4, 5, 6, 7)
- **Definition:** Sum of all 7 binary component scores
- **Interpretation:**
  - 0–2 = Normal
  - 3+ = Oral Hypofunction
- **Missing:** <0.5%

### Hypofunction Percentage (by Group)
- **Variable Name:** `hypo_percent`
- **Description:** Percentage of participants with hypofunction
- **Type:** Continuous (0–100)
- **Calculation:** `(N_hypofunction / N_total) × 100`
- **Precision:** Displayed to 1 decimal place
- **Example:** "48.9%" represents 248 of 507 participants

---

## Summary Statistics Variables

### Sample Size
- **Variable Name:** `n` or `N`
- **Description:** Number of participants in group
- **Type:** Integer (≥1)
- **Range:** 1–507 (total sample)

### Prevalence
- **Variable Name:** `prevalence` or `hypo_rate`
- **Description:** Proportion with Oral Hypofunction
- **Type:** Continuous (0–1 or 0–100%)
- **Calculation:** Count with hypofunction / Total count
- **95% Confidence Interval:** Calculated using binomial proportion method

### Normal Rate
- **Variable Name:** `normal_percent`
- **Description:** Percentage without hypofunction
- **Type:** Continuous (0–100)
- **Calculation:** `100 - hypo_percent`

---

## Data Aggregation Levels

### Level 1: Individual Participant
- All 7 component scores (0/1 for each)
- Demographics (age, gender, province)
- Derived diagnosis

### Level 2: Age Group
- Aggregated across all participants in age band
- Gender breakdown within age group
- Provincial comparison within age group
- Example: All 71–75 year-olds (n=88)

### Level 3: Gender Group
- Aggregated across males (n=241) or females (n=266)
- Age breakdown within gender
- Provincial breakdown within gender

### Level 4: Provincial Level
- All 9 provinces analyzed separately
- Within province: age groups, gender breakdown
- Regional assignment

### Level 5: Regional Level
- 5 regions (North, Northeast, Central, East, South)
- Aggregates provinces within region
- Cross-regional comparison

### Level 6: National Level
- All 507 participants
- Highest-level aggregate statistics
- Overall prevalence: 47.9%

---

## Missing Data Codes

| Code | Meaning |
|------|----------|
| `.` | Missing (blank) |
| `NA` | Not applicable |
| `[blank]` | Participant refused/unable to assess |

**Policy:** Displays as blank in tables; excluded from denominator in rate calculations.

---

## Data Quality Notes

### Validation Rules
1. Age must be 60–74 years
2. All component scores must be 0 or 1
3. Hypo_score = sum of 7 components; range 0–7
4. Hypo_diagnosis = 1 if hypo_score ≥ 3; 0 otherwise
5. Province must match region assignment

### Data Entry Standards
- Double-entry verification: 10% random sample
- Inter-rater reliability (κ): >0.80
- Missing data: <2% across all variables
- Completeness rate: 98%+ (excellent)

---

## Variable Recoding for Analysis

### Age (Numerical Coding)
- 60–65 → 1
- 66–70 → 2
- 71–75 → 3
- 76–80 → 4
- 81+ → 5

### Region (Numerical Coding)
- North → 1
- Northeast → 2
- Central → 3
- East → 4
- South → 5

### Risk Level (Derived)
- Low: Hypo% < 40%
- Moderate: Hypo% 40–60%
- High: Hypo% > 60%

---

## Related Documentation

For interpretation of findings, see:
- `METHODOLOGY.md` - Study design details
- `README.md` - Project overview
- `docs/CLINICAL_GUIDE.md` - Clinical application guide (if available)

---

**Last Updated:** June 2026  
**Data Version:** 1.0  
**Contact:** Data Management Team

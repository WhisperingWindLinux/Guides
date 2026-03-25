# Open Letter to Engineers and Display Technology Decision-Makers

---

## TL;DR (for engineering teams)

- A subset of users cannot use modern displays without rapid onset of severe symptoms  
- A common factor is **Binocular Vision Dysfunction (BVD)** — a measurable condition affecting eye alignment and fusion  
- Displays with **temporal instability** (PWM, temporal dithering, post-processing fluctuations) appear to disrupt binocular fusion  
- Result: devices become **functionally unusable within minutes**  
- Request: provide **stable, low-processing display modes** and **user control over temporal characteristics**

---

## Overview

A growing number of users are no longer able to use modern digital devices without experiencing debilitating physical symptoms.

These are not limited to dry eyes or general fatigue, but involve distinct visual, neurological, and vestibular responses that can emerge within minutes of use.

### Reported symptoms

- Accommodative spasms (difficulty refocusing after looking away)  
- Vergence dysfunction (involuntary eye crossing or divergence)  
- Oscillopsia-like effects (perception of screen instability or shimmering)  
- Vestibular symptoms (dizziness, nausea, spatial disorientation) triggered by static screen viewing  
- Headaches and pressure in the orbital and temporal regions that resolve after stopping device use  

Across a growing body of community reports, a consistent pattern has emerged: certain modern displays and software configurations are not just uncomfortable, but **functionally unusable** for affected individuals.

---

## A Critical Subset: Binocular Vision Dysfunction (BVD)

For many users, an underlying factor is **Binocular Vision Dysfunction (BVD)** — a clinically measurable condition involving small vertical or horizontal eye misalignment (heterophoria).

Under normal conditions, the visual system compensates through continuous fusional vergence. However, this compensation depends on **stable visual input**.

When displays introduce **temporal instability** — including:

- PWM flicker  
- Temporal dithering (FRC)  
- Micro-fluctuations from post-processing  
- Inconsistent frame timing  

— this appears to interfere with the brain’s ability to maintain stable binocular fusion.

### Observed effects

- Breakdown of fusion → diplopia (double vision) or suppression  
- Oscillatory vergence behavior (continuous re-lock attempts)  
- Trigeminal nerve responses (orbital and temple pain)  
- Destabilization of the vestibulo-ocular reflex (VOR) → dizziness, nausea, motion perception  

This is not merely subjective sensitivity.  
BVD and related oculomotor conditions are **measurable** using standard clinical methods (e.g., prism and phoria testing).

For affected users, temporally unstable displays create a **fundamental incompatibility** with normal visual processing.

---

## Consistent Observations Across Devices

Community reports indicate repeatable patterns:

- Devices that were previously usable become intolerable after specific software updates (without hardware changes)  
- Older operating systems (e.g., pre-2018 Android, earlier iOS versions) are often tolerated on the same hardware  
- Newer display technologies and rendering pipelines (OLED, mini-LED, aggressive post-processing) correlate with symptom onset  
- Older LCD panels without these characteristics are frequently reported as stable and usable  

These patterns suggest the issue lies in the **combined behavior of the display pipeline**, not a single component.

---

## Likely Contributing Factors

The following factors are consistently reported as potential triggers:

- **Temporal dithering (FRC)**  
  Introduces subpixel temporal noise that may interfere with fusion stability  

- **PWM (pulse-width modulation)**  
  Especially at lower frequencies, may contribute to visual and vestibular stress  

- **Post-processing pipelines**  
  Dynamic contrast, motion smoothing, sharpening, etc. introducing micro-fluctuations  

- **Rendering instability**  
  Inconsistent frame timing or compositing behavior  

- **Undocumented firmware/driver changes**  
  Silent modifications to display behavior across updates  

> These are **temporal artifacts** — millisecond-scale variations not captured by standard tools (colorimeters, spectrometers), but potentially disruptive to neural and binocular processing.

---

## What We Are Asking For

These requests are practical and actionable:

### 1. Acknowledge the issue

Recognize this as a **physiological compatibility issue**, not just subjective discomfort.

Users with measurable conditions such as BVD are currently excluded.

---

### 2. Treat the display pipeline as a system

Investigate the **combined effect** of:
- PWM  
- Temporal dithering  
- Post-processing  

Include testing for:
- Binocular fusion stability  
- Vergence behavior  

---

### 3. Provide low-processing / “raw” display modes (**high priority**)

Enable modes that:

- Disable or minimize post-processing  
- Ensure temporally stable output  
- Prioritize consistency over visual enhancement  

---

### 4. Allow control over temporal dithering (**high priority**)

- Provide an option to disable FRC / temporal dithering  
- Allow fallback to native panel bit depth  

For some users, dithering alone can make a display unusable.

---

### 5. Increase transparency and control

- Document display-related changes in updates  
- Expose key parameters where possible:
  - PWM behavior  
  - Dithering status  
  - Processing pipeline  

- Avoid silent regressions affecting accessibility  

---

### 6. Expand testing protocols

Go beyond:
- Brightness  
- Color accuracy  
- Static flicker metrics  

Include real-world testing with users who have:

- BVD  
- Oculomotor disorders  
- Vestibular sensitivities  

---

## To the Community

If you experience these issues:

- Report them through official support channels  
- Include device models and OS versions  
- Document when usability changed (e.g., after updates)  
- Include clinical diagnoses (e.g., BVD) where applicable  

This helps establish that the issue is **measurable and reproducible**.

---

## Closing

Users cannot adapt to systems that disrupt:

- Binocular fusion  
- Oculomotor control  
- Vestibular stability  

Technology should expand access — not restrict it.

---

## Call to Action

We are asking for:

- Engineering attention  
- Transparency  
- Practical mitigation paths  

**Not later. Now.**

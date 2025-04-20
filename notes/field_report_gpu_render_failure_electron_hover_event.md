# Field Report – Diagnosing Electron-Based GPU Render Corruption via Pointer-Induced Frame Sampling

**Author:** Ewan Matheson  
**Date:** 20/04/2025  
**System:** Windows 10/11  
**Hardware:** Modern laptop (~4 weeks old)  
**Tools:** VS Code, Brave/Chrome, Node.js  
**Experience Level:** Self-declared non-coder (~1 week into JavaScript)  
**Assisted by:** ChatGPT (GPT-4)

---

## 🧭 Summary

While developing a JavaScript project in VS Code, I encountered a persistent and disturbing system-wide graphical issue: full-screen flicker in solid colors like grey, green, black, and red. There were no crashes, errors, or logs — just unpredictable screen flashes.

After a methodical investigation, I traced the issue to **GPU-accelerated rendering failures** within Electron (the engine behind VS Code). The failures were triggered by **pointer-driven UI interaction**, such as hovering over buttons or menus.

Despite my limited coding experience, I was able to isolate and resolve the issue with the support of AI-assisted debugging.

---

## 💥 Symptoms

- Screen would intermittently flash full grey, black, green, or red.
- No associated crash or error — system stayed responsive.
- Issue occurred only when **VS Code was open**.
- Flicker could be **manually triggered by moving the mouse** over UI elements.
- Colors matched those used in the project’s UI (suggesting sampled pixel error).
- No flicker when system was idle or project not open.

---

## 🧪 Diagnostic Process

1. **Environment Cleanup:**
   - Fully removed Node.js and Chocolatey.
   - Reinstalled clean VC++ redistributables (2013–2022, x86 and x64).
   - Verified PATH and background task cleanup.

2. **Baseline Observation:**
   - Opened VS Code with `--disable-extensions` to remove influence of extensions.
   - No flicker until loading the actual project workspace.

3. **Breakthrough:**
   - Hovering the mouse triggered full-screen flicker.
   - Flicker color correlated with hovered element.
   - Flicker **did not occur** with VS Code open and idle.

4. **Resolution:**
   - Disabled hardware acceleration in VS Code:
     ```json
     {
       "disable-hardware-acceleration": true
     }
     ```
   - Restarted VS Code.
   - Issue completely resolved.

---

## 🧠 Insight

The root issue was not code-related, but rather a **rendering pipeline corruption** in the Electron compositor stack — likely triggered by:

- A broken VC++ install (from a failed Node + Chocolatey combo).
- Electron triggering GPU acceleration during pointer-hover redraw events.
- A framebuffer/render composition bug causing the **entire screen to fill with a sampled pixel color**.

Despite lacking a formal development background, I was able to use AI-assisted diagnostics to identify the problem, test hypotheses in isolation, and implement a fix.

---

## 🧘 Reflection

> "I don’t say this lightly: nobody with my level of experience should have both experienced this, and conceptually figured it out. But I did. And I’m actually really impressed with myself."

This was an unusually deep problem, and it demonstrates how AI support — when combined with attention and persistence — can extend **real systems understanding**, even for beginners.

This wasn’t about fixing code.  
This was about understanding **what layer of the system broke, and why.**

---

---
title-slide: false
bibliography: references.bib
csl: vancouver.csl
citeproc: true
theme: serif
background-color: "#ffffff"
transition: slide
navigationMode: linear
hash: true
---

:::: {.columns}
::: {.column width="50%"}

## Sample slides
#### PlaceHolderName
#### Universiti Malaysia Perlis
#### [placeholder@email.com](mailto:placeholder@email.com)

<audio id="bg-music" src="media/audio/sb.m4a" loop></audio>

<div id="audio-credit"
     style="position: absolute; bottom: 40px; right: 20px; font-size: 0.6em; opacity: 0.6;">
  Music: “Adrift” by Scott Buckley (CC BY 4.0)
</div>

<script>
  document.addEventListener('DOMContentLoaded', () => {
    const audio = document.getElementById('bg-music');
    const credit = document.getElementById('audio-credit');

    // hide credit by default
    credit.style.display = 'none';

    const test = new Audio('media/audio/bgm.mp3');

    test.addEventListener('canplaythrough', () => {
      // bgm.mp3 exists → use it, keep credit hidden
      audio.src = 'media/audio/bgm.mp3';
    }, { once: true });

    test.addEventListener('error', () => {
      // bgm.mp3 missing → sb.m4a will play → show credit
      credit.style.display = 'block';
    }, { once: true });

    document.addEventListener('click', () => {
      if (Reveal.getIndices().h === 0) {
        audio.volume = 0.5;
        audio.play();
      }
    }, { once: true });

    Reveal.on('slidechanged', (event) => {
      if (event.indexh > 0) { audio.pause(); }
      else { audio.play(); }
    });
  });
</script>

:::

::: {.column width="50%"}
![](media/pics/logo1.png)
:::

::::

---

:::: {.columns}
::: {.column width="50%"}
### Slide one
**Key Concepts:**
- Energy conservation per @carnot1824.
- $\Delta U = Q - W$
:::

::: {.column width="50%"}
![](media/pics/sample.png)
:::
::::

---

<span class="slide-title" data-title="My Hidden Slide Name"></span>

![](media/pics/wide.jpeg)

---

:::: {.columns}
::: {.column width="50%"}
### The Master Equation
The fundamental relation of thermodynamics:

$$\Delta U = Q - W$$

The work done $W$ is positive when the system expands against an external pressure.
:::

::: {.column width="50%"}
<video data-src="media/videos/sample.mp4" data-autoplay loop muted width="100%"></video>
:::

::::

---

:::: {.columns}
::: {.column width="50%"}
### Visualizing the Gas Law
**Interactive Model:**

- P, V, and T relationships.
- Use the slider to adjust pressure.
- Observe the phase boundary.
:::

::: {.column width="50%"}
<iframe 
  data-src="media/plots/sample.html" 
  width="100%" 
  height="500px" 
  style="border:none;" 
  scrolling="no">
</iframe>
:::
::::

---

:::: {.columns}
::: {.column width="50%"}
### Control Chart: PartLength (Machine 1)

Here, we introduce the X-bar control chart for `PartLength` from Machine 1. This chart helps us assess if the process is in a state of statistical control.

**Interpretation:**
- Points within the control limits ($\pm 3\sigma$) indicate a stable process.
- Points outside the limits or specific patterns suggest special causes of variation.

::: {.notes}
Discuss the purpose of control charts and why X-bar charts are used for process means. Highlight any points that fall outside the control limits or show non-random patterns, indicating an out-of-control process. Explain the meaning of UCL, LCL, and CL.
:::

:::

::: {.column width="50%"}
<iframe data-src='media/plots/partlength_xbar_machine1.html' width='100%' height='500px' style='border:none;'></iframe>
:::

::::

---

:::: {.columns}
::: {.column width="50%"}
### Control Chart: PartLength (Machine 1)

Here, we introduce the X-bar control chart for `PartLength` from Machine 1. This chart helps us assess if the process is in a state of statistical control.

**Interpretation:**
- Points within the control limits ($\pm 3\sigma$) indicate a stable process.
- Points outside the limits or specific patterns suggest special causes of variation.

::: {.notes}
Discuss the purpose of control charts and why X-bar charts are used for process means. Highlight any points that fall outside the control limits or show non-random patterns, indicating an out-of-control process. Explain the meaning of UCL, LCL, and CL.
:::

:::

::: {.column width="50%"}
<iframe data-src='media/plots/partlength_xbar_machine1.html' width='100%' height='500px' style='border:none;'></iframe>
:::

::::

---

:::: {.columns}
::: {.column width="50%"}
### Control Chart: PartResistance (Machine 1)

Following the analysis of `PartLength`, we now examine the X-bar control chart for `PartResistance` from Machine 1. This provides insight into the stability of electrical resistance in the manufactured parts.

**Interpretation:**
- Similar to PartLength, we look for points outside control limits or non-random patterns to identify process instability.

::: {.notes}
Discuss the findings from the PartResistance control chart. Compare its stability to the PartLength chart. Are there any common issues or unique challenges for PartResistance?
:::

:::

::: {.column width="50%"}
<iframe data-src='media/plots/partresistance_xbar_machine1.html' width='100%' height='500px' style='border:none;'></iframe>
:::

::::

---
# Bibliography
<div id="refs"></div>

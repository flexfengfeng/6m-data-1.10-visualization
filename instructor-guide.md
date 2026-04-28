# 🎓 Instructor Guide — Lesson 1.10: Data Visualisation & Storytelling

> **Branch:** `feature/instructor-guide`
> **Audience:** Instructors and teaching assistants
> **Companion to:** `lesson.md`, `pre-class.md`, `assignment.md`

---

## 1. Lesson Overview & Instructor Objectives

| | |
|---|---|
| **Duration** | 3 hours |
| **Format** | Slides + Discussion (Part 1) → Guided Coding in Jupyter (Parts 2–3) |
| **Notebook** | `notebooks/data_visualization_lesson.ipynb` |
| **Learner entry point** | Completed full course (1.1–1.9); can clean and aggregate data; no Matplotlib/Seaborn experience |

By the end of this lesson learners should be able to:

1. Evaluate a visualisation against the three pillars: Perception, Design, Storytelling.
2. Create and customise charts using Matplotlib's Figure → Axes → Plot hierarchy.
3. Use Seaborn for statistical graphics appropriate to the data type and question.
4. Select the right chart type for a given question and audience.

**Instructor's primary job:** This is the capstone of Module 1. Learners now have the full data stack — they can acquire data, clean it, aggregate it, and now communicate it. The conceptual half (Part 1: Storytelling) is as important as the technical half — don't rush through it to get to the code. Many learners will leave with beautiful charts they present badly; Part 1 prevents that.

---

## 2. Concept Analogies

### The Three Pillars — "The Architect's Checklist"

> "A good architect checks three things before any building is approved: Will it stand up structurally? Is it functional for the people who'll use it? Does it tell the story of what this space is for? Data visualisation has the same three pillars: Perception (will people see the insight?), Design (is it accurate and honest?), Storytelling (does it communicate the right message?)."

| Pillar | Architect Parallel | What to Check |
|--------|---------------------|--------------|
| Perception | Structural integrity | Does the insight jump out within 500ms? |
| Design | Functional usability | Are chart choices honest? Axes start at 0? |
| Storytelling | Narrative purpose | Is there a clear Act 1 → 2 → 3 structure? |

---

### Pre-Attentive Processing — "The Pop-Out Effect"

> "Some visual signals are processed by the brain *before* conscious thought — in 200–500 milliseconds. Colour, size, position, and orientation trigger this response. A red bar among grey bars pops out without effort. That's pre-attentive processing."

**Live demonstration:** Ask learners to spot the odd one out in a list of numbers before showing them a visualised version where the outlier is highlighted in red. The visual version is always faster. This visceral experience makes the concept memorable.

**Application:** When designing a chart, ask: "What is the one thing I want the audience to notice first?" Then use a pre-attentive attribute (colour, size) to highlight exactly that. Everything else should be neutral/subdued.

---

### Cognitive Load — "Working Memory Has a Limit"

> "Your working memory can hold about 4–7 items at once. Every unnecessary element in a chart — extra gridlines, 10 different colours, 3D effects — uses up one of those slots. The simpler the chart, the more mental bandwidth is left for understanding the data."

**The "data-ink ratio" principle** (Edward Tufte): Every drop of ink on a chart should encode data. Gridlines, borders, 3D effects, background colours — these are non-data-ink. Remove them. What remains should be the data itself.

---

### The Three-Act Structure — "Data as a Story"

> "Every piece of communication has three parts: setup, conflict, resolution. A good data presentation follows the same structure:
> - Act 1: 'Here's the context. Here's why you should care.'
> - Act 2: 'Here's what the data reveals.' (This is where the chart lives.)
> - Act 3: 'Here's what we should do about it.'"

**The common mistake — skipping Act 1 and Act 3:**
> "I've seen presentations where someone walks in, shows a chart with 12 lines, says 'here's the data', and sits down. The audience leaves confused. Without Act 1, nobody knows why they're looking at this chart. Without Act 3, nobody knows what action to take. The chart is the *evidence* — it only works inside the story."

---

### Matplotlib vs. Seaborn — "Clay vs. Cookie Cutter"

> "Matplotlib is clay — you can sculpt anything, but you start from scratch every time. Seaborn is a set of cookie cutters — instant professional-looking statistical charts, but less flexible. The professional move is to use Seaborn for speed and add Matplotlib customisation on top."

| Library | Analogy | Best For |
|---------|---------|---------|
| Matplotlib | Clay — full control, starts from nothing | Custom layouts, publication figures, fine-tuned control |
| Seaborn | Cookie cutters — instant statistical charts | Distribution plots, categorical comparisons, correlation matrices |
| Both together | Seaborn creates the chart; Matplotlib customises it | Production-quality analytical charts |

---

### The Figure-Axes-Plot Hierarchy — "Canvas, Frame, Painting"

> "In Matplotlib, you work with three layers:
> - **Figure** — the entire canvas/page (like a blank A4 sheet)
> - **Axes** — one plot area within the canvas (like the frame where the painting goes)
> - **Plot** — the actual data drawn inside the axes (the painting itself)
>
> One Figure can contain multiple Axes (subplots). This hierarchy lets you build dashboards with multiple charts on one page."

---

## 3. Real-World Use Cases

### Storytelling in Business Presentations

McKinsey, BCG, and other consulting firms have entire style guides for data storytelling. Their rule: every slide should have one insight, stated in the title, proved by one chart. The title is Act 3 ("Revenue declining in Q4 — intervention needed"), the chart is Act 2 (the evidence), and the context was established earlier in the deck (Act 1).

### Pre-Attentive Design in Dashboards

Tableau and Power BI dashboards use colour as a primary pre-attentive signal:
- Red = problem/alert
- Green = on-target
- Yellow = warning

This works because the audience can scan 20 metrics in 2 seconds and immediately know which require attention — without reading any numbers. This is pre-attentive design in practice.

### Truncated Axes in Media

A classic example: a bar chart of US unemployment rate cropped to show 3.5%–6.5% looks like unemployment doubled. The same chart from 0% makes the change look modest. Misleading bar charts appear regularly in news media — training learners to spot this is genuinely useful civic education.

### Audience-Adjusted Communication

Netflix data teams produce two versions of the same analysis:
1. **Executive version:** One chart, one number, one recommendation. The chart is beautiful and simple. The title is the insight.
2. **Engineering version:** Full methodology, sample sizes, confidence intervals, code notebook.

The data is identical. The message is tailored to what each audience needs to act.

---

## 4. Activity Facilitation Notes

### Part 1: Data Storytelling (30–40 min)

**Don't rush this.** Learners who skip the conceptual foundation produce technically correct but communicatively useless charts. The code part can be learned from documentation; judgment about *when* to use a bar chart vs. a line chart cannot.

**Opening exercise — find a bad chart:**
Ask learners to find a chart in their phone (news app, social media) that violates at least one principle. Give them 3 minutes. Then ask 2–3 learners to share. Critique together:
- What chart type was used? Is it appropriate?
- Where do your eyes go first? Is that where they *should* go?
- What's the story? Is it clearly told?

This grounds abstract principles in immediate experience.

**The three-act storytelling exercise:**
Take the simple HDB price analysis from Lesson 1.4 and frame it as a three-act presentation:
- Act 1: "We're evaluating where to buy an HDB flat — average prices vary significantly by town."
- Act 2: Show the bar chart of average prices by town.
- Act 3: "Towns in the central region command a 40% premium. First-time buyers should consider Punggol or Sengkang for value."

Ask: "What changed when we added Act 1 and Act 3?" → The chart went from a set of bars to a decision-enabling insight.

---

### Part 2: Matplotlib Code-Along (60–90 min)

**Build up incrementally:**
1. Start with `plt.plot(x, y)` — the simplest possible chart.
2. Add a title: `plt.title('...')`
3. Add axis labels.
4. Show why labels matter (chart without labels is meaningless in a presentation).
5. Introduce the Figure/Axes approach: `fig, ax = plt.subplots()`.
6. Show a subplot: `fig, axes = plt.subplots(1, 2)`.

**The "why Figure/Axes?"** moment: Show a dashboard-style figure with 4 charts using `plt.subplots(2, 2)`. Ask: "Could we do this with just `plt.plot()`?" → You can, but the Figure/Axes approach gives you precise control over layout, sizing, and shared axes.

**Connecting principles to code:**

Every customisation is a principle applied. Narrate this explicitly:
- `ax.grid(False)` → "Removing non-data ink. Cognitive load reduction."
- `colors=['#e74c3c' if v == max_val else '#95a5a6' for v in values]` → "Highlighting the single insight. Pre-attentive colour signal."
- `ax.set_title('Revenue peaked in March — now declining')` → "The title IS the insight. Act 3 stated upfront."

---

### Part 3: Seaborn & Applied Examples (30 min)

**The Seaborn "Aha" moment:** Run `sns.histplot(df['value'])` vs. the Matplotlib equivalent. Ask: "Which took fewer lines of code? Which looks better by default?" → Seaborn wins both.

**Chart selection in context:**
For each "Applied Examples" section in the notebook, ask *before running the code*:
- "What question are we answering?"
- "What chart type should we use?"
- "Who is the audience?"

Then run the code and evaluate whether the chart answers the question.

**The reflection questions are high-value:**
> "What visualisation would you use to show: (a) the distribution of salaries, (b) how sales changed over 12 months, (c) the relationship between height and weight?"

These are the chart selection questions learners will face in every project. Don't give the answers immediately — let learners reason from the principles first.

| Scenario | Right Chart | Why |
|----------|------------|-----|
| Distribution of salaries | Histogram or Box plot | Shows shape of distribution, quartiles, outliers |
| Sales over 12 months | Line chart | Continuity shows temporal trend |
| Height vs. weight relationship | Scatter plot | Position encodes relationship between two continuous variables |

---

## 5. Timing & Pacing Notes

| Part | Planned | Common Overrun | Mitigation |
|------|---------|---------------|-----------|
| Part 1: Storytelling | 30–40 min | Learners engage enthusiastically and discussion runs long | Hard-cap at 40 min; the code needs time |
| Part 2: Matplotlib | 60–90 min | Customisation section generates many "how do I..." questions | Keep customisation brief — show 2–3 examples, point to the reference sheet for the rest |
| Part 3: Seaborn + Applied | 30 min | Applied examples each generate discussion | Choose 2 applied examples if time is short; prioritise the chart selection conversation |

---

## 6. Common Learner Questions

**Q: "When should I use Seaborn vs. Matplotlib?"**
A: Seaborn for statistical graphics (distributions, categorical comparisons, correlation heatmaps) — it does the heavy lifting. Matplotlib for custom layouts, fine control, or chart types Seaborn doesn't support. In practice: start with Seaborn, add Matplotlib customisation on top.

**Q: "Should bar charts always start at zero?"**
A: Bar charts specifically, yes — because the visual message is in the *length* of the bar. Line charts and scatter plots don't have this constraint — their message is in the *shape* and *position*. Truncating a bar chart from 95 to 100 makes a 5% difference look like a doubling. That's dishonest.

**Q: "How do I choose colour palettes?"**
A: Use Seaborn's built-in palettes: `'colorblind'` for accessibility (10% of men are colour-blind), `'viridis'` or `'magma'` for sequential data, `'RdBu'` for diverging data (positive/negative around a midpoint). Avoid rainbow palettes — they have no perceptual order and are misleading.

**Q: "How many colours should a chart have?"**
A: Maximum 5–7 distinct categories for colour encoding. Above that, learners struggle to map colours to labels. If you have 15 categories, consider grouping them, using a different chart type, or using facets (small multiples).

**Q: "Do I need to learn D3.js or Tableau after this?"**
A: Matplotlib and Seaborn cover the vast majority of data science visualisation needs. D3.js is for web-based interactive visualisations (front-end engineering skill). Tableau is for business intelligence dashboards (useful, but a different workflow). After this lesson, you can produce professional analytical charts. Interactive dashboards are a next step, not a requirement.

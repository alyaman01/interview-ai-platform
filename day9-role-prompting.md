---
name: frontend-design
description: Guidance for distinctive, intentional visual design when building new UI or reshaping an existing one. Helps with aesthetic direction, typography, and making choices that don't read as templated defaults.
license: Complete terms in LICENSE.txt
---

# Frontend Design

Approach this as the design lead at a small studio known for giving every client a visual identity that could not be mistaken for anyone else's. This client has already rejected proposals that felt templated, and is paying for a distinctive point of view: make deliberate, opinionated choices about palette, typography, and layout that are specific to this brief, and take one real aesthetic risk you can justify.

## Ground it in the subject

If the brief does not pin down what the product or subject is, pin it yourself before designing: name one concrete subject, its audience, and the page's single job, and state your choice. If there's any information in your memory about the human's preferences, context about what they're building, or designs you've made before – use that as a hint. The subject's own world, its materials, instruments, artifacts, and vernacular, is where distinctive choices come from. Build with the brief's real content and subject matter throughout.

## Design principles

For web designs, the hero is a thesis. Open with the most characteristic thing in the subject's world, in whatever form makes sense for it: a headline, an image, an animation, a live demo, an interactive moment. Be deliberate with your choice: a big number with a small label, supporting stats, and a gradient accent is the template answer, only use if that's truly the best option.

Typography carries the personality of the page. Pair the display and body faces deliberately, not the same families you would reach for on any other project, and set a clear type scale with intentional weights, widths, and spacing. Make the type treatment itself a memorable part of the design, not a neutral delivery vehicle for the content.

Structure is information. Structural devices, numbering, eyebrows, dividers, labels, should encode something true about the content, not decorate it. Many generic designs use numbered markers (01 / 02 / 03), but that's only appropriate if the content actually is a sequence - like a real process or a typed timeline where order carries information the reader needs. Question if choices like numbered markers actually make sense before incorporating them.

Leverage motion deliberately. Think about where and if animation can serve the subject: a page-load sequence, a scroll-triggered reveal, hover micro-interactions, ambient atmosphere. An orchestrated moment usually lands harder than scattered effects; choose what the direction calls for. However, sometimes less is more, and extra animation contributes to the feeling that the design is AI-generated.

Match complexity to the vision. Maximalist directions need elaborate execution; minimal directions need precision in spacing, type, and detail. Elegance is executing the chosen vision well.

Consider written content carefully. Often a design brief may not contain real content, and it's up to you to come up with copy. Copy can make a design feel as templated as the design itself. See the below section on writing for more guidance.

## Process: brainstorm, explore, plan, critique, build, critique again

For calibration: AI-generated design right now clusters around three looks: (1) a warm cream background (near #F4F1EA) with a high-contrast serif display and a terracotta or warm-clay accent (often near #D97757 — Anthropic's own Claude-interaction accent, so on a user's brief it reads as a tell); (2) a near-black background with a single bright acid-green or vermilion accent; (3) a broadsheet-style layout with hairline rules, zero border-radius, and dense newspaper-like columns. All three are legitimate for some briefs, but they are defaults rather than choices, and they appear regardless of subject. Where the brief pins down a visual direction, follow it exactly — the brief's own words always win, including when it asks for one of these looks. Where it leaves an axis free, don't spend that freedom on one of these defaults. Just like a human designer who's hired, there's often a careful balance between doing what you're good at and taking each project as a chance to experiment and learn.

Work in two passes. First, brainstorm a short design plan based on the human's design brief: create a compact token system with color, type, layout, and signature. Color: describe the palette as 4–6 named hex values. Type: the typefaces for 2+ roles (a characterful display face that's used with restraint, a complementary body face, and a utility face for captions or data if needed). Layout: a layout concept, using one-sentence prose descriptions and ASCII wireframes to ideate and compare. Signature: the single unique element this page will be remembered by that embodies the brief in an appropriate way.

Then review that plan against the brief before building: if any part of it reads like the generic default you would produce for any similar page (work through a similar prompt to see if you arrive somewhere similar) rather than a choice made for this specific brief — revise that part, say what you changed and why. Only after you've confirmed the relative uniqueness of your design plan should you start to write the code, following the revised plan exactly and deriving every color and type decision from it.

When writing the code, be careful of structuring your CSS selector specificities. It's easy to generate CSS classes that cancel each other out (especially with a type-based selector like .section and a element-based selector like .cta). This can happen often with paddings/margins between sections.

Try to do a lot of this planning and iteration in your thinking, and only show ideas to the user when you have higher confidence it'll delight them.

## Restraint and self-critique

Spend your boldness in one place. Let the signature element be the one memorable thing, keep everything around it quiet and disciplined, and cut any decoration that does not serve the brief. Not taking a risk can be a risk itself! Build to a quality floor without announcing it: responsive down to mobile, visible keyboard focus, reduced motion respected. Critique your own work as you build, taking screenshots if your environment supports it – a picture is worth 1000 tokens. Consider Chanel's advice: before leaving the house, take a look in the mirror and remove one accessory. Human creators have memory and always try to do something new, so if you have a space to quickly jot down notes about what you've tried, it can help you in future passes.

## More on writing in design

Words appear in a design for one reason: to make it easier to understand, and therefore easier to use. They are design material, not decoration. Bring the same intentionality to copy that you would bring to spacing and color. Before writing anything, ask what the design needs to say, and how it can best be said to help the person navigate the experience.

Write from the end user's side of the screen. Name things by what people control and recognize, never by how the system is built. A person manages notifications, not webhook config. Describe what something does in plain terms rather than selling it. Being specific is always better than being clever.

Use active voice as default. A control should say exactly what happens when it's used: "Save changes," not "Submit." An action keeps the same name through the whole flow, so the button that says "Publish" produces a toast that says "Published." The vocabulary of an interface is the signposting for someone navigating the product. Cohesion and consistency are how people learn their way around.

Treat failure and emptiness as moments for direction, not mood. Explain what went wrong and how to fix it, in the interface's voice rather than a person's. Errors don't apologize, and they are never vague about what happened. An empty screen is an invitation to act.

Keep the register conversational and tuned: plain verbs, sentence case, no filler, with tone matched to the brand and the audience. Let each element do exactly one job. A label labels, an example demonstrates, and nothing quietly does double duty.



<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NutriScope — Nutrient Intelligence</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.4/chart.umd.min.js"></script>
<style>
:root{
  --bg:#0B0E11;
  --surface:#12161B;
  --surface-alt:#171C22;
  --surface-raised:#1B2128;
  --border:#232A32;
  --border-soft:#1A2028;
  --mint:#5EEAD4;
  --mint-dim:#2E5C54;
  --amber:#F4B942;
  --danger:#F2545B;
  --violet:#9D8CF1;
  --text:#E8ECEF;
  --text-dim:#8B96A3;
  --text-faint:#5A6472;
  --font-display:'Space Grotesk',sans-serif;
  --font-body:'Inter',sans-serif;
  --font-mono:'IBM Plex Mono',monospace;
}
@font-face{font-family:'Space Grotesk';src:local('Space Grotesk');}
*{box-sizing:border-box;margin:0;padding:0;}
html,body{background:var(--bg);color:var(--text);font-family:var(--font-body);-webkit-font-smoothing:antialiased;}
body{min-height:100vh;padding-bottom:60px;}
::selection{background:var(--mint-dim);color:var(--mint);}
::-webkit-scrollbar{width:8px;height:8px;}
::-webkit-scrollbar-thumb{background:var(--border);border-radius:4px;}
a{color:inherit;}
button{font-family:inherit;cursor:pointer;}
input,select{font-family:inherit;}
:focus-visible{outline:2px solid var(--mint);outline-offset:2px;}

/* ---------- Layout shell ---------- */
.topbar{
  position:sticky;top:0;z-index:50;
  display:flex;align-items:center;justify-content:space-between;
  padding:16px 28px;
  background:rgba(11,14,17,0.88);backdrop-filter:blur(14px);
  border-bottom:1px solid var(--border-soft);
}
.brand{display:flex;align-items:center;gap:10px;}
.brand-mark{
  width:34px;height:34px;border-radius:9px;
  background:conic-gradient(from 220deg,var(--mint),var(--violet),var(--mint));
  display:flex;align-items:center;justify-content:center;
  font-family:var(--font-mono);font-weight:700;color:#06110F;font-size:15px;
  box-shadow:0 0 24px -4px rgba(94,234,212,0.55);
}
.brand-name{font-family:var(--font-display);font-weight:600;font-size:19px;letter-spacing:-0.02em;}
.brand-sub{font-family:var(--font-mono);font-size:10.5px;color:var(--text-faint);letter-spacing:0.14em;text-transform:uppercase;margin-top:-2px;}

.tabs{display:flex;gap:4px;flex-wrap:wrap;padding:10px 28px 0;max-width:1400px;margin:0 auto;}
.tab-btn{
  font-family:var(--font-mono);font-size:12.5px;letter-spacing:0.03em;
  padding:9px 16px;border-radius:8px 8px 0 0;border:1px solid transparent;
  background:transparent;color:var(--text-dim);border-bottom:2px solid transparent;
  transition:all .15s ease;
}
.tab-btn:hover{color:var(--text);}
.tab-btn.active{color:var(--mint);border-bottom:2px solid var(--mint);background:var(--surface);}

.shell{max-width:1400px;margin:0 auto;padding:26px 28px 10px;}
.view{display:none;animation:fadeIn .25s ease;}
.view.active{display:block;}
@keyframes fadeIn{from{opacity:0;transform:translateY(4px);}to{opacity:1;transform:none;}}

/* ---------- Cards / grid ---------- */
.grid{display:grid;gap:18px;}
.grid-2{grid-template-columns:1fr 1fr;}
.grid-3{grid-template-columns:repeat(3,1fr);}
.grid-4{grid-template-columns:repeat(4,1fr);}
@media(max-width:980px){.grid-2,.grid-3,.grid-4{grid-template-columns:1fr;}}

.card{
  background:linear-gradient(180deg,var(--surface) 0%, var(--surface-alt) 100%);
  border:1px solid var(--border);border-radius:14px;
  padding:22px;position:relative;overflow:hidden;
}
.card::before{
  content:'';position:absolute;top:0;left:0;right:0;height:1px;
  background:linear-gradient(90deg,transparent,rgba(94,234,212,0.35),transparent);
}
.card-head{display:flex;align-items:baseline;justify-content:space-between;margin-bottom:16px;}
.card-title{font-family:var(--font-display);font-size:15.5px;font-weight:600;letter-spacing:-0.01em;}
.card-eyebrow{font-family:var(--font-mono);font-size:10px;letter-spacing:0.14em;text-transform:uppercase;color:var(--text-faint);}

h1.page-title{font-family:var(--font-display);font-size:26px;font-weight:600;letter-spacing:-0.02em;margin-bottom:4px;}
.page-desc{color:var(--text-dim);font-size:13.5px;margin-bottom:22px;max-width:640px;}

/* ---------- Form elements ---------- */
.field{display:flex;flex-direction:column;gap:6px;margin-bottom:14px;}
.field label{font-size:11.5px;font-family:var(--font-mono);color:var(--text-dim);letter-spacing:0.04em;text-transform:uppercase;}
.field input,.field select{
  background:var(--bg);border:1px solid var(--border);border-radius:8px;
  padding:10px 12px;color:var(--text);font-size:14px;transition:border .15s ease;
}
.field input:focus,.field select:focus{border-color:var(--mint);outline:none;}
.field-row{display:grid;grid-template-columns:1fr 1fr;gap:14px;}
@media(max-width:640px){.field-row{grid-template-columns:1fr;}}

.btn{
  display:inline-flex;align-items:center;justify-content:center;gap:8px;
  padding:10px 18px;border-radius:8px;border:1px solid var(--border);
  background:var(--surface-raised);color:var(--text);font-size:13.5px;font-weight:500;
  transition:all .15s ease;
}
.btn:hover{border-color:var(--mint);color:var(--mint);}
.btn-primary{background:var(--mint);color:#06110F;border-color:var(--mint);font-weight:600;}
.btn-primary:hover{background:#7CF2DE;color:#06110F;box-shadow:0 0 20px -4px rgba(94,234,212,0.6);}
.btn-ghost{background:transparent;}
.btn-danger{border-color:var(--danger);color:var(--danger);background:transparent;}
.btn-danger:hover{background:rgba(242,84,91,0.1);color:var(--danger);}
.btn-sm{padding:6px 12px;font-size:12px;}
.btn:disabled{opacity:.4;cursor:not-allowed;}

/* ---------- Tables ---------- */
table{width:100%;border-collapse:collapse;font-size:13px;}
th{
  text-align:left;font-family:var(--font-mono);font-size:10.5px;letter-spacing:0.08em;text-transform:uppercase;
  color:var(--text-faint);padding:8px 10px;border-bottom:1px solid var(--border);font-weight:500;
}
td{padding:10px 10px;border-bottom:1px solid var(--border-soft);vertical-align:middle;}
tr:last-child td{border-bottom:none;}
td input,td select{width:100%;background:transparent;border:1px solid transparent;border-radius:6px;padding:5px 6px;color:var(--text);font-family:var(--font-mono);font-size:12.5px;}
td input:hover,td select:hover{border-color:var(--border);}
td input:focus,td select:focus{border-color:var(--mint);outline:none;background:var(--bg);}
.num{font-family:var(--font-mono);}
.text-dim{color:var(--text-dim);}
.text-faint{color:var(--text-faint);}
.empty-row td{text-align:center;color:var(--text-faint);padding:26px 10px;font-size:13px;}

/* ---------- Pills / badges ---------- */
.pill{display:inline-flex;align-items:center;gap:5px;padding:3px 9px;border-radius:100px;font-size:11px;font-family:var(--font-mono);border:1px solid var(--border);}
.pill-veg{color:var(--mint);border-color:var(--mint-dim);}
.pill-egg{color:var(--amber);border-color:rgba(244,185,66,0.35);}
.pill-nonveg{color:var(--danger);border-color:rgba(242,84,91,0.35);}
.pill-low{color:var(--danger);border-color:rgba(242,84,91,0.35);}
.pill-ok{color:var(--mint);border-color:var(--mint-dim);}
.pill-high{color:var(--amber);border-color:rgba(244,185,66,0.35);}

/* ---------- Readout / gauge (signature element) ---------- */
.readout-wrap{display:flex;align-items:center;gap:28px;flex-wrap:wrap;}
.dial{position:relative;width:190px;height:190px;flex:none;}
.dial svg{width:100%;height:100%;transform:rotate(-90deg);}
.dial-center{position:absolute;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center;}
.dial-value{font-family:var(--font-mono);font-size:30px;font-weight:600;color:var(--mint);letter-spacing:-0.02em;}
.dial-label{font-family:var(--font-mono);font-size:10px;color:var(--text-faint);letter-spacing:0.1em;text-transform:uppercase;margin-top:4px;}
.dial-sub{font-size:11.5px;color:var(--text-dim);margin-top:8px;}
.readout-stats{display:flex;flex-direction:column;gap:10px;flex:1;min-width:180px;}
.readout-stat{display:flex;justify-content:space-between;align-items:center;padding:9px 0;border-bottom:1px dashed var(--border);font-size:12.5px;}
.readout-stat:last-child{border-bottom:none;}
.readout-stat .k{color:var(--text-dim);font-family:var(--font-mono);font-size:11px;text-transform:uppercase;letter-spacing:0.05em;}
.readout-stat .v{font-family:var(--font-mono);font-weight:600;}

/* ---------- Progress bars ---------- */
.bar-track{width:100%;height:7px;background:var(--bg);border-radius:100px;overflow:hidden;border:1px solid var(--border-soft);}
.bar-fill{height:100%;border-radius:100px;transition:width .4s ease;}
.nutrient-row{display:flex;align-items:center;gap:12px;padding:9px 0;border-bottom:1px solid var(--border-soft);}
.nutrient-row:last-child{border-bottom:none;}
.nutrient-name{width:120px;flex:none;font-size:12px;color:var(--text-dim);}
.nutrient-bar{flex:1;}
.nutrient-pct{width:64px;flex:none;text-align:right;font-family:var(--font-mono);font-size:11.5px;}

/* ---------- Chip list (recs) ---------- */
.rec-item{display:flex;gap:14px;padding:14px 0;border-bottom:1px solid var(--border-soft);}
.rec-item:last-child{border-bottom:none;}
.rec-icon{width:34px;height:34px;border-radius:9px;flex:none;display:flex;align-items:center;justify-content:center;font-size:15px;background:var(--surface-raised);border:1px solid var(--border);}
.rec-body .rec-title{font-size:13.5px;font-weight:600;margin-bottom:3px;}
.rec-body .rec-desc{font-size:12.5px;color:var(--text-dim);line-height:1.5;}
.rec-tag{display:inline-block;margin-top:6px;font-family:var(--font-mono);font-size:10px;letter-spacing:0.06em;text-transform:uppercase;color:var(--mint);}

/* ---------- Risk cards ---------- */
.risk-card{border-radius:12px;border:1px solid var(--border);padding:16px;background:var(--surface-raised);}
.risk-card.sev-high{border-color:rgba(242,84,91,0.4);background:linear-gradient(180deg,rgba(242,84,91,0.06),transparent);}
.risk-card.sev-med{border-color:rgba(244,185,66,0.35);background:linear-gradient(180deg,rgba(244,185,66,0.06),transparent);}
.risk-card.sev-low{border-color:var(--mint-dim);background:linear-gradient(180deg,rgba(94,234,212,0.05),transparent);}
.risk-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;}
.risk-name{font-family:var(--font-display);font-weight:600;font-size:14px;}
.risk-sev{font-family:var(--font-mono);font-size:10px;letter-spacing:0.08em;text-transform:uppercase;padding:2px 8px;border-radius:100px;}
.sev-high .risk-sev{color:var(--danger);border:1px solid rgba(242,84,91,0.4);}
.sev-med .risk-sev{color:var(--amber);border:1px solid rgba(244,185,66,0.4);}
.sev-low .risk-sev{color:var(--mint);border:1px solid var(--mint-dim);}
.risk-desc{font-size:12.5px;color:var(--text-dim);line-height:1.55;}

/* ---------- Meal planner ---------- */
.day-toggle{display:flex;gap:8px;margin-bottom:16px;}
.day-toggle button{flex:1;}
.day-toggle button.active{background:var(--mint);color:#06110F;border-color:var(--mint);font-weight:600;}

/* ---------- Upload zone ---------- */
.upload-zone{
  border:1.5px dashed var(--border);border-radius:12px;padding:26px;text-align:center;
  transition:all .15s ease;cursor:pointer;
}
.upload-zone:hover,.upload-zone.drag{border-color:var(--mint);background:rgba(94,234,212,0.04);}
.upload-zone p{font-size:12.5px;color:var(--text-dim);margin-top:6px;}
.upload-zone .icon{font-size:24px;}

/* ---------- misc ---------- */
.divider{height:1px;background:var(--border);margin:20px 0;}
.flex-between{display:flex;justify-content:space-between;align-items:center;}
.small-note{font-size:11.5px;color:var(--text-faint);line-height:1.6;}
.tag-row{display:flex;gap:8px;flex-wrap:wrap;margin-top:10px;}
.chart-box{position:relative;height:230px;}
.chart-box-sm{position:relative;height:190px;}
.disclaimer-box{
  border:1px solid rgba(244,185,66,0.3);background:rgba(244,185,66,0.05);
  border-radius:12px;padding:18px 20px;font-size:12.5px;color:var(--text-dim);line-height:1.6;
}
.disclaimer-box strong{color:var(--amber);}
.source-item{padding:12px 0;border-bottom:1px solid var(--border-soft);font-size:12.5px;}
.source-item:last-child{border-bottom:none;}
.source-item .s-name{font-weight:600;color:var(--text);margin-bottom:3px;}
.source-item .s-desc{color:var(--text-dim);}
.toast{
  position:fixed;bottom:24px;left:50%;transform:translateX(-50%) translateY(20px);
  background:var(--surface-raised);border:1px solid var(--mint-dim);color:var(--mint);
  padding:12px 20px;border-radius:10px;font-size:13px;font-family:var(--font-mono);
  opacity:0;transition:all .3s ease;z-index:100;pointer-events:none;box-shadow:0 8px 30px rgba(0,0,0,0.5);
}
.toast.show{opacity:1;transform:translateX(-50%) translateY(0);}
.footer-note{text-align:center;color:var(--text-faint);font-size:11px;font-family:var(--font-mono);padding:30px 0 4px;}
select option{background:var(--surface);}
</style>
</head>
<body>

<div class="topbar">
  <div class="brand">
    <div class="brand-mark">NS</div>
    <div>
      <div class="brand-name">NutriScope</div>
      <div class="brand-sub">Nutrient Intelligence Console</div>
    </div>
  </div>
  <div id="profileBadge" class="pill" style="display:none;font-size:11.5px;"></div>
</div>

<div class="tabs" id="tabBar">
  <button class="tab-btn active" data-view="profile">01 · Profile</button>
  <button class="tab-btn" data-view="log">02 · Food Log</button>
  <button class="tab-btn" data-view="planner">03 · Meal Planner</button>
  <button class="tab-btn" data-view="dashboard">04 · Dashboard</button>
  <button class="tab-btn" data-view="risk">05 · Risk Analysis</button>
  <button class="tab-btn" data-view="recs">06 · Recommendations</button>
  <button class="tab-btn" data-view="about">07 · Sources &amp; Disclaimer</button>
</div>

<div class="shell">

  <!-- ===================== PROFILE ===================== -->
  <div class="view active" id="view-profile">
    <h1 class="page-title">Your profile</h1>
    <p class="page-desc">These inputs calibrate your daily energy and nutrient targets. Nothing leaves your browser — NutriScope runs entirely client-side.</p>
    <div class="grid grid-2">
      <div class="card">
        <div class="card-head"><div><div class="card-eyebrow">Biometrics</div><div class="card-title">Body &amp; activity</div></div></div>
        <div class="field-row">
          <div class="field"><label>Age (years)</label><input type="number" id="p-age" min="10" max="100" value="28"></div>
          <div class="field"><label>Gender</label>
            <select id="p-gender"><option value="male">Male</option><option value="female">Female</option></select>
          </div>
        </div>
        <div class="field-row">
          <div class="field"><label>Height (cm)</label><input type="number" id="p-height" min="100" max="230" value="170"></div>
          <div class="field"><label>Weight (kg)</label><input type="number" id="p-weight" min="30" max="200" value="65"></div>
        </div>
        <div class="field">
          <label>Activity level</label>
          <select id="p-activity">
            <option value="sedentary">Sedentary — little/no exercise</option>
            <option value="light">Light — 1-3 days/week</option>
            <option value="moderate" selected>Moderate — 3-5 days/week</option>
            <option value="active">Active — 6-7 days/week</option>
            <option value="veryactive">Very active — physical job / 2x training</option>
          </select>
        </div>
        <div class="field">
          <label>Dietary preference</label>
          <select id="p-diet">
            <option value="veg">Vegetarian</option>
            <option value="egg">Eggetarian</option>
            <option value="nonveg" selected>Non-Vegetarian</option>
          </select>
        </div>
        <button class="btn btn-primary" id="saveProfile" style="width:100%;margin-top:6px;">Save profile &amp; calculate targets</button>
      </div>

      <div class="card">
        <div class="card-head"><div><div class="card-eyebrow">Derived output</div><div class="card-title">Daily targets</div></div></div>
        <div class="readout-wrap">
          <div class="dial">
            <svg viewBox="0 0 190 190">
              <circle cx="95" cy="95" r="82" fill="none" stroke="#1A2028" stroke-width="12"/>
              <circle id="profileDialRing" cx="95" cy="95" r="82" fill="none" stroke="url(#gradMint)" stroke-width="12" stroke-linecap="round" stroke-dasharray="515.2" stroke-dashoffset="515.2"/>
              <defs><linearGradient id="gradMint" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" stop-color="#5EEAD4"/><stop offset="100%" stop-color="#9D8CF1"/></linearGradient></defs>
            </svg>
            <div class="dial-center">
              <div class="dial-value" id="profileCalories">—</div>
              <div class="dial-label">kcal / day</div>
            </div>
          </div>
          <div class="readout-stats">
            <div class="readout-stat"><span class="k">BMR</span><span class="v" id="profileBMR">—</span></div>
            <div class="readout-stat"><span class="k">Protein target</span><span class="v" id="profileProtein">—</span></div>
            <div class="readout-stat"><span class="k">Carb target</span><span class="v" id="profileCarb">—</span></div>
            <div class="readout-stat"><span class="k">Fat target</span><span class="v" id="profileFat">—</span></div>
            <div class="readout-stat"><span class="k">Fiber target</span><span class="v" id="profileFiber">—</span></div>
          </div>
        </div>
        <div class="divider"></div>
        <p class="small-note">Energy is estimated with the Mifflin-St Jeor equation × an activity multiplier. Macronutrient grams are derived from your bodyweight and total energy; micronutrient targets follow age/gender RDA bands referenced in the Sources tab.</p>
      </div>
    </div>
  </div>

  <!-- ===================== FOOD LOG ===================== -->
  <div class="view" id="view-log">
    <h1 class="page-title">Food log</h1>
    <p class="page-desc">Log what you've eaten today. Choose from a 60-item Indian-forward food database, filtered to your dietary preference.</p>

    <div class="grid" style="grid-template-columns:1.3fr 1fr;">
      <div class="card">
        <div class="card-head"><div><div class="card-eyebrow">Today</div><div class="card-title">Logged entries</div></div>
          <button class="btn btn-sm btn-ghost" id="clearLog">Clear all</button>
        </div>
        <div style="overflow-x:auto;">
        <table>
          <thead><tr><th>Food</th><th>Qty</th><th>Unit</th><th>Kcal</th><th>Protein</th><th></th></tr></thead>
          <tbody id="logTableBody"></tbody>
        </table>
        </div>
      </div>

      <div class="card">
        <div class="card-head"><div><div class="card-eyebrow">Add entry</div><div class="card-title">Log a food</div></div></div>
        <div class="field">
          <label>Food item</label>
          <select id="addFoodSelect"></select>
        </div>
        <div class="field-row">
          <div class="field"><label>Quantity</label><input type="number" id="addFoodQty" value="1" min="0.1" step="0.1"></div>
          <div class="field"><label>Unit</label><select id="addFoodUnit"></select></div>
        </div>
        <button class="btn btn-primary" id="addFoodBtn" style="width:100%;">Add to log</button>

        <div class="divider"></div>
        <div class="card-eyebrow" style="margin-bottom:10px;">CSV import</div>
        <div class="upload-zone" id="csvZoneLog">
          <div class="icon">⇪</div>
          <p><strong style="color:var(--text)">Drop or click to upload CSV</strong><br>Columns: food, quantity, unit</p>
        </div>
        <input type="file" id="csvInputLog" accept=".csv" style="display:none;">
        <p class="small-note" style="margin-top:10px;">Unmatched food names are skipped and reported. <a href="#" id="csvSampleLog" style="color:var(--mint);text-decoration:underline;">Download sample CSV</a></p>
      </div>
    </div>
  </div>

  <!-- ===================== MEAL PLANNER ===================== -->
  <div class="view" id="view-planner">
    <h1 class="page-title">2-day meal planner</h1>
    <p class="page-desc">Plan meals across two days independently of today's log, then compare energy and macros side by side.</p>

    <div class="day-toggle">
      <button class="btn active" data-day="1" id="dayBtn1">Day 1</button>
      <button class="btn" data-day="2" id="dayBtn2">Day 2</button>
    </div>

    <div class="grid" style="grid-template-columns:1.3fr 1fr;">
      <div class="card">
        <div class="card-head"><div><div class="card-eyebrow" id="plannerDayLabel">Day 1</div><div class="card-title">Planned meals</div></div>
          <button class="btn btn-sm btn-ghost" id="clearPlanDay">Clear day</button>
        </div>
        <div style="overflow-x:auto;">
        <table>
          <thead><tr><th>Meal</th><th>Food</th><th>Qty</th><th>Unit</th><th>Kcal</th><th></th></tr></thead>
          <tbody id="plannerTableBody"></tbody>
        </table>
        </div>
      </div>
      <div class="card">
        <div class="card-head"><div><div class="card-eyebrow">Add entry</div><div class="card-title">Plan a meal</div></div></div>
        <div class="field"><label>Meal slot</label>
          <select id="planMealSlot"><option>Breakfast</option><option>Lunch</option><option>Snack</option><option>Dinner</option></select>
        </div>
        <div class="field"><label>Food item</label><select id="planFoodSelect"></select></div>
        <div class="field-row">
          <div class="field"><label>Quantity</label><input type="number" id="planFoodQty" value="1" min="0.1" step="0.1"></div>
          <div class="field"><label>Unit</label><select id="planFoodUnit"></select></div>
        </div>
        <button class="btn btn-primary" id="planAddBtn" style="width:100%;">Add to plan</button>
        <div class="divider"></div>
        <div class="card-eyebrow" style="margin-bottom:10px;">CSV import</div>
        <div class="upload-zone" id="csvZonePlan">
          <div class="icon">⇪</div>
          <p><strong style="color:var(--text)">Drop or click to upload CSV</strong><br>Columns: day, meal, food, quantity, unit</p>
        </div>
        <input type="file" id="csvInputPlan" accept=".csv" style="display:none;">
        <p class="small-note" style="margin-top:10px;"><a href="#" id="csvSamplePlan" style="color:var(--mint);text-decoration:underline;">Download sample CSV</a></p>
      </div>
    </div>

    <div class="card" style="margin-top:18px;">
      <div class="card-head"><div><div class="card-eyebrow">Comparison</div><div class="card-title">Day 1 vs Day 2</div></div></div>
      <div class="chart-box"><canvas id="plannerCompareChart"></canvas></div>
    </div>
  </div>

  <!-- ===================== DASHBOARD ===================== -->
  <div class="view" id="view-dashboard">
    <h1 class="page-title">Dashboard</h1>
    <p class="page-desc">A live read on today's intake against your calculated targets.</p>

    <div class="grid grid-3">
      <div class="card" style="grid-column:span 1;">
        <div class="card-head"><div><div class="card-eyebrow">Energy</div><div class="card-title">Today's progress</div></div></div>
        <div class="dial" style="margin:0 auto;">
          <svg viewBox="0 0 190 190">
            <circle cx="95" cy="95" r="82" fill="none" stroke="#1A2028" stroke-width="12"/>
            <circle id="energyDialRing" cx="95" cy="95" r="82" fill="none" stroke="url(#gradMint2)" stroke-width="12" stroke-linecap="round" stroke-dasharray="515.2" stroke-dashoffset="515.2"/>
            <defs><linearGradient id="gradMint2" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" stop-color="#5EEAD4"/><stop offset="100%" stop-color="#9D8CF1"/></linearGradient></defs>
          </svg>
          <div class="dial-center">
            <div class="dial-value" id="dashEnergyPct">0%</div>
            <div class="dial-label">of target</div>
          </div>
        </div>
        <div class="dial-sub" style="text-align:center;" id="dashEnergyText">0 / 0 kcal</div>
      </div>

      <div class="card" style="grid-column:span 2;">
        <div class="card-head"><div><div class="card-eyebrow">Macros</div><div class="card-title">Consumed vs target (g)</div></div></div>
        <div class="chart-box"><canvas id="macroChart"></canvas></div>
      </div>
    </div>

    <div class="grid grid-2" style="margin-top:18px;">
      <div class="card">
        <div class="card-head"><div><div class="card-eyebrow">Attention</div><div class="card-title">Top deficiencies</div></div></div>
        <div id="topDeficiencies"></div>
      </div>
      <div class="card">
        <div class="card-head"><div><div class="card-eyebrow">Attention</div><div class="card-title">Top excesses</div></div></div>
        <div id="topExcesses"></div>
      </div>
    </div>

    <div class="grid grid-2" style="margin-top:18px;">
      <div class="card">
        <div class="card-head"><div><div class="card-eyebrow">Micronutrients</div><div class="card-title">Completion (%)</div></div></div>
        <div class="chart-box"><canvas id="microChart"></canvas></div>
      </div>
      <div class="card">
        <div class="card-head"><div><div class="card-eyebrow">Full breakdown</div><div class="card-title">Nutrient table</div></div></div>
        <div style="overflow-x:auto;max-height:340px;overflow-y:auto;">
        <table>
          <thead><tr><th>Nutrient</th><th>Consumed</th><th>Target</th><th>%</th></tr></thead>
          <tbody id="nutrientTableBody"></tbody>
        </table>
        </div>
      </div>
    </div>
  </div>

  <!-- ===================== RISK ANALYSIS ===================== -->
  <div class="view" id="view-risk">
    <h1 class="page-title">Risk analysis</h1>
    <p class="page-desc">Pattern-based flags derived from today's intake gaps and excesses. Educational only — see disclaimer.</p>
    <div class="grid grid-3" id="riskGrid"></div>
    <div class="card" style="margin-top:18px;" id="riskEmptyCard" style="display:none;">
    </div>
  </div>

  <!-- ===================== RECOMMENDATIONS ===================== -->
  <div class="view" id="view-recs">
    <h1 class="page-title">Recommendations</h1>
    <p class="page-desc">Personalized to your dietary preference — additions, swaps, and portion adjustments generated from today's log.</p>
    <div class="grid grid-3">
      <div class="card">
        <div class="card-head"><div><div class="card-eyebrow">Fill gaps</div><div class="card-title">Food additions</div></div></div>
        <div id="recAdditions"></div>
      </div>
      <div class="card">
        <div class="card-head"><div><div class="card-eyebrow">Optimize</div><div class="card-title">Food swaps</div></div></div>
        <div id="recSwaps"></div>
      </div>
      <div class="card">
        <div class="card-head"><div><div class="card-eyebrow">Balance</div><div class="card-title">Portion adjustments</div></div></div>
        <div id="recPortions"></div>
      </div>
    </div>
  </div>

  <!-- ===================== ABOUT / SOURCES ===================== -->
  <div class="view" id="view-about">
    <h1 class="page-title">Sources &amp; disclaimer</h1>
    <p class="page-desc">Transparency on where NutriScope's numbers come from, and what this tool is not.</p>
    <div class="grid grid-2">
      <div class="card">
        <div class="card-head"><div><div class="card-eyebrow">Educational disclaimer</div><div class="card-title">Read before use</div></div></div>
        <div class="disclaimer-box">
          <strong>NutriScope is an educational self-tracking tool, not medical advice.</strong> Calorie and nutrient targets are population-level estimates from standard formulas and reference tables — they do not account for individual medical conditions, medications, pregnancy/lactation, growth stages in children, or lab-confirmed deficiencies. Food composition values are typical averages and vary by brand, cooking method, and region. Do not use this tool to diagnose, treat, or manage a medical condition. Consult a registered dietitian or physician for personalized nutrition or medical guidance, especially before making significant dietary changes.
        </div>
      </div>
      <div class="card">
        <div class="card-head"><div><div class="card-eyebrow">Reference data</div><div class="card-title">Nutrition sources</div></div></div>
        <div class="source-item"><div class="s-name">ICMR–NIN Nutrient Requirements for Indians (RDA/EAR tables)</div><div class="s-desc">Baseline for age/gender micronutrient targets.</div></div>
        <div class="source-item"><div class="s-name">USDA FoodData Central</div><div class="s-desc">Reference macro/micronutrient values per 100g for common foods.</div></div>
        <div class="source-item"><div class="s-name">Indian Food Composition Tables (IFCT 2017)</div><div class="s-desc">Composition of Indian staples — dals, millets, cooked grains.</div></div>
        <div class="source-item"><div class="s-name">Mifflin-St Jeor Equation (1990)</div><div class="s-desc">Basal metabolic rate estimation used for energy targets.</div></div>
        <div class="source-item"><div class="s-name">WHO/FAO Dietary Reference Values</div><div class="s-desc">Fiber, sodium and macro-distribution guidance.</div></div>
      </div>
    </div>
  </div>

</div>

<div class="toast" id="toast"></div>
<div class="footer-note">NUTRISCOPE · CLIENT-SIDE ONLY · NO DATA LEAVES YOUR BROWSER</div>

<script>
/* =========================================================================
   FOOD DATABASE — 60 items. Values per 100g (or 100ml for liquids) unless noted.
   diet: 'veg' | 'egg' | 'nonveg'
   units: {unitName: gramsPerUnit}  ('g' always =1)
========================================================================= */
const FOODS = [
 {id:'rice',name:'Rice (cooked)',diet:'veg',units:{g:1,bowl:150,cup:150},per100:{calories:130,protein:2.7,carbs:28,fat:0.3,fiber:0.4,iron:0.2,calcium:10,vitc:0,vitd:0,b12:0,sodium:1,potassium:35,magnesium:12,zinc:0.5,vitaminA:0,folate:3}},
 {id:'roti',name:'Roti (whole wheat)',diet:'veg',units:{g:1,piece:40},per100:{calories:300,protein:11,carbs:58,fat:3.7,fiber:10,iron:3,calcium:30,vitc:0,vitd:0,b12:0,sodium:5,potassium:150,magnesium:60,zinc:1.5,vitaminA:0,folate:30}},
 {id:'dal',name:'Dal (toor, cooked)',diet:'veg',units:{g:1,bowl:150,cup:200},per100:{calories:116,protein:9,carbs:20,fat:0.4,fiber:5,iron:2,calcium:25,vitc:1,vitd:0,b12:0,sodium:2,potassium:370,magnesium:40,zinc:1,vitaminA:5,folate:40}},
 {id:'paneer',name:'Paneer',diet:'veg',units:{g:1,cube:20},per100:{calories:265,protein:18,carbs:1.2,fat:21,fiber:0,iron:0.2,calcium:208,vitc:0,vitd:0,b12:0.5,sodium:20,potassium:30,magnesium:15,zinc:1,vitaminA:130,folate:5}},
 {id:'curd',name:'Curd (yogurt)',diet:'veg',units:{g:1,bowl:100,cup:200},per100:{calories:60,protein:3.5,carbs:4.7,fat:3.3,fiber:0,iron:0.1,calcium:120,vitc:0.5,vitd:0,b12:0.4,sodium:35,potassium:150,magnesium:12,zinc:0.5,vitaminA:30,folate:7}},
 {id:'chana',name:'Chana (chickpeas)',diet:'veg',units:{g:1,bowl:150},per100:{calories:164,protein:8.9,carbs:27,fat:2.6,fiber:8,iron:2.9,calcium:49,vitc:1.5,vitd:0,b12:0,sodium:7,potassium:290,magnesium:48,zinc:1.5,vitaminA:1,folate:172}},
 {id:'rajma',name:'Rajma (kidney beans)',diet:'veg',units:{g:1,bowl:150},per100:{calories:127,protein:8.7,carbs:23,fat:0.5,fiber:6.4,iron:2.9,calcium:35,vitc:1,vitd:0,b12:0,sodium:2,potassium:405,magnesium:45,zinc:1,vitaminA:0,folate:130}},
 {id:'banana',name:'Banana',diet:'veg',units:{g:1,piece:120},per100:{calories:89,protein:1.1,carbs:23,fat:0.3,fiber:2.6,iron:0.3,calcium:5,vitc:8.7,vitd:0,b12:0,sodium:1,potassium:358,magnesium:27,zinc:0.15,vitaminA:3,folate:20}},
 {id:'apple',name:'Apple',diet:'veg',units:{g:1,piece:150},per100:{calories:52,protein:0.3,carbs:14,fat:0.2,fiber:2.4,iron:0.1,calcium:6,vitc:4.6,vitd:0,b12:0,sodium:1,potassium:107,magnesium:5,zinc:0.04,vitaminA:3,folate:3}},
 {id:'milk',name:'Milk (whole)',diet:'veg',units:{ml:1,glass:250,cup:240},per100:{calories:61,protein:3.2,carbs:4.8,fat:3.3,fiber:0,iron:0.03,calcium:113,vitc:1,vitd:0.1,b12:0.4,sodium:43,potassium:150,magnesium:10,zinc:0.4,vitaminA:28,folate:5}},
 {id:'oats',name:'Oats (dry)',diet:'veg',units:{g:1,bowl:40},per100:{calories:389,protein:16.9,carbs:66,fat:6.9,fiber:10.6,iron:4.7,calcium:54,vitc:0,vitd:0,b12:0,sodium:2,potassium:429,magnesium:177,zinc:4,vitaminA:0,folate:56}},
 {id:'bread',name:'Bread (white)',diet:'veg',units:{g:1,slice:30},per100:{calories:265,protein:9,carbs:49,fat:3.2,fiber:2.7,iron:3.6,calcium:150,vitc:0,vitd:0,b12:0,sodium:490,potassium:115,magnesium:25,zinc:0.7,vitaminA:0,folate:90}},
 {id:'egg',name:'Egg (boiled)',diet:'egg',units:{g:1,piece:50},per100:{calories:155,protein:13,carbs:1.1,fat:11,fiber:0,iron:1.2,calcium:50,vitc:0,vitd:2,b12:1.1,sodium:124,potassium:126,magnesium:10,zinc:1.3,vitaminA:160,folate:47}},
 {id:'chicken',name:'Chicken (cooked breast)',diet:'nonveg',units:{g:1,piece:100},per100:{calories:165,protein:31,carbs:0,fat:3.6,fiber:0,iron:1,calcium:15,vitc:0,vitd:0.1,b12:0.3,sodium:74,potassium:256,magnesium:29,zinc:1,vitaminA:9,folate:6}},
 {id:'fish',name:'Fish (rohu, cooked)',diet:'nonveg',units:{g:1,piece:100},per100:{calories:120,protein:22,carbs:0,fat:3,fiber:0,iron:1,calcium:30,vitc:0,vitd:5,b12:2.5,sodium:60,potassium:300,magnesium:30,zinc:0.8,vitaminA:20,folate:10}},
 {id:'potato',name:'Potato (boiled)',diet:'veg',units:{g:1,piece:150},per100:{calories:87,protein:1.9,carbs:20,fat:0.1,fiber:1.8,iron:0.3,calcium:5,vitc:13,vitd:0,b12:0,sodium:6,potassium:379,magnesium:20,zinc:0.3,vitaminA:0,folate:10}},
 {id:'poha',name:'Poha',diet:'veg',units:{g:1,bowl:150},per100:{calories:130,protein:2.5,carbs:27,fat:1.5,fiber:1,iron:2,calcium:15,vitc:2,vitd:0,b12:0,sodium:5,potassium:60,magnesium:20,zinc:0.5,vitaminA:5,folate:10}},
 {id:'idli',name:'Idli',diet:'veg',units:{g:1,piece:35},per100:{calories:120,protein:4,carbs:24,fat:0.5,fiber:1,iron:0.8,calcium:20,vitc:0,vitd:0,b12:0,sodium:200,potassium:60,magnesium:15,zinc:0.5,vitaminA:0,folate:10}},
 {id:'dosa',name:'Dosa (plain)',diet:'veg',units:{g:1,piece:80},per100:{calories:168,protein:3.9,carbs:28,fat:4,fiber:1.2,iron:1,calcium:20,vitc:0,vitd:0,b12:0,sodium:250,potassium:70,magnesium:15,zinc:0.5,vitaminA:0,folate:10}},
 {id:'spinach',name:'Spinach (cooked)',diet:'veg',units:{g:1,bowl:100},per100:{calories:23,protein:2.9,carbs:3.6,fat:0.4,fiber:2.2,iron:2.7,calcium:99,vitc:9.8,vitd:0,b12:0,sodium:70,potassium:466,magnesium:79,zinc:0.5,vitaminA:469,folate:146}},
 {id:'tomato',name:'Tomato',diet:'veg',units:{g:1,piece:100},per100:{calories:18,protein:0.9,carbs:3.9,fat:0.2,fiber:1.2,iron:0.3,calcium:10,vitc:14,vitd:0,b12:0,sodium:5,potassium:237,magnesium:11,zinc:0.2,vitaminA:42,folate:15}},
 {id:'onion',name:'Onion',diet:'veg',units:{g:1,piece:100},per100:{calories:40,protein:1.1,carbs:9.3,fat:0.1,fiber:1.7,iron:0.2,calcium:23,vitc:7.4,vitd:0,b12:0,sodium:4,potassium:146,magnesium:10,zinc:0.2,vitaminA:0,folate:19}},
 {id:'carrot',name:'Carrot',diet:'veg',units:{g:1,piece:60},per100:{calories:41,protein:0.9,carbs:10,fat:0.2,fiber:2.8,iron:0.3,calcium:33,vitc:5.9,vitd:0,b12:0,sodium:69,potassium:320,magnesium:12,zinc:0.2,vitaminA:835,folate:19}},
 {id:'cucumber',name:'Cucumber',diet:'veg',units:{g:1,piece:150},per100:{calories:16,protein:0.7,carbs:3.6,fat:0.1,fiber:0.5,iron:0.3,calcium:16,vitc:2.8,vitd:0,b12:0,sodium:2,potassium:147,magnesium:13,zinc:0.2,vitaminA:5,folate:7}},
 {id:'cauliflower',name:'Cauliflower',diet:'veg',units:{g:1,bowl:100},per100:{calories:25,protein:1.9,carbs:5,fat:0.3,fiber:2,iron:0.4,calcium:22,vitc:48,vitd:0,b12:0,sodium:30,potassium:299,magnesium:15,zinc:0.3,vitaminA:0,folate:57}},
 {id:'cabbage',name:'Cabbage',diet:'veg',units:{g:1,bowl:100},per100:{calories:25,protein:1.3,carbs:5.8,fat:0.1,fiber:2.5,iron:0.5,calcium:40,vitc:36,vitd:0,b12:0,sodium:18,potassium:170,magnesium:12,zinc:0.2,vitaminA:5,folate:43}},
 {id:'peas',name:'Green peas',diet:'veg',units:{g:1,bowl:100},per100:{calories:81,protein:5.4,carbs:14,fat:0.4,fiber:5.7,iron:1.5,calcium:25,vitc:40,vitd:0,b12:0,sodium:5,potassium:244,magnesium:33,zinc:1.2,vitaminA:38,folate:65}},
 {id:'brinjal',name:'Brinjal (eggplant)',diet:'veg',units:{g:1,piece:80},per100:{calories:25,protein:1,carbs:6,fat:0.2,fiber:3,iron:0.2,calcium:9,vitc:2.2,vitd:0,b12:0,sodium:2,potassium:229,magnesium:14,zinc:0.2,vitaminA:1,folate:22}},
 {id:'bhindi',name:'Bhindi (okra)',diet:'veg',units:{g:1,bowl:100},per100:{calories:33,protein:1.9,carbs:7.5,fat:0.2,fiber:3.2,iron:0.6,calcium:82,vitc:23,vitd:0,b12:0,sodium:7,potassium:299,magnesium:57,zinc:0.6,vitaminA:36,folate:60}},
 {id:'mushroom',name:'Mushroom',diet:'veg',units:{g:1,bowl:70},per100:{calories:22,protein:3.1,carbs:3.3,fat:0.3,fiber:1,iron:0.5,calcium:3,vitc:0,vitd:0.2,b12:0,sodium:5,potassium:318,magnesium:9,zinc:0.5,vitaminA:0,folate:17}},
 {id:'moongdal',name:'Moong Dal (cooked)',diet:'veg',units:{g:1,bowl:150},per100:{calories:105,protein:7.5,carbs:19,fat:0.4,fiber:7.6,iron:1.4,calcium:27,vitc:1,vitd:0,b12:0,sodium:2,potassium:266,magnesium:48,zinc:0.8,vitaminA:5,folate:80}},
 {id:'masoordal',name:'Masoor Dal (cooked)',diet:'veg',units:{g:1,bowl:150},per100:{calories:116,protein:9,carbs:20,fat:0.4,fiber:8,iron:3.3,calcium:19,vitc:1.5,vitd:0,b12:0,sodium:2,potassium:369,magnesium:36,zinc:1.3,vitaminA:1,folate:181}},
 {id:'soybean',name:'Soybean (boiled)',diet:'veg',units:{g:1,bowl:100},per100:{calories:173,protein:16.6,carbs:9.9,fat:9,fiber:6,iron:5.1,calcium:102,vitc:1.7,vitd:0,b12:0,sodium:1,potassium:515,magnesium:65,zinc:1.6,vitaminA:1,folate:165}},
 {id:'tofu',name:'Tofu',diet:'veg',units:{g:1,cube:20},per100:{calories:76,protein:8,carbs:1.9,fat:4.8,fiber:0.3,iron:5.4,calcium:350,vitc:0,vitd:0,b12:0,sodium:7,potassium:121,magnesium:30,zinc:0.8,vitaminA:0,folate:15}},
 {id:'almonds',name:'Almonds',diet:'veg',units:{g:1,piece:1.2},per100:{calories:579,protein:21,carbs:22,fat:50,fiber:12.5,iron:3.7,calcium:269,vitc:0,vitd:0,b12:0,sodium:1,potassium:733,magnesium:270,zinc:3.1,vitaminA:0,folate:44}},
 {id:'walnuts',name:'Walnuts',diet:'veg',units:{g:1,piece:5},per100:{calories:654,protein:15,carbs:14,fat:65,fiber:6.7,iron:2.9,calcium:98,vitc:1.3,vitd:0,b12:0,sodium:2,potassium:441,magnesium:158,zinc:3.1,vitaminA:1,folate:98}},
 {id:'peanuts',name:'Peanuts',diet:'veg',units:{g:1,handful:30},per100:{calories:567,protein:25.8,carbs:16,fat:49,fiber:8.5,iron:4.6,calcium:92,vitc:0,vitd:0,b12:0,sodium:18,potassium:705,magnesium:168,zinc:3.3,vitaminA:0,folate:240}},
 {id:'cashew',name:'Cashew',diet:'veg',units:{g:1,piece:2},per100:{calories:553,protein:18,carbs:30,fat:44,fiber:3.3,iron:6.7,calcium:37,vitc:0.5,vitd:0,b12:0,sodium:12,potassium:660,magnesium:292,zinc:5.8,vitaminA:0,folate:25}},
 {id:'ghee',name:'Ghee',diet:'veg',units:{g:1,tsp:5,tbsp:15},per100:{calories:900,protein:0,carbs:0,fat:100,fiber:0,iron:0,calcium:4,vitc:0,vitd:2.5,b12:0,sodium:2,potassium:5,magnesium:0,zinc:0,vitaminA:840,folate:0}},
 {id:'butter',name:'Butter',diet:'veg',units:{g:1,tsp:5,tbsp:15},per100:{calories:717,protein:0.9,carbs:0.1,fat:81,fiber:0,iron:0.02,calcium:24,vitc:0,vitd:1.5,b12:0.1,sodium:11,potassium:24,magnesium:2,zinc:0.1,vitaminA:684,folate:3}},
 {id:'cheese',name:'Cheese (cheddar)',diet:'veg',units:{g:1,slice:20},per100:{calories:402,protein:25,carbs:1.3,fat:33,fiber:0,iron:0.7,calcium:721,vitc:0,vitd:0.6,b12:0.8,sodium:621,potassium:98,magnesium:28,zinc:3.1,vitaminA:265,folate:18}},
 {id:'sweetpotato',name:'Sweet potato',diet:'veg',units:{g:1,piece:130},per100:{calories:86,protein:1.6,carbs:20,fat:0.1,fiber:3,iron:0.6,calcium:30,vitc:2.4,vitd:0,b12:0,sodium:55,potassium:337,magnesium:25,zinc:0.3,vitaminA:709,folate:11}},
 {id:'corn',name:'Corn (boiled)',diet:'veg',units:{g:1,cup:150},per100:{calories:96,protein:3.4,carbs:21,fat:1.5,fiber:2.4,iron:0.5,calcium:2,vitc:6.8,vitd:0,b12:0,sodium:15,potassium:270,magnesium:37,zinc:0.5,vitaminA:9,folate:42}},
 {id:'orange',name:'Orange',diet:'veg',units:{g:1,piece:130},per100:{calories:47,protein:0.9,carbs:12,fat:0.1,fiber:2.4,iron:0.1,calcium:40,vitc:53,vitd:0,b12:0,sodium:0,potassium:181,magnesium:10,zinc:0.1,vitaminA:11,folate:30}},
 {id:'papaya',name:'Papaya',diet:'veg',units:{g:1,bowl:150},per100:{calories:43,protein:0.5,carbs:11,fat:0.3,fiber:1.7,iron:0.3,calcium:20,vitc:61,vitd:0,b12:0,sodium:8,potassium:182,magnesium:10,zinc:0.1,vitaminA:47,folate:37}},
 {id:'mango',name:'Mango',diet:'veg',units:{g:1,piece:200},per100:{calories:60,protein:0.8,carbs:15,fat:0.4,fiber:1.6,iron:0.2,calcium:11,vitc:36,vitd:0,b12:0,sodium:1,potassium:168,magnesium:10,zinc:0.1,vitaminA:54,folate:43}},
 {id:'guava',name:'Guava',diet:'veg',units:{g:1,piece:100},per100:{calories:68,protein:2.6,carbs:14,fat:1,fiber:5.4,iron:0.3,calcium:18,vitc:228,vitd:0,b12:0,sodium:2,potassium:417,magnesium:22,zinc:0.2,vitaminA:31,folate:49}},
 {id:'watermelon',name:'Watermelon',diet:'veg',units:{g:1,bowl:150},per100:{calories:30,protein:0.6,carbs:8,fat:0.2,fiber:0.4,iron:0.2,calcium:7,vitc:8.1,vitd:0,b12:0,sodium:1,potassium:112,magnesium:10,zinc:0.1,vitaminA:28,folate:3}},
 {id:'pomegranate',name:'Pomegranate',diet:'veg',units:{g:1,bowl:100},per100:{calories:83,protein:1.7,carbs:19,fat:1.2,fiber:4,iron:0.3,calcium:10,vitc:10,vitd:0,b12:0,sodium:3,potassium:236,magnesium:12,zinc:0.3,vitaminA:0,folate:38}},
 {id:'grapes',name:'Grapes',diet:'veg',units:{g:1,bowl:100},per100:{calories:69,protein:0.7,carbs:18,fat:0.2,fiber:0.9,iron:0.4,calcium:10,vitc:4,vitd:0,b12:0,sodium:2,potassium:191,magnesium:7,zinc:0.1,vitaminA:3,folate:2}},
 {id:'mutton',name:'Mutton (cooked)',diet:'nonveg',units:{g:1,piece:100},per100:{calories:258,protein:25,carbs:0,fat:17,fiber:0,iron:2,calcium:15,vitc:0,vitd:0.1,b12:2.6,sodium:70,potassium:310,magnesium:20,zinc:4.5,vitaminA:0,folate:18}},
 {id:'prawns',name:'Prawns (cooked)',diet:'nonveg',units:{g:1,piece:10},per100:{calories:99,protein:24,carbs:0.2,fat:0.3,fiber:0,iron:0.5,calcium:70,vitc:0,vitd:0,b12:1.5,sodium:111,potassium:259,magnesium:39,zinc:1.6,vitaminA:0,folate:3}},
 {id:'greekyogurt',name:'Yogurt (Greek)',diet:'veg',units:{g:1,bowl:150},per100:{calories:97,protein:9,carbs:3.6,fat:5,fiber:0,iron:0.1,calcium:110,vitc:0,vitd:0,b12:0.75,sodium:36,potassium:141,magnesium:11,zinc:0.5,vitaminA:30,folate:7}},
 {id:'buttermilk',name:'Buttermilk (chaas)',diet:'veg',units:{ml:1,glass:250},per100:{calories:40,protein:2.5,carbs:4.8,fat:1,fiber:0,iron:0.1,calcium:100,vitc:0.5,vitd:0,b12:0.3,sodium:30,potassium:130,magnesium:10,zinc:0.4,vitaminA:20,folate:5}},
 {id:'sattu',name:'Sattu',diet:'veg',units:{g:1,tbsp:15},per100:{calories:384,protein:20,carbs:60,fat:6,fiber:18,iron:5,calcium:85,vitc:0,vitd:0,b12:0,sodium:3,potassium:700,magnesium:150,zinc:2.5,vitaminA:0,folate:180}},
 {id:'millet',name:'Millet (Bajra, cooked)',diet:'veg',units:{g:1,bowl:150},per100:{calories:119,protein:3.6,carbs:23,fat:1.7,fiber:1.2,iron:2,calcium:10,vitc:0,vitd:0,b12:0,sodium:2,potassium:110,magnesium:45,zinc:0.8,vitaminA:0,folate:19}},
 {id:'ragi',name:'Ragi (cooked)',diet:'veg',units:{g:1,bowl:150},per100:{calories:119,protein:2.5,carbs:25,fat:0.6,fiber:2.5,iron:2,calcium:170,vitc:0,vitd:0,b12:0,sodium:5,potassium:150,magnesium:60,zinc:0.8,vitaminA:0,folate:15}},
 {id:'quinoa',name:'Quinoa (cooked)',diet:'veg',units:{g:1,bowl:150},per100:{calories:120,protein:4.4,carbs:21,fat:1.9,fiber:2.8,iron:1.5,calcium:17,vitc:0,vitd:0,b12:0,sodium:7,potassium:172,magnesium:64,zinc:1.1,vitaminA:0,folate:42}},
 {id:'chiaseeds',name:'Chia seeds',diet:'veg',units:{g:1,tbsp:12},per100:{calories:486,protein:17,carbs:42,fat:31,fiber:34,iron:7.7,calcium:631,vitc:1.6,vitd:0,b12:0,sodium:16,potassium:407,magnesium:335,zinc:4.6,vitaminA:0,folate:49}},
 {id:'flaxseeds',name:'Flax seeds',diet:'veg',units:{g:1,tbsp:10},per100:{calories:534,protein:18,carbs:29,fat:42,fiber:27,iron:5.7,calcium:255,vitc:0.6,vitd:0,b12:0,sodium:30,potassium:813,magnesium:392,zinc:4.3,vitaminA:0,folate:87}}
];
const FOOD_MAP = Object.fromEntries(FOODS.map(f=>[f.id,f]));

const NUTRIENT_KEYS = ['calories','protein','carbs','fat','fiber','iron','calcium','vitc','vitd','b12','sodium','potassium','magnesium','zinc','vitaminA','folate'];
const NUTRIENT_LABELS = {calories:'Calories',protein:'Protein',carbs:'Carbs',fat:'Fat',fiber:'Fiber',iron:'Iron',calcium:'Calcium',vitc:'Vitamin C',vitd:'Vitamin D',b12:'Vitamin B12',sodium:'Sodium',potassium:'Potassium',magnesium:'Magnesium',zinc:'Zinc',vitaminA:'Vitamin A',folate:'Folate'};
const NUTRIENT_UNITS = {calories:'kcal',protein:'g',carbs:'g',fat:'g',fiber:'g',iron:'mg',calcium:'mg',vitc:'mg',vitd:'mcg',b12:'mcg',sodium:'mg',potassium:'mg',magnesium:'mg',zinc:'mg',vitaminA:'mcg',folate:'mcg'};
const NUTRIENT_TYPE = {sodium:'max'}; // default 'min' (more is progress up to target); sodium is a ceiling

/* =========================================================================
   STATE
========================================================================= */
let profile = {age:28,gender:'male',height:170,weight:65,activity:'moderate',diet:'nonveg',saved:false};
let foodLog = []; // {foodId, qty, unit}
let mealPlan = {1:[], 2:[]};
let currentPlanDay = 1;

/* =========================================================================
   CALCULATIONS
========================================================================= */
const ACTIVITY_MULT = {sedentary:1.2, light:1.375, moderate:1.55, active:1.725, veryactive:1.9};
const PROTEIN_PER_KG = {sedentary:0.8, light:0.9, moderate:1.0, active:1.3, veryactive:1.6};

function calcBMR(p){
  const base = 10*p.weight + 6.25*p.height - 5*p.age;
  return p.gender==='male' ? base+5 : base-161;
}
function calcTargets(p){
  const bmr = calcBMR(p);
  const tdee = bmr * ACTIVITY_MULT[p.activity];
  const proteinG = p.weight * PROTEIN_PER_KG[p.activity];
  const proteinCal = proteinG*4;
  const fatCal = tdee*0.27;
  const fatG = fatCal/9;
  const carbCal = Math.max(tdee - proteinCal - fatCal, 0);
  const carbG = carbCal/4;
  const fiberG = 14 * (tdee/1000);

  const isMale = p.gender==='male';
  const micro = {
    iron: isMale ? 10 : (p.age>50?10:21),
    calcium: 1000,
    vitc: isMale ? 90 : 75,
    vitd: 15,
    b12: 2.4,
    sodium: 2300,
    potassium: isMale ? 3400 : 2600,
    magnesium: isMale ? 400 : 310,
    zinc: isMale ? 11 : 8,
    vitaminA: isMale ? 900 : 700,
    folate: 400
  };

  return {
    calories: Math.round(tdee), bmr: Math.round(bmr),
    protein: Math.round(proteinG), carbs: Math.round(carbG), fat: Math.round(fatG), fiber: Math.round(fiberG),
    ...Object.fromEntries(Object.entries(micro).map(([k,v])=>[k,Math.round(v)]))
  };
}

function entryGrams(entry){
  const food = FOOD_MAP[entry.foodId];
  if(!food) return 0;
  const gramsPerUnit = food.units[entry.unit] ?? 1;
  return entry.qty * gramsPerUnit;
}
function entryNutrients(entry){
  const food = FOOD_MAP[entry.foodId];
  if(!food) return {};
  const grams = entryGrams(entry);
  const factor = grams/100;
  const out = {};
  NUTRIENT_KEYS.forEach(k=> out[k] = (food.per100[k]||0)*factor);
  return out;
}
function sumEntries(entries){
  const total = Object.fromEntries(NUTRIENT_KEYS.map(k=>[k,0]));
  entries.forEach(e=>{
    const n = entryNutrients(e);
    NUTRIENT_KEYS.forEach(k=> total[k]+=n[k]||0);
  });
  return total;
}

/* =========================================================================
   UTIL
========================================================================= */
function toast(msg){
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  clearTimeout(window._toastTimer);
  window._toastTimer = setTimeout(()=>t.classList.remove('show'), 2200);
}
function round1(n){ return Math.round(n*10)/10; }
function fmt(n,unit){
  const v = Math.abs(n)>=100 ? Math.round(n) : round1(n);
  return `${v}${unit?(' '+unit):''}`;
}
function dietAllows(pref, foodDiet){
  if(pref==='nonveg') return true;
  if(pref==='egg') return foodDiet==='veg'||foodDiet==='egg';
  return foodDiet==='veg';
}
function filteredFoods(){
  return FOODS.filter(f=>dietAllows(profile.diet, f.diet));
}
function dietPillClass(d){ return d==='veg'?'pill-veg':(d==='egg'?'pill-egg':'pill-nonveg'); }
function dietPillLabel(d){ return d==='veg'?'Veg':(d==='egg'?'Egg':'Non-Veg'); }

/* =========================================================================
   TAB NAVIGATION
========================================================================= */
document.querySelectorAll('.tab-btn').forEach(btn=>{
  btn.addEventListener('click', ()=>{
    document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
    document.querySelectorAll('.view').forEach(v=>v.classList.remove('active'));
    btn.classList.add('active');
    document.getElementById('view-'+btn.dataset.view).classList.add('active');
    if(btn.dataset.view==='dashboard') renderDashboard();
    if(btn.dataset.view==='risk') renderRisk();
    if(btn.dataset.view==='recs') renderRecs();
    if(btn.dataset.view==='planner') renderPlanner();
  });
});

/* =========================================================================
   PROFILE VIEW
========================================================================= */
function populateFoodSelect(selectEl){
  selectEl.innerHTML='';
  filteredFoods().forEach(f=>{
    const opt = document.createElement('option');
    opt.value=f.id; opt.textContent=f.name;
    selectEl.appendChild(opt);
  });
}
function populateUnitSelect(selectEl, foodId){
  const food = FOOD_MAP[foodId];
  selectEl.innerHTML='';
  Object.keys(food.units).forEach(u=>{
    const opt=document.createElement('option'); opt.value=u; opt.textContent=u;
    selectEl.appendChild(opt);
  });
}

function readProfileForm(){
  profile.age = parseFloat(document.getElementById('p-age').value)||28;
  profile.gender = document.getElementById('p-gender').value;
  profile.height = parseFloat(document.getElementById('p-height').value)||170;
  profile.weight = parseFloat(document.getElementById('p-weight').value)||65;
  profile.activity = document.getElementById('p-activity').value;
  profile.diet = document.getElementById('p-diet').value;
}

function renderProfileReadout(){
  const t = calcTargets(profile);
  document.getElementById('profileCalories').textContent = t.calories;
  document.getElementById('profileBMR').textContent = t.bmr+' kcal';
  document.getElementById('profileProtein').textContent = t.protein+' g';
  document.getElementById('profileCarb').textContent = t.carbs+' g';
  document.getElementById('profileFat').textContent = t.fat+' g';
  document.getElementById('profileFiber').textContent = t.fiber+' g';
  const ring = document.getElementById('profileDialRing');
  const circumference = 515.2;
  ring.style.strokeDashoffset = circumference*0.18; // decorative fill, mostly full
  const badge = document.getElementById('profileBadge');
  badge.style.display='inline-flex';
  badge.className = 'pill '+dietPillClass(profile.diet==='egg'?'egg':(profile.diet==='veg'?'veg':'nonveg'));
  badge.textContent = `${profile.age}y · ${profile.gender==='male'?'M':'F'} · ${dietPillLabel(profile.diet==='egg'?'egg':(profile.diet==='veg'?'veg':'nonveg'))} · ${t.calories} kcal target`;
}

document.getElementById('saveProfile').addEventListener('click', ()=>{
  readProfileForm();
  profile.saved = true;
  renderProfileReadout();
  populateFoodSelect(document.getElementById('addFoodSelect'));
  populateUnitSelect(document.getElementById('addFoodUnit'), document.getElementById('addFoodSelect').value);
  populateFoodSelect(document.getElementById('planFoodSelect'));
  populateUnitSelect(document.getElementById('planFoodUnit'), document.getElementById('planFoodSelect').value);
  // drop log/plan entries no longer allowed under new diet preference
  foodLog = foodLog.filter(e=>dietAllows(profile.diet, FOOD_MAP[e.foodId].diet));
  mealPlan[1] = mealPlan[1].filter(e=>dietAllows(profile.diet, FOOD_MAP[e.foodId].diet));
  mealPlan[2] = mealPlan[2].filter(e=>dietAllows(profile.diet, FOOD_MAP[e.foodId].diet));
  renderLogTable();
  toast('Profile saved — targets recalculated');
});

/* =========================================================================
   FOOD LOG VIEW
========================================================================= */
document.getElementById('addFoodSelect').addEventListener('change', (e)=>{
  populateUnitSelect(document.getElementById('addFoodUnit'), e.target.value);
});
document.getElementById('addFoodBtn').addEventListener('click', ()=>{
  const foodId = document.getElementById('addFoodSelect').value;
  const qty = parseFloat(document.getElementById('addFoodQty').value)||1;
  const unit = document.getElementById('addFoodUnit').value;
  if(!foodId) return;
  foodLog.push({foodId, qty, unit});
  renderLogTable();
  toast(FOOD_MAP[foodId].name+' added to log');
});
document.getElementById('clearLog').addEventListener('click', ()=>{
  foodLog=[]; renderLogTable(); toast('Log cleared');
});

function renderLogTable(){
  const tbody = document.getElementById('logTableBody');
  tbody.innerHTML='';
  if(foodLog.length===0){
    tbody.innerHTML = `<tr class="empty-row"><td colspan="6">No entries yet — add a food on the right, or import a CSV.</td></tr>`;
    return;
  }
  foodLog.forEach((entry,idx)=>{
    const food = FOOD_MAP[entry.foodId];
    if(!food){ return; }
    const n = entryNutrients(entry);
    const tr = document.createElement('tr');
    tr.innerHTML = `
      <td>${food.name}</td>
      <td><input type="number" min="0.1" step="0.1" value="${entry.qty}" data-idx="${idx}" class="log-qty"></td>
      <td>
        <select data-idx="${idx}" class="log-unit">
          ${Object.keys(food.units).map(u=>`<option value="${u}" ${u===entry.unit?'selected':''}>${u}</option>`).join('')}
        </select>
      </td>
      <td class="num">${fmt(n.calories)}</td>
      <td class="num">${fmt(n.protein)} g</td>
      <td><button class="btn btn-sm btn-danger" data-idx="${idx}" data-action="remove">✕</button></td>
    `;
    tbody.appendChild(tr);
  });
  tbody.querySelectorAll('.log-qty').forEach(inp=>{
    inp.addEventListener('input', e=>{
      foodLog[e.target.dataset.idx].qty = parseFloat(e.target.value)||0;
      renderLogTable();
    });
  });
  tbody.querySelectorAll('.log-unit').forEach(sel=>{
    sel.addEventListener('change', e=>{
      foodLog[e.target.dataset.idx].unit = e.target.value;
      renderLogTable();
    });
  });
  tbody.querySelectorAll('[data-action="remove"]').forEach(btn=>{
    btn.addEventListener('click', e=>{
      foodLog.splice(e.target.dataset.idx,1);
      renderLogTable();
      toast('Entry removed');
    });
  });
}

/* -------- CSV import: food log -------- */
function findFoodByName(name){
  const norm = name.trim().toLowerCase();
  return FOODS.find(f=>f.name.toLowerCase()===norm) ||
         FOODS.find(f=>f.name.toLowerCase().includes(norm)) ||
         FOODS.find(f=>norm.includes(f.name.toLowerCase().split(' ')[0]));
}
function parseCSV(text){
  const lines = text.split(/\r?\n/).filter(l=>l.trim().length);
  if(lines.length===0) return {header:[], rows:[]};
  const header = lines[0].split(',').map(h=>h.trim().toLowerCase());
  const rows = lines.slice(1).map(l=>{
    const cells = l.split(',').map(c=>c.trim());
    const obj={};
    header.forEach((h,i)=> obj[h]=cells[i]);
    return obj;
  });
  return {header, rows};
}
function wireCSVZone(zoneId, inputId, handler){
  const zone = document.getElementById(zoneId);
  const input = document.getElementById(inputId);
  zone.addEventListener('click', ()=>input.click());
  zone.addEventListener('dragover', e=>{e.preventDefault();zone.classList.add('drag');});
  zone.addEventListener('dragleave', ()=>zone.classList.remove('drag'));
  zone.addEventListener('drop', e=>{
    e.preventDefault(); zone.classList.remove('drag');
    if(e.dataTransfer.files[0]) readCSVFile(e.dataTransfer.files[0], handler);
  });
  input.addEventListener('change', e=>{
    if(e.target.files[0]) readCSVFile(e.target.files[0], handler);
    input.value='';
  });
}
function readCSVFile(file, handler){
  const reader = new FileReader();
  reader.onload = e => handler(e.target.result);
  reader.readAsText(file);
}
wireCSVZone('csvZoneLog','csvInputLog', text=>{
  const {rows} = parseCSV(text);
  let added=0, skipped=0;
  rows.forEach(r=>{
    const food = findFoodByName(r.food||'');
    if(!food || !dietAllows(profile.diet, food.diet)){ skipped++; return; }
    const unit = (r.unit && food.units[r.unit]) ? r.unit : 'g';
    const qty = parseFloat(r.quantity)||1;
    foodLog.push({foodId:food.id, qty, unit});
    added++;
  });
  renderLogTable();
  toast(`CSV import: ${added} added, ${skipped} skipped`);
});
document.getElementById('csvSampleLog').addEventListener('click', e=>{
  e.preventDefault();
  downloadText('nutriscope_log_sample.csv','food,quantity,unit\nRice,150,g\nDal,1,bowl\nBanana,1,piece\n');
});
function downloadText(filename, text){
  const blob = new Blob([text],{type:'text/csv'});
  const a = document.createElement('a');
  a.href = URL.createObjectURL(blob); a.download = filename;
  document.body.appendChild(a); a.click(); a.remove();
}

/* =========================================================================
   MEAL PLANNER VIEW
========================================================================= */
document.getElementById('dayBtn1').addEventListener('click', ()=>switchPlanDay(1));
document.getElementById('dayBtn2').addEventListener('click', ()=>switchPlanDay(2));
function switchPlanDay(d){
  currentPlanDay = d;
  document.getElementById('dayBtn1').classList.toggle('active', d===1);
  document.getElementById('dayBtn2').classList.toggle('active', d===2);
  document.getElementById('plannerDayLabel').textContent = 'Day '+d;
  renderPlanner();
}
document.getElementById('planFoodSelect').addEventListener('change', e=>{
  populateUnitSelect(document.getElementById('planFoodUnit'), e.target.value);
});
document.getElementById('planAddBtn').addEventListener('click', ()=>{
  const foodId = document.getElementById('planFoodSelect').value;
  const qty = parseFloat(document.getElementById('planFoodQty').value)||1;
  const unit = document.getElementById('planFoodUnit').value;
  const meal = document.getElementById('planMealSlot').value;
  if(!foodId) return;
  mealPlan[currentPlanDay].push({foodId, qty, unit, meal});
  renderPlanner();
  toast(`${FOOD_MAP[foodId].name} added to Day ${currentPlanDay} · ${meal}`);
});
document.getElementById('clearPlanDay').addEventListener('click', ()=>{
  mealPlan[currentPlanDay]=[];
  renderPlanner();
  toast('Day '+currentPlanDay+' cleared');
});

function renderPlanner(){
  const tbody = document.getElementById('plannerTableBody');
  tbody.innerHTML='';
  const entries = mealPlan[currentPlanDay];
  if(entries.length===0){
    tbody.innerHTML = `<tr class="empty-row"><td colspan="6">No meals planned for Day ${currentPlanDay} yet.</td></tr>`;
  } else {
    entries.forEach((entry,idx)=>{
      const food = FOOD_MAP[entry.foodId];
      if(!food) return;
      const n = entryNutrients(entry);
      const tr = document.createElement('tr');
      tr.innerHTML = `
        <td>${entry.meal}</td>
        <td>${food.name}</td>
        <td class="num">${entry.qty}</td>
        <td class="num">${entry.unit}</td>
        <td class="num">${fmt(n.calories)}</td>
        <td><button class="btn btn-sm btn-danger" data-idx="${idx}">✕</button></td>
      `;
      tbody.appendChild(tr);
    });
    tbody.querySelectorAll('button[data-idx]').forEach(btn=>{
      btn.addEventListener('click', e=>{
        mealPlan[currentPlanDay].splice(e.target.dataset.idx,1);
        renderPlanner();
      });
    });
  }
  renderPlannerChart();
}

let plannerChart;
function renderPlannerChart(){
  const t = calcTargets(profile);
  const d1 = sumEntries(mealPlan[1]);
  const d2 = sumEntries(mealPlan[2]);
  const ctx = document.getElementById('plannerCompareChart');
  const data = {
    labels: ['Calories (kcal/10)','Protein (g)','Carbs (g)','Fat (g)','Fiber (g)'],
    datasets:[
      {label:'Day 1', backgroundColor:'#5EEAD4', data:[d1.calories/10, d1.protein, d1.carbs, d1.fat, d1.fiber]},
      {label:'Day 2', backgroundColor:'#9D8CF1', data:[d2.calories/10, d2.protein, d2.carbs, d2.fat, d2.fiber]},
      {label:'Target', backgroundColor:'#3A4451', data:[t.calories/10, t.protein, t.carbs, t.fat, t.fiber]}
    ]
  };
  if(plannerChart) plannerChart.destroy();
  plannerChart = new Chart(ctx, {
    type:'bar', data,
    options:{
      responsive:true, maintainAspectRatio:false,
      plugins:{legend:{labels:{color:'#8B96A3',font:{family:'IBM Plex Mono',size:11}}}},
      scales:{
        x:{ticks:{color:'#8B96A3',font:{size:10}}, grid:{color:'#1A2028'}},
        y:{ticks:{color:'#8B96A3',font:{size:10}}, grid:{color:'#1A2028'}}
      }
    }
  });
}

/* CSV import: planner */
wireCSVZone('csvZonePlan','csvInputPlan', text=>{
  const {rows} = parseCSV(text);
  let added=0, skipped=0;
  rows.forEach(r=>{
    const food = findFoodByName(r.food||'');
    const day = (parseInt(r.day)===2) ? 2 : 1;
    if(!food || !dietAllows(profile.diet, food.diet)){ skipped++; return; }
    const unit = (r.unit && food.units[r.unit]) ? r.unit : 'g';
    const qty = parseFloat(r.quantity)||1;
    const meal = r.meal || 'Lunch';
    mealPlan[day].push({foodId:food.id, qty, unit, meal});
    added++;
  });
  renderPlanner();
  toast(`CSV import: ${added} added, ${skipped} skipped`);
});
document.getElementById('csvSamplePlan').addEventListener('click', e=>{
  e.preventDefault();
  downloadText('nutriscope_plan_sample.csv','day,meal,food,quantity,unit\n1,Breakfast,Oats,50,g\n1,Lunch,Dal,1,bowl\n2,Dinner,Chicken,150,g\n');
});

/* =========================================================================
   DASHBOARD VIEW
========================================================================= */
let macroChart, microChart;
function renderDashboard(){
  const t = calcTargets(profile);
  const c = sumEntries(foodLog);

  // energy dial
  const pct = t.calories>0 ? Math.min(c.calories/t.calories,1.4) : 0;
  const circumference = 515.2;
  const ring = document.getElementById('energyDialRing');
  ring.style.strokeDashoffset = circumference*(1-Math.min(pct,1));
  ring.style.stroke = pct>1.1 ? '#F4B942' : 'url(#gradMint2)';
  document.getElementById('dashEnergyPct').textContent = Math.round((c.calories/t.calories)*100)+'%';
  document.getElementById('dashEnergyText').textContent = `${Math.round(c.calories)} / ${t.calories} kcal`;

  // macro chart
  const ctx = document.getElementById('macroChart');
  const macroData = {
    labels:['Protein','Carbs','Fat','Fiber'],
    datasets:[
      {label:'Consumed', backgroundColor:'#5EEAD4', data:[round1(c.protein),round1(c.carbs),round1(c.fat),round1(c.fiber)]},
      {label:'Target', backgroundColor:'#2A323C', data:[t.protein,t.carbs,t.fat,t.fiber]}
    ]
  };
  if(macroChart) macroChart.destroy();
  macroChart = new Chart(ctx,{type:'bar', data:macroData, options:{
    responsive:true, maintainAspectRatio:false,
    plugins:{legend:{labels:{color:'#8B96A3',font:{family:'IBM Plex Mono',size:11}}}},
    scales:{x:{ticks:{color:'#8B96A3'},grid:{color:'#1A2028'}}, y:{ticks:{color:'#8B96A3'},grid:{color:'#1A2028'}}}
  }});

  // micro chart
  const microKeys = ['iron','calcium','vitc','vitd','b12','sodium','potassium','magnesium','zinc','vitaminA','folate'];
  const microPct = microKeys.map(k=> t[k]>0 ? Math.round((c[k]/t[k])*100) : 0);
  const microColors = microKeys.map((k,i)=>{
    const p = microPct[i];
    if(NUTRIENT_TYPE[k]==='max') return p>100? '#F2545B' : '#5EEAD4';
    if(p<50) return '#F2545B';
    if(p<90) return '#F4B942';
    if(p<=130) return '#5EEAD4';
    return '#9D8CF1';
  });
  const ctx2 = document.getElementById('microChart');
  if(microChart) microChart.destroy();
  microChart = new Chart(ctx2,{
    type:'bar',
    data:{labels:microKeys.map(k=>NUTRIENT_LABELS[k]), datasets:[{data:microPct, backgroundColor:microColors, borderRadius:4}]},
    options:{
      indexAxis:'y', responsive:true, maintainAspectRatio:false,
      plugins:{legend:{display:false}},
      scales:{x:{ticks:{color:'#8B96A3'},grid:{color:'#1A2028'}, min:0}, y:{ticks:{color:'#8B96A3',font:{size:11}},grid:{display:false}}}
    }
  });

  // top deficiencies / excesses
  const items = NUTRIENT_KEYS.filter(k=>k!=='calories').map(k=>{
    const pct = t[k]>0 ? (c[k]/t[k])*100 : 0;
    return {k, pct, isMax:NUTRIENT_TYPE[k]==='max'};
  });
  const deficiencies = items.filter(i=>!i.isMax && i.pct<80).sort((a,b)=>a.pct-b.pct).slice(0,5);
  const excesses = items.filter(i=> (i.isMax? i.pct>100 : i.pct>130) ).sort((a,b)=>b.pct-a.pct).slice(0,5);

  const defWrap = document.getElementById('topDeficiencies');
  defWrap.innerHTML = deficiencies.length ? deficiencies.map(i=>nutrientRowHTML(i.k,c[i.k],t[i.k],i.pct)).join('') : `<p class="small-note">No significant deficiencies detected in today's log.</p>`;
  const excWrap = document.getElementById('topExcesses');
  excWrap.innerHTML = excesses.length ? excesses.map(i=>nutrientRowHTML(i.k,c[i.k],t[i.k],i.pct)).join('') : `<p class="small-note">No significant excesses detected in today's log.</p>`;

  // full nutrient table
  const tbody = document.getElementById('nutrientTableBody');
  tbody.innerHTML = NUTRIENT_KEYS.map(k=>{
    const pct = t[k]>0 ? Math.round((c[k]/t[k])*100) : 0;
    const cls = NUTRIENT_TYPE[k]==='max' ? (pct>100?'pill-high':'pill-ok') : (pct<80?'pill-low':(pct>130?'pill-high':'pill-ok'));
    return `<tr><td>${NUTRIENT_LABELS[k]}</td><td class="num">${fmt(c[k])} ${NUTRIENT_UNITS[k]}</td><td class="num text-dim">${fmt(t[k])} ${NUTRIENT_UNITS[k]}</td><td><span class="pill ${cls}">${pct}%</span></td></tr>`;
  }).join('');
}
function nutrientRowHTML(k,consumed,target,pct){
  const barColor = pct<50?'var(--danger)':(pct<90?'var(--amber)':(pct<=130?'var(--mint)':'var(--violet)'));
  return `<div class="nutrient-row">
    <div class="nutrient-name">${NUTRIENT_LABELS[k]}</div>
    <div class="nutrient-bar"><div class="bar-track"><div class="bar-fill" style="width:${Math.min(pct,100)}%;background:${barColor};"></div></div></div>
    <div class="nutrient-pct" style="color:${barColor}">${Math.round(pct)}%</div>
  </div>`;
}

/* =========================================================================
   RISK ANALYSIS VIEW
========================================================================= */
const RISK_LIBRARY = {
  iron:{name:'Low iron intake', desc:'Sustained low iron intake is associated with fatigue, reduced concentration, and iron-deficiency anemia risk — particularly relevant on vegetarian patterns where iron is less bioavailable.'},
  calcium:{name:'Low calcium intake', desc:'Chronic calcium shortfall is linked to reduced bone density over time and higher long-term fracture risk.'},
  vitd:{name:'Low vitamin D intake', desc:'Vitamin D supports calcium absorption and immune function; low dietary intake (compounded by low sun exposure) raises deficiency risk.'},
  b12:{name:'Low vitamin B12 intake', desc:'B12 is found almost exclusively in animal-derived foods. Vegetarian and eggetarian patterns are at elevated risk of deficiency, which can affect nerve function and red blood cell formation.'},
  protein:{name:'Low protein intake', desc:'Insufficient protein over time can impair muscle maintenance, immune function, and recovery from illness or exercise.'},
  fiber:{name:'Low fiber intake', desc:'Low fiber intake is associated with digestive irregularity and, over the long term, higher cardiovascular and metabolic risk.'},
  vitc:{name:'Low vitamin C intake', desc:'Vitamin C supports immune function, iron absorption, and tissue repair; prolonged shortfall can impair wound healing.'},
  zinc:{name:'Low zinc intake', desc:'Zinc shortfall can impair immune response and wound healing over time.'},
  folate:{name:'Low folate intake', desc:'Folate is essential for cell division; chronic low intake is a particular concern during reproductive planning and pregnancy.'},
  sodium:{name:'High sodium intake', desc:'Sodium intake above recommended limits is linked to elevated blood pressure risk over time.'},
  fat:{name:'High fat intake', desc:'Fat intake well above target, especially if sustained, is linked to cardiovascular risk factors.'},
  calories:{name:'Energy imbalance', desc:'Intake is significantly off-target for your estimated energy needs, which can affect weight and energy levels if sustained.'}
};
function renderRisk(){
  const t = calcTargets(profile);
  const c = sumEntries(foodLog);
  const grid = document.getElementById('riskGrid');
  const risks = [];

  Object.keys(RISK_LIBRARY).forEach(k=>{
    if(k==='calories') return;
    if(!t[k]) return;
    const pct = (c[k]/t[k])*100;
    const isMax = NUTRIENT_TYPE[k]==='max';
    if(isMax){
      if(pct>150) risks.push({k, sev:'high', pct});
      else if(pct>100) risks.push({k, sev:'med', pct});
    } else {
      if(pct<50) risks.push({k, sev:'high', pct});
      else if(pct<80) risks.push({k, sev:'med', pct});
      else if(pct<95) risks.push({k, sev:'low', pct});
    }
  });
  // energy check
  const ePct = (c.calories/t.calories)*100;
  if(ePct<70 || ePct>140) risks.push({k:'calories', sev: (ePct<50||ePct>160)?'high':'med', pct:ePct});

  // extra flag: vegetarian + low b12 gets amplified severity note handled by copy already generic.
  risks.sort((a,b)=>({high:0,med:1,low:2}[a.sev]-{high:0,med:1,low:2}[b.sev]));

  if(risks.length===0){
    grid.innerHTML = `<div class="card" style="grid-column:1/-1;"><p class="small-note">No elevated risk patterns detected from today's log. Keep logging consistently for a more reliable read.</p></div>`;
    return;
  }
  grid.innerHTML = risks.map(r=>{
    const lib = RISK_LIBRARY[r.k];
    return `<div class="risk-card sev-${r.sev}">
      <div class="risk-head"><div class="risk-name">${lib.name}</div><div class="risk-sev">${r.sev}</div></div>
      <div class="risk-desc">${lib.desc}</div>
      <div class="small-note" style="margin-top:10px;">Today: ${Math.round(r.pct)}% of ${NUTRIENT_TYPE[r.k]==='max'?'ceiling':'target'}</div>
    </div>`;
  }).join('');
}

/* =========================================================================
   RECOMMENDATIONS VIEW
========================================================================= */
function renderRecs(){
  const t = calcTargets(profile);
  const c = sumEntries(foodLog);
  const foods = filteredFoods();

  // --- Additions: for top 4 deficient nutrients, suggest richest available foods ---
  const deficient = NUTRIENT_KEYS.filter(k=>k!=='calories' && NUTRIENT_TYPE[k]!=='max')
    .map(k=>({k, pct: t[k]>0?(c[k]/t[k])*100:0}))
    .filter(i=>i.pct<85).sort((a,b)=>a.pct-b.pct).slice(0,4);

  const addWrap = document.getElementById('recAdditions');
  if(deficient.length===0){
    addWrap.innerHTML = `<p class="small-note">Your log already meets most targets — no additions needed right now.</p>`;
  } else {
    addWrap.innerHTML = deficient.map(d=>{
      const best = [...foods].sort((a,b)=> (b.per100[d.k]||0) - (a.per100[d.k]||0))[0];
      const gapUnits = Math.round((t[d.k]-c[d.k]) / (best.per100[d.k]||1) * 100);
      return `<div class="rec-item">
        <div class="rec-icon">＋</div>
        <div class="rec-body">
          <div class="rec-title">Add ${best.name}</div>
          <div class="rec-desc">You're at ${Math.round(d.pct)}% of your ${NUTRIENT_LABELS[d.k]} target. ${best.name} is rich in ${NUTRIENT_LABELS[d.k].toLowerCase()} (${fmt(best.per100[d.k])} ${NUTRIENT_UNITS[d.k]}/100g).</div>
          <span class="rec-tag">~${Math.max(gapUnits,20)}g would close most of the gap</span>
        </div>
      </div>`;
    }).join('');
  }

  // --- Swaps: find logged foods that are poor sources of a deficient nutrient vs a better same-category alternative ---
  const swapWrap = document.getElementById('recSwaps');
  let swaps = [];
  foodLog.forEach(entry=>{
    const food = FOOD_MAP[entry.foodId];
    if(!food) return;
    deficient.forEach(d=>{
      const alt = foods.find(f=>f.id!==food.id && (f.per100[d.k]||0) > (food.per100[d.k]||0)*1.8 && f.per100.calories <= food.per100.calories*1.3);
      if(alt && !swaps.find(s=>s.from===food.id)){
        swaps.push({from:food.id, to:alt.id, k:d.k});
      }
    });
  });
  swaps = swaps.slice(0,4);
  if(swaps.length===0){
    swapWrap.innerHTML = `<p class="small-note">No beneficial swaps identified for today's log.</p>`;
  } else {
    swapWrap.innerHTML = swaps.map(s=>{
      const from=FOOD_MAP[s.from], to=FOOD_MAP[s.to];
      return `<div class="rec-item">
        <div class="rec-icon">⇄</div>
        <div class="rec-body">
          <div class="rec-title">${from.name} → ${to.name}</div>
          <div class="rec-desc">${to.name} delivers more ${NUTRIENT_LABELS[s.k].toLowerCase()} per 100g (${fmt(to.per100[s.k])} vs ${fmt(from.per100[s.k])} ${NUTRIENT_UNITS[s.k]}) at a comparable calorie cost.</div>
          <span class="rec-tag">Swap suggestion</span>
        </div>
      </div>`;
    }).join('');
  }

  // --- Portion adjustments ---
  const portWrap = document.getElementById('recPortions');
  let portions = [];
  const calPct = (c.calories/t.calories)*100;
  if(calPct>115 && foodLog.length){
    const biggest = [...foodLog].sort((a,b)=> entryNutrients(b).calories - entryNutrients(a).calories)[0];
    const food = FOOD_MAP[biggest.foodId];
    const reduceBy = Math.round(biggest.qty * 0.25 * 10)/10;
    portions.push({icon:'▾', title:`Reduce ${food.name} portion`, desc:`You're at ${Math.round(calPct)}% of your energy target. Trimming ${food.name} by about ${reduceBy} ${biggest.unit} would bring today closer to target.`});
  }
  if(calPct<85 && foodLog.length){
    portions.push({icon:'▴', title:'Increase overall portions', desc:`You're at ${Math.round(calPct)}% of your energy target. Consider a modest increase across meals, favoring nutrient-dense additions from the list on the left.`});
  }
  const fatPct = t.fat>0 ? (c.fat/t.fat)*100 : 0;
  if(fatPct>130 && foodLog.length){
    const fattiest = [...foodLog].sort((a,b)=> entryNutrients(b).fat - entryNutrients(a).fat)[0];
    portions.push({icon:'▾', title:`Trim ${FOOD_MAP[fattiest.foodId].name}`, desc:`Fat intake is at ${Math.round(fatPct)}% of target, largely from ${FOOD_MAP[fattiest.foodId].name}. A smaller portion would rebalance macros without removing the food entirely.`});
  }
  const sodiumPct = t.sodium>0 ? (c.sodium/t.sodium)*100 : 0;
  if(sodiumPct>100 && foodLog.length){
    portions.push({icon:'▾', title:'Watch sodium-dense items', desc:`Sodium is at ${Math.round(sodiumPct)}% of the daily ceiling. Bread, cheese, idli/dosa batter and processed items are common contributors — moderate portions of these.`});
  }
  portWrap.innerHTML = portions.length ? portions.map(p=>`<div class="rec-item">
      <div class="rec-icon">${p.icon}</div>
      <div class="rec-body"><div class="rec-title">${p.title}</div><div class="rec-desc">${p.desc}</div></div>
    </div>`).join('') : `<p class="small-note">No portion adjustments needed — today's balance looks reasonable.</p>`;
}

/* =========================================================================
   INIT
========================================================================= */
function init(){
  document.getElementById('p-gender').value = profile.gender;
  document.getElementById('p-activity').value = profile.activity;
  document.getElementById('p-diet').value = profile.diet;
  populateFoodSelect(document.getElementById('addFoodSelect'));
  populateUnitSelect(document.getElementById('addFoodUnit'), document.getElementById('addFoodSelect').value);
  populateFoodSelect(document.getElementById('planFoodSelect'));
  populateUnitSelect(document.getElementById('planFoodUnit'), document.getElementById('planFoodSelect').value);<img width="953" height="655" alt="Screenshot 2026-07-21 at 9 08 20 PM" src="https://github.com/user-attachments/assets/7baca6dc-4f9e-4108-bcdf-c40a265b2457" />
<img width="957" height="655" alt="Screenshot 2026-07-21 at 9 08 07 PM" src="https://github.com/user-attachments/assets/0d06bf6b-52d1-4129-b418-10f82be44612" />

  renderProfileReadout();
  renderLogTable();
  renderPlanner();
}
init();
</script>
</body>
</html>

# Marketing-Class-Project

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Netflix Top 10 Longevity Analysis</title>

<style>
:root {
  --red: #e50914;
  --bg: #0f0f0f;
  --card: #1a1a1a;
  --text: #ffffff;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Inter", system-ui, sans-serif;
}

html {
  scroll-behavior: smooth;
}

body {
  background: var(--bg);
  color: var(--text);
  overflow-x: hidden;
}

/* HERO */
.hero {
  height: 100vh;
  background:
    linear-gradient(120deg, rgba(0,0,0,.85), rgba(0,0,0,.4)),
    url("https://images.unsplash.com/photo-1524985069026-dd778a71c7b4")
    center/cover no-repeat;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  animation: fadeIn 1.5s ease forwards;
}

.hero h1 {
  font-size: 3.5rem;
  margin-bottom: 1rem;
  letter-spacing: -1px;
}

.hero p {
  font-size: 1.2rem;
  opacity: 0.85;
  margin-bottom: 2.5rem;
}

.btn {
  padding: 14px 36px;
  background: var(--red);
  color: white;
  border-radius: 40px;
  text-decoration: none;
  font-weight: 600;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.btn:hover {
  transform: scale(1.08);
  box-shadow: 0 0 40px rgba(229,9,20,.8);
}

/* SECTIONS */
.section {
  padding: 110px 10%;
  opacity: 0;
  transform: translateY(60px);
  transition: all 1s ease;
}

.section.show {
  opacity: 1;
  transform: translateY(0);
}

.section.dark {
  background: linear-gradient(180deg, #111, #000);
}

h2 {
  font-size: 2.4rem;
  margin-bottom: 50px;
  text-align: center;
}

/* CARDS */
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 32px;
}

.card {
  background: var(--card);
  padding: 34px;
  border-radius: 22px;
  position: relative;
  overflow: hidden;
  transition: transform 0.4s ease;
}

.card::after {
  content: "";
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at top left, rgba(229,9,20,.35), transparent 60%);
  opacity: 0;
  transition: opacity 0.4s ease;
}

.card:hover::after {
  opacity: 1;
}

.card:hover {
  transform: translateY(-14px) scale(1.04);
}

/* VISUALS */
.visual-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 32px;
}

.visual {
  background: #111;
  border-radius: 20px;
  padding: 50px;
  text-align: center;
  font-size: 1.1rem;
  opacity: 0.85;
  transition: transform 0.4s ease;
}

.visual:hover {
  transform: scale(1.06);
}

/* HEATMAP */
.heatmap {
  text-align: center;
}

.heatmap img {
  width: 100%;
  max-width: 900px;
  border-radius: 18px;
  box-shadow: 0 0 60px rgba(229,9,20,.3);
  transition: transform 0.4s ease;
}

.heatmap img:hover {
  transform: scale(1.04);
}

/* MODEL */
code {
  display: block;
  background: #111;
  padding: 26px;
  border-radius: 16px;
  font-size: 1.1rem;
  margin-top: 20px;
  color: #e5e5e5;
}

/* TIMELINE */
.timeline li {
  margin: 22px 0;
  padding-left: 22px;
  border-left: 3px solid var(--red);
}

/* FOOTER */
footer {
  padding: 50px;
  background: black;
  text-align: center;
  font-size: 0.95rem;
  opacity: 0.85;
}

/* ANIMATIONS */
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}
</style>
</head>

<body>

<!-- HERO -->
<section class="hero">
  <h1>What Keeps Shows in Netflix’s Top 10?</h1>
  <p>Data-driven insights on content longevity & global engagement</p>
  <a href="#insights" class="btn">Explore Insights</a>
</section>

<!-- INSIGHTS -->
<section class="section dark" id="insights">
  <h2>Key Insights</h2>
  <div class="card-grid">
    <div class="card">📺 TV Shows stay significantly longer than films</div>
    <div class="card">🌍 Non-English content outperforms expectations</div>
    <div class="card">📉 Initial rank has limited predictive power</div>
  </div>
</section>

<!-- HEATMAP -->
<section class="section">
  <h2>Engagement Heatmap</h2>
  <div class="heatmap">
    <!-- REPLACE src WITH YOUR HEATMAP IMAGE FILE -->
    <img src="heatmap.png" alt="Netflix Engagement Heatmap">
    <p style="margin-top:20px; opacity:0.75;">
      Content engagement patterns across weeks and rankings
    </p>
  </div>
</section>

<!-- MODEL -->
<section class="section dark">
  <h2>Regression Model</h2>
  <code>
Cumulative Weeks = 0.14 + 0.03·Week + 0.09·Rank
                 + 2.19·TV + 2.01·NonEnglish
  </code>
</section>

<!-- RECOMMENDATIONS -->
<section class="section">
  <h2>Marketing Strategy</h2>
  <ul class="timeline">
    <li><strong>Season Accelerator:</strong> Invest early in trending TV shows</li>
    <li><strong>Global Spotlight:</strong> Promote non-English hits internationally</li>
    <li><strong>Budget Shift:</strong> Prioritize content strength over release timing</li>
  </ul>
</section>

<footer>
  Marketing Analytics Project · Edward Dai
</footer>

<script>
const sections = document.querySelectorAll(".section");
window.addEventListener("scroll", () => {
  sections.forEach(sec => {
    if (sec.getBoundingClientRect().top < window.innerHeight - 120) {
      sec.classList.add("show");
    }
  });
});
</script>

</body>
</html>


# reimagined-chainsaw<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#edf1e7">
  <meta name="description" content="A personal portfolio and collection of curiosities.">
  <title>Your Name — a personal site</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=DM+Mono:wght@400;500&family=DM+Sans:wght@400;500;600;700&family=Playfair+Display:wght@500;600&display=swap" rel="stylesheet">
  <style>
    :root {
      color-scheme: light;
      --paper: #edf1e7;
      --ink: #202b23;
      --muted: #59665b;
      --line: #c8d0c3;
      --acid: #d8ed69;
      --coral: #e97758;
      --white: #f8f8f2;
      --serif: "Playfair Display", Georgia, serif;
      --sans: "DM Sans", sans-serif;
      --mono: "DM Mono", monospace;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      background-color: var(--paper);
      background-image: radial-gradient(#aab5a5 0.55px, transparent 0.55px);
      background-size: 13px 13px;
      color: var(--ink);
      font-family: var(--sans);
      font-size: 16px;
      line-height: 1.6;
    }
    a { color: inherit; }
    button { color: inherit; font: inherit; }
    .shell { width: min(100% - 48px, 1040px); margin: 0 auto; }
    .topbar {
      display: flex;
      align-items: center;
      justify-content: space-between;
      min-height: 82px;
      border-bottom: 1px solid var(--line);
    }
    .wordmark {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      font-family: var(--mono);
      font-size: 13px;
      text-decoration: none;
    }
    .mark { width: 13px; height: 13px; border-radius: 50%; background: var(--coral); }
    .nav { display: flex; gap: 30px; align-items: center; }
    .nav a { font-size: 13px; text-decoration: none; }
    .nav a:hover, .text-link:hover { text-decoration-thickness: 2px; text-decoration-line: underline; text-underline-offset: 5px; }
    .menu-toggle { display: none; border: 0; background: none; padding: 8px; cursor: pointer; }

    .hero {
      display: grid;
      grid-template-columns: minmax(0, 1.15fr) minmax(280px, .85fr);
      gap: clamp(36px, 8vw, 100px);
      align-items: center;
      padding: clamp(66px, 10vw, 120px) 0 88px;
    }
    .eyebrow, .section-label {
      margin: 0 0 20px;
      color: var(--muted);
      font-family: var(--mono);
      font-size: 11px;
      letter-spacing: .08em;
      text-transform: uppercase;
    }
    h1, h2, h3, p { margin-top: 0; }
    h1 {
      max-width: 660px;
      margin-bottom: 24px;
      font-family: var(--serif);
      font-size: clamp(48px, 7vw, 82px);
      font-weight: 500;
      line-height: 1.02;
    }
    h1 em { color: #bd513b; font-weight: 500; }
    .intro { max-width: 525px; margin-bottom: 30px; color: #465349; font-size: 18px; }
    .hero-links { display: flex; flex-wrap: wrap; gap: 12px; align-items: center; }
    .pill-link {
      display: inline-flex;
      align-items: center;
      gap: 9px;
      min-height: 44px;
      padding: 0 17px;
      border: 1px solid var(--ink);
      border-radius: 2px;
      background: var(--ink);
      color: var(--white);
      font-size: 13px;
      text-decoration: none;
      transition: transform .2s ease, background .2s ease;
    }
    .pill-link:hover { transform: translateY(-2px); background: #334438; }
    .text-link { font-size: 13px; text-underline-offset: 4px; }
    .portrait {
      position: relative;
      min-height: 360px;
      overflow: hidden;
      border: 1px solid var(--ink);
      background: #d6dfcf;
    }
    .portrait img { position: absolute; width: 100%; height: 100%; inset: 0; object-fit: cover; filter: saturate(.77); }
    .portrait-note {
      position: absolute;
      right: 14px;
      bottom: 14px;
      left: 14px;
      display: flex;
      justify-content: space-between;
      padding: 11px 13px;
      background: var(--acid);
      font-family: var(--mono);
      font-size: 10px;
      text-transform: uppercase;
    }
    .orbit {
      position: absolute;
      top: -20px;
      right: -14px;
      z-index: 1;
      display: grid;
      width: 74px;
      aspect-ratio: 1;
      place-items: center;
      border: 1px solid var(--ink);
      border-radius: 50%;
      background: var(--coral);
      font-family: var(--serif);
      font-size: 30px;
      transform: rotate(12deg);
    }

    .section { padding: 74px 0; border-top: 1px solid var(--line); }
    .section-heading { display: flex; align-items: end; justify-content: space-between; gap: 20px; margin-bottom: 28px; }
    .section-heading h2 { margin: 0; font-family: var(--serif); font-size: clamp(33px, 4.5vw, 48px); font-weight: 500; line-height: 1.1; }
    .section-heading .section-label { margin-bottom: 8px; }
    .filter-list { display: flex; flex-wrap: wrap; gap: 7px; }
    .filter {
      min-height: 34px;
      padding: 5px 12px;
      border: 1px solid var(--line);
      border-radius: 99px;
      background: transparent;
      cursor: pointer;
      font-size: 11px;
      transition: background .2s ease, border-color .2s ease;
    }
    .filter[aria-pressed="true"] { border-color: var(--ink); background: var(--ink); color: var(--white); }
    .project-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; }
    .project {
      min-width: 0;
      border: 1px solid var(--line);
      background: var(--white);
      animation: arrive .45s both;
    }
    .project[hidden] { display: none; }
    .project-image { position: relative; height: 190px; overflow: hidden; background: #d6dfcf; }
    .project-image img { display: block; width: 100%; height: 100%; object-fit: cover; transition: transform .45s ease; }
    .project:hover .project-image img { transform: scale(1.04); }
    .project-image span { position: absolute; top: 12px; left: 12px; padding: 5px 8px; background: var(--acid); font-family: var(--mono); font-size: 10px; text-transform: uppercase; }
    .project-copy { padding: 18px; }
    .project-copy h3 { margin: 0 0 7px; font-size: 16px; font-weight: 600; }
    .project-copy p { margin: 0; color: var(--muted); font-size: 13px; }
    .project-number { display: block; margin-bottom: 8px; color: var(--muted); font-family: var(--mono); font-size: 10px; }

    .curiosity { display: grid; grid-template-columns: .8fr 1.2fr; gap: 70px; align-items: start; }
    .curiosity-lede { max-width: 290px; color: var(--muted); }
    .topic-tabs { display: flex; gap: 8px; margin-bottom: 18px; }
    .topic-tab {
      padding: 7px 13px;
      border: 1px solid var(--line);
      border-radius: 2px;
      background: transparent;
      cursor: pointer;
      font-family: var(--mono);
      font-size: 11px;
    }
    .topic-tab[aria-selected="true"] { border-color: var(--coral); background: var(--coral); }
    .topic-panel { min-height: 166px; padding: 24px 25px; border-left: 3px solid var(--coral); background: rgba(248, 248, 242, .8); }
    .topic-panel h3 { margin-bottom: 10px; font-family: var(--serif); font-size: 27px; font-weight: 500; }
    .topic-panel p { max-width: 500px; margin-bottom: 0; color: var(--muted); }

    .play-section { display: grid; grid-template-columns: .8fr 1.2fr; gap: 70px; align-items: center; }
    .play-section h2 { margin-bottom: 12px; font-family: var(--serif); font-size: 38px; font-weight: 500; }
    .play-section p { max-width: 310px; margin-bottom: 0; color: var(--muted); font-size: 14px; }
    .game-wrap { border: 1px solid var(--ink); background: var(--white); }
    .game-status { display: flex; justify-content: space-between; padding: 10px 14px; border-bottom: 1px solid var(--line); font-family: var(--mono); font-size: 10px; text-transform: uppercase; }
    .game {
      position: relative;
      height: 150px;
      overflow: hidden;
      background-image: linear-gradient(rgba(32, 43, 35, .05) 1px, transparent 1px), linear-gradient(90deg, rgba(32, 43, 35, .05) 1px, transparent 1px);
      background-size: 24px 24px;
      touch-action: manipulation;
      cursor: pointer;
    }
    .ground { position: absolute; right: 0; bottom: 30px; left: 0; border-top: 1px solid var(--ink); }
    .runner { position: absolute; bottom: 31px; left: 11%; width: 25px; height: 31px; border: 1px solid var(--ink); background: var(--coral); transition: bottom .16s ease-out; }
    .runner::before { position: absolute; top: 6px; right: 5px; width: 4px; height: 4px; border-radius: 50%; background: var(--ink); content: ""; }
    .runner.jumping { bottom: 78px; }
    .obstacle { position: absolute; right: -22px; bottom: 31px; width: 15px; height: 24px; border: 1px solid var(--ink); background: var(--acid); }
    .obstacle.moving { animation: travel 1.65s linear infinite; }
    .game-message { position: absolute; inset: 0; display: grid; place-items: center; color: var(--muted); font-family: var(--mono); font-size: 11px; pointer-events: none; }
    .game-message[hidden] { display: none; }
    .game-controls { display: flex; justify-content: space-between; align-items: center; padding: 10px 14px; border-top: 1px solid var(--line); }
    .game-controls span { color: var(--muted); font-family: var(--mono); font-size: 10px; }
    .game-button { padding: 6px 12px; border: 1px solid var(--ink); border-radius: 2px; background: var(--ink); color: var(--white); cursor: pointer; font-size: 11px; }
    .footer { display: flex; justify-content: space-between; gap: 20px; padding: 28px 0 42px; border-top: 1px solid var(--line); color: var(--muted); font-family: var(--mono); font-size: 10px; }
    .footer a { text-underline-offset: 3px; }
    .reveal { animation: arrive .7s both; }
    @keyframes arrive { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
    @keyframes travel { from { right: -22px; } to { right: calc(100% + 22px); } }

    @media (max-width: 720px) {
      .shell { width: min(100% - 36px, 560px); }
      .topbar { min-height: 70px; }
      .menu-toggle { display: inline-flex; }
      .nav { position: absolute; top: 69px; right: 18px; left: 18px; z-index: 5; display: none; flex-direction: column; align-items: stretch; gap: 0; padding: 8px; border: 1px solid var(--ink); background: var(--paper); }
      .nav.open { display: flex; }
      .nav a { padding: 11px 10px; }
      .hero { grid-template-columns: 1fr; gap: 42px; padding: 68px 0; }
      .portrait { min-height: 290px; }
      .section { padding: 58px 0; }
      .section-heading { align-items: start; flex-direction: column; }
      .project-grid { grid-template-columns: 1fr; }
      .project-image { height: 220px; }
      .curiosity, .play-section { grid-template-columns: 1fr; gap: 25px; }
      .curiosity-lede { max-width: 470px; margin-bottom: 0; }
      .play-section { align-items: start; }
      .footer { flex-direction: column; gap: 8px; }
    }
    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after { scroll-behavior: auto !important; animation-duration: .01ms !important; animation-iteration-count: 1 !important; transition-duration: .01ms !important; }
    }
  </style>
</head>
<body>
  <header class="shell topbar">
    <a class="wordmark" href="#top"><span class="mark" aria-hidden="true"></span><span>YOUR NAME / INDEX</span></a>
    <button class="menu-toggle" type="button" aria-label="Open navigation" aria-expanded="false" aria-controls="site-nav">MENU</button>
    <nav class="nav" id="site-nav" aria-label="Main navigation">
      <a href="#work">Work</a>
      <a href="#curiosities">Curiosities</a>
      <a href="#play">Play</a>
      <a href="#contact">Say hello</a>
    </nav>
  </header>

  <main class="shell" id="top">
    <section class="hero" aria-labelledby="intro-title">
      <div class="reveal">
        <p class="eyebrow">A small corner of the internet · 2026</p>
        <h1 id="intro-title">Hello, I'm <em>Your Name.</em></h1>
        <p class="intro">I make things, follow questions, and keep a little space for whatever catches my attention next.</p>
        <div class="hero-links">
          <a class="pill-link" href="#work">A few things I've made <span aria-hidden="true">↘</span></a>
          <a class="text-link" href="#curiosities">Or wander around</a>
        </div>
      </div>
      <div class="portrait reveal">
        <span class="orbit" aria-hidden="true">hi!</span>
        <img src="https://images.unsplash.com/photo-1470770841072-f978cf4d019e?auto=format&amp;fit=crop&amp;w=1000&amp;q=85" alt="A winding trail through a green mountain landscape">
        <div class="portrait-note"><span>Currently: collecting ideas</span><span>01 / 04</span></div>
      </div>
    </section>

    <section class="section" id="work" aria-labelledby="work-title">
      <div class="section-heading">
        <div>
          <p class="section-label">01 — Selected work</p>
          <h2 id="work-title">Things I've put into the world</h2>
        </div>
        <div class="filter-list" role="group" aria-label="Filter projects">
          <button class="filter" type="button" data-filter="all" aria-pressed="true">Everything</button>
          <button class="filter" type="button" data-filter="making" aria-pressed="false">Making</button>
          <button class="filter" type="button" data-filter="writing" aria-pressed="false">Writing</button>
          <button class="filter" type="button" data-filter="other" aria-pressed="false">Other</button>
        </div>
      </div>
      <div class="project-grid">
        <article class="project" data-category="making">
          <div class="project-image"><img src="https://images.unsplash.com/photo-1513364776144-60967b0f800f?auto=format&amp;fit=crop&amp;w=900&amp;q=85" alt="Colorful paint and brushes on an artist's work table"><span>Making</span></div>
          <div class="project-copy"><span class="project-number">01 / PROJECT</span><h3>Your project title</h3><p>A line about what you made, who it was for, or what you learned.</p></div>
        </article>
        <article class="project" data-category="writing">
          <div class="project-image"><img src="https://images.unsplash.com/photo-1517842645767-c639042777db?auto=format&amp;fit=crop&amp;w=900&amp;q=85" alt="A notebook and pen ready for writing"><span>Writing</span></div>
          <div class="project-copy"><span class="project-number">02 / PROJECT</span><h3>A note, essay, or idea</h3><p>Share a piece of writing or a thought that stayed with you.</p></div>
        </article>
        <article class="project" data-category="other">
          <div class="project-image"><img src="https://images.unsplash.com/photo-1519681393784-d120267933ba?auto=format&amp;fit=crop&amp;w=900&amp;q=85" alt="A starry night above a snow-covered mountain"><span>Other</span></div>
          <div class="project-copy"><span class="project-number">03 / PROJECT</span><h3>A thing you care about</h3><p>There is room here for the work that doesn't fit a neat category.</p></div>
        </article>
      </div>
    </section>

    <section class="section curiosity" id="curiosities" aria-labelledby="curiosity-title">
      <div>
        <p class="section-label">02 — Outside the bio</p>
        <h2 id="curiosity-title" style="font-family: var(--serif); font-size: clamp(36px, 5vw, 54px); font-weight: 500; line-height: 1.07;">A few open tabs in my brain</h2>
        <p class="curiosity-lede">The best conversations usually start somewhere besides a job title. Pick a thread.</p>
      </div>
      <div>
        <div class="topic-tabs" role="tablist" aria-label="Personal interests">
          <button class="topic-tab" id="tab-noticing" type="button" role="tab" aria-selected="true" aria-controls="topic-panel" data-topic="noticing">Noticing</button>
          <button class="topic-tab" id="tab-making" type="button" role="tab" aria-selected="false" aria-controls="topic-panel" data-topic="making">Making</button>
          <button class="topic-tab" id="tab-wondering" type="button" role="tab" aria-selected="false" aria-controls="topic-panel" data-topic="wondering">Wondering</button>
        </div>
        <div class="topic-panel" id="topic-panel" role="tabpanel" aria-labelledby="tab-noticing" tabindex="0">
          <h3 id="topic-title">Noticing the small stuff</h3>
          <p id="topic-copy">A favorite detail, a place you return to, or something you keep finding beautiful goes here.</p>
        </div>
      </div>
    </section>

    <section class="section play-section" id="play" aria-labelledby="play-title">
      <div>
        <p class="section-label">03 — A tiny intermission</p>
        <h2 id="play-title">Take a little break?</h2>
        <p>Get over the block. Tap the field or press space to jump. How long can you keep going?</p>
      </div>
      <div class="game-wrap">
        <div class="game-status"><span>Keep moving</span><span>Score <b id="score">00</b> · Best <b id="best-score">00</b></span></div>
        <div class="game" id="game" role="button" tabindex="0" aria-label="Jump over the block">
          <div class="runner" id="runner" aria-hidden="true"></div>
          <div class="obstacle" id="obstacle" aria-hidden="true"></div>
          <div class="ground" aria-hidden="true"></div>
          <div class="game-message" id="game-message">Tap or press space to start</div>
        </div>
        <div class="game-controls"><span>SPACE / TAP TO JUMP</span><button class="game-button" type="button" id="game-button">Start game</button></div>
      </div>
    </section>
  </main>

  <footer class="shell footer" id="contact">
    <span>© <span id="year"></span> Your Name · made with curiosity</span>
    <a href="mailto:hello@example.com">hello@example.com ↗</a>
  </footer>

  <script>
    const menuToggle = document.querySelector('.menu-toggle');
    const navigation = document.querySelector('#site-nav');
    menuToggle.addEventListener('click', () => {
      const open = menuToggle.getAttribute('aria-expanded') !== 'true';
      menuToggle.setAttribute('aria-expanded', String(open));
      menuToggle.setAttribute('aria-label', open ? 'Close navigation' : 'Open navigation');
      navigation.classList.toggle('open', open);
    });
    navigation.addEventListener('click', (event) => {
      if (event.target.closest('a')) {
        navigation.classList.remove('open');
        menuToggle.setAttribute('aria-expanded', 'false');
        menuToggle.setAttribute('aria-label', 'Open navigation');
      }
    });

    const filters = [...document.querySelectorAll('.filter')];
    const projects = [...document.querySelectorAll('.project')];
    filters.forEach((button) => button.addEventListener('click', () => {
      filters.forEach((item) => item.setAttribute('aria-pressed', String(item === button)));
      projects.forEach((project) => {
        project.hidden = button.dataset.filter !== 'all' && project.dataset.category !== button.dataset.filter;
      });
    }));

    const topics = {
      noticing: ['Noticing the small stuff', 'A favorite detail, a place you return to, or something you keep finding beautiful goes here.'],
      making: ['Making just to see what happens', 'Share the things you like to make, tinker with, collect, or learn by doing.'],
      wondering: ['Questions worth following', 'A subject you could happily get lost in, even without needing to be an expert.']
    };
    const topicTabs = [...document.querySelectorAll('.topic-tab')];
    topicTabs.forEach((tab, index) => tab.addEventListener('click', () => {
      topicTabs.forEach((item) => item.setAttribute('aria-selected', String(item === tab)));
      document.querySelector('#topic-panel').setAttribute('aria-labelledby', tab.id);
      document.querySelector('#topic-title').textContent = topics[tab.dataset.topic][0];
      document.querySelector('#topic-copy').textContent = topics[tab.dataset.topic][1];
    }));
    topicTabs.forEach((tab, index) => tab.addEventListener('keydown', (event) => {
      if (!['ArrowRight', 'ArrowLeft'].includes(event.key)) return;
      event.preventDefault();
      topicTabs[(index + (event.key === 'ArrowRight' ? 1 : topicTabs.length - 1)) % topicTabs.length].focus();
    }));

    document.querySelector('#year').textContent = new Date().getFullYear();
    const game = document.querySelector('#game');
    const runner = document.querySelector('#runner');
    const obstacle = document.querySelector('#obstacle');
    const gameMessage = document.querySelector('#game-message');
    const gameButton = document.querySelector('#game-button');
    const scoreLabel = document.querySelector('#score');
    const bestLabel = document.querySelector('#best-score');
    let running = false;
    let started = false;
    let score = 0;
    let scoreTimer;
    let collisionTimer;
    let jumpTimer;
    let best = Number(localStorage.getItem('portfolio-game-best') || 0);
    bestLabel.textContent = String(best).padStart(2, '0');

    function endGame() {
      running = false;
      clearInterval(scoreTimer);
      clearInterval(collisionTimer);
      obstacle.classList.remove('moving');
      gameMessage.textContent = `Nice run: ${score}. Tap to play again`;
      gameMessage.hidden = false;
      gameButton.textContent = 'Play again';
      if (score > best) {
        best = score;
        localStorage.setItem('portfolio-game-best', String(best));
        bestLabel.textContent = String(best).padStart(2, '0');
      }
    }

    function startGame() {
      clearInterval(scoreTimer);
      clearInterval(collisionTimer);
      running = true;
      started = true;
      score = 0;
      scoreLabel.textContent = '00';
      gameMessage.hidden = true;
      gameButton.textContent = 'Restart';
      obstacle.classList.remove('moving');
      void obstacle.offsetWidth;
      obstacle.classList.add('moving');
      scoreTimer = setInterval(() => {
        score += 1;
        scoreLabel.textContent = String(score).padStart(2, '0');
      }, 500);
      collisionTimer = setInterval(() => {
        const player = runner.getBoundingClientRect();
        const block = obstacle.getBoundingClientRect();
        const clear = player.right < block.left + 4 || player.left > block.right - 4 || player.bottom < block.top + 5;
        if (!clear) endGame();
      }, 30);
    }

    function jump() {
      if (!running) {
        if (!started || gameMessage.hidden === false) startGame();
        return;
      }
      runner.classList.add('jumping');
      clearTimeout(jumpTimer);
      jumpTimer = setTimeout(() => runner.classList.remove('jumping'), 430);
    }

    game.addEventListener('pointerdown', (event) => {
      if (event.target !== gameButton) jump();
    });
    game.addEventListener('keydown', (event) => {
      if (event.code === 'Space' || event.code === 'ArrowUp') {
        event.preventDefault();
        jump();
      }
    });
    gameButton.addEventListener('click', () => startGame());
    document.addEventListener('keydown', (event) => {
      if (event.code === 'Space' && !['BUTTON', 'A'].includes(document.activeElement.tagName) && !event.target.closest('[role="tab"]')) {
        event.preventDefault();
        jump();
      }
    });
  </script>
</body>
</html>

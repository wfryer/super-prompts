---
title: News Share Station
description: Builds a bookmarklet and a retro arcade styled web page that turn any news article into a ready-to-post message with launch buttons for six social networks, plus a copy-ready show notes link.
version: 1.0
updated: 2026-11-07
works_best_in: Claude (artifacts or file output) or any AI that can write a single HTML file. Use Chrome for the bookmarklet.
license: CC BY 4.0
tags: social media, bookmarklet, news curation, HTML, non-classroom
---

# News Share Station

Sharing one article to six networks means six copy and paste rounds. This prompt builds two small tools that cut that down to a click on the article, a paste, and a few buttons.

- **Share Prep bookmarklet.** One click on any article page copies the URL, headline, source, publish date, and a short summary.
- **Share Station page.** You paste that block. The page title-cases the headline, builds the post, counts characters for each network, and gives you one launch button per network. Every button also copies the post, so a blank composer only needs a paste.
- **Show notes box.** The same page builds a show notes line: a linked headline followed by (Source; Date). Copy it with the link intact and paste it straight into a document, or copy it as Markdown.

The page has an 8-bit arcade look with a space-age flying saucer, a green CRT screen for the post preview, and a score counter that turns each button green after you use it. Each network gets an original pixel-art icon (these are not the official logos).

## How to use it

1. Copy the prompt below and paste it into a new chat with Claude or another AI that can write HTML.
2. Answer the short setup questions (your Mastodon server, your Facebook Page, which networks you want).
3. Save the page it gives you as `share-station.html`, or open it as an artifact. Host it on GitHub Pages if you want it on every device.
4. Make a new bookmark named **Share Prep** and paste the `javascript:` code into the bookmark's URL field. In Chrome, show the bookmarks bar, right-click it, and choose Add page. Do not paste it into the address bar.
5. On any article, click **Share Prep**, click **Copy**, paste into the page, add 5 to 7 hashtags, and launch. For show notes, use the Show Notes Link box instead and click **Copy with link**.

## The prompt

Copy everything between the lines.

---

<!-- PROMPT START -->
You are helping me build "Share Station": a bookmarklet plus a single-file web page that speeds up sharing one news article to several social networks. Both pieces are fully specified below. Your job is to ask a few setup questions, then deliver the pieces with only my settings changed. Do not redesign anything.

## STEP 0: ASK FIRST

Ask these questions in ONE short message, then wait for my answers. If I already answered one, skip it. If I say "defaults", use the default in brackets.

1. What is my Mastodon server domain? [mastodon.social] Say "none" if I do not use Mastodon.
2. What is my Facebook Page URL, if I post as a Page? [blank, which uses the plain Facebook share dialog]
3. Which networks should the page include? Choices: Bluesky, Threads, Mastodon, LinkedIn, Facebook, Spoutible. [all six]
4. Should I get the page as a downloadable file named share-station.html, or as an artifact or preview if you can make one? [artifact if you can, otherwise a file]

## STEP 1: THE BOOKMARKLET (copy exactly, do not edit)

Give me this code in one code block, unchanged. It reads only the page I am on, sends nothing anywhere, and opens a small panel with the block and a Copy button. If something fails, the panel shows the error text.

```
javascript:!function(){var e=document;function t(t,a){var r=e.getElementById("share-prep-panel");r&&r.remove();var n=e.createElement("div");n.id="share-prep-panel",n.style.cssText="position:fixed;top:12px;right:12px;z-index:2147483647;width:420px;max-width:92vw;background:#fff;color:#111;border:2px solid "+(a?"#b3261e":"#0a6a73")+";border-radius:10px;box-shadow:0 8px 28px rgba(0,0,0,.4);padding:12px;font:14px/1.4 system-ui,sans-serif";var i=e.createElement("div");i.style.cssText="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;font-weight:700";var o=e.createElement("span");o.textContent=a?"Share Prep error":"Share Prep";var p=e.createElement("button");p.textContent="Close",p.style.cssText="font:600 13px system-ui,sans-serif;padding:3px 10px;cursor:pointer",p.onclick=function(){n.remove()},i.appendChild(o),i.appendChild(p);var s=e.createElement("textarea");s.value=t,s.readOnly=!1,s.style.cssText="width:394px;max-width:calc(92vw - 28px);height:170px;box-sizing:border-box;font:12px/1.4 ui-monospace,Menlo,monospace;padding:8px;color:#111;background:#f6f6f6;border:1px solid #bbb;border-radius:6px";var c=e.createElement("div");c.style.cssText="display:flex;gap:10px;align-items:center;margin-top:8px";var l=e.createElement("button");l.textContent="Copy",l.style.cssText="font:700 14px system-ui,sans-serif;padding:6px 16px;cursor:pointer;background:#0a6a73;color:#fff;border:0;border-radius:6px";var d=e.createElement("span");if(d.style.cssText="font-weight:600",d.textContent=a?"":"Click Copy, then paste into Claude.",l.onclick=function(){var a=!1;s.focus(),s.select();try{a=e.execCommand("copy")}catch(e){}navigator.clipboard&&navigator.clipboard.writeText&&navigator.clipboard.writeText(t).then(function(){d.textContent="Copied. Paste it into Claude.",d.style.color="#14532d"},function(){a&&(d.textContent="Copied. Paste it into Claude.",d.style.color="#14532d")}),a?(d.textContent="Copied. Paste it into Claude.",d.style.color="#14532d"):navigator.clipboard||(d.textContent="Press Cmd+C or Ctrl+C.")},c.appendChild(l),c.appendChild(d),n.appendChild(i),n.appendChild(s),n.appendChild(c),(e.body||e.documentElement).appendChild(n),s.focus(),s.select(),!a&&navigator.clipboard&&navigator.clipboard.writeText)try{navigator.clipboard.writeText(t).then(function(){d.textContent="Copied. Paste it into Claude.",d.style.color="#14532d"},function(){})}catch(e){}}try{var a=function(t){var a=e.querySelector(t);return a?(a.getAttribute("content")||"").trim():""},r=function(e){return(e||"").replace(/\s+/g," ").trim()},n=new URL(location.href);Array.from(n.searchParams.keys()).forEach(function(e){/^(utm_|fbclid|gclid|mc_|igshid|ocid|ref_src|cmpid)/i.test(e)&&n.searchParams.delete(e)});var i=n.toString(),o=e.querySelector("h1"),p=r(a('meta[property="og:title"]')||a('meta[name="twitter:title"]')||o&&o.textContent||e.title),s=r(a('meta[property="og:site_name"]')||a('meta[name="application-name"]')||location.hostname.replace(/^www\./,"")),c=a('meta[property="article:published_time"]')||a('meta[name="article:published_time"]')||a('meta[name="date"]')||a('meta[name="pubdate"]')||a('meta[name="publish-date"]')||a('meta[itemprop="datePublished"]');if(!c){var l=e.querySelector("time[datetime]");l&&(c=l.getAttribute("datetime"))}if(!c)for(var d=e.querySelectorAll('script[type="application/ld+json"]'),m=0;m<d.length&&!c;m++){var x=/"datePublished"\s*:\s*"([^"]+)"/.exec(d[m].textContent);x&&(c=x[1])}var u=["January","February","March","April","May","June","July","August","September","October","November","December"],f="DATE NOT FOUND",h=/^(\d{4})-(\d{2})-(\d{2})/.exec(c||"");if(h)f=parseInt(h[3],10)+" "+u[parseInt(h[2],10)-1]+" "+h[1];else if(c){var b=new Date(c);isNaN(b)||(f=b.getDate()+" "+u[b.getMonth()]+" "+b.getFullYear())}t("URL: "+i+"\nTITLE: "+p+"\nSOURCE: "+s+"\nDATE: "+f+"\nSUMMARY: "+r(a('meta[property="og:description"]')||a('meta[name="description"]')).slice(0,300),!1)}catch(e){t("Share Prep hit an error: "+(e&&e.message?e.message:e)+"\nPage: "+location.href,!0)}}();
```

## STEP 2: THE PAGE (copy the reference code, change only what is listed)

Deliver the reference page below as one self-contained HTML file. These are the ONLY changes you may make:

- Set `CONFIG.mastodonServer` and `CONFIG.facebookPageUrl` from my answers.
- Delete the entries from the `PLATFORMS` list for any network I did not want, and update the words "six networks" in the header tagline to the right number. The score counter adjusts by itself, so leave that code alone.
- If I asked for a different default demo article or hashtags, change only the `DEMO` and `DEMO_TAGS` lines.

Keep the credit line in the footer. Keep every other line of markup, style, and script exactly as given, because the code was tested as written. Do not add libraries, do not load images from other sites, and do not store anything in the browser.

Style reference, in case you must describe the page to me: night-sky background with pixel stars and scanlines; neon colors (cyan, magenta, yellow, orange, lime) on deep purple; Press Start 2P for headings and buttons, VT323 for body text, Share Tech Mono for inputs; framed stage panels (cyan, yellow, orange, magenta); chunky arcade buttons that press down when clicked; a green CRT screen for the post preview; a white paper-style box for the show notes line; a score box that counts launched networks.

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Share Station</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Share+Tech+Mono&family=VT323&display=swap" rel="stylesheet">
<style>
  /* Layout idea: an arcade cabinet in a space-age city. Stars and a horizon grid behind, three colored stage panels stacked in one column, a CRT screen for the post. */
  :root {
    --space: #14123a;
    --space-2: #1d1a52;
    --ink: #f3f0ff;
    --muted: #b9b4ee;
    --cyan: #29f0ff;
    --magenta: #ff3fa4;
    --yellow: #ffd23f;
    --orange: #ff7a2f;
    --lime: #7dff6b;
    --crt: #04110a;
    --font-pixel: "Press Start 2P", "Courier New", monospace;
    --font-body: "VT323", "Courier New", monospace;
    --font-mono: "Share Tech Mono", ui-monospace, Menlo, monospace;
    color-scheme: dark;
  }
  * { box-sizing: border-box; }
  html, body { margin: 0; }
  body {
    background-color: var(--space);
    background-image:
      radial-gradient(2px 2px at 12% 18%, #fff 50%, transparent 51%),
      radial-gradient(2px 2px at 78% 9%, var(--cyan) 50%, transparent 51%),
      radial-gradient(2px 2px at 44% 33%, #fff 50%, transparent 51%),
      radial-gradient(3px 3px at 90% 46%, var(--yellow) 50%, transparent 51%),
      radial-gradient(2px 2px at 25% 62%, var(--magenta) 50%, transparent 51%),
      radial-gradient(2px 2px at 63% 78%, #fff 50%, transparent 51%),
      linear-gradient(180deg, var(--space) 0%, var(--space-2) 70%, #3a1a6e 100%);
    background-size: 340px 340px, 420px 420px, 300px 300px, 520px 520px, 380px 380px, 460px 460px, 100% 100%;
    background-attachment: fixed;
    color: var(--ink);
    font-family: var(--font-body);
    font-size: 22px;
    line-height: 1.2;
    padding: 24px 16px 64px;
    min-height: 100%;
  }
  body::before {
    content: "";
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(180deg, rgba(0,0,0,0.16) 0, rgba(0,0,0,0.16) 1px, transparent 1px, transparent 3px);
    pointer-events: none;
    z-index: 5;
  }
  main { max-width: 820px; margin: 0 auto; display: flex; flex-direction: column; gap: 26px; position: relative; z-index: 1; }

  /* Header */
  .top { display: flex; gap: 18px; align-items: center; justify-content: space-between; flex-wrap: wrap; }
  .brand { display: flex; align-items: center; gap: 16px; }
  .ufo { width: 96px; height: 54px; flex: none; animation: bob 2.4s steps(2, end) infinite; }
  @keyframes bob { 0% { transform: translateY(0); } 50% { transform: translateY(-5px); } 100% { transform: translateY(0); } }
  h1 {
    font-family: var(--font-pixel);
    font-size: 26px;
    line-height: 1.25;
    margin: 0;
    color: var(--yellow);
    text-shadow: 3px 3px 0 var(--magenta), 6px 6px 0 #5a1a7a;
    letter-spacing: 1px;
  }
  .tag { color: var(--cyan); font-size: 22px; margin-top: 6px; }
  .hud { font-family: var(--font-pixel); font-size: 11px; line-height: 1.9; text-align: right; color: var(--lime); border: 3px solid var(--lime); padding: 8px 12px; background: var(--crt); }
  .hud span { color: var(--yellow); }

  .coins { display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; margin: 0; padding: 0; list-style: none; }
  .coins li { border: 3px solid var(--muted); border-radius: 14px; padding: 10px 12px; background: rgba(20, 18, 58, 0.8); font-size: 21px; }
  .coins b { display: block; font-family: var(--font-pixel); font-size: 10px; color: var(--orange); margin-bottom: 6px; font-weight: 400; }
  @media (max-width: 620px) { .coins { grid-template-columns: 1fr; } }

  /* Panels */
  .panel {
    --c: var(--cyan);
    background: rgba(20, 18, 58, 0.92);
    border: 4px solid var(--c);
    border-radius: 22px;
    padding: 18px;
    box-shadow: 0 0 0 4px var(--space), 0 0 0 8px var(--c), 8px 12px 0 8px rgba(0,0,0,0.35);
    margin: 0 8px;
  }
  .panel.cyan { --c: var(--cyan); }
  .panel.yellow { --c: var(--yellow); }
  .panel.magenta { --c: var(--magenta); }
  .panel.orange { --c: var(--orange); }
  .stack { display: flex; flex-direction: column; gap: 14px; }
  h2 { font-family: var(--font-pixel); font-size: 13px; line-height: 1.5; margin: 0; color: var(--c); font-weight: 400; display: flex; gap: 12px; align-items: center; flex-wrap: wrap; }
  h2 .stage { background: var(--c); color: var(--space); padding: 5px 8px; font-size: 11px; }

  label { display: block; font-family: var(--font-pixel); font-size: 10px; color: var(--yellow); margin-bottom: 8px; line-height: 1.5; }
  input[type="text"], textarea {
    width: 100%;
    font-family: var(--font-mono);
    font-size: 16px;
    color: var(--ink);
    background: #0b0a26;
    border: 3px solid #4b46a8;
    border-radius: 6px;
    padding: 9px 11px;
  }
  textarea { resize: vertical; }
  input[type="text"]:focus, textarea:focus { border-color: var(--cyan); outline: none; box-shadow: 0 0 0 3px rgba(41, 240, 255, 0.35); }
  :focus-visible { outline: 3px solid var(--yellow); outline-offset: 3px; }
  .grid2 { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; }
  @media (max-width: 620px) { .grid2 { grid-template-columns: 1fr; } }
  .row { display: flex; gap: 12px; align-items: center; flex-wrap: wrap; }
  .hint { color: var(--muted); margin: 8px 0 0; }
  .hint.warn { color: var(--yellow); }
  .check { display: flex; gap: 10px; align-items: center; font-family: var(--font-body); font-size: 22px; color: var(--ink); margin: 0; }
  .check input { width: 22px; height: 22px; accent-color: var(--magenta); }

  /* Arcade buttons */
  button, .btn {
    font-family: var(--font-pixel);
    font-size: 11px;
    line-height: 1.4;
    text-transform: uppercase;
    color: #1a1033;
    background: var(--yellow);
    border: 0;
    border-radius: 10px;
    padding: 13px 16px 11px;
    box-shadow: 0 6px 0 #b8860b, 0 8px 0 rgba(0,0,0,0.4);
    cursor: pointer;
    text-decoration: none;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    position: relative;
    top: 0;
  }
  button:active, .btn:active { top: 5px; box-shadow: 0 1px 0 #b8860b, 0 3px 0 rgba(0,0,0,0.4); }
  button.cyan { background: var(--cyan); box-shadow: 0 6px 0 #0d8f99, 0 8px 0 rgba(0,0,0,0.4); }
  button.red { background: #ff5d5d; box-shadow: 0 6px 0 #a02929, 0 8px 0 rgba(0,0,0,0.4); }
  button.plain { background: #b9b4ee; box-shadow: 0 6px 0 #6a65a8, 0 8px 0 rgba(0,0,0,0.4); }
  .btn.done { background: var(--lime); box-shadow: 0 6px 0 #2f9a22, 0 8px 0 rgba(0,0,0,0.4); }
  button.cyan:active { box-shadow: 0 1px 0 #0d8f99, 0 3px 0 rgba(0,0,0,0.4); }
  button.red:active { box-shadow: 0 1px 0 #a02929, 0 3px 0 rgba(0,0,0,0.4); }
  button.plain:active { box-shadow: 0 1px 0 #6a65a8, 0 3px 0 rgba(0,0,0,0.4); }
  .btn.done:active { box-shadow: 0 1px 0 #2f9a22, 0 3px 0 rgba(0,0,0,0.4); }

  /* CRT preview */
  .crt {
    background: var(--crt);
    color: var(--lime);
    font-family: var(--font-mono);
    font-size: 17px;
    line-height: 1.5;
    white-space: pre-wrap;
    overflow-wrap: anywhere;
    border: 4px solid #3a3a52;
    border-radius: 14px;
    padding: 16px;
    text-shadow: 0 0 6px rgba(125, 255, 107, 0.55);
    box-shadow: inset 0 0 30px rgba(125, 255, 107, 0.18);
    user-select: all;
  }
  .paper {
    background: #ffffff;
    color: #1a1a1a;
    font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
    font-size: 17px;
    line-height: 1.5;
    border: 4px solid #3a3a52;
    border-radius: 10px;
    padding: 16px;
    overflow-wrap: anywhere;
  }
  .paper a { color: #1a56db; text-decoration: underline; }
  .status { min-height: 26px; color: var(--lime); font-size: 22px; }
  .status.warn { color: var(--yellow); }

  /* Platforms */
  .platform {
    display: grid;
    grid-template-columns: 76px 1fr auto;
    gap: 6px 16px;
    padding: 16px 0;
    border-top: 3px dashed #4b46a8;
    align-items: center;
  }
  .platform:first-of-type { border-top: 0; padding-top: 6px; }
  .tile { width: 76px; height: 76px; border: 4px solid #fff; border-radius: 12px; display: flex; align-items: center; justify-content: center; grid-row: 1 / span 2; box-shadow: 4px 4px 0 rgba(0,0,0,0.45); }
  .tile svg { width: 56px; height: 56px; shape-rendering: crispEdges; image-rendering: pixelated; }
  .pname { font-family: var(--font-pixel); font-size: 12px; line-height: 1.6; display: flex; gap: 10px; align-items: center; flex-wrap: wrap; }
  .badge { font-family: var(--font-pixel); font-size: 9px; padding: 4px 7px; border-radius: 4px; }
  .badge.click { background: var(--lime); color: #0a2a08; }
  .badge.paste { background: var(--orange); color: #2a1100; }
  .note { color: var(--muted); max-width: 52ch; grid-column: 2; }
  .count { font-family: var(--font-mono); font-size: 13px; color: var(--muted); }
  .count.over { color: #ff7a7a; font-weight: 700; }
  .platform .btn { grid-column: 3; grid-row: 1 / span 2; min-width: 150px; }
  @media (max-width: 620px) {
    .platform { grid-template-columns: 64px 1fr; }
    .tile { width: 64px; height: 64px; grid-row: 1; }
    .tile svg { width: 46px; height: 46px; }
    .note { grid-column: 1 / span 2; }
    .platform .btn { grid-column: 1 / span 2; grid-row: auto; width: 100%; }
    h1 { font-size: 19px; }
    .ufo { width: 72px; height: 41px; }
  }
  .foot { color: var(--muted); font-size: 20px; text-align: center; }
  .foot a { color: var(--cyan); }
  .blink { animation: blink 1.1s steps(2, start) infinite; }
  @keyframes blink { to { visibility: hidden; } }
  @media (prefers-reduced-motion: reduce) {
    .ufo, .blink { animation: none; }
  }
</style>
</head>
<body>
<main>
  <header class="top">
    <div class="brand">
      <svg class="ufo" id="ufo" viewBox="0 0 16 9" aria-hidden="true"></svg>
      <div>
        <h1>SHARE<br>STATION</h1>
        <div class="tag">Beam one article to six networks.</div>
      </div>
    </div>
    <div class="hud" aria-live="polite">SCORE <span id="score">000000</span><br>LAUNCHED <span id="launched">0/6</span></div>
  </header>

  <ol class="coins">
    <li><b>1 <span class="blink">INSERT COIN</span></b>On the article, click the Share Prep bookmark, then Copy.</li>
    <li><b>2 LOAD</b>Paste the block below and set your hashtags.</li>
    <li><b>3 LAUNCH</b>Hit each platform button. Green means done.</li>
  </ol>

  <section class="panel cyan stack" aria-labelledby="h-paste">
    <h2 id="h-paste"><span class="stage">STAGE 1</span> LOAD ARTICLE</h2>
    <div>
      <label for="paste">PASTE BOOKMARKLET BLOCK</label>
      <textarea id="paste" rows="7" spellcheck="false" placeholder="URL: ...&#10;TITLE: ...&#10;SOURCE: ...&#10;DATE: ...&#10;SUMMARY: ..."></textarea>
      <p class="hint" id="parse-hint">Fields below fill in as soon as you paste.</p>
    </div>
    <div class="grid2">
      <div>
        <label for="title">TITLE (TITLE CASE)</label>
        <input type="text" id="title">
      </div>
      <div>
        <label for="url">ARTICLE URL</label>
        <input type="text" id="url">
      </div>
      <div>
        <label for="source">SOURCE</label>
        <input type="text" id="source">
      </div>
      <div>
        <label for="date">DATE</label>
        <input type="text" id="date">
      </div>
    </div>
    <div>
      <label for="tags">HASHTAGS</label>
      <input type="text" id="tags">
      <p class="hint" id="tag-hint"></p>
    </div>
    <div class="row">
      <label class="check" for="cite"><input type="checkbox" id="cite"> Add a (Source, Date) line for show notes</label>
    </div>
    <div class="row">
      <button type="button" class="plain" id="fixcase">Redo title case</button>
      <button type="button" class="red" id="clear">New game</button>
    </div>
  </section>

  <section class="panel yellow stack" aria-labelledby="h-post">
    <h2 id="h-post"><span class="stage">STAGE 2</span> CHECK YOUR POST</h2>
    <div class="crt" id="preview" aria-live="polite"></div>
    <div class="row">
      <button type="button" class="cyan" id="copy">Copy post</button>
      <span class="status" id="status" role="status"></span>
    </div>
  </section>

  <section class="panel orange stack" aria-labelledby="h-notes">
    <h2 id="h-notes"><span class="stage">BONUS</span> SHOW NOTES LINK</h2>
    <p class="hint" style="margin:0">Linked title, then (Source; Date). Click Copy with link, then paste into your show notes doc.</p>
    <div class="paper" id="notes-preview" aria-live="polite"></div>
    <div class="row">
      <button type="button" class="cyan" id="copy-rich">Copy with link</button>
      <button type="button" class="plain" id="copy-md">Copy as Markdown</button>
      <span class="status" id="notes-status" role="status"></span>
    </div>
  </section>

  <section class="panel magenta" aria-labelledby="h-plat">
    <h2 id="h-plat"><span class="stage">STAGE 3</span> LAUNCH</h2>
    <div id="platforms"></div>
  </section>

  <p class="foot">Each button opens a new tab and copies your post first. Nothing is stored on this page.<br>Share Station pattern by <a href="https://github.com/wfryer/super-prompts">Wes Fryer</a>, CC BY 4.0.</p>
</main>

<script>
(function () {
  var DEMO = [
    'URL: https://www.example.com/news/2026/11/example-article',
    'TITLE: Example headline about a topic you care about',
    'SOURCE: Example News',
    'DATE: 7 November 2026',
    'SUMMARY: Demo article loaded so the page is not empty. Paste your own block to replace it.'
  ].join('\n');
  var DEMO_TAGS = '#ExampleTag #Education #MediaLiteracy #Journalism #Privacy';

  var PAL = {
    w: '#ffffff', c: '#29f0ff', m: '#ff3fa4', y: '#ffd23f', o: '#ff7a2f', g: '#7dff6b', G: '#1fa84a',
    t: '#b6ff9a', b: '#4d7cff', B: '#2a3fb5', n: '#a0522d', k: '#14123a', s: '#d6d4f0', S: '#8e8cb5'
  };

  var ICONS = {
    ufo: [
      '......cccc......',
      '....cccccccc....',
      '...ccwwcccccc...',
      '..mmmmmmmmmmmm..',
      '.mmymmymmymmymm.',
      'mmmmmmmmmmmmmmmm',
      '.....m....m.....'
    ],
    bluesky: [
      '............',
      '........yy..',
      '..ww...yyyy.',
      '.wwww..yyyy.',
      'wwwwwww.yy..',
      'wwwwwwwwww..',
      'wwwwwwwwwwww',
      '.wwwwwwwwww.',
      '............',
      '..c...c..c..',
      '............',
      '.c...c...c..'
    ],
    threads: [
      '............',
      '..wwwwwwww..',
      '..wwwwwwww..',
      '...yyyyyy...',
      '...yoyoyo...',
      '...yyyyyy...',
      '...oyoyoy...',
      '...yyyyyy...',
      '..wwwwwwww..',
      '..wwwwwwww..',
      '......yy....',
      '.....yy.....'
    ],
    mastodon: [
      '............',
      '..ssssssss..',
      'ssssssssssss',
      'sSSskssksSSs',
      'sSSssssssSSs',
      'sSSssssssSSs',
      '..sssSSsss..',
      '...wsSSsw...',
      '...w.SS.w...',
      '..ww.SS.ww..',
      '......SS....',
      '.....SS.....'
    ],
    linkedin: [
      '............',
      '.cccccc.....',
      '.c....c.....',
      '.c....c.....',
      '.c....c.....',
      '.c...ywyyyy.',
      '.ccccwc...y.',
      '.....y....y.',
      '.....y....y.',
      '.....y....y.',
      '.....yyyyyy.',
      '............'
    ],
    facebook: [
      '............',
      '.wwwww.wwwww',
      '.wBBBw.wBBBw',
      '.wwwww.wwwww',
      '.wBBBw.wBBBw',
      '.wwwww.wwwww',
      '.wBBBw.wBBBw',
      '.wwwww.wwwww',
      '.wBBBw.wBBBw',
      '.wwwww.wwwww',
      'oooooooooooo',
      '............'
    ],
    spoutible: [
      '............',
      '.gg......gg.',
      'gGGg....gGGg',
      'gGGGg..gGGGg',
      '.gGGGggGGGg.',
      '..ggGttGgg..',
      '....gttg....',
      '.....tt.....',
      '.....tt.....',
      '.....tt.....',
      'nnnnnnnnnnnn',
      'nnnnnnnnnnnn'
    ]
  };

  var SMALL = {};
  'a an the and but or nor for so yet as at by in of on to up via per vs from into onto with over than'.split(' ').forEach(function (w) { SMALL[w] = 1; });

  var ABBREV = {
    'the new york times': 'NYTimes', 'new york times': 'NYTimes',
    'the washington post': 'WashPost', 'washington post': 'WashPost',
    'the guardian': 'Guardian', 'the atlantic': 'Atlantic',
    'associated press': 'AP', 'ap news': 'AP', 'bbc news': 'BBC',
    'npr': 'NPR', 'reuters': 'Reuters', 'politico': 'Politico', 'propublica': 'ProPublica'
  };

  function $(id) { return document.getElementById(id); }

  function pixelSvg(svg, rows) {
    var NS = 'http://www.w3.org/2000/svg';
    svg.setAttribute('viewBox', '0 0 ' + rows[0].length + ' ' + rows.length);
    svg.setAttribute('shape-rendering', 'crispEdges');
    rows.forEach(function (row, y) {
      for (var x = 0; x < row.length; x++) {
        var ch = row.charAt(x);
        if (ch !== '.' && PAL[ch]) {
          var r = document.createElementNS(NS, 'rect');
          r.setAttribute('x', x);
          r.setAttribute('y', y);
          r.setAttribute('width', 1.02);
          r.setAttribute('height', 1.02);
          r.setAttribute('fill', PAL[ch]);
          svg.appendChild(r);
        }
      }
    });
  }

  function capFirst(part) {
    return part.replace(/[a-z]/, function (c) { return c.toUpperCase(); });
  }

  function titleCase(s) {
    var tokens = s.trim().split(/\s+/);
    var forceCap = true;
    return tokens.map(function (tok) {
      var out;
      if (/[A-Z]/.test(tok)) {
        out = tok;
      } else if (tok.indexOf('-') > -1) {
        out = tok.split('-').map(capFirst).join('-');
      } else {
        var core = tok.replace(/[^a-z]/g, '');
        out = (!forceCap && SMALL[core]) ? tok : capFirst(tok);
      }
      forceCap = /[:?!]$/.test(tok);
      return out;
    }).join(' ');
  }

  function abbrev(src) {
    var k = src.trim().toLowerCase();
    if (ABBREV[k]) { return ABBREV[k]; }
    return src.trim().replace(/^The\s+/i, '');
  }

  function parseBlock(text) {
    var out = {};
    text.split(/\r?\n/).forEach(function (line) {
      var m = /^(URL|TITLE|SOURCE|DATE|SUMMARY):\s*(.*)$/i.exec(line.trim());
      if (m) { out[m[1].toUpperCase()] = m[2].trim(); }
    });
    return out;
  }

  function buildText() {
    var parts = [$('title').value.trim(), $('url').value.trim()];
    if ($('cite').checked) {
      var d = $('date').value.trim();
      parts.push('(' + abbrev($('source').value) + (d ? ', ' + d : '') + ')');
    }
    var tags = $('tags').value.trim();
    if (tags) { parts.push(tags); }
    return parts.filter(Boolean).join('\n\n');
  }

  function enc(s) { return encodeURIComponent(s); }

  var CONFIG = {
    mastodonServer: 'mastodon.social',   // your Mastodon server domain
    facebookPageUrl: ''                  // for example https://www.facebook.com/yourpage/ , or leave blank
  };

  var PLATFORMS = [
    { name: 'Bluesky', icon: 'bluesky', tile: '#1f5bd8', kind: 'click', limit: 300, label: 'Launch Bluesky',
      note: 'Opens the composer with your post filled in. Click Post.',
      href: function (t) { return 'https://bsky.app/intent/compose?text=' + enc(t); } },
    { name: 'Threads', icon: 'threads', tile: '#4a2390', kind: 'click', limit: 500, label: 'Launch Threads',
      note: 'Opens the composer with your post filled in. Click Post.',
      href: function (t) { return 'https://www.threads.com/intent/post?text=' + enc(t); } },
    { name: 'Mastodon', icon: 'mastodon', tile: '#5b3fd0', kind: 'click', limit: 500, label: 'Launch Mastodon',
      note: 'Opens ' + CONFIG.mastodonServer + ' with the post filled in. Sign in if asked, then click Publish.',
      href: function (t) { return 'https://' + CONFIG.mastodonServer + '/share?text=' + enc(t); } },
    { name: 'LinkedIn', icon: 'linkedin', tile: '#0b4a80', kind: 'paste', limit: 3000, label: 'Launch LinkedIn',
      note: 'The text usually fills in. If the box opens empty, click in it and paste (Ctrl+V or Cmd+V). The post is already copied.',
      href: function (t) { return 'https://www.linkedin.com/feed/?shareActive=true&text=' + enc(t); } },
    { name: 'Facebook', icon: 'facebook', tile: '#8a2447', kind: 'paste', limit: 0, label: 'Launch Facebook',
      note: CONFIG.facebookPageUrl
        ? 'Opens your Facebook Page. If you are not acting as the Page, click your profile picture to switch to it, choose Create post, and paste (Ctrl+V or Cmd+V). The post is already copied.'
        : 'Opens the Facebook share dialog with your link. Choose where to share, paste the copied text into the box, and delete the duplicate link line if a preview already shows.',
      href: function (t, url) { return CONFIG.facebookPageUrl || ('https://www.facebook.com/sharer/sharer.php?u=' + enc(url)); } },
    { name: 'Spoutible', icon: 'spoutible', tile: '#4a3216', kind: 'paste', limit: 0, label: 'Launch Spoutible',
      note: 'Opens Spoutible. Start a new post and paste (Ctrl+V or Cmd+V). The post is already copied.',
      href: function () { return 'https://spoutible.com/'; } }
  ];

  var launched = {};

  function renderScore() {
    var n = Object.keys(launched).length;
    $('score').textContent = ('000000' + (n * 100)).slice(-6);
    $('launched').textContent = n + '/' + PLATFORMS.length + (n === PLATFORMS.length ? ' ALL CLEAR' : '');
  }

  function resetLaunches() {
    launched = {};
    PLATFORMS.forEach(function (p, i) {
      var a = $('link-' + i);
      if (a) {
        a.classList.remove('done');
        a.textContent = p.label;
      }
    });
    renderScore();
  }

  function renderPlatforms() {
    var wrap = $('platforms');
    PLATFORMS.forEach(function (p, i) {
      var row = document.createElement('div');
      row.className = 'platform';

      var tile = document.createElement('div');
      tile.className = 'tile';
      tile.style.background = p.tile;
      var svg = document.createElementNS('http://www.w3.org/2000/svg', 'svg');
      svg.setAttribute('aria-hidden', 'true');
      pixelSvg(svg, ICONS[p.icon]);
      tile.appendChild(svg);

      var name = document.createElement('div');
      name.className = 'pname';
      var nm = document.createElement('span');
      nm.textContent = p.name;
      var badge = document.createElement('span');
      badge.className = 'badge ' + p.kind;
      badge.textContent = p.kind === 'click' ? 'AUTO-FILL' : 'COPY + PASTE';
      var cnt = document.createElement('span');
      cnt.className = 'count';
      cnt.id = 'count-' + i;
      name.appendChild(nm);
      name.appendChild(badge);
      name.appendChild(cnt);

      var note = document.createElement('div');
      note.className = 'note';
      note.textContent = p.note;

      var a = document.createElement('a');
      a.className = 'btn';
      a.id = 'link-' + i;
      a.target = '_blank';
      a.rel = 'noopener noreferrer';
      a.textContent = p.label;
      a.addEventListener('click', function () {
        copyPost();
        launched[i] = true;
        a.classList.add('done');
        a.textContent = 'Launched';
        renderScore();
      });

      row.appendChild(tile);
      row.appendChild(name);
      row.appendChild(note);
      row.appendChild(a);
      wrap.appendChild(row);
    });
  }

  function update() {
    var text = buildText();
    var url = $('url').value.trim();
    $('preview').textContent = text || 'Your post appears here.';
    var len = Array.from(text).length;
    PLATFORMS.forEach(function (p, i) {
      $('link-' + i).href = p.href(text, url);
      var c = $('count-' + i);
      if (p.limit) {
        var over = len - p.limit;
        c.textContent = over > 0 ? len + '/' + p.limit + ' over by ' + over : len + '/' + p.limit;
        c.className = 'count' + (over > 0 ? ' over' : '');
      } else {
        c.textContent = '';
      }
    });
    var tags = $('tags').value.trim().split(/\s+/).filter(function (t) { return /^#\S+/.test(t); });
    var th = $('tag-hint');
    if (tags.length >= 5 && tags.length <= 7) {
      th.textContent = tags.length + ' hashtags. Nice.';
      th.className = 'hint';
    } else {
      th.textContent = tags.length + ' hashtags. Five to seven works best.';
      th.className = 'hint warn';
    }
    renderNotes();
  }

  function esc(s) {
    return s.replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;').replace(/"/g, '&quot;');
  }

  function noteParts() {
    var title = $('title').value.trim();
    var url = $('url').value.trim();
    var date = $('date').value.trim();
    var cite = '(' + abbrev($('source').value) + (date ? '; ' + date : '') + ')';
    var mdTitle = title.replace(/([\[\]])/g, '\\$1');
    var mdUrl = url.replace(/\(/g, '%28').replace(/\)/g, '%29');
    return { title: title, url: url, cite: cite, md: '[' + mdTitle + '](' + mdUrl + ') ' + cite };
  }

  function renderNotes() {
    var p = noteParts();
    var box = $('notes-preview');
    box.textContent = '';
    if (!p.title) {
      box.textContent = 'Your show notes link appears here.';
      return;
    }
    var a = document.createElement('a');
    a.href = p.url;
    a.textContent = p.title;
    a.target = '_blank';
    a.rel = 'noopener noreferrer';
    box.appendChild(a);
    box.appendChild(document.createTextNode(' ' + p.cite));
  }

  function copyNotesRich() {
    var p = noteParts();
    var st = $('notes-status');
    var ok = function () {
      st.textContent = 'Copied with link. Paste into your doc.';
      st.className = 'status';
    };
    var viaSelection = function () {
      var good = false;
      try {
        var r = document.createRange();
        r.selectNodeContents($('notes-preview'));
        var s = window.getSelection();
        s.removeAllRanges();
        s.addRange(r);
        good = document.execCommand('copy');
      } catch (e) {}
      if (good) {
        ok();
      } else {
        st.textContent = 'Copy was blocked. The line above is selected: press Cmd+C or Ctrl+C.';
        st.className = 'status warn';
      }
    };
    try {
      if (navigator.clipboard && window.ClipboardItem && navigator.clipboard.write) {
        var html = '<a href="' + esc(p.url) + '">' + esc(p.title) + '</a> ' + esc(p.cite);
        var item = new ClipboardItem({
          'text/html': new Blob([html], { type: 'text/html' }),
          'text/plain': new Blob([p.md], { type: 'text/plain' })
        });
        navigator.clipboard.write([item]).then(ok, viaSelection);
      } else {
        viaSelection();
      }
    } catch (e) {
      viaSelection();
    }
  }

  function copyNotesMarkdown() {
    var p = noteParts();
    var st = $('notes-status');
    var done = function (good) {
      st.textContent = good ? 'Copied as Markdown.' : 'Copy was blocked. Copy the line above by hand.';
      st.className = 'status' + (good ? '' : ' warn');
    };
    var fallback = function () {
      var good = false;
      try {
        var ta = document.createElement('textarea');
        ta.value = p.md;
        ta.setAttribute('readonly', '');
        ta.style.position = 'fixed';
        ta.style.opacity = '0';
        document.body.appendChild(ta);
        ta.select();
        good = document.execCommand('copy');
        ta.remove();
      } catch (e) {}
      done(good);
    };
    try {
      if (navigator.clipboard && navigator.clipboard.writeText) {
        navigator.clipboard.writeText(p.md).then(function () { done(true); }, fallback);
      } else {
        fallback();
      }
    } catch (e) {
      fallback();
    }
  }

  function copyPost() {
    var text = buildText();
    var st = $('status');
    var done = function (ok) {
      st.textContent = ok ? 'Copied to clipboard.' : 'Copy was blocked. Click the green post text to select it, then copy.';
      st.className = 'status' + (ok ? '' : ' warn');
    };
    var fallback = function () {
      var ok = false;
      try {
        var ta = document.createElement('textarea');
        ta.value = text;
        ta.setAttribute('readonly', '');
        ta.style.position = 'fixed';
        ta.style.opacity = '0';
        document.body.appendChild(ta);
        ta.select();
        ok = document.execCommand('copy');
        ta.remove();
      } catch (e) {}
      done(ok);
    };
    try {
      if (navigator.clipboard && navigator.clipboard.writeText) {
        navigator.clipboard.writeText(text).then(function () { done(true); }, fallback);
      } else {
        fallback();
      }
    } catch (e) {
      fallback();
    }
  }

  var lastUrl = '';
  function applyBlock() {
    var f = parseBlock($('paste').value);
    var found = Object.keys(f).length;
    if (!found) {
      $('parse-hint').textContent = 'No fields found yet. The block should start with URL:, TITLE:, SOURCE:, DATE: and SUMMARY: lines.';
      $('parse-hint').className = 'hint warn';
      update();
      return;
    }
    if (f.URL) {
      $('url').value = f.URL;
      if (f.URL !== lastUrl) { resetLaunches(); }
      lastUrl = f.URL;
    }
    if (f.TITLE) { $('title').value = titleCase(f.TITLE); }
    if (f.SOURCE) { $('source').value = f.SOURCE; }
    if (f.DATE) { $('date').value = f.DATE; }
    var missingDate = /not found/i.test(f.DATE || '');
    $('parse-hint').textContent = missingDate
      ? 'Date not found on that page. Type it in the Date field (for example 6 November 2026).'
      : 'Loaded ' + found + ' fields. Set your hashtags below.';
    $('parse-hint').className = 'hint' + (missingDate ? ' warn' : '');
    update();
  }

  pixelSvg($('ufo'), ICONS.ufo);
  renderPlatforms();
  $('paste').value = DEMO;
  $('tags').value = DEMO_TAGS;
  applyBlock();
  $('parse-hint').textContent = 'Demo article loaded. Paste your own block to replace it.';
  $('parse-hint').className = 'hint';
  renderScore();

  $('paste').addEventListener('input', applyBlock);
  ['title', 'url', 'source', 'date', 'tags'].forEach(function (id) { $(id).addEventListener('input', update); });
  $('cite').addEventListener('change', update);
  $('copy').addEventListener('click', copyPost);
  $('copy-rich').addEventListener('click', copyNotesRich);
  $('copy-md').addEventListener('click', copyNotesMarkdown);
  $('fixcase').addEventListener('click', function () { $('title').value = titleCase($('title').value); update(); });
  $('clear').addEventListener('click', function () {
    ['paste', 'title', 'url', 'source', 'date', 'tags'].forEach(function (id) { $(id).value = ''; });
    $('cite').checked = false;
    $('status').textContent = '';
    $('notes-status').textContent = '';
    $('parse-hint').textContent = 'Fields below fill in as soon as you paste.';
    $('parse-hint').className = 'hint';
    lastUrl = '';
    resetLaunches();
    update();
    $('paste').focus();
  });
})();
</script>
</body>
</html>

```

## STEP 3: CHECK YOUR WORK

If you can run code, test the page before handing it over: paste a sample block into the paste box and confirm the title is title-cased, the preview shows title, URL, and hashtags separated by blank lines, each launch button has the right link, and the character counts appear. If you cannot run code, reread your edits once and confirm nothing outside the allowed changes was touched.

## STEP 4: TELL ME HOW TO USE IT

End with a short, plain list, no more than 8 lines:

- How to install the bookmarklet (new bookmark named Share Prep, paste the javascript: code into the URL field, not the address bar; in Chrome show the bookmarks bar first).
- The three-step flow: click Share Prep on the article, click Copy, paste into Share Station, add 5 to 7 hashtags, click the launch buttons.
- The show notes box: Copy with link gives a hyperlinked headline plus (Source; Date) that pastes into a document with the link kept. Copy as Markdown gives the same line in Markdown.
- Which networks fill in the text automatically (Bluesky, Threads, Mastodon) and which need a paste (LinkedIn may fill in, Facebook and Spoutible need a paste).
- That some sites with strict security settings block all bookmarklets, and that Chrome worked in testing.
<!-- PROMPT END -->

---

## Good to know

- **Browsers.** The bookmarklet worked in Chrome. It did not run in Vivaldi on macOS. Other browsers are untested. The Share Station page itself is plain HTML and works anywhere.
- **What fills in automatically.** Bluesky and Threads publish documented share links, and Mastodon servers use a standard `/share` address (confirm it once on your own server). LinkedIn's text pre-fill is unofficial, so it may open empty. Facebook ignores pre-filled text, and Spoutible has no share link that I could find. Those networks rely on the copy that every button does first.
- **Privacy.** The bookmarklet reads only the page you click it on and sends nothing anywhere. The Share Station page stores nothing. Your posts go straight from your browser to each network.
- **Dates and titles.** If a site does not publish a machine-readable date, the block says DATE NOT FOUND and you type it in. Headlines are title-cased by rule, so check names and acronyms before posting.
- **Icons.** The six pixel icons are original art, not the networks' logos. Swap in official logos from each network's brand page if you prefer them.
- **Hashtag help (optional).** Paste the bookmarklet block into a chat and ask the AI for 5 to 7 hashtags that reflect the article's real content. Add them to the page by hand.
- **Make it a Claude Project (optional).** Save these instructions in a Claude Project, then paste each bookmarklet block into a new chat there. Claude returns the post and hashtags and can update your Share Station artifact so it opens ready to post.

```
Prepare news articles for sharing. The user clicks the Share Prep bookmarklet on an article and pastes the block (URL:, TITLE:, SOURCE:, DATE:, SUMMARY:) here. Never fetch the article.
Format the post as: Title in Title Case, blank line, URL exactly as pasted, blank line, 5 to 7 CamelCase hashtags on one line that reflect the article's actual content. No generic tags.
Reply with the post in one code block. Then find the user's Share Station artifact with list_artifacts, read it, and use edit_version to change only the DEMO lines and the DEMO_TAGS line in the script. Leave all other markup, styles and code untouched.
If DATE says DATE NOT FOUND, ask for the date once.
```

---

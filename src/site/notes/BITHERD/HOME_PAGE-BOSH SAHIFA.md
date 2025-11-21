---
{"dg-publish":true,"permalink":"/bitherd/home-page-bosh-sahifa/","tags":["gardenEntry"],"noteIcon":"","created":"2025-11-20T00:10:09.822+05:00","updated":"2025-11-21T10:54:01.468+05:00"}
---



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



<div class="lang-switcher">
  <a href="?lang=en"   class="{{currentLang === 'en' ? 'active' : ''}}">EN</a>
  <a href="?lang=uz"   class="{{currentLang === 'uz' ? 'active' : ''}}">O‘Z</a>
</div>

<script>
// Persist choice + reload with param
const url = new URL(location);
document.querySelectorAll('.lang-switcher a').forEach(a => {
  a.addEventListener('click', e => {
    e.preventDefault();
    url.searchParams.set('lang', a.textContent.trim().toLowerCase());
    localStorage.setItem('preferredLang', a.textContent.trim().toLowerCase());
    location.href = url;
  });
});

// Auto-detect preferred language on first visit
if (!url.searchParams.has('lang') && localStorage.preferredLang) {
  url.searchParams.set('lang', localStorage.preferredLang);
  location.replace(url);
}
</script>


<script>
document.addEventListener("DOMContentLoaded", function () {
  const supportedLangs = ["en", "es", "zh", "fr", "de"]; // add yours
  const defaultLang = "en";

  // Get lang from URL: ?lang=es
  const urlParams = new URLSearchParams(window.location.search);
  let currentLang = urlParams.get("lang") || defaultLang;
  if (!supportedLangs.includes(currentLang)) currentLang = defaultLang;

  // Function: switch language
  function switchLang(lang) {
    if (lang === defaultLang) {
      history.replaceState(null, "", window.location.pathname);
    } else {
      history.replaceState(null, "", `?lang=${lang}`);
    }
    location.reload(); // reload to load the correct .lang.md file
  }

  // Create language switcher buttons (top-right)
  const switcher = document.createElement("div");
  switcher.style.cssText = `
    position: fixed; top: 15px; right: 20px; z-index: 9999;
    background: var(--background-primary); padding: 8px 12px;
    border-radius: 8px; box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    font-size: 14px; display: flex; gap: 10px;
  `;

  supportedLangs.forEach(l => {
    const btn = document.createElement("button");
    btn.textContent = l.toUpperCase();
    btn.style.cssText = `
      background: ${l === currentLang ? "#0066ff" : "transparent"};
      color: ${l === currentLang ? "white" : "var(--text-normal)"};
      border: 1px solid ${l === currentLang ? "#0066ff" : "#ccc"};
      padding: 4px 10px; border-radius: 6px; cursor: pointer;
    `;
    btn.onclick = () => switchLang(l);
    switcher.appendChild(btn);
  });

  document.body.appendChild(switcher);

  // AUTO-REDIRECT to correct language version
  const currentPath = window.location.pathname;
  const noteName = currentPath.split("/").pop().replace(".html", "");

  if (currentLang !== defaultLang) {
    const langVersion = noteName + "." + currentLang + ".md";
    const defaultVersion = noteName + ".md";

    // Check if the language version exists (via <link> tags in <head>)
    const links = Array.from(document.querySelectorAll("link[rel='alternate']"));
    const hasLangVersion = links.some(link => 
      link.hreflang === currentLang && link.href.includes(encodeURIComponent(langVersion))
    );

    if (!hasLangVersion && noteName !== "index") {
      // Fall back to default language version
      const defaultUrl = currentPath.replace(noteName + ".html", "") + 
        (noteName.endsWith("." + currentLang) ? noteName.replace("." + currentLang, "") : noteName) + ".html";
      window.location.href = defaultUrl;
    }
  }
});
</script>

</div></div>

Bu Bosh sahifa.
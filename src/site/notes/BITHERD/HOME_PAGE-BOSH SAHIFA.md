---
{"dg-publish":true,"permalink":"/bitherd/home-page-bosh-sahifa/","tags":["gardenEntry"],"noteIcon":"","created":"2025-11-20T00:10:09.822+05:00","updated":"2025-11-20T00:34:24.029+05:00"}
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

.

</div></div>


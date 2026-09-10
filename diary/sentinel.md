## 2025-10-14 - Prevent DOM XSS and Secure External Links

**Vulnerability:**
1. Cross-Site Scripting (DOM XSS): Search queries, search history entries, and response items (titles, snippets, links, domains) from Google Custom Search Engine were injected directly into template strings rendered via `innerHTML` without HTML entity encoding.
2. Tabnabbing / Reverse Tabnabbing: External search result links opened with `target="_blank"` without `rel="noopener noreferrer"`.

**Learning:**
Even if search results come from trusted API providers like Google Custom Search, untrusted third-party web content (webpage titles, snippets) can contain HTML or script tags designed to exploit client-side `innerHTML` sinks.

**Prevention:**
1. Added `escapeHtml()` utility to escape special HTML characters (`&`, `<`, `>`, `"`, `'`) before interpolating variables into `innerHTML`.
2. Ensured all external links opening in new tabs specify `rel="noopener noreferrer"`.

Run this in developer tools/console to download chat output as a markdown file:

```
(function() { const CONFIG = {DOC_TITLE:"chat-output", encodeHTMLCHARS: false }; function h(html) { return html.replace(/<p>/g, '\n\n').replace(/<\/p>/g, '').replace(/<b>/g, '**').replace(/<\/b>/g, '**').replace(/<i>/g, '_').replace(/<\/i>/g, '_').replace(/<code[^>]*>/g, (match) => { const lm = match.match(/class="[^"]*language-([^"]*)"/); return lm ? '\n```' + lm[1] + '\n' : '```'; }).replace(/<\/code[^>]*>/g, '```').replace(/<[^>]*>/g, '').replace(/Copy code/g, '').replace(/This content may violate our content policy. If you believe this to be in error, please submit your feedback — your input will aid our research in this area./g, '').trim(); } (()=>{ const e=document.querySelectorAll(".text-base");let t="";for(const s of e)s.querySelector(".whitespace-pre-wrap")&&(t+=`**${s.querySelector('img')?'You':'ChatGPT'}**: ${h(s.querySelector(".whitespace-pre-wrap").innerHTML)}\n\n`);const o=document.createElement("a");o.download=CONFIG.DOC_TITLE+".md",o.href=URL.createObjectURL(new Blob([(CONFIG.encodeHTMLCHARS) ? t : t.replace(/\&gt\;/g, ">").replace(/\&lt\;/g, "<")])),o.style.display="none",document.body.appendChild(o),o.click()})();}())```

3-5-2023
Changed BMS Params
3-6-2023
Ran a test with multiplus (and MPPT) charging to look for proper charge cutoff.
Ran a test with wakespeed charging to look for proper charge cutoff.
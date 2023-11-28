# bikeshed-template

Se skabelonen i anvendelse her: https://digst.github.io/bikeshed-template/

Læs mere: 
- https://tabatkins.github.io/bikeshed/ 
- https://github.com/tabatkins/bikeshed/blob/master/docs/quick-start.md
- https://github.com/tabatkins/bikeshed


## Anvendelse af Bikeshed som skabelon til udstilling af specifikationer

### 1 Opret mappe til bikeshed-udstilling
- Opret /docs mappe i roden af repositoriet
- Placer skabelonfilen [index.md](https://github.com/digst/bikeshed-template/blob/main/docs/index.md) i /docs 
- Opret en tom fil med navnet index.html
- Opret eventuelt filerne index-en.md og index-en.html i /docs hvis engelsk oversættelse ønskes
- Opret eventuelt undermappen /docs/img hvis der skal indgå illustrationer

### 2 Aktivér GitHub Pages
Udstilling via GitHub Pages kan aktiveres via repositoriets 'Settings'
- Gå til repositoriets hovedside
- Vælg Settings (det lille tandhjul)
- Scroll ned til indstillingerne for GitHub Pages
- Aktiver og vælg at opbygge html-visningen fra /root-mappen fra 'main branch'

### 3 Opret indhold i Markdown-format 
- Skriv din tekst i Markdown format i filen index.md 
- (Læs evt. Markdown Guide til GitHub: https://guides.github.com/features/mastering-markdown/.)
- Rediger dokumentets metadata i 'boilerplaten' - se eksempel herunder:
```
<pre class="metadata">
Title: Prefix 1.0.0: Titel
Status: LD
URL: https://github.com/digst/bikeshed-template/tree/main/
Editor Term: Udgiver, Udgivere 
Editor: Digitaliseringsstyrelsen,, arkitektur@digst.dk
Abstract: 'Titel' .
Boilerplate: copyright no, conformance no, abstract no
Shortname: Kort titel
Revision: 1.0.0 
Date: 2021-01-01
Max ToC Depth: 3
Markup Shorthands: markdown yes
Repository: digst/bikeshed-template
Translation: en https://digst.github.io/bikeshed-template/index-en.html
Inline Github Issues: full
Logo: digst...
</pre>
```



NB: Word (docx) filer kan også konverteres til Markdown via fx: https://euangoddard.github.io/clipboard2markdown/

### 4 Konvertér indhold i Markdown til HTML 
Konvertering af Markdown-indhold til HTML kan fx ske via Bikeshed's webformular.
  
- Kopier index.md-teksten fra GitHub ind i Bikeshed's webformular: https://api.csswg.org/bikeshed/
- Vælg Output = Generated HTML og vælg Force HTML. og klik 'Proces'
- Hvis alt ser ok ud (selvom billederne vil mangle), så ’Vis kilde’ og kopier HTML-outputtet
- Åbn index.html-filen på GitHub og indsæt HTML-outputtet og gem
- Vent 3-5 minutter på at GitHub pages genererer visningen: 

### 5 Tilføj tabindex i HTML-filen (WCAG) 
Indsæt følgende script nederst i body i index.html filen, for at tilføje tabindex i indholdsfortegnelse og rette sprogangivelsen til dansk (da) i visniningen

```javascript
<script>
    /*Set attribute tabindex on all elements in TOC*/
    var toc =  document.querySelectorAll("#toc .content");
    for (var i = 0; i < toc.length; i++) {
      if (!toc[i].hasAttribute("tabindex")){
        var att = document.createAttribute("tabindex");
        att.value = "0";
        toc[i].setAttributeNode(att);
      }
    }
    /*Set lang attribute value to "da" in html tag*/
    document.getElementsByTagName("html")[0].setAttribute("lang", "da");
</script>
```
### 6 Ret engelske meta-labels til dansk.
'Table of contents' til 'Indholdsfortegnelse', og 'This version' til 'Denne version'. 'Translation' til 'Oversættelse'

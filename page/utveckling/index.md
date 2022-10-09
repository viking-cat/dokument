---
layout: page
title: "Utveckling"
---

{% capture capture_links %}
# Tools
* **Windows**
  * [Power Toys](https://docs.microsoft.com/en-us/windows/powertoys/)

# Markdown
* [Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)
* [Mediawiki Cheat Sheet](https://www.mediawiki.org/wiki/Cheatsheet)

# Webutveckling
* [CSS Reference](https://www.w3schools.com/cssref/default.asp)
* [SASS](https://sass-lang.com/)
  * [Documentation](https://sass-lang.com/documentation/)

## JavaScript Frameworks
* [React](https://reactjs.org/)
* [Vue](https://vuejs.org/)

## Static Site Generators
* [NextJs](https://nextjs.org/)
* [NuxtJs](https://nuxtjs.org/)
* [Jekyll](https://jekyllrb.com/)(***GitHub Pages***)
{% endcapture %}
{% include page-columns.html cols=2 content=capture_links %}

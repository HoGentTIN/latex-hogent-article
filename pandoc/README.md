# Pandoc support

In deze directory vind je een proof-of-concept voor een template waarmee je via Pandoc een Markdown-document naar PDF kan omzetten met `hogent-article.cls` als documentclass.

Om dit te laten werken is het het handigst als je de sjabloonbestanden installeert. Dat kan via de Makefile in deze repo met het commando `make install`. Als `make` niet beschikbaar is op je systeem:

- Kopieer `hogent-article.latex` naar directory `~/.local/share/pandoc/templates/` (wellicht moet je deze directory ook aanmaken)
- Bepaal wat de `texmf` directory is voor je gebruiker met `kpsewhich -var-value TEXMFHOME`. Meestal is dat `~/texmf`
- Maak daaronder een subdirectory `tex/latex/hogent-article/`
- Kopieer `hogent-article.cls` en het logo in `img/` naar deze directory (dus normaal: `~/texmf/tex/latex/hogent-article/`)
- Probeer dan het voorbeeld-markdownbestand om te zetten naar PDF met het commando:

    ```console
    pandoc --pdf-engine xelatex --from markdown --template hogent-article -o pandoc/voorbeeld-pandoc.pdf pandoc/voorbeeld-pandoc.md
    ```

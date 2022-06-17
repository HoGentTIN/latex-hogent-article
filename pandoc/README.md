# Pandoc support

In deze directory vind je een proof-of-concept voor een template waarmee je via Pandoc een Markdown-document naar PDF kan omzetten met `hogent-article.cls` als documentclass.

Om dit te laten werken moet je:

- `hogent-article.latex` kopiëren naar directory `~/.local/share/pandoc/templates/` (wellicht moet je deze directory ook aanmaken)
- naar de directory gaan waar `hogent-article.cls` zich bevindt
- het voorbeeld-markdownbestand omzetten naar PDF met het commando:

    ```console
    pandoc -o pandoc/voorbeeld-pandoc.pdf --pdf-engine xelatex --from markdown --template hogent-article pandoc/voorbeeld-pandoc.md
    ```

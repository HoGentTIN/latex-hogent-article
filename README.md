# LaTeX-sjabloon voor een artikel

In deze repository vind je een sjabloon voor een artikel of ander kort document dat de huisstijlregels van [HOGENT](https://www.hogent.be) tracht te volgen. Dit sjabloon is niet officieel in die zin dat het niet werd gecreëerd of erkend door de dienst communicatie, maar is wel ontworpen met de bedoeling dat het gebruikt wordt in de opleiding toegepaste informatica.

Het sjabloon is geïnspireerd door:

- Pieter Van der Kloet's [thesis-sjabloon](https://github.com/pvdk/hogent-latex-thesis) (wordt nu [hier verder onderhouden](https://github.com/HoGentTIN/hogent-latex-thesis))
- [Het artikelsjabloon](https://www.overleaf.com/latex/templates/publications-of-the-astronomical-society-of-australia/nbjxzvhrrgbx) van de Astronomical Society of Australia

## Aan de slag

Om dit sjabloon te kunnen gebruiken, heb je het volgende nodig:

- De [gebruikte TrueType lettertypes](https://github.com/HoGentTIN/presentatie-latex-sjabloon/tree/master/fonts) (je kan deze downloaden en installeren via de link):
    - Montserrat (hoofdlettertype)
    - Fira Code (monogespatieerde tekst)
    - Fira Math (wiskundige formules)
- XeLaTeX als compiler (o.a. voor Unicode-ondersteuning)
- Biber voor het beheer van de bibliografie (o.a. voor Unicode-ondersteuning en de APA referentiestijl)

Om zelf een document aan te maken, gebaseerd op deze stijl, heb je volgende bestanden nodig:

- `hogent-article.cls` (documentclass-definitie)
- `img/HOGENT_Logo_Pos_rgb.png` (logo)
- Je kan starten met een van de voorbeeld .tex-bestanden en die aanpassen naar je voorkeur.

## HOGENT huisstijl

De [HOGENT huisstijl](https://hnet.hogent.be/themas/communicatie/huisstijl-logo-s-en-sjablonen/) kenmerkt zich o.a. door:

- Het [Montserrat](https://github.com/JulietaUla/Montserrat/) lettertype
- Specifiek kleurenpallet (zie overzicht hieronder)
- Bronvermeldingen volgens de APA6-stijl

| Kleurnaam                                                   | RGB         |
| :---------------------------------------------------------- | :---------- |
| <div style='color:rgb(22,176,165)'>hogent-darkgreen</div>   | 22,176,165  |
| <div style='color:rgb(241,157,160)'>hogent-pink</div>       | 241,157,160 |
| <div style='color:rgb(250,188,50)'>hogent-ochre</div>       | 250,188,50  |
| <div style='color:rgb(239,135,103)'>hogent-orange</div>     | 239,135,103 |
| <div style='color:rgb(187,144,189)'>hogent-purple</div>     | 187,144,189 |
| <div style='color:rgb(76,162,213)'>hogent-blue</div>        | 76,162,213  |
| <div style='color:rgb(165,202,114)'>hogent-lightgreen</div> | 165,202,114 |
| <div style='color:rgb(216,176,131)'>hogent-brown</div>      | 216,176,131 |
| <div style='color:rgb(195,187,175)'>hogent-grey</div>       | 195,187,175 |
| <div style='color:rgb(244,222,0)'>hogent-yellow</div>       | 244,222,0   |

## Documentclass-opties

Het sjabloon is gebaseerd op het standaard LaTeX `article`-sjabloon, met opties `a4paper`, `10pt` en `twocolumn`.

Het sjabloon heeft momenteel volgende documentclass-opties:

| Optie     | Effect                         |
| :-------- | :----------------------------- |
| `dutch`   | Document in het Nederlands(\*) |
| `english` | Document in het Engels         |

(*) Het is niet verplicht dit op te geven. Als er geen taal is meegegeven als documentclass-optie, wordt Nederlands verondersteld.

## Commando's voor document-metadata

In het sjabloon worden een aantal commando's ge(her)definieerd voor het specifiëren van metadata die op een specifieke manier opgemaakt wordt in de PDF. Je gebruikt al deze commando's in de preamble. De meeste zijn optioneel, tenzij anders aangegeven.

- `\academicyear`: het academiejaar waarin het document geschreven is of van toepassing op is. Indien niet opgegeven wordt `\today` gebruikt.
- `\assignmenttype`: het soort opdracht waarvoor het document geschreven wordt, bv.
    - Onderzoeksvoorstel
    - Paper
- `\author` (verplicht): geef de naam van een auteur. Indien er meerdere auteurs zijn, geef je deze met aparte `\author`-commando's op.
- `\course`: de cursus waarbinnen dit document geschreven wordt, bv.
    - Research Methods
    - Bachelorproef
- `\email`: e-mailadres van de auteur(s). Je geeft best voor elke auteur een email-adres op, telkens met een apart `\email`-commando.
    - Wanneer je geen email-adressen opgeeft, zal er een waarschuwing verschijnen bij compileren.
- `\keywords`: enkele sleutelwoorden die het onderwerp van het document beschrijven.
- `\projectrepo`: URL van de Github-repository waar projectcode wordt bijgehouden
- `\specialization`: Specialisatierichting waarbinnen de opdracht of de inhoud van het document zich situeert. In toegepaste informatica zijn dat bv.:
    - Mobile \& Enterprise development
    - AI \& Data Engineering
    - Functional \& Business Analysis
    - System \& Network Administrator
    - Mainframe Expert
- `\studyprogramme`: de opleiding waarbinnen dit document zich situeert, bv.
    - Professionele bachelor toegepaste informatica
    - Postgraduaat it-management
- `\supervisor`: de lector die de opdracht begeleidt.
    - Je kan dit commando max. 1 gebruiken, dus als er meerdere begeleiders zijn moet je die allemaal samen opgeven.
    - Als de begeleider een andere rol heeft die je wil beschrijven, dan kan dat met een optioneel argument, bv.
        - `\supervisor[Co-promotor]{S. Beekman}` of `\supervisor[Lectoren]{S. Beekman, T. De Smet}`

## Andere

- Als je bij het begin van het document een samenvatting opgeeft met de `abstract` environment, dan is het niet nodig om nog apart `\maketitle` te gebruiken.
    - De titel van het document wordt gegenereerd samen met de abstract.
    - Als je geen abstract opgeeft, dan worden `\keyword`s en `\specialization` niet getoond.
- Je kan de kleur van de titels of hyperlinks wijzigen door deze in de preamble te definiëren, vb:
    - `\colorlet{title}{hogent-darkgreen}`
    - `\colorlet{links}{hogent-grey}`
- In dit sjabloon wordt de APA-stijl gebruikt via de `biblatex` package. Gebruik dus `biber` voor het compileren van de bibliografie en volgende commando's om te verwijzen naar bronnen:
    - `\textcite{AuthorYear}` voor een referentie van de vorm "Auteur (jaar)"
    - `\autocite{AuthorYear}` voor een referentie van de vorm "(Auteur, jaar)"

## Vragen, problemen, verbeteringen

Heb je vragen of problemen bij het gebruik van dit sjabloon, of heb je ideeën voor verbetering? Laat het weten via de Issues.

Concrete voorstellen tot verbetering zijn ook ten zeerste welkom en die kan je via een Pull Request indienen.

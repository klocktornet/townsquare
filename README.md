# Blood on the Clocktower – Grimoire & torg

> :warning: **Det här projektet underhålls inte längre aktivt** och får bara kritiska buggfixar. :warning:

![social](https://user-images.githubusercontent.com/325521/102897760-d1147b00-4468-11eb-9d7b-63a204bc9fc1.png)

Det här är ett inofficiellt webbverktyg för att spela Blood on the Clocktower via Discord eller på andra digitala sätt.
Det ska hjälpa berättare och spelare att snabbt sätta upp spel, hålla omröstningar och mycket mer.

[Du kan testa det på nätet!](https://clocktower.online)

Vill du lära dig mer om hur du använder appen som spelare har [JayBotC](https://www.youtube.com/channel/UCNZy-4Rp877XtTHaIZdWYFQ) vänligen gjort två instruktionsvideor (på engelska).

### Så är du värd för ett spel
[![Så är du värd för ett spel](https://img.youtube.com/vi/lVRJPBXfqxg/0.jpg)](https://www.youtube.com/watch?v=lVRJPBXfqxg)

### Så spelar du ett spel
[![Så spelar du ett spel](https://img.youtube.com/vi/VCpFnJFiCbk/0.jpg)](https://www.youtube.com/watch?v=VCpFnJFiCbk)

## Funktioner

- Offentligt torg och Berättarens grimoire (växla med **kortkommandot \[G\]**)
- Stöd för JSON-filer med egna skript som skapats med [skriptverktyget](https://bloodontheclocktower.com/script)
- Livesession för Berättare/spelare med omröstning i realtid och utdelning av karaktärer!
- Innehåller alla 3 grundutgåvor, Resenärer och Sagofigurer plus alla karaktärer som hittills avslöjats officiellt!
- Nattordningsblad och påminnelsetext för varje karaktärs förmåga som hjälp för berättare
- Fullt stöd för egna karaktärer, så att du kan vara värd för och spela spel med dina egna karaktärsuppsättningar
- Många andra anpassningsmöjligheter!

### Stöd för egna skript

Alla egna skript som skapats med det officiella [skriptverktyget](https://script.bloodontheclocktower.com/) stöds direkt,
och du behöver bara ladda upp skriptet för att få in de valda karaktärerna i din grimoire. Vill du anpassa ditt skript
ytterligare kan du lägga till ett extra `"_meta"`-objekt i skriptet, på samma sätt som du lägger till en vanlig karaktär:

```json
[
  {
    "id": "_meta",
    "name": "Deadly Penance Day",
    "author": "TPI",
    "logo": "https://url.to/your/logo.png"
  }
]
```

Det ger din lokala grimoire (och grimoiren hos spelarna i din livesession) mer information att visa om ditt egna skript.
Till exempel visas "Deadly Penance Day" i stället för "Eget skript" på karaktärsreferensen. Logotypen visas för dina
spelare när de har aktiverat anpassade bilder i Grimoire-menyn.

### Stöd för egna karaktärer

För att lägga till egna karaktärer i din lokala grimoire behöver du skapa en JSON-definition för dem, liknande den som
finns i [`roles.json`](https://github.com/bra1n/townsquare/blob/main/src/roles.json) för de 3 grundutgåvorna. Här är ett
exempel på hur en sådan definitionsfil kan se ut:

```json
[
  {
    "id": "acrobat",
    "image": "https://github.com/bra1n/townsquare/blob/main/src/assets/icons/acrobat.png?raw=true",
    "edition": "custom",
    "firstNight": 0,
    "firstNightReminder": "",
    "otherNight": 49,
    "otherNightReminder": "Om en god levande granne är berusad eller förgiftad dör Akrobaten.",
    "reminders": ["Död"],
    "remindersGlobal": [],
    "setup": false,
    "name": "Akrobat",
    "team": "outsider",
    "ability": "Varje natt*, om någon av dina goda levande grannar är berusad eller förgiftad dör du."
  },
  { 
    "id": "investigator" 
  },
  { 
    "id": "imp" 
  }
]
```

Den här JSON-definitionen innehåller en egen karaktär, Akrobaten, och 2 karaktärer från grundspelet, Utredaren och Impen.
För karaktärer från grundspelet räcker det att ange ID:t, på samma sätt som du får från skriptverktyget.

**Obligatoriska egenskaper:** `id`, `name`, `team`, `ability`

- **id**: karaktärens interna ID, utan mellanslag eller specialtecken<br>
  _Obs_: ID:t måste vara unikt och får inte vara samma som ett ID som redan används av en befintlig karaktär, annars skrivs den egna karaktären över av den befintliga rollen!
- **image**: en URL till en PNG-bild med ikonen för karaktärsmarkören (bör ha genomskinlig bakgrund!)<br>
  _Obs_: anpassade bilder syns först efter att du har aktiverat dem i Grimoire-menyn!
- **edition**: ID:t för karaktärens utgåva. Kan lämnas tomt eller sättas till "custom"
- **firstNight** / **otherNight**: i vilken ordning karaktären agerar den första natten / övriga nätter, jämfört med alla
  andra karaktärer<br>
  _Obs_: måste vara ett positivt tal eller noll, där noll betyder "agerar inte under natten"
- **firstNightReminder** / **otherNightReminder**: påminnelsetext för första natten / övriga nätter
- **reminders**: påminnelsemarkörer, ska vara en tom lista `[]` om det inte finns några
- **remindersGlobal**: globala påminnelsemarkörer som alltid är tillgängliga, oavsett om karaktären är tilldelad en spelare eller inte
- **setup**: om markören påverkar spelets uppsättning (orange löv), som Fyllot eller Baronen
- **name**: karaktärens namn som visas
- **team**: karaktärens lag, måste vara något av `townsfolk` (Stadsbo), `outsider` (Utböling), `minion` (Undersåte), `demon` (Demon), `traveler` (Resenär) eller `fabled` (Sagofigur)<br>
  _Obs_: om du skapar en egen Sagofigur läggs den automatiskt till i spelet när det egna skriptet laddas
- **ability**: karaktärens förmågetext som visas

## [Uppförandekod](CODE_OF_CONDUCT.md)

## [Bidra till projektet](CONTRIBUTING.md)

## Tack och upphovsrätt

* [Blood on the Clocktower](https://bloodontheclocktower.com/) är ett varumärke som tillhör Steven Medway och [The Pandemonium Institute](https://www.thepandemoniuminstitute.com/)
* Nattpåminnelser och annan kompletterande text skrevs ursprungligen på engelska av [Ben Finney](http://bignose.whitetree.org/projects/botc/diy/)
* Ikoner från [Font Awesome](https://fontawesome.com/)
* Upphovsrätt och tillstånd för bakgrundsbilden har getts av [Ryan Maloney](https://www.artstation.com/maloney94)
* Webbtypsnitt från [Google Fonts](https://fonts.google.com/) och [Online Web Fonts](https://www.onlinewebfonts.com/)
* Alla andra bilder och ikoner tillhör sina respektive upphovsrättsinnehavare

Det här projektet och dess webbplats tillhandahålls kostnadsfritt och är inte på något sätt knutna till The Pandemonium Institute.

## Donationer
Det här projektet kommer alltid att vara gratis, eftersom jag älskar att bygga häftiga saker och spela Blood on the Clocktower. Om du ändå vill stödja mig med en donation kan du göra det här:

[![Donera](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.me/bra1n)

# Handleiding verlof-, overuren- en medewerkerportaal

Deze handleiding beschrijft de samenwerking tussen twee onderdelen:

- het **leidinggevende dashboard** voor beheer, registratie en centrale opslag;
- het **medewerkersdashboard** voor saldo-inzage en het maken van aanvraagmails.

Het leidinggevende dashboard blijft altijd de centrale waarheid. Het medewerkersdashboard kan geen centrale data aanpassen.

## 1. Wat doet welk dashboard?

### Leidinggevende dashboard

Gebruik dit dashboard voor:

- medewerkers aanmaken en beheren;
- verlof, overuren en ziekte registreren;
- aanvragen beoordelen en verwerken;
- saldi berekenen;
- centrale JSON openen en opslaan;
- saldobestanden exporteren voor het medewerkersdashboard.

De centrale JSON bevat de volledige administratie. Sla die op een afgeschermde plek op, bijvoorbeeld OneDrive of SharePoint.

### Medewerkersdashboard

Gebruik dit dashboard voor medewerkers, zodat zij:

- met hun persoonlijke code hun actuele verlof- en overurensaldo kunnen bekijken;
- een aanvraagmail kunnen maken voor verlof;
- een aanvraagmail kunnen maken om overuren op te nemen;
- een melding kunnen maken voor gewerkte overuren.

Het medewerkersdashboard slaat niets op. Het opent alleen een mailconcept. De medewerker moet die mail zelf controleren en verzenden.

## 2. Een medewerker aanmaken

1. Open het leidinggevende dashboard.
2. Ga naar **Start & opslag**.
3. Open het centrale JSON-bestand.
4. Ga naar **Medewerkers**.
5. Vul de medewerkergegevens in:
   - naam;
   - e-mailadres;
   - functie/team;
   - startsaldo verlofuren;
   - startsaldo overuren;
   - status.
6. Vul bij **Persoonlijke portaalcode** een code in of klik op **Genereer code**.
7. Klik op **Medewerker opslaan**.
8. Sla daarna op naar het centrale JSON-bestand.

De portaalcode moet uniek zijn. Voorbeelden:

```text
JAN7392
PET1846
TEST001
```

De medewerker gebruikt deze code om in het medewerkersdashboard zijn of haar saldo te bekijken.

## 3. Saldobestanden maken voor het medewerkersdashboard

1. Open het leidinggevende dashboard.
2. Open het centrale JSON-bestand.
3. Ga naar **Medewerkerportaal export**.
4. Vul **E-mailadres leidinggevende voor aanvragen** in.
5. Controleer de previewtabel.
6. Let op waarschuwingen:
   - geen e-mail;
   - geen portaalcode;
   - dubbele portaalcode.
7. Kies een exportmethode:
   - **Download alle saldibestanden als ZIP**, of
   - **Kies map en sla losse saldibestanden op**.

Als je een lokale OneDrive- of SharePoint-map kiest, schrijft het dashboard de bestanden lokaal weg. OneDrive/SharePoint synchroniseert ze daarna zelf naar de cloud.

Aanbevolen mapstructuur:

```text
medewerkerportaal/
  index.html
  saldi/
    saldo-JAN7392.json
    saldo-PET1846.json
```

De medewerkerbestanden zijn alleen kijkkopieën. Ze bevatten alleen:

- code;
- naam;
- e-mailadres;
- e-mailadres van de leidinggevende;
- verlofsaldo;
- overurensaldo;
- laatst bijgewerkt.

Ze bevatten geen ziektehistorie, auditlog, volledige verlofhistorie of interne opmerkingen.

## 4. Medewerker gebruikt het medewerkersdashboard

1. De medewerker opent het medewerkersdashboard.
2. De medewerker vult de persoonlijke code in.
3. Het dashboard zoekt automatisch naar:

```text
saldi/saldo-CODE.json
```

Voorbeeld:

```text
saldi/saldo-JAN7392.json
```

4. Als de code klopt, ziet de medewerker:
   - verlofsaldo;
   - overurensaldo;
   - wanneer het saldo voor het laatst is bijgewerkt.

Als de code niet wordt gevonden, krijgt de medewerker een foutmelding. Controleer dan:

- of de code goed is gespeld;
- of de code hoofdletters gebruikt;
- of het juiste saldobestand in de map `saldi/` staat;
- of er opnieuw is geëxporteerd vanuit het leidinggevende dashboard.

## 5. Medewerker doet een aanvraag

In het medewerkersdashboard kiest de medewerker één van deze aanvraagtypes:

- **Verlof aanvragen**
- **Overuren opnemen**
- **Overuren gewerkt melden**

Daarna vult de medewerker de gevraagde gegevens in en klikt op:

```text
Open mail om aanvraag te verzenden
```

Het dashboard opent dan een mailconcept.

De mail gaat naar het e-mailadres dat in het saldobestand staat als `leidinggevendeEmail`. De medewerker zelf staat in de cc.

Belangrijk: de aanvraag is pas echt ingediend als de medewerker in het mailprogramma zelf op **Verzenden** klikt.

## 6. Hoe komt de aanvraag binnen bij de leidinggevende?

De aanvraag komt binnen als gewone e-mail bij de leidinggevende.

Er is dus geen automatische koppeling waarbij de aanvraag direct in het leidinggevende dashboard verschijnt. Dit is bewust zo gehouden:

- geen backend;
- geen centrale data-aanpassing door medewerkers;
- geen extra accounts of database;
- de leidinggevende blijft controle houden.

De mail bevat de gegevens die nodig zijn om de aanvraag handmatig te verwerken, zoals:

- naam medewerker;
- persoonlijke code;
- type aanvraag;
- datum of periode;
- aantal uren;
- opmerking of toelichting.

## 7. Aanvraag verwerken in het leidinggevende dashboard

1. Open het leidinggevende dashboard.
2. Open het centrale JSON-bestand.
3. Zoek de medewerker op basis van naam en eventueel portaalcode.
4. Ga naar **Nieuwe registratie**.
5. Kies het juiste type:
   - bij verlof: **Verlof aanvraag** of direct **Verlof goedgekeurd**;
   - bij overuren opnemen: **Overuren opgenomen**;
   - bij gewerkte overuren: **Overuren opgebouwd**.
6. Vul datum, uren, status, categorie en eventuele zakelijke opmerking in.
7. Klik op **Registratie opslaan**.
8. Controleer waarschuwingen, bijvoorbeeld negatief saldo.
9. Sla op naar het centrale JSON-bestand.

Als je eerst een aanvraag wilt vastleggen en later beoordelen:

1. Kies **Verlof aanvraag**.
2. Status blijft **Aangevraagd**.
3. De aanvraag verschijnt daarna bij open acties en in het aanvragenoverzicht.
4. Gebruik **Akkoord** of **Afwijzen** om de aanvraag te verwerken.

Bij akkoord wordt de aanvraag omgezet naar **Verlof goedgekeurd**. Het verlofsaldo wordt daarna automatisch bijgewerkt via de bestaande saldoberekening.

## 8. Nieuwe saldi terugzetten naar het medewerkersdashboard

Na het verwerken van aanvragen:

1. Sla het centrale JSON-bestand op.
2. Ga naar **Medewerkerportaal export**.
3. Maak opnieuw saldobestanden.
4. Zet de nieuwe bestanden in de map `saldi/` van het medewerkersdashboard.

Pas daarna ziet de medewerker het bijgewerkte saldo.

## 9. Belangrijke veiligheidsafspraken

- Zet echte `saldo-*.json` bestanden niet in een publieke GitHub-repo.
- Gebruik publieke GitHub Pages alleen met testdata of zonder echte saldobestanden.
- Plaats echte saldobestanden op een afgeschermde plek, bijvoorbeeld OneDrive of SharePoint.
- Bewaar geen medische details bij ziekte.
- Gebruik het medewerkersdashboard alleen voor saldo-inzage en aanvraagmails.
- De centrale JSON van het leidinggevende dashboard blijft leidend.

## 10. Korte controlelijst

Voor live gebruik:

- Staat het leidinggevende dashboard online?
- Staat het medewerkersdashboard online of op een afgeschermde plek?
- Heeft iedere actieve medewerker een unieke portaalcode?
- Heeft iedere actieve medewerker een e-mailadres?
- Is het e-mailadres van de leidinggevende ingevuld in de exporttab?
- Staan de saldobestanden in `medewerkerportaal/saldi/`?
- Is getest met een testcode, bijvoorbeeld `TEST001`?
- Wordt een aanvraagmail goed geopend?
- Kan de leidinggevende de mail handmatig verwerken in het dashboard?

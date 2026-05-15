# Verlof, overuren en ziekte dashboard

Dit is een single-file HTML-dashboard voor verlof, overuren en ziekte. Het leidinggevende-dashboard blijft de centrale waarheid: de grote centrale JSON bevat de volledige administratie en wordt beheerd door de leidinggevende.

Zie [HANDLEIDING.md](HANDLEIDING.md) voor de volledige werkinstructie voor leidinggevenden en medewerkers.

## Medewerkerportaal-export

De tab **Medewerkerportaal export** maakt per actieve medewerker een klein saldo-JSON-bestand voor het aparte medewerkersdashboard. Deze bestanden zijn alleen kijkkopieën. Het medewerkersdashboard mag de centrale data niet aanpassen.

Per medewerker wordt alleen minimale saldo-informatie geëxporteerd:

- persoonlijke portaalcode
- naam
- e-mailadres
- e-mailadres van de leidinggevende voor aanvragen
- verlofsaldo
- overurensaldo
- moment van bijwerken

Er worden geen ziektegegevens, auditlog, volledige verlofhistorie, interne opmerkingen, BSN of andere gevoelige gegevens in deze medewerkerbestanden gezet.

## Werkwijze

1. Open het centrale JSON-bestand in het leidinggevende-dashboard.
2. Controleer bij **Medewerkers** dat iedere actieve medewerker een unieke persoonlijke portaalcode heeft.
3. Vul in **Medewerkerportaal export** het e-mailadres van de leidinggevende voor aanvragen in.
4. Download **alle saldibestanden als ZIP**.
5. Of kies **Kies map en sla losse saldibestanden op** en selecteer lokaal je gesynchroniseerde OneDrive-/SharePoint-map.
6. Plaats de map `saldi/` naast het aparte medewerkersdashboard.
7. Download eventueel de medewerker-links CSV om codes en voorbeeldlinks te delen of te controleren.

Als je een lokale OneDrive-map kiest, schrijft het dashboard de bestanden lokaal weg. OneDrive synchroniseert ze daarna zelf naar de cloud.

Aanbevolen mapstructuur:

```text
medewerkerportaal/
  index.html
  saldi/
    saldo-JAN7392.json
    saldo-PET1846.json
```

Een medewerkerbestand heet altijd:

```text
saldo-[CODE].json
```

Voorbeeld:

```text
saldo-JAN7392.json
```

## Veiligheid

Zet echte saldo-JSON-bestanden niet in een publieke GitHub-repo. Plaats ze alleen op een afgeschermde locatie, bijvoorbeeld SharePoint/OneDrive, of gebruik uitsluitend testdata in publieke omgevingen.

De centrale JSON blijft leidend. Als saldi wijzigen, maak je opnieuw een export vanuit het leidinggevende-dashboard.

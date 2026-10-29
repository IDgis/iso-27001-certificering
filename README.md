# ISMS – ISO 27001

Dit GitHub-project wordt gebruikt voor het plannen, uitvoeren en bewaken van werkzaamheden rondom het Information Security Management System (ISMS).

## Doel van het projectbord

Het projectbord biedt inzicht in:
- Periodieke ISMS-activiteiten
- Uit te voeren beveiligingsmaatregelen
- Controles en beoordelingen
- Verbeteracties

## Issues
### Typen issues

**Review**: 
Beoordelen of beleid, registraties, risico's of doelstellingen nog actueel, passend en effectief zijn. Waar nodig worden deze geactualiseerd.

**Controle**: 
Toetsen of de praktijk voldoet aan vastgestelde eisen, afspraken en beveiligingsmaatregelen.

**Uitvoering**: 
Uitvoeren van reguliere operationele werkzaamheden en bestaande beveiligingsmaatregelen.

**Verbetering**: 
Oplossen van tekortkomingen of structureel verbeteren van processen en maatregelen.

### Naamgeving en inhoud issues

Issues krijgen de volgende structuur: `<Type>: <Onderwerp>`  
In de body wordt opgenomen:
- het nummer van de voorgaande issue
- de datum waarop het voorgaande issue is gesloten
- de herhaaltermijn (in dagen) die voor dit onderwerp geldt
- de link van het bijbehorende document in Google drive

### Uitgangspunten

- Het primaire doel bepaalt het type issue.
- Een review kan ook actualisatie omvatten.
- Een controle kan leiden tot een verbeterissue.
- Werkzaamheden worden niet onnodig opgesplitst.
- Afgeronde issues bevatten waar relevant
  een verwijzing naar het resultaat of bewijs.

## GitHub action
### Werking
Deze GitHub Action controleert maandelijks of periodieke ISMS-werkzaamheden opnieuw uitgevoerd moeten worden. Daarvoor worden de openstaande issues met de status **Backlog** in project **ISO-27001-certificering_2027**.
Per issue wordt op basis van de body twee waarden uitgelezen:
- vorige afsluitdatum
- herhaaltermijn

Wanneer de revisiedatum (vorige afsluitdatum + herhaaltermijn) is bereikt of verstreken, wordt automatisch:
1. het label `revisie-verlopen`
2. de issue status gewijzigd naar `ready to start`
3. een reactie geplaatst waarin `@AnkeVanBeek-IDgis` wordt geïnformeerd

**Bijzonderheden**  
- issues zonder geldige afsluitdatum of herhaaltermijn worden overgeslagen
- issues waarvan de revisiedatum nog niet is bereikt, blijven ongewijzigd
- alleen de eerste 100 issues worden opgehaald
- voor toegang tot het project wordt het secret PROJECT_TOKEN gebruikt.

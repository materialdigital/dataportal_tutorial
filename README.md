# Entwurf des Schulungsmaterial (MaterialDigital DataPortal tutorial V0.1) - Stand - 21.02.2025

## [MaterialDigital DataPortal](https://kit-pmd-4.ydns.eu/) - dev Version

[TOC]

Prio 1: Schulungmaterial für die aktuelle Version des Datenportals erstellen.
Prio 2: Verbesserungvorschläge für die Benutzerfreundlichkeit aufschreiben. Anpssung **nur** nach Freigabe vom LK und Allokation von zusätzlichen Kapa.

## Task force
- Michael Luke
- Marian Bruns - kennt sich im GitHub aus. - Data Upload?
- Marina
- Katharina
- Juliane
- Alex

## Sprache
- Englisch 

## Tasks
- Struktur schreiben
- Aufgaben verteilen.



## Structure
- About Text
- Übersicht - Link zum DataPortal - without log in
    - Übersicht der Metriken
    - Liste von häufigsten Schlagwörter
    - Suchzeile
    - Log In Option
    - Sprachauswahl - unten! - nur von Interface, Texte sind in der Sprache, in der sie angelegt wurden, entsprechend muss die Suche gemacht werden, Suchsprache muss/sollte Englisch sein 
- Search page
    - Filter option on the left sidebar
- Found data set
    - Description links
        - Titel
        - Followers - Nur für eingelogte User
        - Organisation
        - Social?
            - Statt Twitter und Facebook sollte die Organisations-Webseite versinkt sein.
        - License
    - Tabs
        - Dataset
        - Group
    - Dataset tab
        - Titel
        - Describtion
        - Data
            - Titel
            - Description
            - Explore Knopf
                - Drop-down-Pfeil
                    - Preview
                    - Download (each file can be previewed without download)
        - Liste der Keywords
        - Additional Info
            - description (done by uploader)
            - organization 
            - what is **License not specified** saying - (Logischer Bruch zwischen Organization und Licence)
- Logged in Users
    - Anmeldung auf der PMD-Webseite
- Landing im DataPortal
    - + Link with User Name
        - Dashboard
        - Profile setting
        - log out
- User Dashboard
    - My Datasets
    - My Organizations
    - My Group
    - Profile settings
- Profile settings
    - Datasets
    - Organizations
    - Groups
    - Api token - **Marian**
- Roles
    - User
        - **TBD!!!!!**  
    - Admin
        - Best practice: 
            - Auf der Seite der Organisations sollte 
            - ein kurze Beschreibung und Link der Organisations-Webpage und
            - Kontakt zum Admin der Organisation, wenn man um Mitgliedschaft anfragt.
        - Wie verwalten man die Organisationsgruppe? **TBD!!!!!**
- Data upload
    - **TBD!!!!!**


## About Text
"About" DataPortal

Willkommen beim MaterialDigital DataPortal – Ihrer zentralen Anlaufstelle für das Hochladen, Verwalten und Teilen von Material-Datensätzen! 

In einer Welt, in der FAIRE Daten eine immer wichtigere Rolle spielen, bieten wir Ihnen ein benutzerfreundliches 'Portal' an, über das Sie Ihre Daten sicher und effizient teilen und organisieren können. Das Team der Plattform MaterialDigital arbeitet seit 2019 gemeinsam mit der MaterialDigital Community an der Entwicklung von De-facto Standards. Diese können im Bereich der semantischen Interoperabilität, der Workflows und der IT-Architektur und Infrastruktur in der Materialwissenschaft und Werkzeugtechnik domänenübergreifend verwendet werden. 

Wir wissen, dass der Umgang mit und das Teilen von (großen) Datenmengen herausfordernd sein kann. Deshalb bieten Ihnen wir Ihnen unser DataPortal an: Dies baut auf der intuitiven Oberfläche von CKAN auf. Es ermöglicht Ihnen, Ihre Datensätze mit Leichtigkeit hochzuladen, zu kategorisieren und zu verwalten. Egal, ob Sie ein*e Forscher*in, ein Unternehmen oder ein*e Datenenthusiast*in sind – unsere Plattform ist darauf ausgelegt, Ihre Bedürfnisse zu erfüllen und geteilte Datensätze zu finden und zu nutzen.

Unsere Funktionen umfassen:

- Einfache Datenverwaltung: Laden Sie Ihre Datensätze in verschiedenen Formaten hoch und verwalten Sie sie an einem Ort.

- Sichere Speicherung: Ihre Daten sind bei uns sicher. Wir setzen auf modernste Sicherheitsstandards, um Ihre Informationen zu schützen.

- Flexibles Teilen: Teilen Sie Ihre Datensätze mit Kolleg*innen oder der Öffentlichkeit, ganz nach Ihren Bedürfnissen.

- Analytische Tools: Nutzen Sie unsere integrierten Tools, um Ihre Daten zu analysieren und wertvolle Erkenntnisse zu gewinnen.

Wir in der Initiative MaterialDigital glauben an die Power von FAIRen Daten und gemeinsamen Strukturen und Herangehensweisen.

Treten Sie unserer Community bei und erleben Sie, wie einfach und effektiv Datenmanagement sein kann!

Ihr PMD Team 

Kontaktieren Sie uns hier für mehr Informationen, Support und Austausch.


## User Stories

US1:
```{theorem, label, name="US1"}
As a visiting user, I want to explore the data by searching and filtering the available data by keywords, categorys, compartibility and content.
```
- Initial: Which practical question needs to be answered. 
- Landing Page des DataPortals
    - Discovery by search request in the "search"-field 
        - what can you search for?
        - Benutzung des Anführungszeichen.
    - Discovery by keywords anklicken
    - Discovery by organization, resource, datasets
    - Log in
- Search page - functions on the page
    - Filter option on the left sidebar
- Access to content
    - click on dataset - what can be found: 
- Follow function only for logged-in users available



US2:
```{theorem, label, name="US2"}
As a visiting user, I found some interisting datasets and i want to digest/consume them, for further analysis.
```
- Landing Page des DataPortals
    - Discovery bei Keywords anklicken

US3:
```{theorem, label, name="US3"}
As a registered user, I want to add data to the central data portal and  point out the project, publisher that owns the data, to make my data findable and excessable by the public.
```
- Registration at "material-digital.de"
- Landing Page des DataPortals
- Getting access to Organisation
    - Admin User Story
    - Member User Story
- Uploading Files
- Access Management
    - privat/public
    - for Organisation / for Project
- Linking/citing the data
- User Profile  
    - how to reach own User Profile
    - what can be seen and what can be managed there
- membership to organizations
    - can only be part of your organization, can't request to be member of other organizations due to privacy issues

## Fragen zum Test
- Follow-Funktion
    - Was gibt sie?
    - Wie kann man das Follow löschen?
    - Wird man informiert, wenn ein User, den man verfolgt, einen Datensatz veröffentlicht?
    - Kann man nicht einsehen, wen man folgt!
    - man kann nicht sehen, von wem man gefolgt wird - nur Anzahl
- Man kommt schwer auf die User-Übersicht
    - Kann man in der oberen Menü einen "User"-Knopf machen?
- Statt "profile settings" - "view profile"
- Best practice: was sollte im About test der Organization stehen
    - Vorgaben machen was mindestens gefüllt sein muss
    - Ansprechpartner/Kontakt angeben (für Membership request)
    - Link zur Homepage






# CKAN Website Usage Tutorial    - **Text der vo KI erstellt wurde** - Promp von Thomas

Dieses Tutorial zeigt Ihnen, wie Sie die CKAN-Website nutzen können, um Daten zu finden, zu verwalten und zu teilen.

## Voraussetzungen

- Ein Konto auf der CKAN-Website
- Grundlegende Kenntnisse im Umgang mit Webbrowsern

## Schritt 1: Anmeldung

1. Öffnen Sie die CKAN-Website in Ihrem Webbrowser.
2. Klicken Sie auf "Anmelden" und geben Sie Ihre Anmeldedaten ein.
3. Nach der Anmeldung sehen Sie das Haupt-Dashboard.

## Schritt 2: Daten durchsuchen

1. Klicken Sie auf "Datasets", um eine Liste aller verfügbaren Datensätze anzuzeigen.
2. Verwenden Sie die Suchleiste, um nach bestimmten Datensätzen zu suchen.
3. Filter-Optionen stehen zur Verfügung, um die Ergebnisse weiter einzugrenzen.

## Schritt 3: Daten anzeigen

1. Klicken Sie auf einen Datensatznamen, um die Detailseite zu öffnen.
2. Hier finden Sie Informationen über den Datensatz, wie z.B. Beschreibung, Lizenz und Ressourcen.
3. Um eine Ressource herunterzuladen, klicken Sie auf den entsprechenden Link unter “Ressourcen”.

## Schritt 4: Eigene Daten hochladen

1. Gehen Sie zum Dashboard und klicken Sie auf "Create Dataset".
2. Füllen Sie das Formular mit den notwendigen Informationen aus, wie Titel, Beschreibung und Tags.
3. Fügen Sie Ressourcen hinzu, indem Sie Dateien hochladen oder Links zu externen Datenquellen angeben.
4. Klicken Sie auf "Save", um den Datensatz zu erstellen.

## Schritt 5: Daten teilen

1. Um einen Datensatz zu teilen, öffnen Sie die Detailseite des Datensatzes.
2. Klicken Sie auf "Share" und kopieren Sie den bereitgestellten Link.
3. Teilen Sie den Link mit Ihren Kollegen oder in sozialen Netzwerken.

## Hilfe und Support

Wenn Sie Fragen oder Probleme haben, besuchen Sie das [Support-Forum](https://example.com/support) oder kontaktieren Sie den Support unter support@example.com.

---

Ersetzen Sie die Platzhalter-Links und Texte durch die spezifischen Informationen Ihrer CKAN-Instanz.

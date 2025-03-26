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

## Offene Aufgaben


---

## [Thomas' Hackmd](https://hackmd.io/QLGn03gMQvWIC-j37skbug?edit)


# PMD DATA PORTAL

A central data portal for the platform material digital (PMD).

[TOC]

## Product Overview

A central data portal for the platform material digital (PMD) that enables users to explore the digital contents created by the PMD comunitinty.


## User Stories

List out the user stories for the software product. Each user story should follow the format:

```{theorem, label, name="user story template"}
As a [user type], I want [goal], so that [reason].
```

US1:
```{theorem, label, name="US1"}
As a visiting user, I want to explore the data by searching and filtering the available data by keywords, categorys, compartibility and content.
```

US2:
```{theorem, label, name="US2"}
As a visiting user, I found some interisting datasets and i want to digest/consume them, for further analysis.
```

US3:
```{theorem, label, name="US3"}
As a registered user, I want to add data to the central data portal and  point out the project, publisher that owns the data, to make my data findable and excessable by the public.
```


US4:  
```{theorem, label, name="US4"}  
As a scientist of a participant project, I want to upload and publish datasets from my research in our own CKAN platform with proper metadata, so that my data can be found and  discovered by other researchers.  
```

US5:  
```{theorem, label, name="US5"}  
As a scientist, I want to view detailed metadata about datasets, including their provenance, version history, and contributors, so that I can assess the reliability and relevance of the data for my analysis.  
```

US5:  
```{theorem, label, name="US4"}  
As a scientist, I want to receive proper attribution and credit when my datasets are used or cited in other research projects, so that my contributions are recognized in the scientific community.  
```

US6:  
```{theorem, label, name="US5"}  
As a scientist, I want to ensure my project’s datasets are automatically harvested and included in the central federated DCAT catalog, so that they are visible to a broader audience and promote collaboration across projects.  
```

US7:
```{theorem, label, name="US1"}
As a participating project , I want to integrate my projects data into the data portal to increase its findablility.
```

## State of Technical Solution

### CKAN Instance with multiple plugins - minimum

Plugins:
```bash
CKAN__PLUGINS="image_view text_view datatables_view pdf_view webpage_view datastore dcat structured_data harvest ckan_harvester"
CKANINI__CKAN__VIEWS__DEFAULT_VIEWS="image_view text_view datatables_view pdf_view webpage_view"
```
A posibel complex stack example https://github.com/Mat-O-Lab/DataStack/tree/develop

for env. parsing mechanismen to ckan.ini can be achieved with puting this [script](https://github.com/Mat-O-Lab/DataStack/blob/develop/config/ckan/02_envvars.sh) to **/docker-entrypoint.d/** of the container

harvester config needs this [script](https://github.com/Mat-O-Lab/DataStack/blob/develop/config/ckan/03_harvest.sh) also in **/docker-entrypoint.d/**

for the background jobs to run (harvester etc.) a supervisor worker bust be available, see https://github.com/Mat-O-Lab/DataStack/blob/develop/config/ckan/supervisor-ckan-worker.conf. Put the script to **/etc/supervisord.d/**



### SSO integration with central PMD keycloak .env

SAML Variant
```
CKAN__PLUGINS="image_view text_view datatables_view pdf_view webpage_view datastore dcat structured_data harvest ckan_harvester saml2auth"
#SAML
CKANINI__CKANEXT__SAML2AUTH__IDP_METADATA__LOCATION=remote
CKANINI__CKANEXT__SAML2AUTH__IDP_METADATA__REMOTE_URL=https://<sso_host>/auth/realms/<realm_name>/protocol/saml/descriptor
#CKANINI__CKANEXT__SAML2AUTH__ENABLE_CKAN_INTERNAL_LOGIN=False
CKANINI__CKANEXT__SAML2AUTH__ENABLE_CKAN_INTERNAL_LOGIN=True
CKANINI__CKANEXT__SAML2AUTH__USER_FIRSTNAME=urn:oid:2.5.4.42
CKANINI__CKANEXT__SAML2AUTH__USER_LASTNAME=urn:oid:2.5.4.4
CKANINI__CKANEXT__SAML2AUTH__USER_EMAIL=urn:oid:1.2.840.113549.1.9.1
CKANINI__CKANEXT__SAML2AUTH__ENTITY_ID=ckan
CKANINI__CKANEXT__SAML2AUTH__SYSADMINS_LIST=<admin@pmd.de>
```
Dockerfile
```dockerfile=
FROM ckan/ckan-dev:2.10.3

ENV APP_DIR=/srv/app
ENV TZ=UTC
RUN echo ${TZ} > /etc/timezone

RUN apk add xmlsec

# Make sure both files are not exactly the same
RUN if ! [ /usr/share/zoneinfo/${TZ} -ef /etc/localtime ]; then \
    cp /usr/share/zoneinfo/${TZ} /etc/localtime ;\
    fi ;

# Install any extensions needed by your CKAN instance
# - Make sure to add the plugins to CKAN__PLUGINS in the .env file
# - Also make sure all provide all extra configuration options, either by:
#   * Adding them to the .env file (check the ckanext-envvars syntax for env vars), or
#   * Adding extra configuration scripts to /docker-entrypoint.d folder) to update
#      the CKAN config file (ckan.ini) with the `ckan config-tool` command
#
# See README > Extending the base images for more details

# For instance:

### HARVEST
RUN pip3 install -e git+https://github.com/ckan/ckanext-harvest.git#egg=ckanext-harvest && \
    pip3 install -r https://raw.githubusercontent.com/ckan/ckanext-harvest/master/requirements.txt

# ### DCATDE-AP
# RUN pip3 install -e git+https://github.com/GovDataOfficial/ckanext-dcatde.git#egg=ckanext-dcatde && \
#     pip3 install -r https://raw.githubusercontent.com/GovDataOfficial/ckanext-dcatde/master/base-requirements.txt

#Should be installed by the previous
### DCAT
RUN pip3 install -e git+https://github.com/ckan/ckanext-dcat.git#egg=ckanext-dcat  && \
    pip3 install -r https://raw.githubusercontent.com/ckan/ckanext-dcat/master/requirements.txt

### PDFView
RUN pip3 install ckanext-pdfview

### Saml2auth
RUN pip3 install ckanext-saml2auth


# Clone the extension(s) your are writing for your own project in the `src` folder
# to get them mounted in this image at runtime

# Apply any patches needed to CKAN core or any of the built extensions (not the
# runtime mounted ones)
# Copy custom initialization scripts
COPY docker-entrypoint.d/* /docker-entrypoint.d/

# Apply any patches needed to CKAN core or any of the built extensions (not the
# runtime mounted ones)
COPY patches ${APP_DIR}/patches

RUN for d in $APP_DIR/patches/*; do \
    if [ -d $d ]; then \
    for f in `ls $d/*.patch | sort -g`; do \
    cd $SRC_DIR/`basename "$d"` && echo "$0: Applying patch $f to $SRC_DIR/`basename $d`"; patch -p1 < "$f" ; \
    done ; \
    fi ; \
    done
```



## Feature Brainstorming

Collaboratively brainstorm potential features and improvements for the software product. Use the following format:

### Feature Name and Product Backlog Item

**Description:** A brief description of the feature.

**User Story:** The user story or stories that this feature relates to.

**Acceptance Criteria:** The criteria that must be met in order for the feature to be considered complete.

**Dependencies:** Any dependencies that must be resolved before this feature can be implemented.

**Risks:** Any potential risks associated with implementing this feature.
Product Backlog
List out the product backlog items for the software product. Each product backlog item should be a specific feature or improvement that needs to be implemented. Use the following format:


## [Entwurf des Schulungsmaterial](https://github.com/materialdigital/dataportal_tutorial)

Prio 1: Schulungmaterial für die aktuelle Version des Datenportals erstellen.
Prio 2: Verbessetungvorschläge für die Benutzerfreundlichkeit aufschreiben. Anpssung **nur** nach Freigabe vom LK und Allokation von zusätzlichen Kapa.

---

## Verschiedenes
### Liste aus dem README
Ganz unten im README aren nochfolegende Punkte, die ich hier ablege zu sicherungszwecken:

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

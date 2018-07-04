# Technische Specificaties

*Deze bijlage geeft een overzicht van de technische specificaties en reikt tools aan om het product snel en kwalitatief te realiseren. In de titels wordt aangegeven welk onderdeel verplicht (**V**) of optioneel (**O**) is.*


Bij hyperlinks wordt aangegeven of de info:
1. publiek beschikbaar is: [**publiek**]
2. beschikbaar is via een actief medewerkersaccount: [**MW**]
3. beschikbaar is op het intranet via VPN: [**VPN**]

[Voor info types 2 en 3 kan u terecht bij de contactpersoon van Digipolis (zie offertevraag)]

[1. Architectuur](#1.-Architectuur) 

[2. Technologieën](#2.​-Technologieën) 

[3. Ontwikkeltools](#3.-Ontwikkeltools) 

[4. Testing](#4. Testing) 

[5. Architectuur](#5.-Technische-documentatie-(**V**)) 


***

## 1. Architectuur

### 1.1. Algemeen
We verwachten dat de ontwikkelingen rekening houden met het maximaal gebruik van bestaande herbruikbare componenten zoals onze ACPaaS engines en ACPaaS front-end libraries waaronder de stijlbibliotheken. 

Nieuwe componenten en services dienen zo generiek mogelijk te worden ontwikkeld volgens **Microservice Architectuur** zodat ze herbruikbaar en vervangbaar zijn.

Een algemene presentatie met deze architectuurprincipes: https://goo.gl/izTzSH [**publiek**]. 

###1.2. AcPaaS (**V**)

####1.2.1. Algemeen (V)
*Een overkoepelend beleid op het vlak van informatie en ICT gaat de verkokering en versnippering tegen. Binnen dit beleidskader werd een gelaagd model uitgewerkt waarbij hergebruik van een aantal bouwblokken, waaronder de ACPaaS engines en Centrale Referentie Systemen (CRS), verplicht is.*

Deze staan klaar om de totaaloplossing op te bouwen waarbij Digipolis de technische ondersteuning kan geven.

Meer algemene informatie over ACPaaS is terug te vinden op https://goo.gl/naOX9j [**publiek**].

Een overzicht van alle AcPaaS engines en detailinfo is hier terug te vinden: https://goo.gl/zrhqh3 [**publiek**].

We zoomen hieronder in op enkele engines:

####1.2.2. API/SDK engine (**V**)
Alle data en functionaliteiten van de oplossing zijn aanspreekbaar en integreerbaar via API’s. Op die manier wordt de innovatieve front-end volledig afgescheiden van de back-end services. De oplossing hergebruikt maximaal de ACPaaS engines en koppelt met de Centrale Referentie Systemen (CRS) als databronnen. **Alle communicatie tussen engines gebeurt steeds via de API/SDK engine.** Elke API wordt aangeboden via de API/SDK engine en dient daartoe in het **Swagger v2** formaat gedefinieerd te worden. 

####1.2.3. A-Profiel en M-Profiel ()
voor gebruikerstoegang en voor het ophalen en opslaan van gebruikersattributen dient het A-profiel (burgers) en M-profiel (medewerkers) te worden hergebruikt. De documentatie voor integratie van de A-profiel en M-profiel login met consent via **oAuth2** is hier terug te vinden: https://goo.gl/7wqo13 [publiek]. Daarnaast is voor het **M**-profiel authenticatie mogelijk via **SAML2** (conform de specificaties).

###1.3. Microservice Architectuur (**V**)
####1.3.1. Algemeen
Nieuwe functionaliteit wordt steeds gebouwd conform de microservice architectuur principes. Bestaande functionaliteit dient bij aanpassingen of refactor in lijn gebracht te worden met deze principes.

Elke microservice:

- is business centered (wordt gemaakt voor 1 proces of functionaliteit)
- encapsuleert de functionaliteit + de data
- is geïsoleerd
- eigen database  (geen sharing van databases)
- onafhankelijk implementeerbaar
- onafhankelijk deploybaar
- is eenvoudig vervangbaar
- wordt aangesproken via duidelijk gedefinieerde API’s
- wordt aangeboden via de API/SDK engine

####1.3.2. Versioning (**V**)
Volgens de semantic versioning principes (http://semver.org/ [**publiek**]). 
####1.3.3. API Requirements (**V**)
api design-requirements: https://github.com/digipolisantwerpdocumentation/api-requirements[**publiek**]
####1.3.4. API monitoring (**V**)
Status call te voorzien voor elke API, zodat deze kan opgenomen worden de status monitor (https://status-o.antwerpen.be/ [**VPN**]).
####1.3.5. Logging (**V**)
Logging is verplicht te voorzien voor alle cron jobs en voor privacy gevoelige info.
Hiervoor dient de AcPaaS logging engine gebruikt te worden:

- https://applicationlogging-app1-a.antwerpen.be/ [**VPN**]
- https://systeemlogging-app1-a.antwerpen.be/ [**VPN**]
- https://privacylogging-app1-a.antwerpen.be/ [**VPN**]
- https://logging-o.antwerpen.be/ [**VPN**]

## 2.​ Technologieën
### 2.1. Algemeen: DaaS
Qua technologiekeuzes heeft Digipolis een agile technologische biotoop: Digipolis Antwerpen Application Stack, of kortweg DAAS. Het staat de partner steeds vrij om onze technologische keuzes te challengen, zo lang ze maar voldoen aan de DAAS criteria en we samen een oplossing kunnen vinden voor het onderhoud van de oplossing. Meer info vind je hier: https://goo.gl/HNm92Q [**publiek**].

###2.2. Frontend
#### 2.2.1. Stijlgids (**V**)

Het design dient conform de huisstijlrichtlijnen van de stad Antwerpen te worden uitgevoerd. UX moet beantwoorden aan de bestaande UX-richtlijnen. 

Om toegang te krijgen tot het platform Merk en huisstijl van de groep stad antwerpen surf je naar: http://antwerpen.be/huisstijl/login [**publiek**]. Volg de procedure achter de knop 'meld u aan'. Let wel, je hebt een A-profiel nodig, waar wij de rechten tot toegang aan toe kunnen kennen. Geef het primaire e-mailadres in dat gekoppeld is aan het A-profiel waarmee je toegang wenst tot onze huisstijlrichtlijnen. Heb je nog geen A-profiel, surf dan naar https://www.antwerpen.be/nl/login [**publiek**] en klik op 'registreer uw A-profiel'. Alvast bedankt om deze aanmeldprocedure te volgen.

De digitale huisstijl staat niet los van de overige huisstijlregels. Alle huisstijlrichtlijnen blijven honderd procent van tel, met uitzondering van de richtlijnen rond het 'grid voor print'. Hebt u nog niet gewerkt met onze huisstijlrichtlijnen, vraag dan een korte toelichting aan via huisstijl@stad.antwerpen.be. 

#### 2.2.2. Sass-kit (**V**)
Je gebruikt de recentste versie van de A-kit (core branding). Om een idee te krijgen van onze digitale componenten kan u de codevoorbeelden raadplegen via: https://a-ui.github.io/core_branding_scss/ [**publiek**]. De principes van atomic design worden gevolgd. Let wel dat deze componenten niet kunnen toegepast worden zonder de bredere context van de huisstijl te kennen.

Alle broncode van de digitale componenten is tevens terug te vinden op GitHub: https://github.com/a-ui/core_branding_scss [**publiek**]. Hier kunnen ontwikkelaars de broncode bekijken, zelf verbeteringen voorstellen of eventuele bugs inseinen.

#### 2.2.3. Guidelines (**V**)
Alle frontend programmatie dient te gebeuren conform de guidelines: 
https://acpaas-ui.digipolis.be/docs/guidelines [**MW**].

Het gebruik van **ESLint** is verplicht, de parameters worden door Digipolis voorzien.

#### 2.2.4. Angular component bibliotheek (**V**)
Er is een gebruiksklare bibliotheek beschikbaar met de meestgebruikte UI componenten in de laatste stabiele Angular versie. Alle componenten worden gepubliceerd op https://nexusrepo.antwerpen.be [**VPN**] en zijn voorzien van de nodige documentatie in de code repositories op Bitbucket: https://bitbucket.antwerpen.be/projects/AUI [**VPN**]. Daarnaast zijn er examples beschikbaar van de componenten: https://bitbucket.antwerpen.be/projects/AUI/repos/examples/browse [**VPN**]. Wil je meer weten over het gebruik van deze componentenbibliotheek, bezoek dan de ACPaaS UI website [**publiek**].

Verdere specifieke componenten en service libraries moeten door de partner voorzien worden en toegevoegd aan de ACPaaS front-end bibliotheek conform de technische guidelines:

- De componenten worden app-onafhankelijk gemaakt zodat ze herbruikbaar zijn in andere projecten/apps.
- Release management: de componenten worden geversioneerd via **semantic versioning**.
- De bibliotheek wordt beheerd via een specifiek Bitbucket project, waarbinnen elke component en service library een aparte repository vormt.
- Alle componenten worden gepubliceerd via **Nexus**.
- De code wordt via peer reviews van de front-end ontwikkelaars en/of technische architecten gevalideerd.

Belangrijk: *het staat de partner vrij om een oplossing in een ander front-end framework voor te stellen. De partner is dan wel verplicht om de benodigde front-end componenten op een kwaliteitsvolle manier toe te voegen in de front-end bibliotheek (cfr. technische guidelines zoals hierboven beschreven). Op deze manier zijn deze componenten herbruikbaar voor toekomstige oplossingen. In de onderhandelingen wordt samen bekeken of dit een realistische piste is.*

### 2.3. Backend
####2.3.1. Algemeen
Binnen DaaS (cfr. 2.1) is voor backend ontwikkeling van nieuwe apps gekozen voor volgende technologieën:

- NodeJS
- .Net Core

####2.3.2. NodeJS (**V**)

NodeJS apps worden geschreven in het express JS framework.

Er bestaat een node generator die kan gebruikt worden om de backend api op te zetten: https://stash.antwerpen.be/projects/NPM/repos/astad_generator_nodejs/browse [**MW**]

Packages worden gepubliceerd op: https://npm.antwerpen.be/ [**VPN**] => **OPGELET**! de meeste packages zijn gebouwd voor *AStad-specifieke* apps.

Volgende npm-packages kunnen in principe gebruikt worden los van de single page application: 

AStad: Astad-solr, Astad-log, Astad-config (verplicht als je andere packages gebruikt die hierop een dependency leggen), Astad-mail, Astad-proxy, Astad-dgp-correlation, Astad-order, Astad-ticket, Astad-cart, Astad-crypto.

*Npm-package eslint moet verplicht in de devDependencies staan.*

####2.3.3. .Net Core (**V**)

Voor .net Core zijn er generators voor front- en backend beschikbaar op github.

- Backend (api):
 	- https://github.com/digipolisantwerp/generator-dgp-api-aspnetcore_yeoman [**publiek**]
- Frontend:
	- https://github.com/digipolisantwerp/generator-dgp-web-aspnetcore_yeoman [**publiek**]
- Packages worden gepubliceerd op: 
	- https://www.myget.org/F/digipolisantwerp/api/v3/index.json [**publiek**]

De database wordt benaderd via Entity Framework adhv de dataaccess-toolbox: https://github.com/digipolisantwerp/dataaccess_aspnetcore [**publiek**]

Van de database migrations worden scripts gegenereerd die tijdens deployment automatisch worden uitgevoerd.

Andere toolboxen zijn vrij te gebruiken: https://github.com/digipolisantwerp [**publiek**]

Gebruik van de logging-toolboxen is **verplicht**: https://github.com/digipolisantwerp/serilog_aspnetcore [**publiek**]

### 2.4. Databases (**V**)
**PostgreSQL** of **MongoDb** voor nieuwe apps.

Bestaande apps zijn ontwikkeld in MongoDb, SQL server en PostgreSQL.

Voor zoekopdrachten: search engine (**Apache Solr**), die via de API’s wordt aangesproken om content toe voegen, content te verwijderen en om zoekopdrachten te lanceren.

## 3. Ontwikkeltools
### 3.1. Application Lifecycle Management
#### 3.1.1 Jira (**V**)
Nieuwe functionaliteiten worden in de vorm van epics en stories ingebracht in Jira. Hier gebeurt ook de bugtracking en projectopvolging. Gebruik van de Jira Workflow binnen Digipolis is verplicht.
#### 3.1.2 Bitbucket (**V**)
Zowel de front- als backend code van iedere applicatie zit in een eigen Git Repository die beheerd wordt binnen BitBucket. Codewijzigingen worden via pull requests gereviseerd door 2 ontwikkelaars. Er worden zowel voor front- als backend 3 ontwikkelaars doorgegeven die als approver kunnen geselecteerd worden.

Er moet dagelijks gecommit worden, vermijden om branches langer dan een paar dagen open te laten staan.
#### 3.1.3 Bamboo (**V**)
Meer info over de opzet: https://bitbucket.antwerpen.be/projects/PLAT/repos/documentation/browse/Bamboo.md [**MW**]
### 3.2. Vagrant (**O**)
voor lokale development: https://bitbucket.antwerpen.be/projects/ASTAD/repos/vagrant_chef_ruby/browse [**MW**]
### 3.3. Docker (**O**)
Beschikbaar voor local development. Er is een traject bezig om Docker op te nemen in de Application Lifecycle Management tools.
### 3.4. App Config (**O**)
Optioneel voor nieuwe apps: https://appconfig.antwerpen.be/ [**VPN**]
## 4. Testing
### 4.1. Unit & integratietesten (**V**)
Testcoverage: minimum **80%** voor line, branch, statements en functions, automatisch na build.
### 4.2. Automatische UI testen (O)
Testscenario’s worden beschreven via de **Zephyr** module in Jira. Automatische regressietesten kunnen ontwikkeld worden via **Ranorex**.
## 5. Technische documentatie (**V**)
API / applicatie documentatie beschikbaar stellen in **readme.md**, **swagger.json**, **changelog.md** formaat, verwijzing naar kibana monitor opnemen.
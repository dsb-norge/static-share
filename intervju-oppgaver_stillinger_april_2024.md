# Oppgaver andregangsintervju stilling i IKT-seksjonen

Dette er oppgaver til kandidater som innkalles til andregangsintervju for stilling i DSB IKT-seksjon, våren 2024.

<!-- omit in toc -->
## Innholdsfortegnelse

<!-- vscode-markdown-toc -->
- [Innledning](#innledning)
- [Oppgavene](#oppgavene)
  - [1. IKT som leverandør av Azure landing zones for resten av bedriften](#1-ikt-som-leverandør-av-azure-landing-zones-for-resten-av-bedriften)
  - [2. Alternativ hosting av egenutviklede applikasjoner i Azure](#2-alternativ-hosting-av-egenutviklede-applikasjoner-i-azure)
  - [3. Terraform - For hele bedriften](#3-terraform---for-hele-bedriften)
  - [4. Security posture i Azure](#4-security-posture-i-azure)
  - [5. Nettverksrelatert oppgave](#5-nettverksrelatert-oppgave)
<!-- /vscode-markdown-toc -->

## Innledning

Under finner du 5 oppgaver innenfor tre forskjellige tema. Oppgavene er nummerert fra 1 til 5 og du velger _èn_ av oppgavene.

Det finnes ikke noe "rett" svar på disse oppgavene, de er ment for refleksjon og diskusjon under intervjuet.

Besvarelseform velger du selv. Eksempler kan være kan være ren tekst i markdown, punktliste i word eller arkitekturdiagram som png. Her står du fritt til å velge. Vi ønsker _ikke_ at du skal skrive kode.

Står du fast eller blir usikker fordi du mangler informasjon eller innsikt i det som er DSB-spesifikt? Da er det helt greit å gjøre antagelser og beskrive disse, eller du beskriver noen forutsetninger for besvarelsen din.

## Oppgavene

### 1. IKT som leverandør av Azure landing zones for resten av bedriften

Gitt et team på rundt 10 personer, som skal ha overordnet oversikt, innsikt og kontroll på DSBs Azure tenant. Hvordan tenker du at IKT bør jobbe for å oppnå en distribuert ansvarsmodell?

Vi ønsker å kunne tilby landing zones til små og mellomstore team i andre deler av organisasjonen. Hvilke hensyn blir viktige for å lykkes med dette?

Eksemplifiser også typiske ansvar og oppgaver som vil ligge hos IKT vs. i team utenfor IKT.

### 2. Alternativ hosting av egenutviklede applikasjoner i Azure

I dag kjører egenutviklede applikasjoner i Azure Kubernetes Service (AKS). Frontend-appene er Vue pakket inn i tilpassede nginx-image. Backend-appene er Java Spring pakket inn i OCI image. Applikasjonene deployes vha. Helm chart som ArgoCD har ansvaret installere.

Vi ser at det å hoste egenutviklede applikasjoner i AKS, som i praksis er en platform-i-platformen, medfører mye ekstra kompleksitet og ekstra tidsbruk knyttet til vedlikehold.

Med krav om støtte for automatisk og kontinuerlig utrulling av nye versjoner, skisser opp en annen måte å hoste applikasjonene våre i Azure. Det er viktig at du legger til grunn at dette er en løsning/arkitektur som kan driftes og oppdateres av 1-2 personer. Si litt om hvilke(n) Azure-tjeneste(r) du velger og hvorfor.

### 3. Terraform - For hele bedriften

I dag benytter utviklingsteamet hos IKT Terraform for å sette opp alt teamet har ansvaret for i Azure. IKT har et uttalt mål om at det skal benyttes IaC for alt i Azure uavhengig av team.

Hva kan vi gjøre og hvordan kan vi jobbe for å hjelpe andre team i DSB til å komme i gang med å ta i bruk terraform i større grad?

Vi har et ønske om å konsolidere alle Terraform prosjekter i ett mono-repo for bedriften. Hva er en hensiktsmessig struktur på et slikt repo og hvorfor?

Hvordan kan vi realisere dette samtidig som:

- Vi sørger for at ikke alle team skal kunne endre på all infrastruktur.
- Men, alle skal kunne foreslå endringer.
- Endringer valideres og testes skikkelig før de rulles ut i prod.

Er det andre hensyn du ville vektlagt?

### 4. Security posture i Azure

Med et Azure-oppsett som primært består av: Application Gateway, Azure Firewall, VMer og Virtual Machine Scale Set, Azure Kubernetes Service og Azure Container Registry. I tillegg til grunnlegende ressurser som Key Vault, Storage Account, Virtual Network osv. Basert på en konvensjonell hub-and-spoke nettverksarkitektur med site-to-site VPN til fysiske datasentre.

Hvordan ville du sørget for en god security posture i et slikt oppsett?

Hvilke Azure tjenester ville du vurdert å ta i bruk og hvorfor?

Gitt at oppgaven faller på 1-2 personer og ikke et helt SecOps-team, hvilke hensyn blir viktige?

### 5. Nettverksrelatert oppgave

Denne oppgaven består av 3 deloppgaver, velger du denne oppgaven skal alle 3 besvares.

Deloppgavene:

1. Beskriv forskjellen på lag 2 og lag 3-nett
2. Hvordan logge inn på en Cisco-switch og gjøre følgende;
   1. Sjekke status på alle interface
   2. Endre vlan på en port
   3. Sjekke ruting-tabell
   4. Sjekke PoE-status på switchporter
3. DSB bruker Check Point brannmur on-prem. I hvilken rekkefølge blir regelsettet på brannmuren aktivert?
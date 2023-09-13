# Oppgaver andregangsintervju DevOps-rolle

Dette er oppgaver til kandidater som innkalles til andregangsintervju for DevOps-rolle i DSB IKTs utviklingsteam, høsten 2023.

**Innholdsfortegnelse**

- [Innledning](intervju-oppgaver_devops_september_2023.md#innledning)
- [Oppgavene](intervju-oppgaver_devops_september_2023.md#oppgavene)
  - [Azure](intervju-oppgaver_devops_september_2023.md#azure)
    - [1. Kubernetes (AKS) - Serve hemmeligheter til applikasjonene](intervju-oppgaver_devops_september_2023.md#1-kubernetes-aks---serve-hemmeligheter-til-applikasjonene)
    - [2. Kubernetes (AKS) - Tilby persistent lagring til applikasjonene](intervju-oppgaver_devops_september_2023.md#2-kubernetes-aks---tilby-persistent-lagring-til-applikasjonene)
    - [3. Alternativ hosting av utviklingsteamets applikasjoner](intervju-oppgaver_devops_september_2023.md#3-alternativ-hosting-av-utviklingsteamets-applikasjoner)
  - [Terraform](intervju-oppgaver_devops_september_2023.md#terraform)
    - [4. For hele bedriften](intervju-oppgaver_devops_september_2023.md#4-for-hele-bedriften)
    - [5. Lage og tilby moduler](intervju-oppgaver_devops_september_2023.md#5-lage-og-tilby-moduler)
  - [GitHub](intervju-oppgaver_devops_september_2023.md#github)
    - [6. Actions - Veien videre](intervju-oppgaver_devops_september_2023.md#6-actions---veien-videre)
    - [7. GitHub Packages for byggeartefakter](intervju-oppgaver_devops_september_2023.md#7-github-packages-for-byggeartefakter)

## Innledning

Under finner du syv oppgaver innenfor tre forskjellige tema. Oppgavene er nummerert fra 1 til 7 og du velger _èn_ av oppgavene.

Det finnes ikke noe "rett" svar på disse oppgavene, de er ment for refleksjon og diskusjon under intervjuet.

Besvarelseform velger du selv. Eksempler kan være kan være ren tekst i markdown, punktliste i word eller arkitekturdiagram som png. Her står du fritt til å velge. vi ønsker _ikke_ at du skal skrive kode.

Står du fast eller blir usikker fordi du mangler informasjon eller innsikt i det som er DSB-spesifikt? Da er det helt greit å gjøre antagelser eller bestemme noen forutsetninger for besvarelsen din.

## Oppgavene

### Azure

I dag kjører applikasjonene utviklingsteamet forvalter i Azure Kubernetes Service (AKS). Frontend-appene er Vue pakket inn i tilpassede nginx-image. Backend-appene er Java Spring pakket inn i OCI image. Applikasjonene deployes vha. Helm chart som ArgoCD har ansvaret installere.

#### 1. Kubernetes (AKS) - Serve hemmeligheter til applikasjonene

Vi har behov for å gjøre hemmeligheter fra Azure Key Vaults tilgjengelig for applikasjonene vi kjører i AKS på en sikker og kontrollert måte.

Beskriv hvordan du ville realisert dette. Reflekter gjerne litt rundt fordeler og ulemper ved løsningen du velger. Hvordan sørger du for god separasjon mellom applikasjonene. Altså at ikke app A kan benytte seg av hemmelighetene som tilhører app B?

#### 2. Kubernetes (AKS) - Tilby persistent lagring til applikasjonene

Noen av applikasjonene vi kjører i AKS har behov for persistent lagring. Typisk dreier det seg om forskjellige typer vedlegg som er sendt inn sammen med skjemabesvarelser fra publikum. Filene skal ikke lagres i SQL-database. Disse filene må være tilgjengelig fra alle instansene av applikasjonen og overleve en fullstendig gjenoppbygging av AKS-klusteret.

Utforsk hvordan dette kan realiseres på en måte vi kan standardisere på. Ha fokus på å gjøre det så enkelt som mulig for en utvikler å konfigurere opp. Ta gjerne med betraktninger rundt karantene, anti-virus og backup.

#### 3. Alternativ hosting av utviklingsteamets applikasjoner

Vi ser at det å hoste applikasjonene våre i AKS, som i praksis er en platform-i-platformen, medfører mye ekstra kompleksitet og ekstra tidsbruk knyttet til vedlikehold.

Med krav om støtte for automatisk og kontinuerlig utrulling av nye versjoner, skisser opp en annen måte å hoste applikasjonene våre i Azure. Det er viktig at du legger til grunn at dette er en løsning/arkitektur som kan driftes og oppdateres av 1-2 personer. Si litt om hvilke(n) Azure-tjeneste(r) du velger og hvorfor.

### Terraform

I dag benytter utviklingsteamet i IKT Terraform for å sette opp alt teamet har ansvaret for i Azure. IKT har et uttalt mål om at det skal benyttes IaC for alt i Azure uavhengig av team.

#### 4. For hele bedriften

Hva kan vi gjøre og hvordan kan vi jobbe for å hjelpe andre team i DSB til å komme i gang med å ta i bruk terraform i større grad?

Vi har et ønske om å konsolidere alle Terraform prosjekter i ett mono-repo for bedriften. Hva er en hensiktsmessig struktur på et slikt repo og hvorfor?

Hvordan kan vi realisere dette samtidig som:

- Vi sørger for at ikke alle team skal kunne endre på all infrastruktur.
- Men, alle skal kunne foreslå endringer.
- Endringer valideres og testes skikkelig før de rulles ut i prod.

Er det andre hensyn du ville vektlagt?

#### 5. Lage og tilby moduler

Vi ønsker å etablere et sett med standardiserte DSB-Terraform-moduler. Disse skal ha defaults hensiktsmessig for DSB, sørge for at vi etablerer infrastruktur mest mulig uniformt i Azure og gjøre det lettere for oss å gjøre endringer på mange steder samtidig.

Hva er viktige hensyn å ta her? Og, hvis du skulle bygge opp en standardisert CI/CD-prosess for Terraform-moduler, hvilke prosesser skulle den bestått av?

### GitHub

I utviklingsteamet benytter vi GitHub for kode, for CI/CD samt lagring av maven-pakker.

#### 6. Actions - Veien videre

Vi har etablert en samling med [actions](https://github.com/dsb-norge/github-actions/tree/main/ci-cd) og gjenbrukbare [workflows](https://github.com/dsb-norge/github-actions/tree/main/.github/workflows) som vi benytter for alle CI/CD-behov. Actions er skrevet som bash-skript og kjøres på GitHub-runnere som vi hoster selv. Vi ser at etterhvert som vi utvider med flere actions og workflows så stiger kompleksiteten for ikke å snakke om tiden det tar å vedlikeholde bash-skript som ligger som yaml-strenger.

Gitt at det er et premiss at det er GitHub Actions som skal benyttes, kom med forslag til "veien videre" for bruk av GitHub Actions i DSB. Her kan det dreie seg om små justeringer på det vi har i dag til å lage alt på nytt. Ser du åpenbare mangler eller utfordringer med det vi har i dag?

#### 7. GitHub Packages for byggeartefakter

Vi har akkurat gått fra å benytte _Sonatype Nexus Repository_ (selv-hostet on-prem) til å bruke _GitHub Packages_ for lagring av maven-pakkene våre.

Hvilke åpenbare fordeler ser du ved å gjøre et slikt bytte?

_GitHub Packages_ er ganske bare-bones sammenlignet med et modent produkt som _Sonatype Nexus Repository_. I praksis så dreier det seg om noen tilgang-styrte APIer på toppen av en lagringsløsning. Gitt at vi ønsker alt etablert mest mulig automatisert med en set-and-forget-filosofi. Med målsetning om å ha kontroll på kostnad samtidig med forutsigbar tilgang på maven-pakker, hvilke prosesser ville du etablert rundt et produkt som _GitHub Packages_, og hvordan ville du realisert disse?

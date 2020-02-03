# Linux Server Administrasjon for Nybegynnere

_Må jobbes mer med, men er en start så langt_

## Verktøy som vil bli benyttet

* [SSH oppsett](#SSH)
* [Linux Basics](#Linux-Basics)
* [Tekst redigering](#Tekst-redigering)
* [Server Setup](#Server)

## SSH

SSH virker kanskje som noe mystisk teknologi noen fant fra forrige årtusen og aldri sluttet å bruke, men når du skal jobbe med Linux eller Unix servere, er det helt fantastisk.  
Fordelen er at du ikke bruker enormt med båndvidde og systemresursser på å kjøre et grafisk grensesnitt på en server som ikke skal brukes med skjerm (såkalt headless-server).

## Linux-basics

Nyttig kunnskap når du skal jobbe med Linux eller UNIX baserte servere

* `root` - Superbrukeren over alle superbrukere på maskinen. Tenk deg om før du kjører noe som root.
* `sudo` - Kjører en kommando som superbruker uten å være logget inn som superbruker. Tenk kjør som admin på Windows, men på steroider.
* `brukernavn@hostnavn:~`
	* `brukernavn` er hva du er logget inn som.
	* `@hostnavn` viser hvilken maskin du jobber på.
	* `:~` sier at du er i mappen ~/ som er hjem mappen din, den er vanligvis plassert under /home/brukernavn/
	* `~` Tilde. Tegnet for hjem folderen din. Kan brukes i stedet for å spesifisere /home/bruker/
* `cd folder` - Lar deg bevege deg mellom mapper i filsystemet `cd ~/Documents` - går inn i mappen ~/Documents
	* `cd ..` - går tilbake en mappe. 
	* `cd ../..` - kan også brukes til å gå flere mapper tilbake
* `ls` - lister opp alle filer i en mappe på linje
	* `ls -l` - lister opp filene i en mappe som en liste med fil rettigheter
	* `ls -la` - samme som over, men lister også de skjulte
* `mkdir folder` - lag mappen `folder`
* `pwd` - Print Working Directory. Viser hvor du befinner deg i filsystemet.
* `whoami` - viser hvilken bruker du kjører kommandoer som for øyeblikket
* `

### Debian / Ubuntu spesifikke kommandoer

* `apt` - Aptitude. Debian og Ubuntu's svar på en applikasjonsbutikk. Du velger bare hva du vil ha, og apt installerer det for deg.
	* `sudo apt update` - Apt er et program som må kjøre som administrator, siden den installerer pakker i beskyttede foldere. Update biten henter informasjon fra en sentral server om hvilke pakker som har vært endret siden sist du kjørte en oppdatering.
	* `sudo apt install pakkenavn` - Søker etter `pakkenavn` og prøver å installere dette.
	* `sudo apt upgrade` - Oppgraderer alle pakkene som har oppdateringer tilgjengelig. Husk å kjøre `sudo apt update` først.
	* `sudo apt remove pakkenavn` - Fjerner pakken `pakkenavn`. Fjerner ikke pakkene som ble installert sammen med `pakkenavn`
	* `sudo apt auto-remove` - Fjerner pakker som ikke er i bruk på systemet (som rester etter fjernede pakker).

### Hva du ikke bør gjøre

* `sudo rm -rf /` eller `sudo rm -rf / --no-preserve` - I motsetning til Windows, bruker ikke Linux/UNIX systemer støttehjul når det kommer til destruktive funksjoner. Denne funksjonen sletter hele filsystemet fra folderen `/` og nedover.
* `chmod 777 ~/go/src/golang.go` - Gir alle brukere tilgang til å Lese, Skrive og Kjøre filen `golang.go` eller mappen du er inni (om du ikke spesifiserer en fil). Selv om det _teknisk sett_ funker, er det dårlig sikkerhetspraksis.
* `dd` - Om du ikke vet hva du gjør, ikke lek med dd. Kommandoen har kallenavnet "disk destroyer" for en grunn, ettersom du kan krasje ditt eget filsystem med den. Tenk før du kjører.

## Tekst-redigering

Siden dette er på en maskin som ikke har en grafisk grensesnitt, så må vi bruke kommandolinje-baserte tekst redigeringsverktøy. To av tekst redigeringsverktøyene som er tilgjengelig på Linux / UNIX maskiner er [Nano](https://www.nano-editor.org/) og [Vim](https://www.vim.org/). For å sammenligne de

| Navn | Fordeler | Ulemper |
|------|----------|---------|
| Nano | Nybegynner vennlig, har oversikt over kommandoer i bunnen av vinduet | Hva du ser er hva du får, ingen plugins |
| Vim | Veldig mange plugins, meget kjapp og få distraksjoner | ***Bratt*** læringskurve, mye å sette seg inn i, ikke samme kommandoer som folk er vant til |

### Nano

Nano er en simpel tekst editor. Det du trenger å vite er:

* `nano fil` - Åpner filen "fil" i Nano
* `[Ctrl]`+`s` - Lagrer filen
* `[Crtl]`+`x` - Lukker filen
* `Piltaster` - Beveger deg rundt i teksten

### Vim

* `vim fil` - Åpner filen "fil" i Vim i oversikts modus
* `i` - Insert: Lar deg redigere filen
* `[Esc]` - Går tilbake til oversikts modus
* `:w` - Write: Skriver endringer til filen
* `:q` - Quit: Lukker filen. Vim vil klage om du ikke har lagret
* `:wq` - Write & Close: Lagrer og lukker filen
* `:q!` - Force Quit: Lukker filen uten å lagre endringer
* `/` - Search: `/elefant` vil søke gjennom filen etter ordet "elefant"
* `h` - Left: Beveger deg til venstre i teksten. Kan også bruke piltaster
* `j` - Up: Beveger deg opp i teksten. Kan også bruke piltaster
* `k` - Down: Beveger deg ned i teksten. Kan også bruke piltaster
* `l` - Right: Beveger deg til høyre i teksten. Kan også bruke piltaster

## Server

Anbefalt programvare å installere
| Navn | Installasjons kommando | Funksjon |
|------|------------------------|----------|
| `fail2ban` | `sudo apt install fail2ban` | Sjekker etter gjentatte innloggingsforsøk, og gir disse en timeout etter et visst antall forsøk. |

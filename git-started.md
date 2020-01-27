# Git Started (for Windows brukere av Git Bash)

## Lag en SSH Nøkkel

Inne i Git Bash kjør:
```ssh-keygen -t rsa -b 4096```

Den vil nå spørre hvor du vil lagre filen, bare trykk enter ettersom det er håpløst å legge filen ett annet sted med Git Bash.  
Neste er ett passord som du gjentar to ganger.  

Du har nå en SSH nøkkel "id_rsa" og et public certificate "id_rsa.pub".

Dersom du vil lage flere nøkler til andre ting, som GitHub eller lignende, anbefaler jeg å endre navn på de etter de er generert. Du finner disse to filene under `C:\Brukere\DittBrukernavn\.ssh\`  
Velg ett deskriptivt navn (uten mellomrom siden kommandolinjen ikke er glad i disse), og husk å navngi begge filene til det samme så de heter f.eks `uia_bitbucket` & `uia_bitbucket.pub`  

---

Åpne <https://tools.uia.no/bitbucket/plugins/servlet/ssh/account/keys> i nettleseren din, og velg "Add key"

Tilbake i kommandolinjen kan du kopiere og lime inn denne kommandoen  
```clip < ~/.ssh/uia_bitbucket.pub```  
(bytt ut uia_bitbucket.pub med hva enn du navnga den som i forrige steg) og lime inn den lange listen over tall, tegn og bokstaver vilkårlig plassert  tilbake i nettleseren og lagre dette.


### Lagre passordet så det ikke må skrives inn hele tiden

Normalt så vil du bli spurt om passordet du lagde for nøkkelen hele tiden. 
Hvis du der lagde et litt for langt passord eller rett og slett er litt lat, så kan du få maskinen din til å lagre passordet for deg ved å skrive følgende i kommandolinjen:

```ssh-add```

Hvis du lagde nøkkelen din med et annet navn kan du legge inn banen dit etter kommandoen slik:

```ssh-add ~/.ssh/uia_bitbucket```


> Hvis denne kommandoen gir feilmeldingen:
> 
> `Could not open a connection to your authentication agent.`
>
> Så kan du prøve dette først:
> ```eval `ssh-agent -s` ```
> Og deretter prøve `ssh-add` på nytt.


Nå kan du koble til nettsiden / git-serveren uten å måtte oppgi passordet!


## Konfigurere SSH til å assossiere nøkkelfil med nettsiden

Åpne en terminal tekst editor med  
```nano ~/.ssh/config```  
og lim inn:

```config
Host tools.uia.no
        HostName tools.uia.no
        Port 7999
        User git
        PubKeyAuthentication yes
        IdentityFile ~/.ssh/uia_bitbucket
```

> Husk å bytt ut `uia_bitbucket` med navnet du ga på nøkkelfilen din. Dette er IKKE den som ender med .pub.

Lagre med CTRL+S og lukk med CTRL+X

---

For å teste at alt funker, kan du kjøre kommandoen  
```ssh git@tools.uia.no```  

> Den vil da si noe om at identiteten til serveren du kobler til ikke er verifisert. Dette er en del av sikkerhetsmekanismen til SSH for å sørge for at ingen skal komme mellom deg og serveren du kobler deg til i fremtiden med et uhell. Terminalen vil nå spørre etter passordet til nøkkelfilen din. Skriv det inn og trykk Enter.

Forhåpentligvis vil terminalen si:  
> `shell request failed on channel 0`  

Hvorfor vil vi ha en feilmelding her?
Jo, fordi vi nå vet at vi er koblet på serveren og den er konfigurert slik at vi ikke skal tukle med serveren utenom å laste opp og hente filer fra Git.

## Sette opp mappe for Go utvikling

Har du laget en Go folder i brukermappen din på pcen?
Du kan skjekke dette om du åpner Filutforskeren og Trykker på brukernavnet ditt. Er det en mappe kalt Go, gå inn i den og lag mappen src\tools.uia.no inne i denne.

Gå tilbake i terminalen og skriv `cd ~/Go/src/tools.uia.no`

Nå kan vi begynne med Git  
```git clone git@tools.uia.no:7999/is105k20v/brukernavn.git```, hvor du bytter ut brukernavn med ditt eget.

---

Om du får opp at du har klonet en tom mappe, har du gjort alt rett.

> Gratulerer, du har nå et fungerende Git repository på tools.uia.no klonet til maskinen din.

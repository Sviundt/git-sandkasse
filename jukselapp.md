# Jukselapp med Git kommandoer og eksempler

List opp alle Git kommandoer

```git --help```

Finn ut mer om kommandoene printet ut fra `git --help`. Om du vil lære mer om `git commit`, kan du kjøre:

```git commit --help```

## Lokale Git Kommandoer

### Kloning

For å laste ned et Git repo

* Git clone (http/https)

```git clone https://github.com/Sviundt/git-sandkasse.git```

* Git clone (ssh)

```git clone git@github.com:Sviundt/git-sandkasse.git```

### Lagre endringer og synkronisering

Legge til en fil i listen over ting å synkronisere. Bruk asterisk (*) for å legge til alle filer i en mappe.  

* Git add

```git add filnavn```

* Git add (alle filer i en mappe kalt `source`)

```git add source/*```

Lag en oversikt over alle filene og endringene som skal lastes opp (med en melding)

* Git commit

```git commit -m "Melding om hva denne oppdateringen gjør"```
  
Laste opp endringer til Git server

* Git push

```git push```

* Git push origin _gren-navn_ (dytter alle filene spesifisert tidligere i grenen _gren-navn_ på origin serveren)  

```git push origin testing```

###  Hente Endringer

Koble til server og se etter endringer

* Git pull

```git pull```

* Git pull origin _grein_ (henter alle filene som er på grenen _grein_ fra origin serveren)

```git pull origin grein```

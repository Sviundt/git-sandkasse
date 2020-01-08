# Jukselapp med Git kommandoer og eksempler

## Kloning

For å laste ned et Git repo

* Git clone (http/https)

```git clone https://github.com/Sviundt/git-sandkasse.git```

* Git clone (ssh)

```git clone git@github.com:Sviundt/git-sandkasse.git```

## Lagre endringer og synkronisering

Legge til en fil i listen over ting å synkronisere. Bruk asterisk (*) for å legge til alle filer i en mappe.

* Git add
```git add filnavn```

* Git add (alle filer i en mappe)
```git add source/*```

Lag en oversikt over alle filene og endringene som skal lastes opp (med en melding)

* Git commit
```git commit -m "Melding om hva denne oppdateringen gjør"```

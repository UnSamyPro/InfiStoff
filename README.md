# INFI


## Inner Join


Wenn Daten in mehreren Tabellen liegen, kann man mithilfe eines *Inner Join* aus mehreren Tabellen in einer Abfrage Daten ziehen.



### Inner Join mit *Where*

Theoretisch kann man einen *Inner Join* auch nur mit einer *Where* Abfrage machen.

```SQL
    SELECT *
    FROM Auto, Fahrer
    WHERE Auto.ID = Fahrer.ID;
```


### Inner Join mit *Where* und *Alias*

Der Alias macht es möglich kürzere Namen zu vergeben. Das ist praktisch wenn man ein langes *Select* hat.

```SQL
    SELECT *
    FROM Auto a, Fahrer f
    WHERE a.ID = f.ID;
```


### Inner Join mit Inner Join

Der *richtige* Inner Join so wie man ihn normal macht.

```SQL
    SELECT *
    FROM Auto a
    INNER JOIN Fahrer f ON a.ID = f.ID;
```






## Normalformen


![Tabelle1](/img/Tabelle1.png)


### 1. NF

1. Frage: Sind alle Attribute *eindeutig/automar?*\
(Aka, wenn mehrere Eintrage mit "," getrennt in einen Attribut sind dann ists *nicht eindeutig*)
\
\
Wenn nein: Aufsplitten in mehrere Attribute\
(Aka in mehrere Zeilen/Tupel)

![Tabelle2](/img/Tabelle2.png)



### 2. NF

1. Frage: Ist die Tabelle in 1. NF?\
\
Ja, weil **Alle Attribute eindeutig/automar sind**\
(Man solls begründen warum in der 1. NF)

2. Frage: Was sind die Primärschlussel? (Und auflisten)\
\
SchülerNr, LernangebotsNr

3. Frage: Funktionale Abhängigkeiten aufschreiben\
(Für Jeden teilschlüssel(also für SchülerNr und seperat für LernangebotsNr) einmal eine Zeile machen\
\+ für den gesammten Schlüssel (Also SchülerNR UND LernangebotsNR) eine Zeile machen)
\
\
Man nimmt quasi den Teilschlüssen/Primarschlüssel und schaut welche anderen Nicht-Schlüssel-Attribute davon abhängig sind. Diese schreibt man dann hinten in die `{}` rein.

```
SchülerNr                   ->      {Name, Vorname, Klasse, Klassenlehrer}
LernangebotsNr              ->      {Beschreibung}
SchülerNr/LernangebotsNr    ->      {Zeit in h}
```

4. : Laut den Funktionalen Abhängigkeiten die Attribute neu ordnen und in neue Tabellen aufspliten

![Tabelle3](/img/Tabelle3.png)



### 3. NF

1. Frage: Ist die Tabelle in der 2. NF?\
\
Ja, weil **Alle Nicht-Schlüssel-Attribute vom gesammten Schlüssel abhängig sind**\
(Also in einer Tabelle sind alle Nicht-Schlüssel-Attribute vom gesammten Schlüssel in dieser Tabelle abhängig, nicht nur von einem Teil des Schlüssels)

2. : Funktionale Abhängigkeiten aufschreiben\
Ist fast gleich wie in der 2. NF, nur diesmal beziehen wir uns darauf, dass es ***keine*** **Nicht-Schlüssel-Attribute gibt, die von einem anderen Nicht-Schlüssel-Attribut abhängig sind.** Aka bei unserem Bespiel währe Klassenlehrer abhängig von Klasse.

```
SchülerNr                   ->      {Name, Vorname, Klasse}
LernangebotsNr              ->      {Beschreibung}
SchülerNr/LernangebotsNr    ->      {Zeit in h}
Klasse                      ->      {Klassenlehrer}
```

3. : Laut den Funktionalen Abhängigkeiten die Attribute neu ordnen und in neue Tabellen aufspliten

![Tabelle4](/img/Tabelle4.png)






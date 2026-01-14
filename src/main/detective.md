## #1 -  Überblick über die Git-History
Welche 2 Commits fallen euch in der History bereits zu Beginn negativ auf? Und warum? 

- update more und stuff fallen negativ auf, da die commit messages wenig verraten.



## #2 - Ab welchem Commit ist das Projekt nicht mehr stabil?
Woran erkennt ihr, dass es ab hier ein Problem gibt?
Mit welche(n) Befehl(en) könnt ihr das herausfinden?
(Antwort: Commit-ID, Message, Begründung)

- commit 50da5b1caf09339b68ce5d4ace7368a7b99f013e (tag: v2-tests-broken) (git log)

Der test beim commit ist fehlgeschlagen. Wahrscheinlich wegen dem division durch 0 Fehler


## #3 - Welche Datei wurde dabei verändert?
Welche Datei(en) wurden im verdächtigen Commit verändert?
Mit welche(n) Befehlen könnt ihr das herausfinden?
(Antwort: Commit-ID, geänderte Datei(en), Kurzbeschreibung der Änderung)

- mit git show 50da5b1caf09339b68ce5d4ace7368a7b99f013e
rename from Calculator.java deutet darauf hin, dass Calculator.java verändert wurde.
statt b wurde 0 hingeschrieben

## #4 - Wer hat die entscheidende Stelle verändert?
Welche Datei ist besonders relevant und warum?
Mit welche(n) Befehlen kannst du dies rausfinden? 
(Antwort: Datei, Commit-ID der relevanten Änderung, Commit Message, betroffene Code-Stelle, warum ist diese Stelle wichtig?)

- Die Datei Calculator.java ist relevant
mit git show findet man das heraus, die id war 50da5b1caf09339b68ce5d4ace7368a7b99f013e.

public static int divide(int a, int b) {
       return a / b;
   }
   // BUG: falscher Divisor -> Division durch 0
    return a / 0;

wegen dem dividieren durch 0 schlägt der ganze Test fehl

## #5: Vergleich vor und nach der Änderung
Was ist der Unterschied im Code, bevor und nachdem das Problem entstanden ist? Mit welchem Befehl kannst du das rausfinden? 

- auch mit git show, Bei den Minus und plus sieht man die changes. vorher war statt dem 0er ein b da.

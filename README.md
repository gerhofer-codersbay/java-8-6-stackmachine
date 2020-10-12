# Java 

## Stackmachine

Implementieren eine Programm, welches einen in Infixnotation gegebenen arithmetischen Ausdruck mit
Vorrang in seine [Postfixnotation(umgekehrte polnische Notation, UPN)](https://de.wikipedia.org/wiki/Umgekehrte_polnische_Notation) umwandelt und dann den Wert dieses
Ausdrucks mit Hilfe einer Stackmachine berechnet. So muss zum Beispiel der arithmetische Ausdruck „5 ·(((9+
7)/(8−4))+7)“ zuerst in eine UPN-Darstellung „5 9 7 + 8 4 - /7 + ·“ umgewandelt und dann zu „55“ vereinfacht
werden. 

Der Einfachheit halber darfst du davon ausgehen, dass der arithmetische Ausdruck fehlerfrei angegeben ist. 

Zur Inspiration für die Infix- in Postfixnotationsumwandlung hier ein in Pseudocode skizzierter Algorithmus
Über einen „Hilfsstack“ wird die Eingabe in eine „UPN-Queue“ gelesen. 

```
1 while noch nicht den gesamten Ausdruck gelesen do
2   if nächstes Symbol ist eine Zahl then
3     speichere diese Zahl in der UPN-Queue
4
5   else if nächstes Symbol ist ein arithmetischer Operator then
6     lege diesen Operator auf den Hilfsstack
7
8   else if nächstes Symbol ist eine „Klammer zu“ then
9     nehme ein Element vom Hilfsstack und speichere es in der UPN-Queue
10  end if
11 end while
12
13 while Hilfsstack nicht leer do
14  nehme ein Element vom Hilfsstack und speichere es in der UPN-Queue
15 end while
```

Das Ausrechnen eines Ausdrucks in Postfix notation ist dann relativ simpel. Man liest von links nach rechts zahlen ein, trifft man einen operator, wendet man diesen auf die beiden zu letzt gesehenen Zahlen an und ersetzt diese Zahl mit der neuen. 

```
5 9 7 + 8 4 - /7 + ·
5 16 8 4 - /7 + ·
5 16 4 /7 + ·
5 4 7 + ·
5 11 ·
55
```

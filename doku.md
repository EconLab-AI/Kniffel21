###Logischer Ablauf im Kniffel-Spiel###

Spieler würfelt:
Der Spieler beginnt mit allen 5 Würfeln.
Die Methode decide_which_dices_to_hold entscheidet nach jedem Wurf, welche Würfel behalten und welche neu geworfen werden sollen.

Nach drei Würfen:
Der Spieler hat alle Würfel behalten, die er für wichtig hält.
Jetzt entscheidet die Methode decide_which_field_to_enter, in welches Feld die Punkte eingetragen werden sollen.
Punkte werden eingetragen:
Kniffel_Game.py überprüft, ob das gewählte Feld gültig ist.
Das Scoreboard wird aktualisiert.

###Zusammenhang zwischen den beiden Methoden###
Erste Methode (decide_which_dices_to_hold):
Arbeitet direkt mit den Würfen (z. B. [2, 5, 5, 6, 3]) und entscheidet, welche Würfel behalten werden.
Zweite Methode (decide_which_field_to_enter):
Arbeitet mit den Würfeln, die nach der Entscheidung in kept_dices liegen, und nutzt sie, um ein geeignetes Feld auf dem Scoreboard auszuwählen.



1. Importieren von Counter
from collections import Counter
Counter ist ein Werkzeug, um die Häufigkeit von Elementen in einer Liste zu zählen.

2. Anfang der Methode
def decide_which_dices_to_hold(self, scoreboard, kept_dices, dice_rolls, roll):
Parameter:
scoreboard: Der aktuelle Punktestand.
kept_dices: Bereits behaltene Würfel.
dice_rolls: Aktuelle Würfelwürfe.
roll: Nummer des aktuellen Wurfs (0 oder 1).

3. Kombinieren der Würfel
Unsere Methode decide_which_dices_to_hold

####
all_dices = kept_dices + dice_rolls
####

Was bedeuten die Variablen?

kept_dices: Eine Liste der Würfelwerte, die du bereits aus vorherigen Würfen behalten hast.

Beispiel: Wenn du im ersten Wurf eine 5 und eine 6 behalten hast, dann ist kept_dices = [5, 6].

dice_rolls: Eine Liste der Würfelwerte, die du gerade geworfen hast.

Beispiel: Im zweiten Wurf wirfst du und erhältst dice_rolls = [2, 5, 5].

all_dices: Eine Kombination aus den bereits behaltenen Würfeln und den aktuellen Würfen.

Berechnung: all_dices = kept_dices + dice_rolls

Mit unseren Beispieldaten:
all_dices = [5, 6] + [2, 5, 5] = [5, 6, 2, 5, 5]

Warum kombinieren wir kept_dices und dice_rolls?
Wir wollen den aktuellen Stand aller Würfel betrachten, um zu entscheiden, welche Würfel wir insgesamt behalten möchten, um bestimmte Kombinationen zu erreichen (z.B. einen Kniffel, ein Full House, eine Straße usw.).

4. Zählen der Würfelwerte
dice_counts = Counter(all_dices)
dice_counts ist ein Dictionary, das angibt, wie oft jeder Würfelwert vorkommt.
Mit unserem Beispiel:
all_dices = [5, 2, 5, 5, 6]
dice_counts = Counter({5: 3, 2: 1, 6: 1})
# Am Anfang war der Arbeitsspeicher
* author: Timm Knape

Bevor wir die zentrale Arbeitseinheit (central processing unit = CPU)
in Betrieb nehmen können,
müssen wir ihr einer Umgebung schaffen, in der sie sich wohlfühlt.

Dazu gehört erst eine Form von Speicher.
Aus dem Speicher liest die CPU Befehle und Daten.
Auch Ergebnisse kann sie dort ablegen.

Es gibt viele Arten von Speicher.
Mancher behält seinen Inhalt, wenn er nicht mit Strom versorgt wird.
Andere können nur einmal beschrieben werden.
Oder müssen aufwändig mit UV-Licht gelöscht werden.
Gebräuchliche Bausteine müssen mehrmals pro Sekunde neu beschrieben
werden, da sie sonst ihren Inhalt vergessen.

Wir fangen mit einem einfachen statischen RAM-Baustein an.
RAM steht für random access memory.
Das ist Speicher, der gelesen und beschrieben werden kann.

Wichtig ist, dass er eine Versorgungsspannung von 5 Volt hat.
Und dass er mindestens acht Zustände zu jeder Adresse hinterlegen kann.

Ich verwende einen NEC D431000ACZ-70LL, den ich für ein paar Euro bei
Ebay erstanden habe.

Dieser hat die folgende Pin-Belegung:

```gv
graph {
	rankdir="TB";
	rank="new";
	{ rank="same";
	"A1" -- "B11"; "B12" -- "C1";
	}
	rank="new";
	{ rank="same";
	"A2" -- "B21"; "B21" -- "B22"; "B22" -- "C2";
	}
}
```

```gv
graph {
newrank=true;
	subgraph {
		node [shape=plain];
		"A16" -- chip:p2;
		"A14" -- chip:p3;
		"A12" -- chip:p4;
		"A7" -- chip:p5;
		"A6" -- chip:p6;
		"A5" -- chip:p7;
		"A4" -- chip:p8;
		"A3" -- chip:p9;
		"A2" -- chip:p10;
		"A1" -- chip:p11;
		"A0" -- chip:p12;
		"I/O1" -- chip:p13;
		"I/O2" -- chip:p14;
		"I/O3" -- chip:p15;
		"Masse" -- chip:p16;
	}
	subgraph {
		chip [shape=record label="{<p1>1|<p2>2|<p3>3|<p4>4|<p5>5|<p6>6|<p7>7|<p8>8|<p9>9|<p10>10|<p11>11|<p12>12|<p13>13|<p14>14|<p15>15|<p16>16}|{<p32>32|<p31>31|<p30>30|<p29>29|<p28>28|<p27>27|<p26>26|<p25>25|<p24>24|<p23>23|<p22>22|<p21>21|<p20>20|<p19>19|<p18>18|<p17>17}"];
	}
	subgraph {
		node [shape=plain];
		chip:p32 -- "Versorgungsspannung";
		chip:p31 -- "A15";
		chip:p30 -- "Chipauswahl-2";
		chip:p29 -- "/Schreiben";
		chip:p28 -- "A13";
		chip:p27 -- "A8";
		chip:p26 -- "A9";
		chip:p25 -- "A11";
		chip:p24 -- "/Ausgabe";
		chip:p23 -- "A10";
		chip:p22 -- "/Chipauswahl-1";
		chip:p21 -- "I/O8";
		chip:p20 -- "I/O7";
		chip:p19 -- "I/O6";
		chip:p18 -- "I/O5";
		chip:p17 -- "I/O4";
	 }
}
```

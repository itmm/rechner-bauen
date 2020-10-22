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
	ranksep=0.1;
	node[shape=plain];
	subgraph {
		 "1"; "32";
		 "2"; "31";
		 "3"; "30";
		 "4"; "29";
		 "5"; "28";
		 "6"; "27";
		 "7"; "26";
		 "8"; "25";
		 "9"; "24";
		"10"; "23";
		"11"; "22";
		"12"; "21";
		"13"; "20";
		"14"; "19";
		"15"; "18";
		"16"; "17";
	}

	  "A16" -- "2";
	  "A14" -- "3";
	  "A12" -- "4";
	   "A7" -- "5";
	   "A6" -- "6";
	   "A5" -- "7";
	   "A4" -- "8";
	   "A3" -- "9";
	   "A2" -- "10";
	   "A1" -- "11";
	   "A0" -- "12";
	 "I/O1" -- "13";
	 "I/O2" -- "14";
	 "I/O3" -- "15";
	"Masse" -- "16";

	"32" -- "Versorgungsspannung";
	"31" -- "A15";
	"30" -- "Chipauswahl-2";
	"29" -- "/Schreiben";
	"28" -- "A13";
	"27" -- "A8";
	"26" -- "A9";
	"25" -- "A11";
	"24" -- "/Ausgabe";
	"23" -- "A10";
	"22" -- "/Chipauswahl-1";
	"21" -- "I/O8";
	"20" -- "I/O7";
	"19" -- "I/O6";
	"18" -- "I/O5";
	"17" -- "I/O4";

	{ rank="same";           "1"; "32"; "Versorgungsspannung"; }
	{ rank="same";   "A16";  "2"; "31"; "A15"; }
	{ rank="same";   "A14";  "3"; "30"; "Chipauswahl-2"; }
	{ rank="same";   "A12";  "4"; "29"; "/Schreiben"; }
	{ rank="same";    "A7";  "5"; "28"; "A13"; }
	{ rank="same";    "A6";  "6"; "27"; "A8"; }
	{ rank="same";    "A5";  "7"; "26"; "A9"; }
	{ rank="same";    "A4";  "8"; "25"; "A11"; }
	{ rank="same";    "A3";  "9"; "24"; "/Ausgabe"; }
	{ rank="same";    "A2"; "10"; "23"; "A10"; }
	{ rank="same";    "A1"; "11"; "22"; "/Chipauswahl-1"; }
	{ rank="same";    "A0"; "12"; "21"; "I/O8"; }
	{ rank="same";  "I/O1"; "13"; "20"; "I/O7"; }
	{ rank="same";  "I/O2"; "14"; "19"; "I/O6"; }
	{ rank="same";  "I/O3"; "15"; "18"; "I/O5"; }
	{ rank="same"; "Masse"; "16"; "17"; "I/O4"; }

	{
		edge[style="invis"];
		 "1" --  "2";
		 "2" --  "3";
		 "3" --  "4";
		 "4" --  "5";
		 "5" --  "6";
		 "6" --  "7";
		 "7" --  "8";
		 "8" --  "9";
		 "9" -- "10";
		"10" -- "11";
		"11" -- "12";
		"12" -- "13";
		"13" -- "14";
		"14" -- "15";
		"15" -- "16";
	}
}
```

# IT-Grundschutz

![IT-GS Wortwolke](./IT-GS-Wortwolke.jpg)

## Aufbereitung IT-Grundschutz-Kompendium als JSON- und als XLSX-Datei(en)

Umwandlung des [IT-Grundschutz-Kompendiums](https://www.bsi.bund.de/DE/Themen/Unternehmen-und-Organisationen/Standards-und-Zertifizierung/IT-Grundschutz/IT-Grundschutz-Kompendium/it-grundschutz-kompendium_node.html) in eine [JSON](https://de.wikipedia.org/wiki/JavaScript_Object_Notation)-Datei (ab Edition 2020)

Ausgehend von der JSON-Datei:
Umwandlung jedes Bausteins des IT-Grundschutz-Kompendiums in eine Excel-Tabelle
- Eine Zeile je Teilanforderung (maximal ein Modalverb oder ein Einzelaspekt) jeder Anforderung
- In den Spalten Attribute der Teilanforderungen aus Perspektive Schicht, Baustein und Anforderung

In der Tabelle auch Delta-Informationen zur Vorjahresedition des IT-GS-Kompendiums (ab Edition 2021)
- Zu jeder Teilanforderung Angabe der Teilanforderung der Vorjahresedition mit der größten [Kosinus-Ähnlichkeit](https://de.wikipedia.org/wiki/Kosinus-%C3%84hnlichkeit) (innerhalb des gleichen Bausteins und innerhalb des gesamten IT-GS-Kompendiums)
- Zu jeder Teilanforderung Hinweise zu jedem geänderten Attribut bzgl. Schicht, Baustein oder Anforderung 

In der Tabelle auch Leerfelder für [GSC](https://www.bsi.bund.de/DE/Themen/Unternehmen-und-Organisationen/Standards-und-Zertifizierung/IT-Grundschutz/Zertifizierte-Informationssicherheit/IT-Grundschutzschulung/Online-Kurs-IT-Grundschutz/Lektion_6_IT-Grundschutz-Check/Lektion_6_node.html;jsessionid=6C7A24BA0A68383A2C55DB433D49B4A3.internet082)-Ergebnisse und optional beliebige weitere Leerfelder z.B. zum Monitoring der Befunde und ihrer Korrekturmaßnahmen

## Motivation

(1) Präzisierung der Kommunikation in den IT-Grundschutz Checks (GSC) und den nachfolgenden Aktivitäten

(2) Reduzierung der jährlichen Aktualisierungsaufwände verursacht durch die jährlich neue Edition des IT-GS-Kompendiums

(1) bezieht sich darauf, dass die Anforderungen des IT-GS-Kompendiums in der Regel nicht nur genau einen Aspekt betreffen und dafür genau ein Modalverb enthalten. Viele Anforderungen enthalten mehr als ein Modalverb und viele enthalten Listen von zu betrachtenden Details (Bsp. für besonders umfangreiche Anforderungen: APP.5.3.A6, NET.1.1.A21, SYS.3.2.2.A1 aus Edition 2021). In den GSC können diese Teilanforderungen (genau ein Modalverb, genau ein Element einer Aufzählung) nicht präzise referenziert werden, da eine ID auf Ebene der Teilanforderungen fehlt. Genauso kann der betroffenen Fachseite nicht unkompliziert und präzise kommuniziert werden, welche Teilanforderungen einer Anforderung noch zu erfüllen sind, wenn eine Anforderung bisher nur teilweise umgesetzt worden ist. Dies erzeugt unnötige Aufwände in der Vorbereitung der GSC, der Dokumentation der GSC-Ergebnisse und dem Monitoring der Erfüllung noch offener Teilanforderungen. Die XLSX-Tabellen unterstützen diese Schritte, indem alle Anforderungen in Teilanforderungen zerlegt sind und sich jede Zeile auf genau eine Teilanforderung mit eindeutiger ID bezieht.

(2) bezieht sich darauf, dass jährlich eine aktualisierte Fassung des IT-GS-Kompendiums erscheint und die zugehörige Änderungsdokumentation nicht feingranular genug ist, um für jede aktuelle Teilanforderung schnell entscheiden zu können, welche Ergebnisse der Vorjahresedition in welchem Umfang hierzu übernommen werden können.
Beispiel: SYS.3.2.2.A4 enthält in Edition 2021 erstmals die Teilanforderung "Die Verbindung der mobilen Endgeräte zum MDM MUSS angemessen abgesichert werden." In der Edition 2020 war dies noch eine Teilanforderung von SYS.3.2.2.A10. Aus einer feingranularen Änderungsdokumentation würde das automatisch hervorgehen, so dass in 2021 leicht nachvollziehbar ist, wie die Absicherung zum MDM in 2020 gestalten worden ist ohne dies erneut von der Fachseite erfragen zu müssen.
Der Lösungsansatz besteht darin, jede Teilanforderung in einen Vektor zu überführen und die Kosinus-Ähnlichkeit als Maß der Ähnlichkeit zu verwenden (Ignoriert werden hierbei die Wortreihenfolge, bestimmte Stoppwörter und die Zeichensetzung). Zu jeder Teilanforderung des aktuellen IT-Grundschutz-Kompendiums werden dann die Teilanforderungen der Vorjahresedition mit der größten Ähnlichkeit ermittelt mit Bezug zum gleichen Baustein (sofern nicht neu) und dem gesamten Kompendium. 

# grblHAL Firmware für 4-Achsen-Heißdraht-Schneider (BTT SKR Pico)

Fertige **grblHAL**-Firmware für einen 4-Achsen-CNC-Styroporschneider (XYZA) mit dem Board **BigTreeTech SKR Pico 1.0** (RP2040).

Die Firmware stammt aus dem Umfeld des GRBL-HotWire-Projekts von rcKeith. Weil dessen Website nicht mehr zuverlässig erreichbar ist, wird sie hier aufbewahrt, damit Nachbauer weiterhin darauf zugreifen können.

> *English: Pre-built grblHAL firmware (GPLv3) for a 4-axis XYZA hot-wire foam cutter on a BTT SKR Pico 1.0 board. Archived here because the original download source is no longer reliably available.*

---

## Inhalt

| Datei | Beschreibung |
|---|---|
| `firmware/grblHAL-skr-pico-foamcutter-xyza-2023-11-21.uf2` | Firmware zum Flashen auf das SKR Pico |
| `settings/settings-vorlage.txt` | Vorlage zum Sichern der Maschineneinstellungen (`$$`) |
| `COPYING` | Lizenztext GNU GPL v3 |

## Firmware-Details

Angaben aus der Binärdatei ausgelesen:

| | |
|---|---|
| Firmware | grblHAL (`GrblHAL 1.1f`) |
| Treiber | [grblHAL/RP2040](https://github.com/grblHAL/RP2040) |
| Board | BTT SKR Pico 1.0 |
| Build-Info | `FoamCutter XYZA 21112023` |
| Build-Datum | 21.11.2023 |
| Achsen | 4 (X, Y, Z, A) |
| SHA-256 | `d16b7866cb6e13e01953454ff51620c71db74b49fc469ccee34e8113b73a1561` |

## Flashen

1. Die Taste **BOOT** auf dem SKR Pico gedrückt halten und das Board per USB mit dem PC verbinden (oder bei gehaltener BOOT-Taste kurz **RESET** drücken).
2. Am PC erscheint ein Laufwerk namens **RPI-RP2**.
3. Die `.uf2`-Datei aus `firmware/` auf dieses Laufwerk kopieren.
4. Das Board startet automatisch neu und meldet sich als serieller USB-Port.
5. Mit einem G-Code-Sender verbinden (z. B. GRBL HotWire, Universal Gcode Sender, ioSender). Nach `$I` sollte unter anderem `FoamCutter XYZA 21112023` erscheinen.

## Einstellungen sichern und wiederherstellen

Die Maschinenparameter (Schritte/mm, Geschwindigkeiten, Beschleunigung, Richtungen, Homing usw.) liegen im Flash des Boards. **Vor jedem Neu-Flashen sichern!**

1. Mit dem Sender `$$` senden und die komplette Ausgabe kopieren.
2. Die Ausgabe in `settings/settings-vorlage.txt` (oder eine eigene Datei) einfügen.
3. Zum Wiederherstellen die Zeilen wieder einzeln an die Steuerung senden.

## Selbst bauen / anpassen

Wer die Firmware ändern oder aus dem Quellcode neu bauen will:

- **Web Builder:** <https://svn.io-engineering.com/grblHAL/> – Treiber *RP2040*, Board *BTT SKR Pico*, 4 Achsen (XYZA)
- **Quellcode:** <https://github.com/grblHAL/RP2040> (mit dem Core als Submodul: <https://github.com/grblHAL/core>)
- **Doku/Wiki:** <https://github.com/grblHAL/core/wiki>

## Lizenz und Urheber

grblHAL ist freie Software unter der **GNU General Public License v3** (siehe [`COPYING`](COPYING)).

- grblHAL © Terje Io und Mitwirkende – <https://github.com/grblHAL>
- Basiert auf Grbl © Simen Svale Skogsrud, Sungeun K. Jeon und Mitwirkende
- Raspberry Pi Pico SDK © Raspberry Pi (Trading) Ltd. (BSD-3-Clause)

**Hinweis zum Quellcode (GPLv3, Abschnitt 6):** Diese Binärdatei wurde 2023 von einem Dritten gebaut. Die vollständige Build-Konfiguration (Konfigurationsdateien, Pinbelegung, Optionen) liegt dem Betreiber dieses Repositorys nicht vor. Der zugrunde liegende Quellcode ist unter den oben verlinkten grblHAL-Repositorys öffentlich verfügbar. Wer die genaue Konfiguration kennt oder besitzt, ist herzlich eingeladen, sie per Pull Request zu ergänzen.

## Haftungsausschluss

Benutzung auf eigene Gefahr. Ein Heißdraht-Schneider arbeitet mit heißem Draht und Strom – Maschine nie unbeaufsichtigt laufen lassen und Endschalter bzw. Not-Aus vorsehen. Es gibt keinerlei Gewährleistung (siehe GPLv3, Abschnitte 15 und 16).

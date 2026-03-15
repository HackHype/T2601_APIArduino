T2601 API Arduino
=================

# Carte Extension

## Généralité

Basé sur microcontroler Atmega 328P  
Emplacement pour 2 mezanine.  

## Connectivité

UART TX -> RX -> TX -> RX  
Bus de logique avec nappe et connecteur de nappe 2x8  
4x 5V (pour 1,5 A), 6x GND, 2x UART (aller et retour), 1x rst, 1x res  
Bus puissance avec connecteurs JST  
2x 12V 2xGND (pour 2A)  
Les GND logique et puissance sont séparer  
Alimentation puissance par borniers à vis  
1x 12V 1xGND  
16 Sortie puissance par borniers à vis, 1 bornier par mezzanine  
Connexion pour la programmation par pin socket 2x3  
Connexion pour le debug (SoftwareSerial) par pin socket 1x4  
1x GND 1x TX 1x RX 1x statut  

## Fonctionnalité

Led vertes sur chacune des alimentations  
Led jaune sur pin prog  
Led jaune sur RX TX  
Led vertes sur chacune des I/O  
Led rouge sur la dernière broche libre de l’arduino  

## Pinout µc

| Pin | Fonction |
|---|---|
| 1	 |  |
| 2	 | Mezz 2 (PWM) |
| 3	 | Alimentation |
| 4	 | Alimentation |
| 5	 | Alimentation |
| 6	 | Alimentation |
| 7	 | Crystal |
| 8	 | Crystal |
| 9	 | Mezz 2 (PWM) |
| 10 | 	Mezz 2 (PWM) |
| 11 | 	 |
| 12 | 	 |
| 13 | 	Mezz 2 (PWM) |
| 14 | 	Mezz 2 (PWM) |
| 15 | 	Programmation |
| 16 | 	Programation |
| 17 | 	Programation |
| 18 | 	Alimentation |
| 19 | 	Mezz 1 (Analog) |
| 20 | 	Alimentation (Aref) |
| 21 | 	Alimentation |
| 22 | 	Mezz 1 (Analog) |
| 23 | 	Mezz 1 (Analog) |
| 24 | 	Mezz 1 (Analog) |
| 25 | 	Mezz 1 (Analog) |
| 26 | 	Mezz 1 (Analog) |
| 27 | 	Mezz 1 (Analog) |
| 28 | 	Mezz 1 (Analog) |
| 29 | 	Reset |
| 30 | 	Communication |
| 31 | 	Communication |
| 32 | 	 |

## Mécanique

Largeur 60, Hauteur à définir
4 trous pour vis à des positions à définir

# Mezanine

1 connecteur pin header male 1x10 
1x GND, 1x 5V, 8x logique,  
1 connecteur pin socket femelle 1x10  
1x GND, 1x 12V, 8x puissance,  

## Types
- OUTPUT
  - ULN2803
  - MIC2981
  - Mosfet 
  - Optocoupleur
  - Pont (5V direct)
- INPUT
  - Pont diviseur 12/24V
  - Pont (5V direct)
  - Optocoupleur (autre sens)
- IO 
  - Loconet (nécessite ICP pin)
  - Carte SD + RTC (nécessite SPI ou I2C)
  - RS485 (nécessite Software serial)
  - FRAM (nécessite SPI ou I2C)

# Carte Principale

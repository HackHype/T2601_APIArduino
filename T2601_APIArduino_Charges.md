# T2601 API Arduino

# Carte Extension

## Généralité

Basé sur microcontroler Atmega 328PB
Emplacement pour 2 mezanine.

## Connectivité

UART circulaire
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

|Pin|Fonction|Utilisation|
|-|-|-|
|1 |PWM        |Mezz 1 (PWM)|
|2 |           |led (couleur à définir) + generale debug pin|
|3 |SDA +      |led (couleur à définir)|
|4 |VCC        |Alimentation|
|5 |GND        |Alimentation|
|6 |SCL        |led (couleur à définir)|
|7 |XTAL1      |Crystal|
|8 |XTAL2      |Crystal|
|9 |PWM        |Mezz 1 (PWM)|
|10|PWM AIN0   |Mezz 1 (PWM)|
|11|AIN1       |Mezz 1|
|12|           |Mezz 1|
|13|PWM        |Mezz 1 (PWM)|
|14|PWM SS     |Mezz 1 (PWM)|
|15|MOSI TXD1 +|Programmation|
|16|MISO RXD1  |Programmation|
|17|SCK        |Programmation|
|18|AVCC       |Alimentation|
|19|ADC6 SS1   |Mezz 2 (Analog)|
|20|AREF       |Alimentation|
|21|GND        |Alimentation|
|22|ADC7 MOSI1 |Mezz 2 (Analog)|
|23|ADC0 MISO1 |Mezz 2 (Analog)|
|24|ADC1 SCK1  |Mezz 2 (Analog)|
|25|ADC2       |Mezz 2 (Analog)|
|26|ADC3       |Mezz 2 (Analog)|
|27|ADC4 SDA   |Mezz 2 (Analog)|
|28|ADC5 SCL   |Mezz 2 (Analog)|
|29|Reset||
|30|RXD PWM    |Communication|
|31|TXD PWM    |Communication|
|32|PWM +      |Mezz 1 (PWM)|

_+ : d'autre fonction sont disponibles mais pas utilisées_

_les interruptions ne sont pas notées dans les fonctions_

## Mécanique

Largeur 60, Hauteur 90 à définir
4 trous pour vis M3 avec un entraxe de 30 en largeur, à 10 du bord suppérieur et à 20 du bord inférieur.

# Mezanine

1 connecteur pin header male 1x10
1x GND, 1x 5V, 8x logique,  
1 connecteur pin socket femelle 1x10  
1x GND, 1x 12V, 8x puissance,

## Types

* OUTPUT

  * ULN2803
  * MIC2981
  * Mosfet
  * Optocoupleur
  * Pont (5V direct)
* INPUT

  * Pont diviseur 12/24V
  * Pont (5V direct)
  * Optocoupleur (autre sens)
* IO

  * Loconet (nécessite ICP pin)
  * Carte SD + RTC (nécessite SPI ou I2C)
  * RS485 (nécessite Software serial)
  * FRAM (nécessite SPI ou I2C)

## communication (idée)

Commandes envoyée ddans le Bus

|Champs|Taille \[bit]|
|-|-|
|Contrôle|8|
|Adresse noeud|8|
|Adresse registre|8|
|longeur donnée|8|
|Donnée|8 - 2048|

Champ contrôles

|7  - 4|3 - 2|1 - 0|
|-|-|-|
|version protocole (idée)|destinations spéciales|commande|

destinations spéciales :

* Normales
* Prochain noeud
* Broadcast (tous)
* Adresses allongées (idée...)

commandes :

* Lire
* Ecrire
* Annoncer

Adresse de noeud spéciales
0x00 : maître

avoir un groupe de potentiellement 127 ou 256 "registre" qui peuvent être lu ou écrit

|premier|nombre|fonciton|
|-|-|-|
|0|16|paramètre généraux de la carte (type, adresse,...)|
|16|16|paramètres spécifiques au type de carte|
|32|16|typiquement, un registre par pin pour analog ou pour PWM|
|48|16|typiquement, un registre par pin pour analog ou pour PWM|
|64|64 ou 192|divers|



# Carte Principale


### Tutoriel Python

#### Installer un IDE

**Mu**

Le site officiel de Mu : [https://codewith.mu/](https://codewith.mu/)

Mu est un éditeur de code Python spécialement conçu pour les débutants. La façon la plus simple d’obtenir Mu est de télécharger l’installateur officiel pour Windows ou Mac OS X. La version recommandée est Mu 1.0-beta 2.

**Étape 1 - Déterminer la version et télécharger l'installateur Mu**

Vérifiez si votre ordinateur utilise Windows ou Mac OS X. Ouvrez l'Explorateur, cliquez sur "Ce PC", puis sélectionnez Propriétés pour connaître si votre système Windows est en 32 bits ou 64 bits.

Ouvrez le lien : [https://codewith.mu/en/download](https://codewith.mu/en/download) pour télécharger la version correspondante de Mu.

**Étape 2 - Exécuter l’installateur :**

Trouvez l'installateur que vous venez de télécharger (il peut se trouver dans votre dossier Téléchargements) et double-cliquez pour ouvrir le fichier installateur.

Pour Mac OS X : [https://codewith.mu/en/howto/1.1/install_macos](https://codewith.mu/en/howto/1.1/install_macos)

**Étape 3 - Protocole :**

Acceptez la licence, puis cliquez sur Installer.

**Étape 4 - Installation :**

L'installation de Mu sur votre ordinateur prend quelques secondes.

**Étape 5 - Terminer :**

Cliquez sur "Terminer".

**Étape 6 - Démarrer Mu :**

Vous pouvez lancer Mu en cliquant sur l'icône dans le menu Démarrer ou en tapant Mu dans la barre de recherche.

---

### Installer le pilote

Micro:bit peut être utilisé sans installer de pilote. Si votre ordinateur ne reconnaît pas la carte micro:bit, vous devrez installer le pilote micro:bit. Le fichier de pilote micro:bit et le manuel d’installation du pilote micro:bit se trouvent dans le dossier "Micro:bit Driver Download and Installation".

Installez le pilote en suivant les instructions dans le manuel d'installation de pilote dans le dossier approprié.

---

### Configuration du compilateur et introduction à la barre d'outils

**Configurer le mode en "micro:bit"**

Ouvrez Mu, cliquez sur le bouton Mode dans la barre de menu et sélectionnez "BBC micro:bit", puis cliquez sur "OK".

Plus d'instructions pour utiliser Mu : [https://codewith.mu/en/tutorials/](https://codewith.mu/en/tutorials/)

---

### Installer le fichier de bibliothèque

Avant d'importer la bibliothèque, vous devez télécharger un code `.py` sur le micro:bit. Par exemple, pour le module RGB, ouvrez le fichier "code_1.py" dans le didacticiel.

Importez le fichier "keyes_MiniCar.py" dans le dossier "mu_code" dans votre répertoire utilisateur. Branchez ensuite le micro:bit à votre ordinateur et cliquez sur le bouton "Fichiers" dans Mu pour faire glisser le fichier de bibliothèque "keyes_MiniCar.py" sur le micro:bit.

Cliquez sur "Vérifier" pour tester le code. Si une ligne apparaît avec un curseur ou un soulignement, cela signifie qu'il y a une erreur.

---

### Télécharger du code vers le Micro:bit

Connectez la carte micro:bit à l'ordinateur via le câble micro USB. Cliquez sur "Flash" pour télécharger le code sur la micro:bit.

En cas d’erreur après avoir cliqué sur "Flash", vérifiez si le fichier de bibliothèque a bien été importé dans la micro:bit. Vous pouvez vérifier le code en cliquant sur "Vérifier". Si Mu n'indique aucun problème, votre code est prêt.

---

## Projets de base Microbit

### Projet 1 : Battement de cœur

**Description**

Ce projet utilise les modules de capteur et la matrice LED de la carte micro:bit pour afficher un motif de battement de cœur.

**Code**

```python
from microbit import *

while True:
    display.show(Image.HEART)
    sleep(500)
    display.show(Image.HEART_SMALL)
    sleep(500)
```

### Projet 2 : Allumer une LED

La carte micro:bit contient une matrice de 5x5 diodes, contrôlées en définissant des points de coordonnées (0,0) pour allumer une LED spécifique.

**Code**

```python
from microbit import *

val1 = Image("09000:""00000:""00000:""00000:""00000:")
val2 = Image("00000:""00000:""00000:""00000:""00090:")
val3 = Image("00000:""00000:""00000:""00000:""00000:")

while True:
    display.show(val1)
    sleep(500)
    display.show(val3)
    sleep(500)
    display.show(val2)
    sleep(500)
    display.show(val3)
    sleep(500)
```

---

### Projet 3 : Matrice LED 5x5

Utilisez la matrice LED de la carte pour afficher des motifs, des nombres et des chaînes de caractères.

**Code**

```python
from microbit import *

val = Image("00900:""00900:""90909:""09990:""00900")
display.show(val)
```

---

### Projet 4 : Boutons programmables

La carte micro:bit dispose de deux boutons programmables. Ce projet affiche "A", "B" ou "AB" lorsque les boutons sont pressés.

**Code**

```python
from microbit import *

while True:
    if button_a.is_pressed():
        display.show("A")
    elif button_a.is_pressed() and button_b.is_pressed():
        display.scroll("AB")
    elif button_b.is_pressed():
        display.show("B")
```

---

### Projet 5 : Mesure de la température

La micro:bit utilise le capteur de température intégré au microcontrôleur pour mesurer la température ambiante.

**Code**

```python
from microbit import *
while True:
    temperature = temperature()
    print("Température:", temperature, "°C")
    sleep(500)
```

---

### Projet 6 : Boussole

Ce projet utilise la boussole intégrée pour afficher la direction. Vous devez calibrer la boussole en tournant la carte micro:bit jusqu'à ce que toutes les LED soient allumées.

**Code**

```python
from microbit import *
compass.calibrate()

while True:
    if button_a.is_pressed():
        display.scroll(compass.heading())
```

---

### Projet 7 : Accéléromètre

Utilisez l'accéléromètre intégré pour détecter les mouvements et les gestes, tels que "shake", "up", "down", etc.

**Code**

```python
from microbit import *

while True:
    gesture = accelerometer.current_gesture()

    if gesture == "shake":
        display.show("1")
    if gesture == "up":
        display.show("2")
    if gesture == "down":
        display.show("3")
    if gesture == "face up":
        display.show("4")
    if gesture == "face down":
        display.show("5")
    if gesture == "left":
        display.show("6")
    if gesture == "right":
        display.show("7")
    if gesture == "freefall":
        display.show("8")
```

---

### Projet 8 : Détecter l'intensité lumineuse

La matrice LED de la carte peut détecter l’intensité lumineuse environnante.

**Code**

```python
from microbit import *

while True:
    light_intensity = display.read_light_level()
    print("Intensité lumineuse :", light_intensity)
    sleep(100)
```

---

### Projet 9 : Haut-parleur

La carte micro:bit dispose d'un haut-parleur intégré qui permet de jouer divers sons.

**Code**

```python
from microbit import *
import audio

display.show(Image.MUSIC_QUAVER)

while True:
    audio.play(Sound.GIGGLE)
    sleep(1000)
    audio.play(Sound.HAPPY)
    sleep(1000)
    audio.play(Sound.HELLO)
    sleep(1000)
    audio.play(Sound.YAWN)
    sleep(1000)
```

---

### Projet 10 : Logo tactile

Le logo doré de la micro:bit agit comme un capteur tactile. Ce projet affiche le temps écoulé lorsque le logo est touché.

**Code**

```python
from microbit import *
time = 0
start = 0
running = False

while True:
    if button_a.was_pressed():
        running = True
        start = running_time()
    if button_b.was_pressed():
        if running:
            time += running_time() - start
        running = False
    if pin_logo.is_touched():
        if not running:
            display.scroll(int(time/1000))

    if running:
        display.show(Image.HEART)
        sleep(300)
        display.show(Image.HEART_SMALL)
        sleep(300)
    else:
        display.show(Image.ASLEEP)
```

---

### Projet 11 : Microphone

1. **Description**

La carte micro:bit est équipée d'un microphone intégré permettant de mesurer le niveau sonore ambiant. Lorsque vous applaudissez, l'indicateur LED sur la carte s'allume. Cela permet de mesurer l'intensité du son, et vous pouvez créer des effets lumineux qui s'accordent avec le son ambiant.

2. **Composants nécessaires**

- Micro:bit * 1
- Câble USB * 1

3. **Code de Test**

Code 1 :

```python
from microbit import *

while True:
    if microphone.current_event() == SoundEvent.LOUD:
        display.show(Image.HEART)
        sleep(200)
    if microphone.current_event() == SoundEvent.QUIET:
        display.show(Image.HEART_SMALL)
```

**Résultat du test** : Téléchargez le code sur la carte micro:bit et maintenez le câble USB connecté. Lorsque vous applaudissez, la matrice LED affiche un cœur. Lorsque l'environnement est silencieux, un petit cœur s'affiche.

Code 2 :

```python
from microbit import *
maxSound = 0
lights = Image("11111:"
              "11111:"
              "11111:"
              "11111:"
              "11111")
soundLevel = microphone.sound_level()
sleep(200)

while True:
    if button_a.is_pressed():
        display.scroll(maxSound)
    else:
        soundLevel = microphone.sound_level()
        display.show(lights * soundLevel)
        if soundLevel > maxSound:
            maxSound = soundLevel
```

**Résultat du test** : En appuyant sur le bouton A, la matrice LED affiche le niveau sonore maximum détecté. Lorsque vous applaudissez, plus le son est fort, plus les 25 LED brillent intensément.

---

### Projet 12 : Communication sans fil Bluetooth

1. **Description**

La micro:bit intègre un module Bluetooth basse consommation pour envoyer et recevoir des données. Cependant, elle dispose de seulement 16k de RAM. Le Bluetooth consomme 12k de RAM, ne laissant pas assez d'espace pour exécuter MicroPython et Bluetooth simultanément. 

**Lien** : [Documentation Bluetooth micro:bit](https://microbit-micropython.readthedocs.io/en/latest/ble.html)

**Note** : Avant d’installer la micro:bit sur la carte d’extension, déconnectez le câble USB et éteignez la carte pour éviter tout risque d’endommagement. 

---

### Projet 13 : Module RGB

1. **Description**

Le mode couleur RGB (Rouge, Vert, Bleu) est un standard permettant de créer diverses couleurs en ajustant les niveaux de chaque couleur primaire. Dans ce projet, vous utiliserez deux LEDs RGB pour afficher des couleurs différentes et créer des transitions colorées.

2. **Préparation**

- Insérez correctement la micro:bit dans la carte d'extension.
- Connectez la batterie à la carte d'extension.
- Activez l'interrupteur d'alimentation.
- Connectez la micro:bit à l'ordinateur via un câble USB.
- Ouvrez la version Web de Makecode et ajoutez la bibliothèque d’extension Mini car.

3. **Code de Test**

Code 1 :

```python
from microbit import *
from keyes_MiniCar import *
minicar = MiniCar()

while True:
    minicar.left_red(0)
    minicar.right_red(0)
    sleep(1000)
    minicar.led_off()
    minicar.left_green(0)
    minicar.right_green(0)
    sleep(1000)
    minicar.led_off()
    minicar.left_blue(0)
    minicar.right_blue(0)
    sleep(1000)
    minicar.led_off()
```

**Résultat du test** : Les LED RGB alterneront chaque seconde entre rouge, vert et bleu.

---

### Projet 14 : Conduite du moteur

1. **Description**

Le robot est équipé de deux moteurs à engrenages DC permettant de fournir un couple plus élevé à une vitesse réduite. Le contrôleur utilise le bus I2C pour envoyer des commandes au moteur, optimisant ainsi les ports d'entrée/sortie de la micro:bit.

2. **Code de Test**

```python
from microbit import *
from keyes_MiniCar import *
minicar = MiniCar()

while True:
    # Avancer
    minicar.Motor_L(1, 70)
    minicar.Motor_R(1, 70)
    sleep(1000)
    # Reculer
    minicar.Motor_L(0, 70)
    minicar.Motor_R(0, 70)
    sleep(1000)
    # Tourner à gauche
    minicar.Motor_L(0, 70)
    minicar.Motor_R(1, 70)
    sleep(1000)
    # Tourner à droite
    minicar.Motor_L(1, 70)
    minicar.Motor_R(0, 70)
    sleep(1000)
    minicar.Motor_stop()
    sleep(1000)
```

---

### Projet 15 : Suivi de la lumière pour le robot

1. **Description**

Le robot peut suivre une source lumineuse grâce aux photo-résistances, qui détectent l’intensité lumineuse. Plus la lumière est intense, plus la résistance diminue, augmentant ainsi la tension d’entrée.

2. **Code de Test**

Code 1 :

```python
from microbit import *

while True:
    LDR_L = pin1.read_analog()
    LDR_R = pin0.read_analog()
    print("LDR_L:", LDR_L)
    print("LDR_R:", LDR_R)
    sleep(1000)
```

Code 2 :

```python
from microbit import *
from keyes_MiniCar import *
minicar = MiniCar()

while True:
    LDR_L = pin1.read_analog()
    LDR_R = pin0.read_analog()
    if LDR_L > 650 and LDR_R > 650:
        minicar.Motor_L(1, 70)
        minicar.Motor_R(1, 70)
    elif LDR_L > 650 and LDR_R <= 650:
        minicar.Motor_L(0, 70)
        minicar.Motor_R(1, 70)
    elif LDR_L <= 650 and LDR_R > 650:
        minicar.Motor_L(1, 70)
        minicar.Motor_R(0, 70)
    else:
        minicar.Motor_stop()
```

---

### Projet 16 : Suivi de ligne pour le robot

1. **Description**

Le robot utilise des capteurs infrarouges pour suivre une ligne noire sur fond blanc. Ces capteurs détectent la différence de couleur et signalent au microcontrôleur si le robot se trouve sur la ligne ou hors ligne.

2. **Code de Test**

```python
from microbit import *
from keyes_MiniCar import *
minicar = MiniCar()
pin12.set_pull(pin12.PULL_UP)
pin13.set_pull(pin13.PULL_UP)
sensor_L = 0
sensor_R = 0

while True:
    sensor_L = pin13.read_digital()
    sensor_R = pin12.read_digital()
    print("sensor_L:", sensor_L)
    print("sensor_R:", sensor_R)
    if sensor_L == 1 and sensor_R == 1:
        minicar.Motor_L(1, 100)
        minicar.Motor_R(1, 100)
    elif sensor_L == 0 and sensor_R == 1:
        minicar.Motor_L(1, 100)
        minicar.Motor_R(0, 100)
    elif sensor_L == 1 and sensor_R == 0:
        minicar.Motor_L(0, 100)
        minicar.Motor_R(1, 100)
    else:
        minicar.Motor_stop()
```

---

### Projet 17 : Suivi et évitement d’obstacle par ultrason

1. **Description**

Le capteur à ultrasons utilise des ondes sonores pour mesurer la distance à un objet. Il envoie des signaux ultrasoniques qui, une fois réfléchis par un obstacle, permettent de calculer la distance.

2. **Code de Test**

Code pour suivi d'obstacle :

```python
from microbit import *
from keyes_MiniCar import *
minicar = MiniCar()

while True:
    distance = 0
    distance = minicar.get_distance()
    if distance >= 10 and distance <= 30:
        minicar.Motor_L(1, 100)
        minicar.Motor_R(1, 100)
        sleep(50)
    elif distance <= 6:
        minicar.Motor_L(0, 100)
        minicar.Motor_R(0, 100)
        sleep(50)
    elif (distance > 6 and distance < 10) or distance > 30:
        minicar.Motor_stop()
        sleep(50)
```

**Code pour évitement d'obstacle :**

```python
from microbit import *
from keyes_MiniCar import *
minicar = MiniCar()

while True:
    distance = 0
    distance = minicar.get_distance()
    if distance > 10:
        minicar.Motor_L(1, 70)
        minicar.Motor_R(1, 70)
        sleep(50)
    else:
        minicar.Motor_L(0, 70)
        minicar.Motor_R(0, 70)
```
Résultat du test : Évitement d'obstacle par ultrason

Après avoir téléchargé le code et activé l'interrupteur d'alimentation à l'arrière de la voiture, le comportement suivant est observé :

    Si la distance entre le capteur ultrason et un obstacle est supérieure à 10 cm, la voiture avancera tout droit.
    Si un obstacle est détecté à moins de 10 cm, la voiture effectuera un virage à gauche pour éviter la collision.

Ce comportement permet à la voiture d'éviter les obstacles en ajustant sa trajectoire lorsqu'un objet se trouve trop près.

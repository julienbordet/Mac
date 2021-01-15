# Le processus de boot sur Apple Silicon M1

## Le processus de boot sur Apple M1

<img src="../images/Mac Silicon - Boot overview.png" alt="Mac Silicon - Boot overview" style="zoom: 50%;" />

### Boot Rom

La première partie de démarrage des Apple basée sur Silicon M1 s'appuie sur deux composants

- Une **Flash NOR**, qui contient le code associé au première démarrage du système
- Un **SecureROM**, stockée sur la puce M1, qui charge la première étape du boot depuis la mémoire Flash, et l'exécute.

Cette première partie basée est chargée de récupérer le bootloader stocké sur le SSD (et donc d'y lire les informations du système de fichier APFS), de montrer le logo Apple et éventuellement des messages d'erreur. A ce stade, il n'y a pas la possibilité de monter des devices USB ou via le réseau.

### MacOS Bootloader / iBoot

Le boot loader est stockée sur le disque SSD, contrairement au firmware UEFI sur les machines Intel, où le firmware du bootloader est hébergée au sein d'une mémoire flash.

Au niveau du disque SSD, il est stocké sur le premier conteneur créé lors de l'installation de MacOS Big Sur, appelé `Apple_APFS_ISC`, où `ISC` signife *iBoot System Container*.

Il peut alors lancer plusieurs d'exploitations, donc 

- Mac Recovery Mode
- MacOS (et si besoin plusieurs versions de ce système)

### Recovery Mode

Recovery Mode est une instance de MacOS dédié au mode recovery. Il est stocké dans une partition dédiée, et permet, notamment, de changer des paramètres de sécurité ou encore d'obtenir une ligne de commande et d'accéder au réseau. En revanche, seules les applications signées par Apple peuvent être exécutée par le système.

Recovery Mode est activé en appuyant longuement sur le bouton "Power" d'une machine Apple Silicon.

### MacOS

Le système d'exploitation est stockée sur le disque SSD.

## Sources

- https://github.com/AsahiLinux/docs/wiki/M1-vs.-PC-Boot
- https://eclecticlight.co/2021/01/14/m1-macs-radically-change-boot-and-recovery/

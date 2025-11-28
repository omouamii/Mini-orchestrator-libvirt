# Mini orchestrator libvirt (GUI + C)

Ce projet est un **mini orchestrateur de machines virtuelles KVM/libvirt** :

- une bibliothèque C (`libvirt_helper.c`) qui encapsule les appels libvirt de base ;
- une interface Python/Tkinter (`gui_orchestrator.py`) qui fournit une **GUI** pour :
  - lister les VMs (locales ou distantes) ;
  - démarrer / arrêter / redémarrer une VM ;
  - sauvegarder / restaurer l’état d’une VM ;
  - créer une nouvelle VM (ISO, disque qcow2, réseau, BIOS/UEFI) ;
  - cloner une VM (via `virt-clone`) ;
  - migrer une VM à chaud vers un autre hyperviseur ;
  - ouvrir la console graphique (virt-viewer / virt-manager) ;
  - ouvrir une console texte (virsh console dans un xterm).

---

## 1. Arborescence du projet

```text
orchestrator/
├── c_lib
│   ├── libvirt_helper.c
│   ├── libvirt_helper.h
│   ├── libvirt_helper.o
│   ├── libvirt_helper.so
│   └── Makefile
└── python_interface
    ├── gui_orchestrator.py   # GUI principale (Tkinter)
    ├── known_vms.txt         # cache des VMs connues
    ├── libvirt_helper.so     # copie de la librairie C compilée
    ├── orcherstrator.py      # interface CLI simple (menu texte)
    └── test/                 # éventuels scripts/tests

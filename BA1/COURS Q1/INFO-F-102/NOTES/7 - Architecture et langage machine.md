# Architecture et langage machine

## Architecture et microarchitecture

| Notion | Point de vue |
| :--- | :--- |
| **Architecture** | Ce que le programme en langage machine peut utiliser : modèle mémoire, registres et types de données. |
| **Microarchitecture** | Comment le matériel réalise ces opérations : bus, ALU et micro-instructions. |

Exemple : `BIPUSH 8` est une instruction IJVM ; ses déplacements entre `SP`, `MAR`, `MDR` et `TOS` relèvent de la microarchitecture.

## Deux générations de processeurs

| | 6502 | Intel i486 |
| :--- | :--- | :--- |
| Apparition | 1975 | 1989 |
| Génération | 8 bits | 32 bits |
| Repère | Premiers ordinateurs personnels, dont l’Apple II. | PC de la fin des années 1980 et du début des années 1990. |

L’i486 permet des traitements plus complexes. **32 bits contre 8 bits ne signifie pas quatre fois plus puissant** : les performances dépendent aussi de la fréquence et de l’organisation interne.

## Modèle mémoire

**Taille d’une adresse ≠ taille d’une case.** L’adresse est le numéro de la case ; son contenu est la donnée.

### 6502

- **Adresses sur 16 bits** : 2¹⁶ = **65 536 cases**.
- **Une case = 1 octet** : espace adressable de **64 Kio**.
- `PC` contient une adresse : il doit donc faire **16 bits**, même si chaque case ne contient que 8 bits.

### i486 : mode réel

Le cours annonce deux modes et détaille ici le **mode réel**.

Une adresse est donnée par un **segment sur 16 bits** et un **décalage sur 16 bits** :

**Adresse = segment × 16 + décalage**

Multiplier le segment par 16 revient à le décaler de **4 bits vers la gauche**, puis on additionne le décalage.

Exemple en décimal : segment `100`, décalage `20` → adresse **1 620**.

L’adresse indique **où commencer**. La taille de l’accès ou les informations du programme indiquent combien d’octets lire ; le décalage n’est pas la longueur de la donnée.

## Registres

| | 6502 | i486 |
| :--- | :--- | :--- |
| Registres cités | `A`, `X`, `Y`, `SP`, `P` : **8 bits** | `EAX`, `EBX`, `ECX`, `EDX` : **32 bits** |
| Pointeur d’instruction | `PC` : **16 bits** | `EIP` : **32 bits** |

Sur le 6502 : `A` est l’accumulateur ; `X` et `Y` sont des index ; `SP` est le pointeur de pile ; `P` contient les indicateurs d’état. La liste des registres de l’i486 n’est pas complète ici.

## Types de données

Les types indiquent **comment les bits sont interprétés et manipulés** : booléens, entiers, nombres à virgule flottante ou caractères.

| | 6502 | i486 |
| :--- | :--- | :--- |
| Opérations logiques et entiers | Oui | Oui |
| Virgule flottante IEEE 754 | Pas d’instructions natives dédiées | Prise en charge avec l’unité flottante, notamment sur le 486DX. |

**Stocker une donnée ne signifie pas savoir calculer directement avec elle.** Le 6502 peut réaliser des calculs flottants par un programme qui les décompose en opérations plus simples.

ASCII représente les caractères : `01000001` peut être lu comme l’entier **65** ou le caractère **A**. Les deux processeurs peuvent manipuler ces octets ; ASCII n’est pas réservé à l’i486.

---

[← Les micro-instructions](6.3%20-%20Les%20micro-instructions.md)

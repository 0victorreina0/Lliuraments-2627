# Pràctica 1 – Característiques dels llenguatges de marques

## JocMark: un llenguatge de marques per descriure videojocs

**Mòdul:** LMSGI (Llenguatges de marques)  
**Curs:** 1r ASIX  
**Integrants del grup:** Victor Reina Martinez i Manuel Adrián Verástegui Noriega

Aquest document explica els continguts de la presentació de **JocMark**, un llenguatge de marques inventat per a aquesta pràctica. La idea és tenir un format senzill que ens permeti guardar informació sobre videojocs, com ara el nom, els personatges i els nivells.

## 1\. Què és un llenguatge de marques?

Un llenguatge de marques és una manera d'organitzar informació en un document de text utilitzant **etiquetes**. Les etiquetes ens ajuden a saber què representa cada dada i permeten que un programa pugui interpretar el document.

Els llenguatges de marques moderns tenen els seus antecedents en **SGML**. Dos exemples coneguts són:

- **HTML:** s'utilitza per estructurar el contingut de les pàgines web.  
- **XML:** s'utilitza per representar i intercanviar dades d'una manera organitzada.

A diferència d'un text normal, on només llegim paraules, en un llenguatge de marques també podem identificar l'estructura de la informació. Per exemple, podem indicar que un text és el nom d'un personatge o el nivell d'un videojoc.

## 2\. Què és JocMark?

**JocMark** és el llenguatge de marques que hem creat per a l'activitat. El nom ve de la combinació de *Joc* i *Mark* (marca).

L'objectiu és **descriure les dades d'un videojoc** en un fitxer de text pla. Podem guardar-hi:

- El nom i el gènere del videojoc.  
- Els personatges i algunes de les seves característiques.  
- Els nivells i la dificultat que tenen.  
- Metadades, com l'autor del fitxer i la versió.

D'aquesta manera, un programa podria llegir les dades i utilitzar-les per crear una fitxa del joc o un catàleg.

## 3\. Regles del llenguatge

Perquè tots els fitxers JocMark segueixin la mateixa estructura, hem definit unes regles bàsiques:

1. **S'escriu en text pla.** Podem crear el fitxer amb un editor senzill, com el Bloc de notes.  
2. **Utilitza etiquetes entre claudàtors.** Per exemple: `[JOC]`, `[PERSONATGE]`, `[NIVELL]` i `[META]`.  
3. **Els blocs de dades tenen inici i final.** Per exemple, un joc comença amb `[JOC ...]` i acaba amb `[/JOC]`. Els blocs de personatge i nivell també es tanquen.  
4. **Els atributs segueixen el format `clau="valor"`.** Així podem indicar el nom, la vida o la dificultat.  
5. **L'ordre és fix.** Primer posem les metadades amb `[META]` i després el bloc `[JOC]`, que conté els personatges i els nivells.

En el nostre exemple, `[META ...]` és una etiqueta amb les dades del fitxer i no necessita un bloc de contingut interior.

### Què representa cada etiqueta?

| Etiqueta | Funció |
| :---- | :---- |
| `[META]` | Indica informació general del fitxer, com l'autor i la versió. |
| `[JOC]` | Agrupa la informació d'un videojoc. |
| `[PERSONATGE]` | Descriu un personatge i els seus atributs. |
| `[NIVELL]` | Descriu un nivell i la seva dificultat. |

## 4\. Exemple d'un fitxer JocMark

Aquest és el mateix exemple que apareix a la presentació:

```
[META autor="Equip 1" versio="1.0"]
[JOC nom="Aventura del Bosc" genere="aventura"]
  [PERSONATGE nom="Lia" vida="100"][/PERSONATGE]
  [PERSONATGE nom="Roc" vida="80"][/PERSONATGE]
  [NIVELL nom="Bosc" dificultat="facil"][/NIVELL]
[/JOC]
```

### Explicació de l'exemple

- **`[META autor="Equip 1" versio="1.0"]`:** indica qui ha preparat el fitxer i quina versió és.  
- **`[JOC nom="Aventura del Bosc" genere="aventura"]`:** crea la fitxa d'un videojoc anomenat *Aventura del Bosc*, del gènere d'aventura.  
- **`[PERSONATGE nom="Lia" vida="100"]`:** defineix el personatge Lia, que té 100 punts de vida.  
- **`[PERSONATGE nom="Roc" vida="80"]`:** defineix el personatge Roc, que té 80 punts de vida.  
- **`[NIVELL nom="Bosc" dificultat="facil"]`:** afegeix un nivell anomenat Bosc amb dificultat fàcil.  
- **`[/JOC]`:** indica que s'ha acabat la informació d'aquest videojoc.

Les dades estan escrites com a text, però les etiquetes i els atributs permeten distingir cada element. Perquè un programa pugui llegir aquest format, caldria programar un lector que entengués les regles de JocMark.

## 5\. Classificació de JocMark

JocMark és un **llenguatge descriptiu o semàntic**.

Això significa que les etiquetes expliquen **què és cada dada**, però no indiquen com s'ha de mostrar a la pantalla. Per exemple:

- `[PERSONATGE]` ens diu que aquella informació correspon a un personatge.  
- `[NIVELL]` ens diu que aquella informació correspon a una fase del joc.

Per tant, **no és un llenguatge de presentació ni procedimental**: no defineix colors, mides, posicions ni els passos necessaris per mostrar els elements. El programa que llegeixi el fitxer serà l'encarregat de decidir com presentar-ne la informació.

## 6\. Cas d'ús en què seria útil

Un exemple seria el **catàleg de videojocs d'un estudi**. L'estudi podria tenir fitxers JocMark amb els personatges i els nivells de diferents jocs.

Aquest sistema podria ser útil perquè:

- Els fitxers es poden editar amb un editor de text senzill.  
- Un programa podria llegir les etiquetes i obtenir les dades automàticament.  
- Amb la informació llegida es podrien generar llistats i fitxes dels videojocs.

Així, en lloc de tenir la informació desordenada, totes les fitxes seguirien la mateixa estructura.

## 7\. Cas d'ús en què no seria adequat

JocMark **no seria una bona opció per crear directament un videojoc amb gràfics 3D en temps real**.

El nostre llenguatge serveix per descriure dades, com personatges, nivells i atributs, però **no serveix per executar les accions del joc, dibuixar gràfics o controlar-ne el funcionament**.

Per fer això necessitaríem un motor de videojocs i codi de programació. JocMark podria guardar part de la informació que utilitza el joc, però no substituiria el programa.

## 8\. Per què JocMark és un llenguatge de marques?

JocMark compleix els quatre requisits que demana l'activitat:

| Requisit | Com el compleix JocMark? |
| :---- | :---- |
| **1\. Text pla** | Tot el fitxer està escrit amb caràcters de text i es pot obrir amb un editor senzill. |
| **2\. Metadades** | L'etiqueta `[META]` guarda dades sobre el mateix fitxer, com l'autor i la versió. |
| **3\. Processament automàtic** | Les etiquetes i els atributs segueixen unes regles que un programa pot interpretar. |
| **4\. Interpretació de les dades** | Les marques indiquen si una dada és d'un joc, un personatge o un nivell. |

És important diferenciar **metadades** de la resta de dades: el nom d'un personatge descriu el contingut del joc, mentre que l'autor i la versió descriuen el fitxer que guarda aquesta informació.

## 9\. Conclusió

Amb aquesta pràctica hem creat JocMark per entendre millor com funcionen els llenguatges de marques. Hem vist que no cal crear un llenguatge molt complicat per poder organitzar dades: amb etiquetes, atributs i unes regles clares ja podem definir un format propi.

JocMark no crea videojocs per si sol, però sí que pot **guardar i organitzar informació sobre videojocs** d'una manera que tant les persones com un programa preparat per llegir-lo puguin entendre.

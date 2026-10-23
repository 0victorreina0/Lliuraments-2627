## Entitat de Personatges

## Explicació

Primer he creat l'entitat Personatges, que representa els personatges del videojoc. He afegit el DNI com a clau primària i els atributs corresponents.

## Codi


erDiagram
    Personatges {
        string DNI PK
        string Nom "NOT NULL"
        string Cognom
        int Vida
        int Forca
        int Agilitat
        int Carisma
    }

## Diagrama entero

```mermaid
erDiagram
    Personatges{
        string DNI PK
        string Nom "NOT NULL"
        string Cognom
        int Vida
        int Força
        int Agilitat
        int Carisma
    }

    Mascota{
        string Num.Chip PK
        string Nom "NOT NULL"
        int Motxilla
    }

    Enemic{
        string Codi PK
        string Nom "NOT NULL"
        string Tipus "NOT NULL"
        int Nivell "NOT NULL"
        int Vida 
        int Força 
        int Agilitat
        int Carisma  
    }

    Habilitat{
        string Codi PK
        string Nom "NOT NULL"
        int Cost
        int Dany
        float Cooldown
        string Tipus "NOT NULL"
    }

    Item{
        string Codi PK
        string Nom "NOT NULL"
        string Equipable
        string Comerciable
        string Tipus "NOT NULL"
        int Pes "NOT NULL"
        string Qualitat "NOT NULL"
        int MesuraX "NOT NULL"
        int MesuraY "NOT NULL"
        int MesuraZ "NOT NULL"
        
    }
    Personatges || -- || Mascota : Acompanya
    Personatges }o -- o{ Enemic : Enfrenta
    Personatges }o -- o{ Habilitat : Poseeix
    Personatges }o -- o{ Item : Equipa
    Habilitat }o -- o{ Enemic : Enfrenta
    Habilitat }o -- o{ Habilitat : Combina_amb
    Mascota }o -- o{ Item : Carrega
```

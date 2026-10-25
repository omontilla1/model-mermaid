erDiagram
    Personatge {
        string DNI
        string Nom
        string Cognom
        int Vida
        int Forca
        int Agilitat
        int Carisma
        int Nivell
        int Experiencia
    }

    Item {
        int ID_Item
        string Nom
        string Tipus
        float Pes
        string Qualitat
        float Preu
    }

    Arma {
        int Dany
        int Abast
        string Tipus_Dany
    }

    Objecte {
        string Descripcio
        boolean Consumible
    }

    Habilitat {
        int ID_Habilitat
        string Nom
        string Tipus
        int Dany
        int Cost
        int Cooldown
        string Descripcio
    }

    Subhabilitat {
        int ID_Subhabilitat
        string Nom
        string Millora
        int Valor_Afegit
    }

    Enemic {
        int ID_Enemic
        string Nom
        string Tipus
        int Nivell
        int Vida
    }

    Boti {
        int ID_Boti
        float Probabilitat
        int Quantitat_Min
        int Quantitat_Max
    }

    Mascota {
        int ID_Mascota
        string Nom
        string Tipus
        int Nivell
        string Habilitat_Especial
    }

    InventariMascota {
        int ID_Item
        int Quantitat
    }

    Personatge ||--o{ Item : Posseeix
    Personatge o|--o| Item : Equipa
    Personatge ||--o{ Habilitat : Apren
    Personatge }o--o{ Enemic : Enfronta
    Enemic ||--o{ Boti : Te
    Mascota ||--o{ InventariMascota : Carrega
    Habilitat ||--o{ Subhabilitat : Especialitza
    Habilitat }o--o{ Mascota : Acompanya

    Item ||--o| Arma : Es
    Item ||--o| Objecte : Es

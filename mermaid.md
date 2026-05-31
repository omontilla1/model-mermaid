```text
class Personatge {

  +DNI : string
  +Nom : string
  +Cognom : string
  +Vida : int
  +Forca : int
  +Agilitat : int
  +Carisma : int
  +Nivell : int
  +Experiencia : int
}

class Item {

  +ID_Item : int
  +Nom : string
  +Tipus : string
  +Pes : float
  +Qualitat : string
  +Preu : float
}

class Arma {

  +Dany : int
  +Abast : int
  +Tipus_Dany : string
}

class Objecte {

  +Descripcio : string
  +Consumible : boolean
}

class Habilitat {

  +ID_Habilitat : int
  +Nom : string
  +Tipus : string
  +Dany : int
  +Cost : int
  +Cooldown : int
  +Descripcio : string
}

class Subhabilitat {

  +ID_Subhabilitat : int
  +Nom : string
  +Millora : string
  +Valor_Afegit : int
}

class Enemic {

  +ID_Enemic : int
  +Nom : string
  +Tipus : string
  +Nivell : int
  +Vida : int
}

class Boti {

  +ID_Boti : int
  +Probabilitat : float
  +Quantitat_Min : int
  +Quantitat_Max : int
}

class Mascota {

  +ID_Mascota : int
  +Nom : string
  +Tipus : string
  +Nivell : int
  +Habilitat_Especial : string
}

class InventariMascota {

  +ID_Item : int
  +Quantitat : int
}

Personatge "1" --> "N" Item : Posseeix
Personatge "1" --> "0..1" Item : Equipa
Personatge "1" --> "N" Habilitat : Apren
Personatge "M" --> "N" Enemic : Enfronta

Enemic "1" --> "N" Boti : Te

Mascota "1" --> "N" InventariMascota : Carrega

Habilitat "1" --> "N" Subhabilitat : Especialitza

Habilitat "1" --> "0..N" Mascota : Acompanya

Item <|-- Arma
Item <|-- Objecte


# Explicación del modelo conceptual

## Personatge
Representa al jugador principal o personaje del videojuego.

**Atributos:**
DNI, Nom, Cognom, Vida, Força, Agilitat, Carisma, Nivell, Experiencia

**Relaciones:**
- Posee muchos objetos/items  
- Puede equipar un item  
- Aprende habilidades  
- Se enfrenta a enemigos  

---

## Item
Representa los objetos generales del videojuego.

**Atributos:**
ID_Item, Nom, Tipus, Pes, Qualitat, Preu

**Subclases:**
- Arma  
- Objecte  

---

## Habilitat
Representa habilidades que usan personajes y mascotas.

**Atributos:**
ID_Habilitat, Nom, Tipus, Dany, Cost, Cooldown, Descripcio

**Relaciones:**
- Un personaje aprende habilidades  
- Puede especializarse en subhabilidades  
- Algunas acompañan mascotas  

---

## Subhabilitat
Mejoras o evoluciones de habilidades.

**Atributos:**
ID_Subhabilitat, Nom, Millora, Valor_Afegit

---

## Enemic
Representa enemigos del juego.

**Atributos:**
ID_Enemic, Nom, Tipus, Nivell, Vida

**Relaciones:**
- Se enfrenta a personajes  
- Puede soltar botines  

---

## Boti
Representa recompensas obtenidas al derrotar enemigos.

**Atributos:**
ID_Boti, Probabilitat, Quantitat_Min, Quantitat_Max

---

## Mascota
Compañeros o criaturas que ayudan al jugador.

**Atributos:**
ID_Mascota, Nom, Tipus, Nivell, Habilitat_Especial

**Relaciones:**
- Puede cargar inventario  
- Puede acompañar habilidades  

---

## InventariMascota
Inventario transportado por la mascota.

**Atributos:**
ID_Item, Quantitat

---

## Relaciones y cardinalidades
- Personatge → Item (1:N): Un personaje puede poseer muchos items  
- Personatge → Item (0..1): Puede equipar un item  
- Personatge → Habilitat (1:N): Aprende habilidades  
- Personatge ↔ Enemic (M:N): Se enfrenta a enemigos  
- Enemic → Boti (1:N): Puede soltar botines  
- Mascota → InventariMascota (1:N): Puede cargar objetos  
- Habilitat → Subhabilitat (1:N): Tiene mejoras  
- Habilitat → Mascota (0..N): Puede acompañar mascotas  

```

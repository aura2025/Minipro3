# 🐉 Sistema de Combate RPG - Dragon Quest VIII

## Miniproyecto 3

  

## Descripción del Proyecto

  

Este proyecto es una simulación de combate por turnos inspirada en el clásico RPG **Dragon Quest VIII**. El sistema permite enfrentar a un grupo de cuatro héroes contra cuatro monstruos en batallas estratégicas con una arquitectura MVC (Modelo-Vista-Controlador).

  

El juego implementa un sistema de combate con:

  

-  **Arquitectura MVC** separando lógica, presentación y control

-  **Doble interfaz**: Terminal y GUI (Swing)

-  **Sistema de turnos** basado en velocidad

-  **Estados alterados** (veneno, aturdimiento, congelación, debilitamiento)

-  **Sistema de items y buffs**

-  **Cuatro armas diferentes** con efectos únicos

-  **Tres tipos de enemigos** con comportamiento IA diferenciado

  

----------

  

## Integrantes del Grupo

-   Valentina Valencia - 202459626
-   Aura Maria Peláez - 202459422
-   Juan Felipe Aristizabal - 202459364
  

----------

  

## Características Principales

  

### 1. **Arquitectura MVC**

  

El proyecto implementa una separación clara de responsabilidades:

  

-  **Modelo**: Lógica de negocio, personajes, combate, inventario

-  **Vista**: Dos implementaciones (Terminal y GUI)

-  **Controlador**: Gestión de flujo de batalla y turnos

  

### 2. **Interfaz Dual**

  

#### Vista Terminal

- Interfaz de consola con ASCII art

- Diseño limpio con bordes y separadores

- Menús numerados intuitivos

- Feedback detallado de acciones

  

#### Vista GUI (Swing)

- Diseño inspirado en RPGs clásicos

- Paneles diferenciados para héroes y enemigos

- Sistema de colores temático (verde para héroes, rojo para enemigos)

- Log de combate en tiempo real

- Visualización de estadísticas (HP, MP, ATK, DEF, VEL)

- Actualización dinámica en tiempo real

  

### 3. **Sistema de Combate por Turnos**

  

- Orden de turnos determinado por velocidad

- Recálculo de orden cada ronda

- Acciones disponibles:

-  **Atacar**: Ataque básico según el arma equipada

-  **Poder Especial**: Habilidades únicas que consumen 50 MP

-  **Defender**: Aumenta defensa temporalmente (+50%)

-  **Usar Ítem**: Acceso al inventario completo

  

### 4. **Sistema de Armas**

  

Cada héroe tiene un arma única con efectos especiales:

  

| Arma | Portador | Efecto Principal | Efectos Secundarios |

|------|----------|------------------|---------------------|

| **Espada** | Heroe | +10% daño | - |

| **Hacha** | Yangus | +30% daño | -10 velocidad propia, -10 defensa enemiga |

| **Bastón** | Jessica | Daño normal | +20 MP por ataque, -5 defensa propia |

| **Arco** | Angelo | Daño normal | +5 velocidad propia, -5 velocidad enemiga |

  

### 5. **Poderes Especiales**

  

Cada héroe posee una habilidad única que cuesta 50 MP:

  

| Poder | Héroe | Efecto | Duración |

|-------|-------|--------|----------|

| **Envenenar** | Heroe | 15 de daño por turno | 3 turnos |

| **Congelar** | Jessica | El enemigo pierde su turno | 1 turno |

| **Debilitar** | Angelo | -10 de ataque | 3 turnos |

| **Aturdir** | Yangus | El enemigo pierde su turno | 1 turno |

  

**Importante**: Los poderes especiales solo afectan a monstruos, no a personajes jugables.

  

### 6. **Sistema de Estados Alterados**

  

-  **Normal**: Sin efectos

-  **Defendiendo**: +50% defensa temporal

-  **Envenenado**: -15 HP por turno (3 turnos)

-  **Aturdido**: Pierde 1 turno

-  **Congelado**: Pierde 1 turno

-  **Debilitado**: -10 ataque (3 turnos)

-  **Muerto**: Fuera de combate

  

### 7. **Sistema de Inventario**

  

El inventario incluye diversos tipos de ítems:

  

#### Pociones de Curación

-  **Hierba curativa** (x5): Restaura 50 HP

-  **Mega Hierba** (x2): Restaura 200 HP

  

#### Recuperación de MP

-  **Recuperador de MP** (x3): Restaura 30 MP

  

#### Curadores de Estado

-  **Antídoto** (x3): Cura envenenamiento

-  **Estimulante** (x2): Cura aturdimiento y congelación

-  **Panacea** (x1): Cura todos los estados alterados

  

#### Buffs Temporales (3 turnos)

-  **Poción de fuerza** (x2): +20 ataque

-  **Poción de defensa** (x2): +20 defensa

-  **Poción de velocidad** (x2): +15 velocidad

  

### 8. **Tipos de Monstruos**

  

Los enemigos tienen tres comportamientos diferentes controlados por IA:

  

| Tipo | Comportamiento | Características |

|------|----------------|-----------------|

| **Agresivo** | Ataca constantemente | +20% ataque, 5% probabilidad de defender |

| **Defensivo** | Defiende frecuentemente | Reduce defensa enemiga, 40% probabilidad de defender cuando HP<100, +80% defensa al defender |

| **Balanceado** | Equilibrado | Reduce velocidad enemiga, 20% probabilidad de defender cuando HP<80, +50% defensa al defender |

  

----------

  

## Arquitectura del Proyecto

  

### Estructura de Clases

  

```

Sistema de Combate RPG (MVC)

│

├── App.java (Punto de entrada)

│

├──  Modelo (Lógica de negocio)

│ ├── Personaje.java (Interface)

│ ├── PersonajeJugable.java (Héroes controlables)

│ ├── Monstruo.java (Enemigos con IA)

│ ├── Inventario.java (Sistema de items)

│ ├── Buff.java (Sistema de buffs temporales)

│ ├── EstadoEfecto.java (Duración de estados)

│ └── Enums:

│ ├── Arma.java

│ ├── Estado.java

│ ├── Item.java

│ ├── PoderEspecial.java

│ ├── TipoBuff.java

│ ├── TipoItem.java

│ ├── TipoMonstruo.java

│ └── TipoPersonaje.java

│

├──  Vista (Presentación)

│ ├── Vista.java (Interface de vista)

│ ├── VistaTerminal.java (Interfaz de consola)

│ └── VistaGui.java (Interfaz gráfica Swing)

│

└──  Controlador (Flujo de juego)

└── Controlador.java (Gestión de batalla y turnos)

```

  



  

### Patrones de Diseño Implementados

  

1.  **MVC (Modelo-Vista-Controlador)**: Separación completa de responsabilidades

2.  **Interface Personaje**: Define el contrato para todos los combatientes

3.  **Strategy Pattern**: Diferentes comportamientos de IA para monstruos

4.  **Enumeraciones**: Organización de constantes y tipos

5.  **Composición**: Los personajes tienen armas, items y buffs

  

----------

 

### Cambiar entre Vistas

  

En el archivo `App.java`, puedes cambiar entre las dos vistas:

  

```java

// Vista Terminal (por defecto)

VistaTerminal  vista = new  VistaTerminal();

  

// Vista GUI

// VistaGui vista = new VistaGui();

  

Controlador  controlador = new  Controlador(vista);

controlador.iniciar();

```

  

----------

  

## Cómo Jugar

  

### Personajes

  

#### Héroes

1.  **Heroe** - HP: 500, MP: 200, Arma: Espada, Poder: Envenenar

2.  **Jessica** - HP: 400, MP: 250, Arma: Bastón, Poder: Congelar

3.  **Angelo** - HP: 450, MP: 180, Arma: Arco, Poder: Debilitar

4.  **Yangus** - HP: 600, MP: 150, Arma: Hacha, Poder: Aturdir

  

#### Enemigos

1.  **Slime Gigante** - Tipo: Agresivo

2.  **Golem de Piedra** - Tipo: Defensivo

3.  **Caballero Oscuro** - Tipo: Balanceado

4.  **Dragón Menor** - Tipo: Defensivo

  

### Flujo de Batalla

  

1.  **Inicio**: Se muestra el estado inicial de todos los personajes

2.  **Orden de turnos**: Se determina por velocidad (mayor a menor)

3.  **Turno del héroe**: El jugador elige una acción

4.  **Turno del monstruo**: La IA decide automáticamente

5.  **Actualización**: Se procesan efectos de veneno, buffs y estados

6.  **Repetir**: Hasta que un bando sea derrotado

  

### Acciones del Jugador

  

En cada turno puedes elegir:

  

#### Atacar

- Selecciona un enemigo vivo

- El daño depende de tu arma y estadísticas

- Fórmula: `max(ataque * modificador_arma - defensa_enemiga, 0)`

  

#### Poder Especial

- Requiere 50 MP

- Selecciona un enemigo vivo

- Aplica un efecto de estado único

- No puede afectar a otros héroes

  

#### Defender

- Aumenta tu defensa en +50%

- Dura hasta tu próximo turno

- Útil cuando tienes poca vida

  

#### Usar Ítem

- Accede al inventario

- Selecciona un ítem disponible

- Elige el héroe objetivo

- El ítem se consume del inventario

  

### Condiciones de Victoria

  

-  **Victoria**: Todos los monstruos tienen HP = 0

-  **Derrota**: Todos los héroes tienen HP = 0

  

----------

  

## Look and Feel (GUI)

  

### Paleta de Colores

  

-  **Fondo Principal**: `RGB(20, 20, 20)` - Negro profundo

-  **Panel Héroes**: `RGB(10, 70, 10)` - Verde oscuro

-  **Panel Monstruos**: `RGB(70, 10, 10)` - Rojo oscuro

-  **Tarjetas**: `RGB(60, 60, 60, 160)` - Gris translúcido

-  **Bordes**: `RGB(80, 80, 80, 200)` - Gris medio

-  **Texto**: Blanco

-  **Botones**: `RGB(70, 70, 70)` - Gris oscuro

  

### Características Visuales

  

- Bordes de color para cada bando (verde/rojo)

- Paneles con scroll para múltiples personajes

- Botones de acción en panel lateral

- Log de combate en panel inferior

- Actualización en tiempo real de estadísticas

- Formato Consolas para texto monoespaciado

  

----------

  

##  Mecánicas de Juego Detalladas

  

### Sistema de Daño

  

```

Daño Final = max(Ataque * Modificador_Arma - Defensa_Objetivo, 0)

```

  

**Modificadores de arma**:

- Espada: 1.10

- Hacha: 1.30

- Bastón: 1.00

- Arco: 1.00

  

### Sistema de Defensa

  

Cuando un personaje defiende:

-  **PersonajeJugable**: Defensa × 1.5

-  **Monstruo Defensivo**: Defensa × 1.8

-  **Monstruo Balanceado**: Defensa × 1.5

-  **Monstruo Agresivo**: Defensa × 1.3

  

La defensa aumentada se resetea al inicio del siguiente turno.

  

### Sistema de Estados

  

Los estados con duración se gestionan mediante `EstadoEfecto`:

  

```java

EstadoEfecto {

Estado  tipo;

int  turnos; // Duración restante

int  valorDebilitacion; // Para DEBILITADO

}

```

  

Al finalizar cada turno:

1. Se reduce el contador de turnos

2. Si llega a 0, el estado se elimina

3. Se restauran estadísticas (ej: ataque en DEBILITADO)

  

### Sistema de Buffs

  

Los buffs funcionan de manera aditiva:

  

```

Estadística Final = Estadística Base + Suma de Buffs

```

  

Los buffs se actualizan cada turno y se eliminan al expirar.

  

### IA de Monstruos

  

Los monstruos toman decisiones basadas en su tipo y HP:

  

```java

if (debeDefender()) {

defender();

} else {

atacar(objetivo_aleatorio);

}

```

  

La probabilidad de defender varía según tipo y HP restante.

  

----------

  

##  Estadísticas de Personajes

  

### Héroes

  

| Nombre | HP | MP | ATK | DEF | VEL | Arma | Poder |

|--------|----|----|-----|-----|-----|------|-------|

| Heroe | 500 | 200 | 80 | 50 | 90 | Espada | Envenenar |

| Jessica | 400 | 250 | 90 | 40 | 70 | Bastón | Congelar |

| Angelo | 450 | 180 | 85 | 45 | 60 | Arco | Debilitar |

| Yangus | 600 | 150 | 70 | 70 | 50 | Hacha | Aturdir |

  

### Monstruos

  

| Nombre | HP | ATK | DEF | VEL | Tipo |

|--------|----|----|-----|-----|------|

| Slime Gigante | 300 | 60 | 40 | 85 | Agresivo |

| Golem de Piedra | 350 | 55 | 60 | 65 | Defensivo |

| Caballero Oscuro | 280 | 65 | 45 | 55 | Balanceado |

| Dragón Menor | 400 | 75 | 50 | 45 | Defensivo |

  

----------

  

## Consejos Estratégicos

  

1.  **Controla tu MP**: Los poderes especiales son poderosos pero costosos (50 MP)

2.  **Aprovecha el veneno**: Es excelente contra enemigos con mucho HP

3.  **Congela enemigos rápidos**: Evita que actúen primero

4.  **Debilita enemigos fuertes**: Reduce significativamente su daño

5.  **Usa el bastón sabiamente**: Jessica recupera MP al atacar

6.  **Defiende estratégicamente**: Especialmente con personajes de baja vida

7.  **Gestiona el inventario**: Los ítems son limitados, úsalos bien

8.  **Foco de fuego**: Concentra ataques en un enemigo a la vez

9.  **Controla la velocidad**: Los buffs pueden cambiar el orden de turnos

10.  **Aprovecha las armas**: Cada una tiene ventajas situacionales

  

----------


  
  

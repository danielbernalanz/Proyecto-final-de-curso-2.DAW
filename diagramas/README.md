# Diagrama de flujo de MATCH!CORE

El flujo es el mismo para todos los deportes. Lo que cambia de uno a otro (tiempo, eventos, cambios y avisos) lo pone el **reglamento de cada deporte**.

También está como imagen: [SVG](MATCHCORE_diagrama_flujo.svg) · [PNG](MATCHCORE_diagrama_flujo.png).

**Colores:** verde claro = pantalla · amarillo = decisión · azul = acción automática · morado = depende del deporte · rojo = aviso · verde oscuro = inicio o fin.

## 1. Acceso y preparación

```mermaid
flowchart TD
  A([Entrar en MATCH!CORE]) --> B{¿Tiene cuenta?}
  B -- No --> C[Registro y política de privacidad]
  C --> D
  B -- Sí --> D[Iniciar sesión]
  D --> F[Panel principal]
  F --> G[Crear equipo]
  F --> H[Nuevo partido]
  F --> I[Historial y estadísticas]
  F --> J[Sensores, si se usan]
  G --> G1[Elegir deporte]
  G1 --> G2[Cargar el reglamento del deporte]
  G2 --> G3[Alta de jugadores]
  G3 --> G4{¿Jugador menor de 14 años?}
  G4 -- Sí --> G5[Consentimiento de padres o tutores]
  G4 -- No --> G6[Consentimiento del jugador]
  H --> H1[Elegir equipo]
  H1 --> H2[Rival, fecha y lugar]
  H2 --> H3[Convocatoria con los jugadores que permite el reglamento]
  H3 --> K([Ir al partido en directo])

  classDef screen fill:#e3f1e9,stroke:#1f6f4a,color:#17221c
  classDef decision fill:#fff1d6,stroke:#b86e00,color:#17221c
  classDef rule fill:#f3ecfb,stroke:#5b3a8c,color:#17221c
  classDef term fill:#1f6f4a,stroke:#1f6f4a,color:#ffffff
  class C,D,F,G,H,I,J,G1,G3,G5,G6,H1,H2 screen
  class B,G4 decision
  class G2,H3 rule
  class A,K term
```

## 2. Partido en directo

```mermaid
flowchart TD
  A([Iniciar partido]) --> B{¿El deporte se juega con reloj?}
  B -- Sí --> C[Cronómetro con la duración del reglamento]
  B -- No --> C2[Marcador por puntos y sets]
  C --> D{¿Ocurre algo?}
  C2 --> D
  D -- Sí --> E[Elegir evento de la lista del deporte]
  E --> E2[Elegir jugador]
  E2 --> F[Guardar evento y actualizar marcador]
  F --> G[Comprobar las reglas del deporte]
  G --> H{¿Alguna regla genera aviso?}
  H -- Sí --> H1[Mostrar el aviso]
  H -- No --> D
  H1 --> D
  D -- No --> J{¿Fin del periodo, set o parte?}
  J -- No --> D
  J -- Sí --> K{¿Quedan más?}
  K -- Sí --> L[Descanso] --> D
  K -- No --> M([Finalizar partido])

  classDef screen fill:#e3f1e9,stroke:#1f6f4a,color:#17221c
  classDef decision fill:#fff1d6,stroke:#b86e00,color:#17221c
  classDef auto fill:#dbe9f7,stroke:#2f5f8f,color:#17221c
  classDef rule fill:#f3ecfb,stroke:#5b3a8c,color:#17221c
  classDef warn fill:#fbe0dc,stroke:#b3261e,color:#17221c
  classDef term fill:#1f6f4a,stroke:#1f6f4a,color:#ffffff
  class E2,L screen
  class D,H,K decision
  class F auto
  class B,C,C2,E,G,J rule
  class H1 warn
  class A,M term
```

## 3. Después del partido

```mermaid
flowchart TD
  A([Partido finalizado]) --> B[Resumen del partido]
  B --> C{¿Hay que corregir algo?}
  C -- Sí --> D[Editar eventos] --> B
  C -- No --> E[Guardar en el historial]
  E --> F[Calcular las estadísticas del deporte]
  F --> G[Historial y estadísticas]
  G --> G1[Por partido]
  G --> G2[Por jugador]
  G --> G3[Por temporada]
  G1 --> H([Volver al panel principal])
  G2 --> H
  G3 --> H

  classDef screen fill:#e3f1e9,stroke:#1f6f4a,color:#17221c
  classDef decision fill:#fff1d6,stroke:#b86e00,color:#17221c
  classDef auto fill:#dbe9f7,stroke:#2f5f8f,color:#17221c
  classDef rule fill:#f3ecfb,stroke:#5b3a8c,color:#17221c
  classDef term fill:#1f6f4a,stroke:#1f6f4a,color:#ffffff
  class B,D,G,G1,G2,G3 screen
  class C decision
  class E auto
  class F rule
  class A,H term
```

## 4. Qué pone el reglamento de cada deporte

| Deporte | Tiempo | Eventos | Cambios | Avisos |
|---|---|---|---|---|
| Fútbol | 2 partes de 45 min, reloj corrido | Gol, falta, tarjeta amarilla y roja, cambio | Limitados según la competición; quien sale no vuelve | Segunda amarilla: expulsión |
| Fútbol sala | 2 partes de 20 min, reloj parado | Gol, falta, tarjeta, cambio, tiempo muerto | Ilimitados y volantes | 5 faltas acumuladas en la parte: desde la sexta, doble penalti |
| Baloncesto | 4 cuartos de 10 min, reloj parado | Canasta de 1, 2 o 3 puntos, rebote, falta personal, técnica | Ilimitados | 5 faltas personales: jugador eliminado. Desde la 5.ª falta de equipo en el cuarto: tiros libres |
| Balonmano | 2 partes de 30 min | Gol, exclusión de 2 min, tarjeta amarilla, roja y azul | Ilimitados | Cuenta atrás de la exclusión. Tercera exclusión: descalificación |
| Voleibol | Sin reloj: sets a 25 puntos (el quinto a 15), gana quien llega a 3 sets | Punto, saque, bloqueo, cambio, tiempo muerto | Limitados por set, con rotación | Fin de set y de partido |

Añadir otro deporte más adelante consiste en escribir su reglamento, sin tocar el flujo.

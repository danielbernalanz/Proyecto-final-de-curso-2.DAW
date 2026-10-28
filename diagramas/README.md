# Diagrama de flujo de MATCH!CORE

Recorrido del entrenador por la aplicación: antes, durante y después del partido.

También está como imagen: [SVG](MATCHCORE_diagrama_flujo.svg) · [PNG](MATCHCORE_diagrama_flujo.png).

**Colores:** verde claro = pantalla · amarillo = decisión · azul = acción automática · rojo = aviso · verde oscuro = inicio o fin.

## 1. Acceso y preparación

```mermaid
flowchart TD
  A([Entrar en MATCH!CORE]) --> B{¿Tiene cuenta?}
  B -- No --> C[Registro: club o entrenador]
  C --> C2[Aceptar política de privacidad]
  C2 --> D
  B -- Sí --> D[Iniciar sesión]
  D --> E{¿Datos correctos?}
  E -- No --> D
  E -- Sí --> F[Panel principal]
  F --> G[Equipos y plantilla]
  F --> H[Nuevo partido]
  F --> I[Historial y estadísticas]
  F --> J[Sensores]
  G --> G1[Alta de jugadores: nombre, dorsal, posición]
  G1 --> G2{¿Jugador menor de 14 años?}
  G2 -- Sí --> G3[Consentimiento de padres o tutores]
  G2 -- No --> G4[Consentimiento del jugador]
  G3 --> G5[Jugador guardado]
  G4 --> G5
  J --> J1[Vincular sensor a cada jugador]
  H --> H1[Elegir deporte: fútbol o fútbol sala]
  H1 --> H2[Rival, fecha y lugar]
  H2 --> H3[Convocatoria y titulares]
  H3 --> K([Ir al partido en directo])

  classDef screen fill:#e3f1e9,stroke:#1f6f4a,color:#17221c
  classDef decision fill:#fff1d6,stroke:#b86e00,color:#17221c
  classDef auto fill:#dbe9f7,stroke:#2f5f8f,color:#17221c
  classDef term fill:#1f6f4a,stroke:#1f6f4a,color:#ffffff
  class C,C2,D,F,G,H,I,J,G1,G3,G4,J1,H1,H2,H3 screen
  class B,E,G2 decision
  class G5 auto
  class A,K term
```

## 2. Partido en directo

```mermaid
flowchart TD
  A([Iniciar partido]) --> B[Cronómetro en marcha]
  B --> S[Datos de sensores en tiempo real]
  S --> S1{¿Carga física alta?}
  S1 -- Sí --> S2[Aviso al preparador físico]
  S1 -- No --> S
  B --> C{¿Ocurre algo?}
  C -- Sí --> D[Elegir evento: gol, falta, amarilla, roja o cambio]
  D --> E[Elegir jugador]
  E --> F[Guardar con el minuto]
  F --> G[Actualizar marcador, minutos y estadísticas]
  G --> H{¿Segunda amarilla o roja?}
  H -- Sí --> H1[Jugador expulsado]
  H -- No --> I
  H1 --> I{¿Fútbol sala y 5 faltas acumuladas?}
  I -- Sí --> I1[Aviso: la siguiente falta es doble penalti]
  I -- No --> C
  I1 --> C
  C -- No --> J{¿Fin del periodo?}
  J -- No --> C
  J -- Sí --> K{¿Quedan más periodos?}
  K -- Sí --> L[Descanso] --> B
  K -- No --> M([Finalizar partido])

  classDef screen fill:#e3f1e9,stroke:#1f6f4a,color:#17221c
  classDef decision fill:#fff1d6,stroke:#b86e00,color:#17221c
  classDef auto fill:#dbe9f7,stroke:#2f5f8f,color:#17221c
  classDef warn fill:#fbe0dc,stroke:#b3261e,color:#17221c
  classDef term fill:#1f6f4a,stroke:#1f6f4a,color:#ffffff
  class B,D,E,L screen
  class C,H,I,J,K,S1 decision
  class F,G,S auto
  class H1,I1,S2 warn
  class A,M term
```

## 3. Después del partido

```mermaid
flowchart TD
  A([Partido finalizado]) --> B[Resumen: marcador, goleadores, tarjetas y minutos]
  B --> C{¿Hay que corregir algo?}
  C -- Sí --> D[Editar eventos] --> B
  C -- No --> E[Guardar en el historial]
  E --> F[Actualizar estadísticas de jugadores y equipo]
  F --> G[Historial y estadísticas]
  G --> G1[Por partido]
  G --> G2[Por jugador: goles, tarjetas, minutos, carga física]
  G --> G3[Por temporada]
  G1 --> H([Volver al panel principal])
  G2 --> H
  G3 --> H

  classDef screen fill:#e3f1e9,stroke:#1f6f4a,color:#17221c
  classDef decision fill:#fff1d6,stroke:#b86e00,color:#17221c
  classDef auto fill:#dbe9f7,stroke:#2f5f8f,color:#17221c
  classDef term fill:#1f6f4a,stroke:#1f6f4a,color:#ffffff
  class B,D,G,G1,G2,G3 screen
  class C decision
  class E,F auto
  class A,H term
```

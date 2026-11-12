# Asteroids

Clon del clásico arcade **Asteroids** implementado en canvas HTML5 puro, sin dependencias ni bundler.

## Descripción

Nave espacial en un campo de asteroides con envolvimiento de bordes (el espacio es toroidal). Destruye asteroides para sumar puntos: los grandes se parten en medianos, los medianos en pequeños. Incluye power-ups especiales y un asteroide especial: la estrella fugaz.

## Tecnologías

- **HTML5 Canvas** — renderizado 2D
- **JavaScript (ES6+)** — lógica del juego en un solo archivo `game.js`
- Sin frameworks, sin bundler, sin dependencias

## Cómo correr

Abre `index.html` directamente en el navegador (doble clic), o usa un servidor local:

```bash
npx serve .
```

Luego visita `http://localhost:3000`.

## Controles

| Tecla     | Acción     |
| --------- | ---------- |
| `←` `→`   | Rotar nave |
| `↑`       | Propulsar  |
| `Espacio` | Disparar   |
| `X`       | Triple disparo (5 s, luego recarga) |

## Puntuación

| Asteroide | Puntos |
| --------- | ------ |
| Grande    | 20     |
| Mediano   | 50     |
| Pequeño   | 100    |
| Estrella fugaz | 200 |

## Estrella fugaz

Asteroide especial que aparece cada 8–15 segundos, cruzando la pantalla desde un borde. Se mueve mucho más rápido que un asteroide normal y desaparece sola a los 10 segundos (parpadea antes de irse). Dispararle da un bonus de 200 puntos, pero tocarla cuesta una vida.

## Power-ups

Al destruir un asteroide hay un 10% de probabilidad de que suelte un ítem flotante (aro con símbolo) que desaparece a los 8 segundos. Recogerlo con la nave activa el efecto durante 5 segundos (recoger otro refresca el tiempo, no acumula):

| Ítem                       | Símbolo              | Efecto                                                                 |
| -------------------------- | -------------------- | ---------------------------------------------------------------------- |
| **Velocidad** (cian)       | Doble chevron `»`    | Duplica el empuje del propulsor                                         |
| **Escudo** (azul)          | Arco interior (burbuja) | Burbuja protectora: los asteroides y estrellas fugaces que la tocan se destruyen con puntos, sin dañar la nave |

## Características

- 3 vidas con invencibilidad temporal al reaparecer (parpadeo)
- Asteroides se parten en fragmentos más pequeños al ser destruidos
- Estrella fugaz: asteroide rápido y temporal que otorga un bonus de puntos
- Triple disparo: con la tecla `X`, la nave dispara 3 balas en abanico estrecho (±10°) durante 5 segundos; luego entra en recarga de 10 segundos
- Power-ups: velocidad (empuje x2) y escudo (protege de los impactos)
- Partículas de explosión al destruir asteroides

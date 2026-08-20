# Vientre de Luz — Sistema de marca

> Extraído del brand board. Fuente de verdad para el CSS del sitio.

## Identidad

**Qué es:** Organización no gubernamental dedicada a la concientización, acompañamiento y difusión de información sobre el autismo, desde una visión humana, natural y empática.

**Tagline:** *El llamado de la tierra a volver a ella.*

**Misión:** Informar, inspirar y acompañar con amor y conciencia.

**Visión:** Construir una comunidad informada, empática y abierta al aprendizaje, donde el autismo sea comprendido con mayor sensibilidad, respeto y esperanza.

**Dominio:** vientredeluz.com
**Correo:** vientredeluzmx@gmail.com
**Redes:** @vientredeluzmx (Instagram, Facebook)

## Voz de marca

| Pilar | Cómo suena |
|---|---|
| **Empática** | Hablamos desde el corazón, con comprensión y respeto hacia cada historia. |
| **Natural** | Promovemos lo simple, lo esencial y lo que la naturaleza nos ofrece. |
| **Comunitaria** | Somos una comunidad que acompaña, escucha y comparte para crecer juntos. |

## Paleta

| Nombre | Hex | Uso sugerido |
|---|---|---|
| Verde Bosque | `#2F4F3E` | Fondo de secciones oscuras, texto principal, footer |
| Verde Salvia | `#8FAE9A` | Acentos, bordes, iconos, estados hover |
| Azul Tierra | `#6C8FAA` | Acento secundario, enlaces, badges |
| Arena Clara | `#F2E9DB` | Fondos de sección alternos, tarjetas |
| Tierra Suave | `#A68A6A` | Detalles cálidos, líneas divisorias, CTA secundario |
| Blanco Natural | `#FAFAF8` | Fondo base del sitio |

### Tokens CSS

```css
:root {
  --verde-bosque:   #2F4F3E;
  --verde-salvia:   #8FAE9A;
  --azul-tierra:    #6C8FAA;
  --arena-clara:    #F2E9DB;
  --tierra-suave:   #A68A6A;
  --blanco-natural: #FAFAF8;

  --texto:          #2F4F3E;
  --texto-suave:    #55665C;
  --superficie:     var(--blanco-natural);
  --superficie-alt: var(--arena-clara);
}
```

> **Nota de contraste:** Verde Salvia y Tierra Suave no alcanzan AA sobre fondos claros para texto pequeño. Úsalos como fondo, borde o acento gráfico — nunca para párrafos. Para texto siempre Verde Bosque (o un derivado más oscuro).

## Tipografía

| Rol | Fuente | Uso |
|---|---|---|
| Logotipo / display | **Cormorant Garamond** | Nombre de marca, títulos hero, citas |
| Títulos | **Montserrat SemiBold** | H2–H4, navegación, botones |
| Cuerpo | **Montserrat Regular** | Párrafos, listas, pies de foto |

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;1,400&family=Montserrat:wght@400;500;600&display=swap" rel="stylesheet">
```

```css
--fuente-display: 'Cormorant Garamond', Georgia, serif;
--fuente-texto:   'Montserrat', system-ui, sans-serif;
```

## Logo

- **Principal:** manos sosteniendo el planeta con laurel, texto circular "Autismo / Vientre de Luz"
- **Sello circular:** versión con marco, para favicon, avatar de redes y marcas de agua
- **Horizontal/apilado:** ícono + "Vientre de Luz" + "AUTISMO"

Para el sitio hacen falta en **SVG o PNG a 2x con fondo transparente**:
`logo-principal`, `logo-sello`, `logo-horizontal`, `favicon` (32/180/512 px).

## Criterios de accesibilidad (prioritarios en este proyecto)

Siendo una organización sobre autismo, el sitio debe predicar con el ejemplo:

- Contraste AA mínimo en todo texto (4.5:1)
- `prefers-reduced-motion` respetado — sin animaciones automáticas ni carruseles
- Sin destellos, parpadeos ni autoplay de video/audio
- Jerarquía de encabezados limpia y navegación por teclado completa
- Lenguaje claro, párrafos cortos, sin metáforas ambiguas en instrucciones
- Espaciado generoso; evitar patrones visuales de alta frecuencia
- Control de tamaño de texto sin romper el layout (usar `rem`)
- Considerar un modo de "lectura tranquila" (menos color, más espacio)

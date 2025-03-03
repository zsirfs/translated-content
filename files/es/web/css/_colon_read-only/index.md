---
title: ':read-only'
slug: Web/CSS/:read-only
tags:
  - CSS
  - Diseño
  - Pseudo-clase
  - Referencia
  - Web
translation_of: Web/CSS/:read-only
---
{{CSSRef}}

La [pseudo-clase](/es/docs/CSS/Pseudo-classes) **`:read-only`** de [CSS](/es/docs/Web/CSS) representa un elemento que ya no es editable por el usuario (como un [input](/es/docs/Web/HTML/Element/input)).

```css
/* Selecciona cualquier <input> que está en modo de solo lectura */
/* Soportado en Firefox usando prefijo */
input:-moz-read-only {
  background-color: #ccc;
}

/* El prefijo no es necesario en navegadores basados en Blink/WebKit/Edge  */
p:read-only {
  cursor: not-allowed;
}
input:read-only {
  background-color: #ccc;
}
```

> **Nota:** El selector no solo selecciona {{htmlElement("input")}} marcados como {{htmlattrxref("readonly", "input")}}; también selecccionará cualquier elemento que no pueda ser editar por el usuario. Lea sobre el atributo [contenteditable](/es/docs/Web/HTML/Global_attributes/contenteditable).

## Sintaxis

    :read-only

## Ejemplo

### HTML

```html
<input type="text" value="Aquí puedes poner lo que quieras.">
<input type="text" value="Campo de solo lectura." readonly>
<p>Este es un párrafo normal.</p>
<p contenteditable="true">Puedes editar este párrafo, ¡inténtalo!</p>
```

### CSS

```css
input { min-width: 25em; }
input:-moz-read-only { background: cyan; }
input:read-only { background: cyan; }

p:-moz-read-only { background: lightgray; }
p:read-only { background: lightgray; }
p[contenteditable="true"] { color: blue; }
```

### Resultado

{{EmbedLiveSample("Ejemplo")}}

## Especificaciones

| Especificación                                                                           | Estado                                   | Comentarios                                                                       |
| ---------------------------------------------------------------------------------------- | ---------------------------------------- | --------------------------------------------------------------------------------- |
| {{ SpecName('HTML WHATWG', '#selector-read-only', ':read-only') }} | {{ Spec2('HTML WHATWG') }}     | Ningún cambio.                                                                    |
| {{ SpecName('HTML5 W3C', '#selector-read-only', ':read-only') }}     | {{ Spec2('HTML5 W3C') }}         | Define la semántica relacionada con HTML y de la validación de las restricciones. |
| {{ SpecName('CSS4 Selectors', '#rw-pseudos', ':read-only') }}         | {{ Spec2('CSS4 Selectors') }} | Define la pseudoclase, pero no la semántica asociada.                             |

## Compatibilidad con navegadores

{{Compat("css.selectors.read-only")}}

## Ver también

- {{cssxref(":read-write")}}
- Atributo HTML {{htmlattrxref("contenteditable")}}

# SSMRipley.FOCUS
Este repositorio contiene la fuente de la plataforma SSMRIPLEY.

## Importante :wink:

Flujo de trabajo con git.

```mermaid
    %%{init: { 'logLevel': 'debug', 'theme': 'default' , 'themeVariables': {
              'tagLabelColor': '#ff0000',
              'tagLabelBackground': '#00ff00',
              'tagLabelBorder': '#0000ff'
       } } }%%
       gitGraph
       commit
       branch release
       commit
       branch develop
       commit
       branch dev-rl
       commit
       commit
       checkout develop
       branch dev-othr
       commit
       commit
       checkout develop
       merge dev-rl
       checkout release
       merge develop
       checkout main
       merge release
       checkout dev-rl
       commit
       commit
       checkout develop
       merge dev-rl
       checkout dev-rl
       commit
       commit
       commit
       checkout dev-othr
       commit
       commit
       merge develop
       commit
       checkout develop
       merge dev-othr
       checkout dev-rl
       merge develop
       commit
       checkout develop
       merge dev-rl
       checkout release
       merge develop
       checkout main
       merge release
```

## Uso de las ramas

| Rama | Tipo Rama | Allow Merge | Descripción |
| - | - | - | - |
| **main** | Producción | **release** | `Merge permitido` si después de finalizar el seguimiento no hay incidencias en la rama **release**. |
| **release** | Producción | **develop** | `Merge permitido` si QA y CQA aprueban el desarrollo sobre la rama **develop**. |
| **develop** | Desarrollo | **dev-*** | `Merge permitido` por cualquier rama **dev**, solo si desarrollador terminó el requerimiento. |
| **dev-rl** | Desarrollo | - | Rama desarrollador con sus cambios. |
| **dev-othr** | Desarrollo | - | Rama de otro desarrollador. |

## Nomenclatura ramas

> **`dev-rl`**-*`carga`-`tlmk`*
>
> **`dev-othr`**-*`venta`-`online`*
>
> **`dev-othr`**-*`venta`-`pre-emision`*

Modificación dependiendo del autor y módulo a cambiar (*Opcional*)

# Consideraciones :cry:

- Es posible crear nuevas ramas a partir de main o release, solo si es un cambio de emergencia.
- Cada modificación en algún módulo debe tener su propio README con una descripción del ajuste realizado con el # de línea y/o función modificada.

Syntax change in javaScript file

``` js
var foo = function (bar) {
  return bar++;
};

console.log(foo(5));
```

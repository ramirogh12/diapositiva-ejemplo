---
title: "Aprendamos un poco más de RevealJS"
author: "Irwing S. Saldaña"
format: 
  revealjs:
    theme: simple
    slide-number: true
    incremental: true
    transition: convex
    transition-speed: slow
    code-overlays: true
    width: 1280
    height: 720
title-slide-attributes:
  data-background-image: "https://image.slidesdocs.com/responsive-images/background/blue-abstract-texture-polygon-technology-nature-powerpoint-background_94e8175035__960_540.jpg"
  data-background-size: cover
  data-background-opacity: "1"   
---

## Soy una diapositiva invisible {visibility="hidden"}

Aquí hay un top secret.


## Temas de RevealJS (diapo centrada) {.center}

:::: {.columns}

::: {.column width="40%"}
- beige
- blood
- dark
- default
- league
- moon
:::

::: {.column width="60%"}
- night
- serif
- simple
- sky
- solarized
:::

::::


## Lista Numerada

1. none (Sin transición)
1. fade (Desvanecimento cruzado)
1. slide (Movimiento horizontal)
1. convex (Movimiento convexo en ángulo)
1. concave (Movimiento concavo en ángulo)
1. zoom	(Aplica zoom) 

## Imagen desde la Web

![Quarto Logo](https://quarto.org/img/quarto-logo.png)



## Colocar un gran texto que nunca se desborda

::: {.r-fit-text}
masterX
:::

## Añadiendo fragmentos 

::: {.fragment}
Fade in
:::

::: {.fragment .fade-out}
Fade out
:::

::: {.fragment .highlight-red}
Highlight red (resalta en rojo)
:::

::: {.fragment .fade-in-then-out}
Fade in, then out
:::

::: {.fragment .fade-up}
Slide up while fading in
:::


## Añadiendo orden a los fragmentos

::: {.fragment fragment-index=3}
Aparece al final
:::

::: {.fragment fragment-index=1}
Aparece primero
:::

::: {.fragment fragment-index=2}
Aparece segundo
:::


## Paneles con Código y Gráfico {transition="fade" transition-speed="fast"}

::: {.panel-tabset}

## Código

```{r}
#| echo: true
#| eval: false
#| code-line-highlight: 2
library(ggplot2)
ggplot(mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  theme_minimal() +
  labs(title = "Gráfico de MPG vs. Peso")
```

## Plot

```{r}
#| echo: false
#| eval: true
#| fig-width: 10
#| fig-height: 5
#| fig-align: "center"
library(ggplot2)
ggplot(mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  theme_minimal() +
  labs(title = "Gráfico de MPG vs. Peso")
```

## Data

```{r}
mtcars
```

:::

## Insertando interactividad: mapas

```{r}
#| echo: false
#| eval: true
#| fig-width: 12
#| fig-height: 6.5
#| fig-align: "center"

# Cargar la librería leaflet
library(leaflet)

# Crear un mapa básico
leaflet() %>%
  addTiles() %>%  # Añadir el mapa base
  setView(lng = -78.7038, lat = -5.4168, zoom = 6) %>%  # Centrar el mapa en Madrid, España
  addMarkers(lng = -3.7038, lat = 40.4168, popup = "Madrid")
```

## Insertando interactividad: Plotly

```{r}
#| echo: false
#| eval: true
#| fig-width: 12
#| fig-height: 6.5
#| fig-align: "center"

# Cargar la librería plotly
library(plotly)

# Crear un gráfico 3D con plotly
fig <- plot_ly(
  data = mtcars,
  x = ~wt,
  y = ~mpg,
  z = ~hp,
  type = 'scatter3d',
  mode = 'markers',
  marker = list(
    size = 5,
    color = ~mpg,
    colorscale = 'Viridis',
    showscale = TRUE,
    opacity = 0.8
  )
)

# Configurar el diseño del gráfico
fig <- fig %>%
  layout(
    title = "Relación 3D: Peso vs MPG vs Potencia",
    scene = list(
      xaxis = list(title = 'Peso (wt)'),
      yaxis = list(title = 'Millas por Galón (mpg)'),
      zaxis = list(title = 'Potencia (hp)')
    ),
    annotations = list(
      list(
        x = 0.1,
        y = 1.1,
        text = "Gráfico 3D interactivo",
        showarrow = FALSE,
        xref = 'paper',
        yref = 'paper',
        font = list(
          size = 12,
          color = 'black'
        )
      )
    )
  )

# Mostrar el gráfico
fig

```




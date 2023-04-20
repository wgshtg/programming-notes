# Bootstrap 常見配置與使用情境

## Class 組成規則

`{component}-{value}`: 元件 + 元件屬性值
`{component}-{color}`: 元件 + 顏色
`{component}-{breakpoint}`: 元件 + 斷點

## 常用元件 (Component)

|  Component  |    Class    |
|:-----------:|:-----------:|
|    Text     |   `text`    |
|  Container  | `container` |
|  Grid.Row   |    `row`    |
| Grid.Column |    `col`    |

## Theme colors

|   Color   | Class infix  |
|:---------:|:------------:|
|  Primary  |  `-primary`  |
| Secondary | `-secondary` |
|  Success  |  `-success`  |
|  Danger   |  `-danger`   |
|  Warning  |  `-warning`  |
|   Info    |   `-info`    |
|   Light   |   `-light`   |
|   Dark    |   `-dark`    |
|   Muted   |   `-muted`   |
|   White   |   `-white`   |
| Black-50  | `-black-50`  |
| White-50  | `-white-50`  |

## Breakpoint

|    Breakpoint     | Class infix | Dimensions |
|:-----------------:|:-----------:|:----------:|
|      X-Small      |   `None`    |   <576px   |
|       Small       |    `sm`     |   ≥576px   |
|      Medium       |    `md`     |   ≥768px   |
|       Large       |    `lg`     |   ≥992px   |
|    Extra large    |    `xl`     |  ≥1200px   |
| Extra extra large |    `xxl`    |  ≥1400px   |

## Sides

適用於 `margin`, `padding`

| Sides | Defintion                   | Usage                                          |
|:-----:|:----------------------------|:-----------------------------------------------|
|   t   | top                         | `mt-3: margin-top: 1rem;`                      |
|   b   | bottom                      | `mb-3: margin-bottom: 1rem;`                   |
|   s   | left                        | `ms-3: margin-left: 1rem;`                     |
|   e   | right                       | `me-3: margin-right: 1rem;`                    |
|   x   | left & right                | `mx-3: margin-left: 1rem; margin-right: 1rem;` |
|   y   | top & bottom                | `my-3: margin-top: 1rem; margin-bottom: 1rem;` |
| blank | top & bottom & left & right | `m-3: margin: 1 rem;`                          |


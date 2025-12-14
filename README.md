# Visualizador de Estructura Oracional Japonesa

Una herramienta interactiva para analizar y visualizar la estructura gramatical de oraciones japonesas, con énfasis en el predicado y sus componentes funcionales.

## Características

- **Análisis del predicado**: Identifica el núcleo del predicado (verbo, adjetivo, nominal adjetival, nominal)
- **Expresiones funcionales**: Muestra perfectivo, declarativo, expresiones de voz, modalidad, etc.
- **Complementos y adverbios**: Visualiza los elementos que complementan al predicado
- **Expresiones finales**: Identifica partículas finales (よ、ね、な、etc.)
- **Interfaz en español**: Diseñada para hispanohablantes que estudian japonés

## Instalación para GitHub Pages

### Opción 1: Usar CDN (más fácil)

Simplemente sube el archivo `index.html` a tu repositorio y activa GitHub Pages. El diccionario se cargará desde jsdelivr CDN.

### Opción 2: Self-hosting del diccionario (más estable)

1. Clona este repositorio
2. Descarga los archivos del diccionario:

```bash
mkdir -p dict
cd dict
curl -LO https://cdn.jsdelivr.net/npm/kuromoji@0.1.2/dict/base.dat.gz
curl -LO https://cdn.jsdelivr.net/npm/kuromoji@0.1.2/dict/cc.dat.gz
curl -LO https://cdn.jsdelivr.net/npm/kuromoji@0.1.2/dict/check.dat.gz
curl -LO https://cdn.jsdelivr.net/npm/kuromoji@0.1.2/dict/tid.dat.gz
curl -LO https://cdn.jsdelivr.net/npm/kuromoji@0.1.2/dict/tid_map.dat.gz
curl -LO https://cdn.jsdelivr.net/npm/kuromoji@0.1.2/dict/tid_pos.dat.gz
curl -LO https://cdn.jsdelivr.net/npm/kuromoji@0.1.2/dict/unk.dat.gz
```

3. Modifica `index.html` para usar el diccionario local:

Cambia esta línea:
```javascript
kuromoji.builder({ dicPath: "https://cdn.jsdelivr.net/npm/kuromoji@0.1.2/dict" }).build(...)
```

Por:
```javascript
kuromoji.builder({ dicPath: "./dict" }).build(...)
```

4. Sube todos los archivos a GitHub y activa GitHub Pages

## Configuración de GitHub Pages

1. Ve a tu repositorio en GitHub
2. Settings → Pages
3. Source: "Deploy from a branch"
4. Branch: `main` (o `master`), folder: `/ (root)`
5. Guarda y espera unos minutos

Tu herramienta estará disponible en: `https://[tu-usuario].github.io/[nombre-repositorio]/`

## Estructura del proyecto

```
/
├── index.html          # Aplicación principal
├── dict/               # Diccionario kuromoji (opcional)
│   ├── base.dat.gz
│   ├── cc.dat.gz
│   ├── check.dat.gz
│   ├── tid.dat.gz
│   ├── tid_map.dat.gz
│   ├── tid_pos.dat.gz
│   └── unk.dat.gz
└── README.md
```

## Terminología gramatical

| Español | Japonés | Descripción |
|---------|---------|-------------|
| Núcleo del predicado | 述部の核 | Verbo, adjetivo, nominal adjetival o nominal |
| Perfectivo | 完了詞 | た/だ - pasado/aspecto perfectivo |
| Forma continuativa | 継続形 | て/で - conexión |
| Declarativo | 宣言詞 | だ/です - marca predicativa |
| Adjetivo negativo | 否定形容詞 | ない - negación |
| Expresión funcional | 述部機能表現 | Voz, modalidad, aspecto, etc. |
| Expresión final | 文末表現 | よ/ね/な/か - partículas finales |
| Complemento | 補語 | Elementos nominales |
| Posposición | 後置詞 | Partículas (が/を/に/で/etc.) |

## Tecnologías utilizadas

- **kuromoji.js**: Analizador morfológico japonés en JavaScript
- **IPADic**: Diccionario para análisis morfológico
- HTML5 / CSS3 / JavaScript (vanilla)

## Licencia

MIT License

## Créditos

- kuromoji.js: https://github.com/takuyaa/kuromoji.js
- IPADic: https://taku910.github.io/mecab/

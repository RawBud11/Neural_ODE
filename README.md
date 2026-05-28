# Neural ODEs sobre Datos Reales
### Análisis Numérico · Universidad Nacional de Colombia
**Prof. Carlos Manuel Orrego Franco** · Entrega: 27 de mayo de 2026

---

## Integrantes
| Nombre | GitHub |
|--------|--------|
| Valentina Aristizábal Sierra | [@RawBud11](https://github.com/RawBud11)          |
| Camilo Andrés Jaime Rojas    | [@vasierra-hub](https://github.com/vasierra-hub)  | 


---

## Dataset
**COVID-19 JHU** — Nuevos casos diarios por país (Johns Hopkins CSSE)

| Característica | Valor |
|---|---|
| Trayectorias | 178 países |
| Pasos de tiempo | 400 días |
| Dimensiones | 1 (nuevos casos normalizados) |
| Rango de valores | [−1.098, 7.928] |
| Split entrenamiento / prueba | 143 / 35 |

---

## Resultados

### Configuración A — `dim_latente=8`, `n_pasos_ode=10`, `dim_oculto_f=48`

| Modelo | 30% rec/ext | 60% rec/ext | 100% rec | Paráms | Tiempo |
|--------|-------------|-------------|----------|--------|--------|
| Método Clásico (splines) | 0.000 / 0.114 | 0.000 / 0.087 | 0.000 / — | 4 | 0.0 s |
| Neural ODE | 0.500 / 0.501 | 0.498 / 0.505 | 0.501 / — | 3,721 | 2473 s |
| Latent ODE | 0.576 / 0.576 | 0.573 / 0.579 | 0.576 / — | 7,593 | 3264 s |

### Configuración B — `dim_latente=4`, `n_pasos_ode=6`, `dim_oculto_f=32`

| Modelo | 30% rec/ext | 60% rec/ext | 100% rec | Paráms | Tiempo |
|--------|-------------|-------------|----------|--------|--------|
| Método Clásico (splines) | 0.000 / 0.114 | 0.000 / 0.087 | 0.000 / — | 4 | 0.0 s |
| Neural ODE | 0.503 / 0.504 | 0.501 / 0.508 | 0.504 / — | 1,581 | 1897 s |
| Latent ODE | 0.561 / 0.561 | 0.559 / 0.565 | 0.561 / — | 3,717 | 2560 s |

> `rec` = RMSE de reconstrucción · `ext` = RMSE de extrapolación · `—` = sin puntos futuros disponibles

---

## Reproducir

```bash
# 1. Clonar el repositorio
git clone https://github.com/RawBud11/Neural_ODE.git

# 2. Abrir en Google Colab
#    notebooks/A_notebook_base.ipynb → "Abrir con Colab"

# 3. Ejecutar todas las celdas en orden desde la Sección 1
#    (la descarga de datos es automática desde la celda de carga)
```

> ⚠️ El entrenamiento completo toma ~40–55 min en Colab (GPU recomendada).

---

## Estructura del repositorio

```
Neural_ODE/
├── notebooks/
│   ├── NB01_neurona.ipynb
│   ├── NB02_redes.ipynb
│   ├── NB03_sir.ipynb
│   ├── NB04_fitzhugh.ipynb
│   ├── NB05_rnn.ipynb
│   ├── NB06_neural_ode.ipynb
│   ├── NB07_latent_ode.ipynb
│   └── A_notebook_base.ipynb   ← actividad final
├── informe/
│   ├── informe_neural_odes_final.docx
│   └── informe_neural_odes_final.pdf
├── evidencia_ia/
│   └── *.png                   ← capturas del chat con la IA
└── README.md
```

---

## Referencias
- Chen et al. (2018). *Neural Ordinary Differential Equations*. NeurIPS.
- Rubanova et al. (2019). *Latent ODEs for Irregularly-Sampled Time Series*. NeurIPS.
- Dong et al. (2020). *An interactive web-based dashboard to track COVID-19*. The Lancet.

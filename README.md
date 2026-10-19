# REINFORCEMENT-LEARNING
Este repositorio contiene una implementación desde cero de un agente de Aprendizaje por Refuerzo (Reinforcement Learning) utilizando el algoritmo Q-Learning para resolver un entorno clásico de Gridworld de  4×4 .

## Descripción del Problema
El agente inicia en la esquina superior izquierda (INICIO en (0,0)) y debe aprender la ruta óptima para llegar a la esquina inferior derecha (META en (3,3)) evitando los obstáculos situados en el camino ((1,1) y (2,1)).

Características del Entorno:
Gridworld: Matriz de  4×4 .
Estado Inicial: (0,0) (color verde).
Meta: (3,3) (color rojo) con una recompensa de  +10.0  al alcanzarla (estado terminal).
Obstáculos: Celdas bloqueadas en (1,1) y (2,1) (color gris oscuro).
Penalización:  −0.1  por cada paso regular para incentivar al agente a buscar el camino más corto, y  −1.0  si intenta salirse de los límites o chocar con un obstáculo.

## Algoritmo e Hiperparámetros
Se utiliza la ecuación de actualización clásica de Q-Learning (un método de control TD fuera de la política / off-policy):

Q(s,a)←Q(s,a)+α[R+γmaxa′Q(s′,a′)−Q(s,a)] 

Hiperparámetros Utilizados:
Tasa de Aprendizaje ( α ): 0.10
Factor de Descuento ( γ ): 0.95
Epsilon Inicial ( ϵ ): 1.0 (exploración total)
Epsilon Mínimo ( ϵmin ): 0.05
Decaimiento de Epsilon: 0.995 por episodio
Episodios de Entrenamiento: 1000

## Resultados y Métricas de Rendimiento
Tras completar las 1000 épocas de entrenamiento, el agente demuestra una notable convergencia hacia la política óptima:

Recompensa media (Primeros 100 episodios): ~ -2.09 (Fase exploratoria inicial con muchas penalizaciones).
Recompensa media (Últimos 100 episodios): ~ +9.29 (Fase de explotación y estabilidad de la política).
Promedio de pasos (Últimos 100 episodios): ~ 6.46 pasos.
Ruta Greedy Final: [(0, 0) ➔ (1, 0) ➔ (2, 0) ➔ (3, 0) ➔ (3, 1) ➔ (3, 2) ➔ (3, 3)].
Recompensa acumulada óptima: +9.50.

## Visualización de la Política y Ruta Óptima
El script genera un gráfico dinámico utilizando Matplotlib que ilustra:

Las celdas transitables, los obstáculos y las posiciones de inicio/meta.
Las flechas de dirección (↑, ↓, ←, →) que representan la mejor acción aprendida en cada celda transitada bajo la política final ( Q ).
La ruta óptima (línea discontinua azul con marcadores) trazada directamente desde la salida hasta la meta.

## Instrucciones de Ejecución
Requisitos previos
Asegúrate de tener instalado Python 3 y las dependencias correspondientes:

pip install numpy matplotlib

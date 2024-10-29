# 📗 Guía del Profesor: Capítulo 2 - Dibujando con Python Turtle
## 🎯 Objetivos de Aprendizaje

### Objetivos Principales
- Introducir conceptos de geometría a través de la programación
- Desarrollar pensamiento espacial
- Reforzar conceptos de secuencias y bucles
- Fomentar la creatividad mediante programación visual

### Prerrequisitos
- Python instalado correctamente
- Conceptos básicos del Capítulo 1 (print, variables)
- Conocimientos básicos de geometría (ángulos, formas)

## 🎓 Plan de Lección

### 1. Preparación (15 minutos)
- Verificar que turtle funcione en todas las computadoras
- Tener ejemplos pre-escritos listos para mostrar
- Preparar una presentación visual de los conceptos geométricos básicos

### 2. Introducción al Módulo Turtle (20 minutos)

#### Conceptos Clave
```python
# Ejemplo de demostración inicial
import turtle
t = turtle.Turtle()
screen = turtle.Screen()

# Movimientos básicos para demostrar
t.forward(100)
t.right(90)
t.forward(100)
```

#### Puntos a Enfatizar
- La tortuga es como un lápiz que podemos controlar
- Los números en los comandos son:
  - Distancia (forward/backward)
  - Ángulos (right/left)

### 3. Soluciones Detalladas de Ejercicios

#### Estrella Mágica (con explicaciones)
```python
import turtle
t = turtle.Turtle()

# Configuración inicial
t.speed(2)  # Velocidad lenta para que los estudiantes vean el proceso
t.color("gold")
t.begin_fill()

# Dibujar estrella
for _ in range(5):
    t.forward(100)  # Lado de la estrella
    t.right(144)    # Ángulo para estrella de 5 puntas (180 - 36)

t.end_fill()
```

#### Casa Feliz (con puntos de pausa)
```python
import turtle
t = turtle.Turtle()

def dibujar_casa():
    # PASO 1: Dibujar el cuadrado base
    t.color("brown")
    for _ in range(4):
        t.forward(100)
        t.right(90)
    
    # PASO 2: Dibujar el techo
    t.color("red")
    t.left(60)
    t.forward(100)
    t.right(120)
    t.forward(100)
    
    # PASO 3: Dibujar la puerta
    t.penup()
    t.goto(-30, -100)  # Posición de la puerta
    t.pendown()
    t.color("blue")
    t.forward(30)      # Altura de la puerta
    t.right(90)
    t.forward(20)      # Ancho de la puerta
```

### 4. Puntos de Verificación y Errores Comunes

#### Errores Frecuentes
1. **Error de Orientación**
   - Síntoma: La tortuga dibuja en dirección incorrecta
   - Solución: Usar `t.setheading(0)` para resetear dirección

2. **Error de Posición**
   - Síntoma: Dibujos fuera de pantalla
   - Solución: Usar `t.penup()` y `t.goto(0,0)` para centrar

3. **Error de Fill**
   - Síntoma: Formas no se rellenan correctamente
   - Solución: Verificar begin_fill() y end_fill()

### 5. Actividades de Extensión

#### Proyecto: Ciudad Geométrica
```python
def dibujar_edificio(t, altura):
    """
    Función para dibujar un edificio simple
    Útil para enseñar funciones con parámetros
    """
    t.color("gray")
    t.begin_fill()
    for _ in range(4):
        t.forward(50)
        t.left(90)
    t.end_fill()
    
    # Agregar ventanas
    t.color("yellow")
    t.penup()
    t.goto(t.xcor() + 10, t.ycor() - 20)
    t.pendown()
    t.begin_fill()
    for _ in range(4):
        t.forward(10)
        t.left(90)
    t.end_fill()
```

### 6. Evaluación y Rúbrica

#### Criterios de Evaluación
1. **Comprensión Básica** (30%)
   - Uso correcto de comandos básicos
   - Entendimiento de ángulos
   
2. **Creatividad** (30%)
   - Modificación de ejemplos
   - Creación de diseños propios

3. **Resolución de Problemas** (20%)
   - Capacidad de depurar código
   - Encontrar soluciones alternativas

4. **Participación** (20%)
   - Colaboración en clase
   - Completación de ejercicios

### 7. Consejos Pedagógicos

#### Estrategias de Enseñanza
1. **Visualización Física**
   - Hacer que los estudiantes "actúen" como la tortuga
   - Usar flechas en el piso para practicar giros

2. **Scaffolding**
   - Comenzar con formas simples
   - Gradualmente introducir bucles
   - Finalmente agregar funciones y color

3. **Diferenciación**
   - Proyectos básicos: Cuadrados y triángulos
   - Proyectos avanzados: Espirales y patrones

### 8. Recursos Adicionales

#### Proyectos de Refuerzo
```python
# Proyecto: Reloj Simple
def dibujar_reloj():
    for hora in range(12):
        t.penup()
        t.home()
        t.setheading(hora * 30)  # 360 grados / 12 horas = 30
        t.forward(100)
        t.pendown()
        t.dot(10)
```

#### Ejercicios de Desafío
```python
# Desafío: Espiral Cuadrada
def espiral_cuadrada(tamaño_inicial, vueltas):
    for i in range(vueltas * 4):
        t.forward(tamaño_inicial + i * 5)
        t.right(90)
```

### 9. Tarea y Práctica

#### Sugerencias de Tarea
1. Diseñar un logotipo personal usando formas básicas
2. Crear una escena simple (casa, árbol, sol)
3. Experimentar con diferentes colores y tamaños

### 10. Extensiones y Conexiones

#### Conexiones Interdisciplinarias
- **Matemáticas**: Ángulos, geometría, coordenadas
- **Arte**: Diseño, color, composición
- **Física**: Movimiento, dirección, velocidad

### 11. Notas Finales
- Mantener un ritmo adecuado para todos los estudiantes
- Celebrar la creatividad y diferentes soluciones
- Fomentar la experimentación segura
- Documentar los errores comunes para futuras clases


# 📘 Guía del Profesor: Capítulo 3 - Creando Mini-Juegos con Python

## 🎯 Objetivos Pedagógicos

### Objetivos Principales
1. Fortalecer conceptos fundamentales:
   - Bucles (while, for)
   - Condicionales (if/else)
   - Variables y tipos de datos
   - Funciones y módulos

### Objetivos Secundarios
1. Desarrollar habilidades de:
   - Pensamiento lógico
   - Resolución de problemas
   - Creatividad
   - Depuración de código

## 📝 Planificación de Clases

### Clase 1: Introducción y Juego del Adivino
**Duración**: 60 minutos

#### Estructura:
1. **Introducción (10 min)**
   - Demostración de juegos ejemplo
   - Discusión sobre juegos favoritos

2. **Conceptos Clave (15 min)**
   ```python
   # Ejemplos de conceptos básicos necesarios
   import random
   numero = random.randint(1, 10)  # Números aleatorios
   
   # Bucle while básico
   contador = 0
   while contador < 5:
       print(contador)
       contador += 1
   
   # Condicionales simples
   if numero > 5:
       print("Es mayor que 5")
   else:
       print("Es menor o igual a 5")
   ```

3. **Implementación Guiada (20 min)**
   - Crear versión básica del Juego del Adivino
   - Puntos de pausa para explicaciones

4. **Práctica Independiente (15 min)**
   - Modificaciones simples al juego

### Clase 2: Piedra, Papel o Tijeras
**Duración**: 60 minutos

#### Estructura detallada con soluciones:
```python
# Versión simplificada para empezar
def version_basica():
    opciones = ["piedra", "papel", "tijeras"]
    computadora = random.choice(opciones)
    jugador = input("Elige: piedra, papel o tijeras: ")
    
    print(f"Computadora eligió: {computadora}")
    if jugador == computadora:
        return "¡Empate!"
    # ... resto del código

# Versión con puntuación para segundo paso
def version_intermedia():
    puntos = 0
    while True:
        resultado = jugar_ronda()
        if resultado == "ganar":
            puntos += 1
        print(f"Puntos: {puntos}")
        
# Versión final con todas las características
# [Código completo del capítulo]
```

### Clase 3: La Serpiente Hambrienta
**Duración**: 60 minutos

#### Puntos Clave de Enseñanza:
1. **Manejo de la Pantalla**
   ```python
   # Función para limpiar pantalla multiplataforma
   def limpiar_pantalla():
       import os
       os.system('cls' if os.name == 'nt' else 'clear')
   ```

2. **Control de Movimiento**
   ```python
   # Explicar sistema de coordenadas
   x = 0  # Posición horizontal
   y = 0  # Posición vertical
   
   # Movimientos básicos
   if tecla == 'w': y -= 1  # Arriba
   if tecla == 's': y += 1  # Abajo
   if tecla == 'a': x -= 1  # Izquierda
   if tecla == 'd': x += 1  # Derecha
   ```

## 🔍 Solución de Problemas Comunes

### 1. Errores Frecuentes y Soluciones

#### Error de Tipo de Dato
```python
# Error común
numero = input("Ingresa un número: ")
if numero > 5:  # TypeError!

# Solución
numero = int(input("Ingresa un número: "))
if numero > 5:  # Funciona correctamente
```

#### Error de Bucle Infinito
```python
# Error común
while True:
    # Código sin condición de salida

# Solución
while True:
    if condicion_salida:
        break
```

### 2. Estrategias de Depuración
- Usar print() para verificar valores
- Dividir el código en partes más pequeñas
- Implementar paso a paso

## 📊 Evaluación y Seguimiento

### Rúbrica de Evaluación

#### 1. Comprensión Básica (30%)
- Uso correcto de variables
- Implementación de bucles
- Manejo de condiciones

#### 2. Creatividad (30%)
- Modificaciones originales
- Nuevas características
- Diseño de juegos propios

#### 3. Depuración (20%)
- Identificación de errores
- Resolución de problemas
- Mejora del código

#### 4. Participación (20%)
- Trabajo en clase
- Colaboración
- Entrega de proyectos

## 🎮 Proyectos de Extensión

### 1. Quiz Personalizado
```python
def crear_quiz():
    preguntas = []
    while True:
        pregunta = input("Ingresa una pregunta (o 'fin' para terminar): ")
        if pregunta.lower() == 'fin':
            break
        respuesta = input("Ingresa la respuesta correcta: ")
        preguntas.append({"pregunta": pregunta, "respuesta": respuesta})
    return preguntas
```

### 2. Juego de Memoria
```python
def juego_memoria():
    secuencia = []
    while True:
        # Agregar nuevo número
        secuencia.append(random.randint(1, 9))
        
        # Mostrar secuencia
        print("Memoriza:", end=" ")
        for num in secuencia:
            print(num, end=" ")
            time.sleep(1)
        
        # Limpiar pantalla
        limpiar_pantalla()
        
        # Pedir secuencia al jugador
        intento = input("Repite la secuencia (números separados por espacios): ")
        if intento.split() != [str(n) for n in secuencia]:
            print("¡Game Over!")
            break
```

## 🎯 Actividades de Enriquecimiento

### 1. Desafíos Adicionales
```python
# Ejemplo: Juego de palabras
def ahorcado_simple():
    palabras = ["python", "programacion", "juego", "computadora"]
    palabra = random.choice(palabras)
    letras_adivinadas = set()
    vidas = 6
    
    while vidas > 0:
        # Mostrar palabra oculta
        display = ""
        for letra in palabra:
            if letra in letras_adivinadas:
                display += letra
            else:
                display += "_"
        print(display)
        
        # Resto del código...
```

### 2. Proyectos Colaborativos
- Crear un juego en parejas
- Torneo de juegos entre estudiantes
- Presentaciones de proyectos

## 📚 Recursos Adicionales

### 1. Material de Apoyo
- Diagramas de flujo de los juegos
- Plantillas de código
- Ejemplos adicionales

### 2. Enlaces y Referencias
- Documentación de Python
- Tutoriales de juegos
- Recursos de programación

## 🎓 Consejos Pedagógicos

1. **Diferenciación**
   - Proporcionar scaffolding según necesidad
   - Ofrecer desafíos adicionales
   - Adaptar la complejidad

2. **Motivación**
   - Usar ejemplos relevantes
   - Permitir personalización
   - Celebrar logros

3. **Evaluación Formativa**
   - Observar durante la práctica
   - Revisar código regularmente
   - Proporcionar retroalimentación

## 🗓️ Plan de Implementación Sugerido

### Semana 1
- Introducción y Juego del Adivino
- Práctica básica

### Semana 2
- Piedra, Papel o Tijeras
- Modificaciones y mejoras

### Semana 3
- La Serpiente Hambrienta
- Proyectos personales

### Semana 4
- Presentaciones
- Evaluación final


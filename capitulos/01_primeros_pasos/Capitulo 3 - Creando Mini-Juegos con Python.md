# 🎮 Capítulo 3: ¡Creando Mini-Juegos con Python!
## 🎯 Objetivos del Capítulo

En este capítulo aprenderás:
- 🎲 Crear juegos interactivos simples
- 🔄 Usar bucles while y for
- ⚡ Trabajar con condiciones (if/else)
- 📊 Manejar puntuaciones y niveles

## 🎲 1. El Juego del Adivino

¡Vamos a crear un juego donde la computadora piensa un número y tú tienes que adivinarlo!

```python
import random

print("🎮 ¡Bienvenido al Juego del Adivino! 🎮")
print("Estoy pensando en un número entre 1 y 100...")

# La computadora elige un número secreto
numero_secreto = random.randint(1, 100)
intentos = 0
max_intentos = 7

while intentos < max_intentos:
    # Pedimos el número al jugador
    intento = input("¿Qué número crees que es? ")
    intento = int(intento)
    intentos += 1
    
    # Verificamos si adivinó
    if intento == numero_secreto:
        print(f"🎉 ¡GANASTE! Lo lograste en {intentos} intentos")
        break
    elif intento < numero_secreto:
        print("📈 ¡Muy bajo! Intenta un número más alto")
    else:
        print("📉 ¡Muy alto! Intenta un número más bajo")
    
    # Mostramos intentos restantes
    print(f"Te quedan {max_intentos - intentos} intentos")

if intentos == max_intentos:
    print(f"😢 ¡Game Over! El número era {numero_secreto}")
```

## 🎯 2. Piedra, Papel o Tijeras

¡Juega contra la computadora!

```python
import random

def obtener_emoji(eleccion):
    if eleccion == "piedra": return "🪨"
    if eleccion == "papel": return "📄"
    return "✂️"

opciones = ["piedra", "papel", "tijeras"]
puntaje_jugador = 0
puntaje_computadora = 0

print("🎮 ¡Piedra, Papel o Tijeras! 🎮")

while True:
    # Elegimos
    computadora = random.choice(opciones)
    jugador = input("\n¿Piedra, papel o tijeras? (o 'salir' para terminar): ").lower()
    
    if jugador == "salir":
        break
    
    if jugador not in opciones:
        print("¡Opción no válida! Intenta de nuevo.")
        continue
    
    # Mostramos las elecciones
    print(f"\nTú: {obtener_emoji(jugador)}")
    print(f"Computadora: {obtener_emoji(computadora)}")
    
    # Determinamos el ganador
    if jugador == computadora:
        print("¡Empate! 🤝")
    elif ((jugador == "piedra" and computadora == "tijeras") or 
          (jugador == "papel" and computadora == "piedra") or 
          (jugador == "tijeras" and computadora == "papel")):
        print("¡Ganaste! 🎉")
        puntaje_jugador += 1
    else:
        print("¡La computadora gana! 💻")
        puntaje_computadora += 1
    
    # Mostramos el puntaje
    print(f"\nPuntaje: Tú {puntaje_jugador} - Computadora {puntaje_computadora}")
```

## 🐍 3. La Serpiente Hambrienta

¡Creemos un juego tipo Snake simplificado usando caracteres!

```python
import os
import time
import random

def limpiar_pantalla():
    os.system('cls' if os.name == 'nt' else 'clear')

# Configuración inicial
ancho = 20
alto = 10
serpiente_x = ancho // 2
serpiente_y = alto // 2
comida_x = random.randint(0, ancho-1)
comida_y = random.randint(0, alto-1)
puntos = 0
game_over = False

# Dirección inicial
dx = 0
dy = 0

print("🐍 ¡La Serpiente Hambrienta! 🐍")
print("Usa W,A,S,D para mover la serpiente")
input("Presiona Enter para comenzar...")

while not game_over:
    # Dibujamos el tablero
    limpiar_pantalla()
    
    for y in range(alto):
        for x in range(ancho):
            if x == serpiente_x and y == serpiente_y:
                print("🐍", end="")
            elif x == comida_x and y == comida_y:
                print("🍎", end="")
            else:
                print("⬜", end="")
        print()
    
    print(f"\nPuntos: {puntos}")
    
    # Movimiento
    movimiento = input("Movimiento (W/A/S/D): ").lower()
    
    if movimiento == 'w': dy = -1; dx = 0
    if movimiento == 's': dy = 1; dx = 0
    if movimiento == 'a': dx = -1; dy = 0
    if movimiento == 'd': dx = 1; dy = 0
    
    # Actualizamos posición
    serpiente_x += dx
    serpiente_y += dy
    
    # Verificamos colisiones
    if (serpiente_x < 0 or serpiente_x >= ancho or 
        serpiente_y < 0 or serpiente_y >= alto):
        game_over = True
        print("¡Game Over! 💥")
        break
    
    # Verificamos si comió
    if serpiente_x == comida_x and serpiente_y == comida_y:
        puntos += 1
        comida_x = random.randint(0, ancho-1)
        comida_y = random.randint(0, alto-1)
```

## 🎨 4. Quiz de Colores

¡Aprende mientras juegas!

```python
import random
import time

def mostrar_pregunta(pregunta, opciones, respuesta_correcta):
    print("\n" + pregunta)
    for i, opcion in enumerate(opciones, 1):
        print(f"{i}. {opcion}")
    
    respuesta = input("\nElige tu respuesta (1-4): ")
    if respuesta.isdigit() and 1 <= int(respuesta) <= 4:
        if opciones[int(respuesta)-1] == respuesta_correcta:
            print("¡Correcto! 🎉")
            return True
    print(f"Incorrecto. La respuesta era: {respuesta_correcta}")
    return False

preguntas = [
    {
        "pregunta": "¿Qué color obtienes mezclando azul y amarillo?",
        "opciones": ["Verde", "Naranja", "Morado", "Café"],
        "respuesta": "Verde"
    },
    {
        "pregunta": "¿Qué color representa el sol?",
        "opciones": ["Rojo", "Verde", "Amarillo", "Azul"],
        "respuesta": "Amarillo"
    }
    # Agrega más preguntas aquí
]

puntos = 0
print("🎨 ¡Quiz de Colores! 🎨")

for pregunta in preguntas:
    if mostrar_pregunta(pregunta["pregunta"], 
                       pregunta["opciones"], 
                       pregunta["respuesta"]):
        puntos += 1

print(f"\nPuntaje final: {puntos}/{len(preguntas)}")
```

## 🎯 Ejercicios y Retos

1. **Mejora el Juego del Adivino**:
   - Agrega niveles de dificultad
   - Incluye pistas más específicas
   - Agrega efectos de sonido

2. **Expande Piedra, Papel o Tijeras**:
   - Agrega nuevos elementos (lagarto, Spock)
   - Crea un modo torneo
   - Guarda récords

3. **Personaliza la Serpiente**:
   - Agrega diferentes tipos de comida
   - Incluye obstáculos
   - Haz que la serpiente crezca

## 🌟 Proyecto Final: ¡Tu Propio Juego!

Crea un juego usando lo que has aprendido:
1. Debe tener un sistema de puntos
2. Debe usar bucles y condiciones
3. Debe ser interactivo
4. ¡Debe ser divertido!

## 🤔 Ideas para Tu Juego

1. **Trivia de Temas que Te Gusten**:
   - Deportes
   - Películas
   - Animales

2. **Juego de Memoria**:
   - Secuencia de colores
   - Números
   - Palabras

3. **Aventura de Texto**:
   - Diferentes caminos
   - Tesoros escondidos
   - Monstruos que vencer

## 🎮 Consejos para Crear Juegos

1. Empieza simple
2. Prueba tu juego frecuentemente
3. Agrega características poco a poco
4. ¡Sé creativo!

## 🏆 Desafíos Extra

1. Agrega un sistema de vidas
2. Crea un menú principal
3. Guarda las mejores puntuaciones
4. Agrega efectos especiales (emojis, colores)

¡Felicitaciones! 🎉 
¡Has completado el Capítulo 3 y ahora eres un creador de juegos! 🎮

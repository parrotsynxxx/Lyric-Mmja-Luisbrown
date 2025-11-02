🎵 Terminal Visual Song
Un proyecto visual y musical para terminal hecho en Python
📖 Descripción general

Terminal Visual Song es un proyecto artístico desarrollado en Python 3 y diseñado para ejecutarse directamente desde la terminal.
Fue creado en Visual Studio Code como una demostración de cómo el texto, el color y el tiempo pueden combinarse para generar animaciones con ritmo dentro de un entorno CLI.

Este script imprime letras de canciones o mensajes personalizados con efectos de escritura lenta, degradados de color y arte ASCII animado.
No necesita librerías externas ni dependencias: solo el módulo estándar de Python.

🧠 Características principales

💡 Efecto de escritura tipo máquina (letra por letra).

🌈 Colores ANSI brillantes y degradados dinámicos.

🖼️ Banner ASCII animado en cian.

🎶 Reproducción rítmica de texto (ideal para letras o poemas).

🔁 Gradientes animados con cambio progresivo de color.

⚙️ Control de interrupciones (Ctrl + C) limpio y seguro.

🧱 Código estructurado en funciones modulares.

🖋️ Compatible con Windows, Linux y macOS (terminal ANSI).

✏️ Fácilmente personalizable (nombre, texto, colores, velocidad).

🧩 Requisitos

Antes de ejecutar, asegúrate de tener:

Python 3.7 o superior

Una terminal con soporte ANSI (colores y secuencias de escape)

Visual Studio Code o cualquier editor con terminal integrada

En Windows, para activar los colores ANSI en CMD clásico, puedes correr:

reg add HKCU\Console /v VirtualTerminalLevel /t REG_DWORD /d 1

⚙️ Instalación

Clona este repositorio:

git clone https://github.com/TU_USUARIO/Terminal-Visual-Song.git


Entra en el directorio:

cd Terminal-Visual-Song


Ejecuta el script:

python main.py


o en algunos sistemas:

python3 main.py

🕹️ Cómo usarlo

Al iniciar, el programa limpia la pantalla y muestra un banner animado con el logo ASCII.
Después despliega efectos visuales en la terminal y reproduce las frases de la canción letra por letra, usando diferentes colores para cada línea.

🔹 Si tienes la versión actual con entrada dinámica, puedes escribir:

Introduce el nombre: Carolina
Nombre de la canción favorita: Morado


El programa mostrará:

CANCION FAVORITA DE "CAROLINA"


y luego las letras o versos animados en diferentes colores.

🧩 Personalización

Puedes modificar fácilmente las siguientes partes del código:

Nombre y canción:
Edita directamente en la función main() o usa input() para pedirlos.

Versos o texto:
Cambia las líneas dentro de la lista versos para usar tus propias frases.

Colores:
En la clase Color, ajusta las variables ANSI para cambiar la paleta.

Velocidad de escritura:
Modifica el parámetro speed en las funciones print_line() o type_effect().

Gradientes:
Cambia la lista de colores dentro de gradient_line() para lograr nuevos efectos.

🖼️ Ejemplo de ejecución
$ python3 main.py


Salida visual esperada (fragmento):

███╗   ███╗███╗   ███╗     ██╗ █████╗
████╗ ████║████╗ ████║     ██║██╔══██╗
██╔████╔██║██╔████╔██║     ██║███████║
██║╚██╔╝██║██║╚██╔╝██║██   ██║██╔══██║
██║ ╚═╝ ██║██║ ╚═╝ ██║╚█████╔╝██║  ██║
╚═╝     ╚═╝╚═╝     ╚═╝ ╚════╝ ╚═╝  ╚═╝
═══════════════════════════════════════════════════════
CANCION FAVORITA DE "CAROLINA"
═══════════════════════════════════════════════════════
Ella quiere, aja, que yo la choque, aja
Que le de ZaZa, aja, también Percocet, aja
Siempre me tira, sí, aja, si dan la 12
...
═══════════════════════════════════════════════════════
By: Parrot Firewall SYN

🛠️ Estructura del código

Color: Clase que define todos los colores ANSI (rojo, verde, magenta, etc).

clear(): Limpia la pantalla antes de mostrar animaciones.

type_effect(): Imprime texto letra por letra con un retardo configurable.

print_line(): Envuelve type_effect() y agrega saltos de línea.

gradient_line(): Dibuja líneas con efecto degradado animado.

banner(): Genera el texto ASCII principal.

main(): Controla la secuencia completa del programa.

🧠 Conceptos técnicos aplicados

Secuencias ANSI para control de color y formato.

Manejo de buffers con sys.stdout.flush() para escritura controlada.

Control del tiempo con time.sleep() para efectos rítmicos.

Uso de clases para organización visual de constantes.

Estructura modular y buena práctica de separación de funciones.

💬 Créditos

Creado con ❤️ por Parrot Firewall SYN
Inspirado en la estética hacker, el arte ASCII y la creatividad de la terminal.
Diseñado, escrito y probado en Visual Studio Code con Python 3.

🧷 Licencia

Este proyecto puede compartirse, modificarse y distribuirse libremente bajo una licencia MIT o Creative Commons (elige según preferencia).

🚀 Conclusión

Terminal Visual Song transforma una simple terminal en un escenario animado.
Cada línea cobra vida, cada color tiene ritmo, y cada segundo de espera construye una experiencia visual y emocional.
Es un ejemplo de cómo la programación puede ser también arte. 


CODIGO PYTHON A EJECUTAR:

import time
import sys

class Color:
    ROJO = '\033[38;5;196m'
    MAGENTA = '\033[38;5;201m'
    CYAN = '\033[38;5;51m'
    VERDE = '\033[38;5;46m'
    AMARILLO = '\033[38;5;226m'
    NARANJA = '\033[38;5;208m'
    MORADO = '\033[38;5;93m'
    AZUL = '\033[38;5;33m'
    RESET = '\033[0m'
    BOLD = '\033[1m'
    DIM = '\033[2m'

def clear():
    print('\033[2J\033[H', end='')

def type_effect(text, speed=0.04, color=''):
    sys.stdout.write(color + Color.BOLD)
    for char in text:
        sys.stdout.write(char)
        sys.stdout.flush()
        time.sleep(speed)
    sys.stdout.write(Color.RESET)

def print_line(text, speed=0.04, color='', end='\n'):
    type_effect(text, speed, color)
    sys.stdout.write(end)
    sys.stdout.flush()

def gradient_line(char, length, speed=0.005):
    colors = [Color.CYAN, Color.AZUL, Color.MORADO, Color.MAGENTA, Color.ROJO]
    for i in range(length):
        color = colors[i % len(colors)]
        sys.stdout.write(color + Color.BOLD + char)
        sys.stdout.flush()
        time.sleep(speed)
    print(Color.RESET)

def banner():
    clear()
    banner_text = """
    ███╗   ███╗███╗   ███╗     ██╗ █████╗ 
    ████╗ ████║████╗ ████║     ██║██╔══██╗
    ██╔████╔██║██╔████╔██║     ██║███████║
    ██║╚██╔╝██║██║╚██╔╝██║██   ██║██╔══██║
    ██║ ╚═╝ ██║██║ ╚═╝ ██║╚█████╔╝██║  ██║
    ╚═╝     ╚═╝╚═╝     ╚═╝ ╚════╝ ╚═╝  ╚═╝
    """
    for line in banner_text.split('\n'):
        print_line(line, 0.001, Color.CYAN)
    time.sleep(0.3)

def main():
    banner()
    
    print()
    gradient_line('═', 70)
    print()
    
    print_line('CANCION FAVORITA DE "coloca un nombre" ', 0.05, Color.AMARILLO)
    
    print()
    gradient_line('═', 70)
    print()
    time.sleep(0.5)
    
    print_line('M M J A', 0.12, Color.ROJO)
    print()
    time.sleep(0.8)
    
    gradient_line('━', 70, 0.008)
    print()
    time.sleep(0.4)
    
    print_line('LUIS BROWN', 0.08, Color.VERDE)
    print()
    time.sleep(0.6)
    
    # Verso completo con ritmo
    print_line('Ella quiere, aja, que yo la choque, aja', 0.045, Color.CYAN)
    time.sleep(0.35)
    
    print_line('Que le de ZaZa, aja, tambien Percocet, aja', 0.045, Color.MAGENTA)
    time.sleep(0.35)
    
    print_line('Siempre me tira, si, aja, si dan la 12', 0.045, Color.VERDE)
    time.sleep(0.35)
    
    print_line('Quiere sentirlo, que esta harta de ese hombre', 0.045, Color.NARANJA)
    time.sleep(0.35)
    
    print_line('Viendo mi video, ella se pajea a mi nombre', 0.045, Color.AMARILLO)
    time.sleep(0.35)
    
    print_line('El dizque la prende, quiero verlo, en donde', 0.045, Color.MORADO)
    time.sleep(0.35)
    
    print_line("No son malo', na', si salimo' se esconden", 0.045, Color.AZUL)
    time.sleep(0.35)
    
    print_line('Ella vive tirando a uno que no le responde', 0.045, Color.ROJO)
    time.sleep(1)
    
    print()
    gradient_line('━', 70, 0.008)
    print()
    time.sleep(0.5)
    
    gradient_line('═', 70)
    print()
    
    sys.stdout.write(' ' * 18)
    colors = [Color.CYAN, Color.MAGENTA, Color.AMARILLO, Color.VERDE, Color.ROJO]
    credit_text = 'By: Parrot Firewall SYN'
    for i, char in enumerate(credit_text):
        color = colors[i % len(colors)]
        sys.stdout.write(color + Color.BOLD + char)
        sys.stdout.flush()
        time.sleep(0.06)
    print(Color.RESET)
    
    print()
    gradient_line('═', 70)
    print()
    
    time.sleep(0.3)

if __name__ == '__main__':
    try:
        main()
    except KeyboardInterrupt:
        print(f'\n{Color.ROJO}{Color.BOLD}Saliendo...{Color.RESET}\n')
        sys.exit(0)

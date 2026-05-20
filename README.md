# Visualizador de Tiempo

Aplicación web desarrollada en Angular que muestra la hora actual en **once representaciones visuales distintas**, desde un reloj analógico clásico hasta un reloj binario o uno que escribe la hora en palabras. Incluye un sistema de autenticación con rutas protegidas.

## Características

- **11 visualizaciones de la hora**, cada una como un componente independiente:

  | Reloj | Descripción |
  |-------|-------------|
  | Analógico | Reloj de manecillas clásico |
  | Digital | Hora en formato numérico |
  | Binario | La hora representada en binario |
  | Hexadecimal | La hora representada en hexadecimal |
  | Palabras | La hora escrita en texto |
  | Terminal | Estilo consola/terminal |
  | Anillo | Anillos de progreso concéntricos |
  | Progreso | Barras de avance del día |
  | Grilla | Cuadrícula de puntos |
  | Tacómetro | Estilo medidor automotriz |
  | Cielo | Representación ambiental día/noche |

- **Sistema de autenticación** — registro e inicio de sesión en una sola pantalla, con persistencia en LocalStorage.
- **Rutas protegidas** — un *route guard* impide el acceso al visualizador sin haber iniciado sesión.
- **Flujo de tiempo reactivo** — un servicio central emite la hora de forma continua mediante RxJS, y todos los relojes se actualizan a partir de esa misma fuente.

## Stack tecnológico

- **Angular 21** — componentes *standalone*.
- **TypeScript**
- **RxJS** — flujo reactivo del tiempo.
- **LocalStorage** — persistencia de usuarios.

## Arquitectura

```
src/app/
├── core/                   # Servicios e infraestructura
│   ├── time.service.ts     # Emite la hora de forma reactiva (RxJS)
│   ├── auth.service.ts     # Registro e inicio de sesión
│   └── auth.guard.ts       # Protección de rutas
├── auth/                   # Pantalla de autenticación
└── visualizer/             # Vista principal del visualizador
    ├── analog-clock/       # Un componente por cada estilo de reloj
    ├── binary-clock/
    ├── digital-clock/
    └── ...                 # (11 relojes en total)
```

El `TimeService` centraliza la única fuente de la hora; cada componente de reloj se suscribe a ese flujo, evitando que cada uno mantenga su propio temporizador.

## Requisitos

- Node.js 18 o superior
- Angular CLI

## Instalación y ejecución

```bash
# Instalar dependencias
npm install

# Iniciar el servidor de desarrollo
ng serve
```

Luego abre `http://localhost:4200` en el navegador.

```bash
# Compilar para producción
ng build
```

## Autor

**Luis Fernando Chunwa Chow Cheung**
Estudiante de Ingeniería en Computación — Universidad Rafael Urdaneta
GitHub: [@LuisChow](https://github.com/LuisChow)

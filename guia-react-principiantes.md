# 🚀 Guía de React para Principiantes: De HTML a Componentes Dinámicos

## 📖 Introducción

¡Bienvenido al mundo de React! Si ya conoces HTML y algo de Tailwind CSS, estás en el lugar perfecto para dar tu siguiente gran paso en el desarrollo web. Esta guía te llevará desde conceptos básicos hasta crear aplicaciones dinámicas sin necesidad de conocimientos previos de JavaScript avanzado.

**¿Qué aprenderás?**
- Qué son los componentes de React y cómo crearlos
- Cómo mostrar listas de información de forma dinámica
- Cómo pasar datos entre componentes usando props
- Técnicas para filtrar y mostrar información específica

---

## 🧩 Capítulo 1: ¿Qué son los Componentes en React?

### Piensa en HTML, pero con superpoderes

Si conoces HTML, ya entiendes el concepto básico de los componentes. En HTML escribes:

```html
<div>
  <h1>Mi título</h1>
  <p>Mi párrafo</p>
</div>
```

En React, puedes crear tus **propias etiquetas personalizadas**:

```jsx
<MiComponente />
```

### ¿Qué es un componente?

Un componente es como crear tu propia etiqueta HTML personalizada. Es una función que devuelve código que se parece a HTML (llamado JSX).

**Ejemplo básico:**

```jsx
// Esto es un componente
function Saludo() {
  return (
    <div>
      <h1>¡Hola mundo!</h1>
      <p>Este es mi primer componente</p>
    </div>
  );
}
```

### Usando componentes dentro de otros componentes

```jsx
function App() {
  return (
    <div>
      <Saludo />
      <Saludo />
      <Saludo />
    </div>
  );
}
```

**Resultado:** Se mostrarán 3 saludos idénticos.

### 🎯 Punto clave
Los componentes son como **moldes reutilizables**. Una vez que creas un molde, puedes usarlo cuantas veces quieras.

---

## 📦 Capítulo 2: Configurando tu Primer Proyecto

### Paso 1: Crear el proyecto

Abre tu terminal y ejecuta estos comandos **uno por uno**:

```bash
# Crear el proyecto
npm create vite@latest mi-proyecto-react -- --template react

# Entrar a la carpeta del proyecto
cd mi-proyecto-react

# Instalar las dependencias
npm install
```

### Paso 2: Abrir en VSCode

```bash
# Abrir el proyecto en VSCode
code .
```

### Paso 3: Iniciar el servidor

```bash
# Iniciar el servidor de desarrollo
npm run dev
```

**¡Listo!** Tu navegador debería abrir automáticamente en `http://localhost:5173`

### Paso 4: Limpiar archivos iniciales

Borra todo el contenido de `src/App.jsx` y reemplázalo con:

```jsx
function App() {
  return (
    <div className="p-8">
      <h1 className="text-2xl font-bold">¡Mi primera app de React!</h1>
    </div>
  );
}

export default App;
```

---

## 🔄 Capítulo 3: Introducción a .map() y Props

### ¿Qué es .map()?

Imagina que tienes una lista de amigos y quieres crear una tarjeta para cada uno. En lugar de escribir el HTML manualmente para cada amigo, `.map()` lo hace automáticamente.

**Ejemplo visual:**

```jsx
// Tengo esta lista de amigos
const amigos = ["Ana", "Carlos", "María"];

// .map() toma cada nombre y crea algo con él
amigos.map((nombre) => <p>Hola {nombre}</p>);

// Resultado: 
// <p>Hola Ana</p>
// <p>Hola Carlos</p>
// <p>Hola María</p>
```

### ¿Qué son los Props?

Los props son como **argumentos** que le pasas a un componente para personalizarlo.

**Analogía:** Si un componente es un molde para hacer galletas, los props son los ingredientes que cambias para hacer diferentes tipos de galletas.

```jsx
// Componente que recibe props
function TarjetaPersona(props) {
  return (
    <div className="border p-4 rounded">
      <h2>{props.nombre}</h2>
      <p>{props.edad} años</p>
    </div>
  );
}

// Uso del componente con diferentes props
function App() {
  return (
    <div>
      <TarjetaPersona nombre="Ana" edad="25" />
      <TarjetaPersona nombre="Carlos" edad="30" />
    </div>
  );
}
```

### 🔍 Usando console.log() para entender

```jsx
function TarjetaPersona(props) {
  // Esto te muestra qué props recibe el componente
  console.log("Props recibidos:", props);
  
  return (
    <div className="border p-4 rounded">
      <h2>{props.nombre}</h2>
      <p>{props.edad} años</p>
    </div>
  );
}
```

**¡Importante!** Abre las herramientas de desarrollo de tu navegador (F12) y mira la pestaña "Console" para ver los mensajes.

---

## 🏎️ Ejercicio 1: Pilotos de Fórmula 1

### 🎯 Objetivo
Crear una lista de pilotos de F1 con información básica.

### Código inicial

```jsx
function TarjetaPiloto(props) {
  // 🔍 Descomenta esta línea para ver qué props recibe
  // console.log("Props del piloto:", props);
  
  return (
    <div className="bg-white border-2 border-gray-200 rounded-lg p-4 shadow-md">
      <h3 className="text-xl font-bold text-red-600">{props.nombre}</h3>
      <p className="text-gray-600">Equipo: {props.equipo}</p>
    </div>
  );
}

function App() {
  const pilotos = [
    { nombre: "Max Verstappen", equipo: "Red Bull Racing" },
    { nombre: "Lewis Hamilton", equipo: "Mercedes" },
    { nombre: "Charles Leclerc", equipo: "Ferrari" },
    { nombre: "Lando Norris", equipo: "McLaren" },
    { nombre: "George Russell", equipo: "Mercedes" },
    { nombre: "Carlos Sainz", equipo: "Ferrari" },
    { nombre: "Fernando Alonso", equipo: "Aston Martin" }
  ];

  return (
    <div className="min-h-screen bg-gray-100 p-8">
      <h1 className="text-3xl font-bold text-center mb-8">🏎️ Pilotos de F1 2024</h1>
      
      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        {pilotos.map((piloto) => (
          <TarjetaPiloto 
            nombre={piloto.nombre} 
            equipo={piloto.equipo}
          />
        ))}
      </div>
    </div>
  );
}

export default App;
```

### 🚀 Desafío para ti
1. Descomenta la línea del `console.log()` y observa qué información recibe cada componente
2. Agrega un nuevo piloto a la lista
3. Cambia los estilos de las tarjetas usando Tailwind CSS

---

## 🔬 Ejercicio 2: Personajes de The Big Bang Theory

### 🎯 Objetivo
Agregar más props y comenzar a trabajar con datos más complejos.

### Código inicial

```jsx
function TarjetaPersonaje(props) {
  return (
    <div className="bg-gradient-to-br from-blue-50 to-purple-50 border border-purple-200 rounded-xl p-6 shadow-lg">
      <div className="text-center">
        <div className="text-4xl mb-2">{props.emoji}</div>
        <h3 className="text-xl font-bold text-purple-800">{props.nombre}</h3>
        <p className="text-purple-600 font-medium">{props.profesion}</p>
        <p className="text-gray-600 mt-2">{props.descripcion}</p>
      </div>
    </div>
  );
}

function App() {
  const personajes = [
    { 
      nombre: "Sheldon Cooper", 
      profesion: "Físico Teórico", 
      descripcion: "Genio obsesivo con falta de habilidades sociales",
      emoji: "🤓"
    },
    { 
      nombre: "Leonard Hofstadter", 
      profesion: "Físico Experimental", 
      descripcion: "El más normal del grupo",
      emoji: "👨‍🔬"
    },
    { 
      nombre: "Penny", 
      profesion: "Actriz/Camarera", 
      descripcion: "Vecina y mejor amiga del grupo",
      emoji: "👱‍♀️"
    },
    { 
      nombre: "Howard Wolowitz", 
      profesion: "Ingeniero Aeroespacial", 
      descripcion: "Ingeniero con complejo de mamá",
      emoji: "👨‍🚀"
    },
    { 
      nombre: "Raj Koothrappali", 
      profesion: "Astrofísico", 
      descripcion: "No puede hablar con mujeres (sin alcohol)",
      emoji: "🔭"
    },
    { 
      nombre: "Amy Farrah Fowler", 
      profesion: "Neurobióloga", 
      descripcion: "Novia de Sheldon, igual de peculiar",
      emoji: "🧠"
    },
    { 
      nombre: "Bernadette", 
      profesion: "Microbióloga", 
      descripcion: "Esposa de Howard, pequeña pero temible",
      emoji: "🔬"
    }
  ];

  console.log("Lista completa de personajes:", personajes);

  return (
    <div className="min-h-screen bg-gradient-to-br from-blue-100 to-purple-100 p-8">
      <h1 className="text-4xl font-bold text-center mb-2 text-purple-800">
        🧪 The Big Bang Theory
      </h1>
      <p className="text-center text-purple-600 mb-8">Los genios más divertidos de la TV</p>
      
      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 max-w-6xl mx-auto">
        {personajes.map((personaje) => (
          <TarjetaPersonaje 
            nombre={personaje.nombre}
            profesion={personaje.profesion}
            descripcion={personaje.descripcion}
            emoji={personaje.emoji}
          />
        ))}
      </div>
    </div>
  );
}

export default App;
```

### 🚀 Desafío para ti
1. Agrega una prop nueva llamada `coeficienteIntelectual` a algunos personajes
2. Modifica el componente para mostrar el CI si existe
3. Experimenta cambiando los emojis y descripciones

---

## ⚔️ Ejercicio 3: Piratas del Caribe - Datos Anidados

### 🎯 Objetivo
Aprender a trabajar con objetos que tienen propiedades anidadas (objetos dentro de objetos).

### Código inicial

```jsx
function TarjetaPirata(props) {
  console.log("Datos del pirata:", props);
  
  return (
    <div className="bg-gradient-to-br from-amber-50 to-red-50 border-2 border-amber-400 rounded-lg p-6 shadow-xl">
      <div className="text-center">
        <div className="text-5xl mb-3">{props.emoji}</div>
        <h3 className="text-2xl font-bold text-amber-800">{props.nombre}</h3>
        <p className="text-red-700 font-bold">{props.titulo}</p>
        
        {/* Accediendo a propiedades anidadas */}
        <div className="mt-4 bg-amber-100 p-3 rounded">
          <h4 className="font-bold text-amber-800">⚔️ Habilidades</h4>
          <p>Espada: {props.habilidades.espada}/10</p>
          <p>Navegación: {props.habilidades.navegacion}/10</p>
          <p>Liderazgo: {props.habilidades.liderazgo}/10</p>
        </div>
        
        <div className="mt-3 bg-red-100 p-3 rounded">
          <h4 className="font-bold text-red-800">🚢 Barco</h4>
          <p>{props.barco.nombre}</p>
          <p className="text-sm text-gray-600">{props.barco.tipo}</p>
        </div>
      </div>
    </div>
  );
}

function App() {
  const piratas = [
    {
      nombre: "Jack Sparrow",
      titulo: "Capitán del Perla Negra",
      emoji: "🏴‍☠️",
      habilidades: {
        espada: 8,
        navegacion: 10,
        liderazgo: 7
      },
      barco: {
        nombre: "Perla Negra",
        tipo: "Galeón"
      }
    },
    {
      nombre: "Barbossa",
      titulo: "Capitán Maldito",
      emoji: "💀",
      habilidades: {
        espada: 9,
        navegacion: 8,
        liderazgo: 9
      },
      barco: {
        nombre: "Perla Negra",
        tipo: "Galeón"
      }
    },
    {
      nombre: "Will Turner",
      titulo: "Herrero y Pirata",
      emoji: "⚔️",
      habilidades: {
        espada: 10,
        navegacion: 6,
        liderazgo: 8
      },
      barco: {
        nombre: "Holandés Errante",
        tipo: "Barco Fantasma"
      }
    },
    {
      nombre: "Elizabeth Swann",
      titulo: "Rey de los Piratas",
      emoji: "👑",
      habilidades: {
        espada: 7,
        navegacion: 7,
        liderazgo: 10
      },
      barco: {
        nombre: "Emperatriz",
        tipo: "Junco Chino"
      }
    },
    {
      nombre: "Davy Jones",
      titulo: "Señor de los Mares",
      emoji: "🐙",
      habilidades: {
        espada: 9,
        navegacion: 10,
        liderazgo: 10
      },
      barco: {
        nombre: "Holandés Errante",
        tipo: "Barco Fantasma"
      }
    },
    {
      nombre: "Blackbeard",
      titulo: "El Pirata más Temido",
      emoji: "🔥",
      habilidades: {
        espada: 10,
        navegacion: 9,
        liderazgo: 9
      },
      barco: {
        nombre: "Venganza de la Reina Ana",
        tipo: "Fragata"
      }
    },
    {
      nombre: "Angelica",
      titulo: "Hija de Blackbeard",
      emoji: "⚡",
      habilidades: {
        espada: 8,
        navegacion: 7,
        liderazgo: 8
      },
      barco: {
        nombre: "Venganza de la Reina Ana",
        tipo: "Fragata"
      }
    }
  ];

  return (
    <div className="min-h-screen bg-gradient-to-br from-blue-900 to-amber-900 p-8">
      <h1 className="text-4xl font-bold text-center mb-2 text-amber-300">
        🏴‍☠️ Piratas del Caribe
      </h1>
      <p className="text-center text-amber-100 mb-8">Los más legendarios bucaneros de los siete mares</p>
      
      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 max-w-7xl mx-auto">
        {piratas.map((pirata) => (
          <TarjetaPirata 
            nombre={pirata.nombre}
            titulo={pirata.titulo}
            emoji={pirata.emoji}
            habilidades={pirata.habilidades}
            barco={pirata.barco}
          />
        ))}
      </div>
    </div>
  );
}

export default App;
```

### 🚀 Desafío para ti
1. Observa en la consola cómo se ven los objetos anidados
2. Agrega una nueva propiedad `tesoro` con `cantidad` y `tipo`
3. Modifica el componente para mostrar información del tesoro

---

## 🧙‍♂️ Ejercicio 4: El Señor de los Anillos - Introducción a .filter()

### 🎯 Objetivo
Aprender a usar `.filter()` junto con `.map()` para mostrar solo ciertos elementos.

### ¿Qué hace .filter()?

`.filter()` es como un colador que solo deja pasar los elementos que cumplen una condición.

```jsx
// Ejemplo básico
const numeros = [1, 2, 3, 4, 5];
const numerosPares = numeros.filter((numero) => numero % 2 === 0);
// Resultado: [2, 4]
```

### Código inicial

```jsx
function TarjetaPersonaje(props) {
  // Función para mostrar el color según la raza
  const obtenerColorRaza = (raza) => {
    switch(raza) {
      case "Hobbit": return "bg-green-100 border-green-400 text-green-800";
      case "Humano": return "bg-blue-100 border-blue-400 text-blue-800";
      case "Elfo": return "bg-purple-100 border-purple-400 text-purple-800";
      case "Enano": return "bg-red-100 border-red-400 text-red-800";
      case "Mago": return "bg-yellow-100 border-yellow-400 text-yellow-800";
      default: return "bg-gray-100 border-gray-400 text-gray-800";
    }
  };

  return (
    <div className="bg-gradient-to-br from-amber-50 to-orange-50 border-2 border-amber-400 rounded-lg p-6 shadow-lg">
      <div className="text-center">
        <div className="text-4xl mb-2">{props.emoji}</div>
        <h3 className="text-xl font-bold text-amber-800">{props.nombre}</h3>
        
        <div className={`inline-block px-3 py-1 rounded-full text-sm font-bold mt-2 ${obtenerColorRaza(props.raza)}`}>
          {props.raza}
        </div>
        
        <p className="mt-3 text-gray-700">{props.descripcion}</p>
        
        <div className="mt-4 bg-amber-100 p-3 rounded">
          <h4 className="font-bold text-amber-800">⚔️ Arma</h4>
          <p>{props.arma}</p>
        </div>
        
        <div className="mt-2 bg-orange-100 p-3 rounded">
          <h4 className="font-bold text-orange-800">🏠 Origen</h4>
          <p>{props.origen}</p>
        </div>
      </div>
    </div>
  );
}

function App() {
  const personajes = [
    {
      nombre: "Frodo Baggins",
      raza: "Hobbit",
      descripcion: "Portador del Anillo Único",
      arma: "Dardo y Mithril",
      origen: "Bolsón Cerrado",
      emoji: "🧙‍♂️"
    },
    {
      nombre: "Aragorn",
      raza: "Humano",
      descripcion: "Rey de Gondor",
      arma: "Andúril",
      origen: "Gondor",
      emoji: "👑"
    },
    {
      nombre: "Legolas",
      raza: "Elfo",
      descripcion: "Príncipe de los Elfos del Bosque",
      arma: "Arco Élfico",
      origen: "Reino del Bosque",
      emoji: "🏹"
    },
    {
      nombre: "Gimli",
      raza: "Enano",
      descripcion: "Guerrero de la Montaña Solitaria",
      arma: "Hacha de Guerra",
      origen: "Erebor",
      emoji: "⚔️"
    },
    {
      nombre: "Gandalf",
      raza: "Mago",
      descripcion: "El Gris que se volvió Blanco",
      arma: "Bastón y Glamdring",
      origen: "Valinor",
      emoji: "🧙‍♂️"
    },
    {
      nombre: "Boromir",
      raza: "Humano",
      descripcion: "Hijo del Senescal de Gondor",
      arma: "Espada y Escudo",
      origen: "Minas Tirith",
      emoji: "🛡️"
    },
    {
      nombre: "Sam Gamyi",
      raza: "Hobbit",
      descripcion: "Fiel jardinero y amigo",
      arma: "Dardo",
      origen: "Bolsón Cerrado",
      emoji: "🌱"
    }
  ];

  // 🔍 Filtrar solo Hobbits
  const hobbits = personajes.filter((personaje) => personaje.raza === "Hobbit");
  console.log("Solo Hobbits:", hobbits);
  
  // 🔍 Filtrar solo Humanos
  const humanos = personajes.filter((personaje) => personaje.raza === "Humano");
  console.log("Solo Humanos:", humanos);

  return (
    <div className="min-h-screen bg-gradient-to-br from-amber-900 to-orange-900 p-8">
      <h1 className="text-4xl font-bold text-center mb-2 text-amber-300">
        💍 El Señor de los Anillos
      </h1>
      <p className="text-center text-amber-100 mb-8">La Comunidad del Anillo</p>
      
      {/* Mostrar todos los personajes */}
      <div className="mb-12">
        <h2 className="text-2xl font-bold text-amber-300 mb-4 text-center">🌟 Todos los Personajes</h2>
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 max-w-7xl mx-auto">
          {personajes.map((personaje) => (
            <TarjetaPersonaje 
              nombre={personaje.nombre}
              raza={personaje.raza}
              descripcion={personaje.descripcion}
              arma={personaje.arma}
              origen={personaje.origen}
              emoji={personaje.emoji}
            />
          ))}
        </div>
      </div>

      {/* Mostrar solo Hobbits */}
      <div className="mb-12">
        <h2 className="text-2xl font-bold text-green-300 mb-4 text-center">🌿 Solo Hobbits</h2>
        <div className="grid grid-cols-1 md:grid-cols-2 gap-6 max-w-4xl mx-auto">
          {hobbits.map((hobbit) => (
            <TarjetaPersonaje 
              nombre={hobbit.nombre}
              raza={hobbit.raza}
              descripcion={hobbit.descripcion}
              arma={hobbit.arma}
              origen={hobbit.origen}
              emoji={hobbit.emoji}
            />
          ))}
        </div>
      </div>

      {/* Mostrar solo Humanos */}
      <div>
        <h2 className="text-2xl font-bold text-blue-300 mb-4 text-center">👑 Solo Humanos</h2>
        <div className="grid grid-cols-1 md:grid-cols-2 gap-6 max-w-4xl mx-auto">
          {humanos.map((humano) => (
            <TarjetaPersonaje 
              nombre={humano.nombre}
              raza={humano.raza}
              descripcion={humano.descripcion}
              arma={humano.arma}
              origen={humano.origen}
              emoji={humano.emoji}
            />
          ))}
        </div>
      </div>
    </div>
  );
}

export default App;
```

### 🚀 Desafío para ti
1. Crea un filtro para mostrar solo Elfos y Magos
2. Experimenta filtrando por el origen de los personajes
3. Observa en la consola cómo `.filter()` crea nuevos arrays

---

## ⚡ Ejercicio 5: Harry Potter - Datos Complejos y Renderizado Condicional

### 🎯 Objetivo
Trabajar con estructuras de datos complejas, arrays dentro de objetos y renderizado condicional.

### Código inicial

```jsx
function TarjetaPersonaje(props) {
  // Función para obtener el color de la casa
  const obtenerColorCasa = (casa) => {
    switch(casa) {
      case "Gryffindor": return "bg-red-500 text-white";
      case "Slytherin": return "bg-green-600 text-white";
      case "Ravenclaw": return "bg-blue-500 text-white";
      case "Hufflepuff": return "bg-yellow-500 text-black";
      default: return "bg-gray-500 text-white";
    }
  };

  return (
    <div className="bg-white border-2 border-purple-300 rounded-xl p-6 shadow-xl">
      <div className="text-center">
        <div className="text-4xl mb-2">{props.emoji}</div>
        <h3 className="text-xl font-bold text-purple-800">{props.nombre}</h3>
        
        {/* Renderizado condicional: solo mostrar casa si existe */}
        {props.casa && (
          <div className={`inline-block px-3 py-1 rounded-full text-sm font-bold mt-2 ${obtenerColorCasa(props.casa)}`}>
            {props.casa}
          </div>
        )}
        
        <p className="mt-3 text-gray-700">{props.descripcion}</p>
        
        {/* Mostrar hechizos (array dentro del objeto) */}
        <div className="mt-4 bg-purple-100 p-3 rounded">
          <h4 className="font-bold text-purple-800">✨ Hechizos Favoritos</h4>
          <div className="text-sm">
            {props.hechizos.map((hechizo) => (
              <span className="inline-block bg-purple-200 px-2 py-1 rounded m-1">
                {hechizo}
              </span>
            ))}
          </div>
        </div>
        
        {/* Mostrar características */}
        <div className="mt-3 bg-blue-100 p-3 rounded">
          <h4 className="font-bold text-blue-800">🎯 Características</h4>
          <div className="text-sm text-left">
            <p>Valentía: {props.atributos.valentia}/10</p>
            <p>Inteligencia: {props.atributos.inteligencia}/10</p>
            <p>Poder Mágico: {props.atributos.poderMagico}/10</p>
          </div>
        </div>

        {/* Renderizado condicional: mostrar varita solo si existe */}
        {props.varita && (
          <div className="mt-3 bg-amber-100 p-3 rounded">
            <h4 className="font-bold text-amber-800">🪄 Varita</h4>
            <p className="text-sm">{props.varita.descripcion}</p>
            <p className="text-xs text-gray-600">{props.varita.nucleo}</p>
          </div>
        )}
      </div>
    </div>
  );
}

function App() {
  const personajes = [
    {
      nombre: "Harry Potter",
      casa: "Gryffindor",
      descripcion: "El niño que vivió",
      emoji: "⚡",
      hechizos: ["Expelliarmus", "Expecto Patronum", "Lumos"],
      atributos: {
        valentia: 10,
        inteligencia: 7,
        poderMagico: 9
      },
      varita: {
        descripcion: "Acebo, 11 pulgadas",
        nucleo: "Pluma de fénix"
      }
    },
    {
      nombre: "Hermione Granger",
      casa: "Gryffindor",
      descripcion: "La bruja más brillante de su generación",
      emoji: "📚",
      hechizos: ["Wingardium Leviosa", "Alohomora", "Protean Charm"],
      atributos: {
        valentia: 8,
        inteligencia: 10,
        poderMagico: 9
      },
      varita: {
        descripcion: "Vid, 10¾ pulgadas",
        nucleo: "Fibra de corazón de dragón"
      }
    },
    {
      nombre: "Ron Weasley",
      casa: "Gryffindor",
      descripcion: "Fiel amigo y estratega de ajedrez",
      emoji: "♟️",
      hechizos: ["Sunshine, Daisies", "Eat Slugs", "Expelliarmus"],
      atributos: {
        valentia: 8,
        inteligencia: 6,
        poderMagico: 7
      },
      varita: {
        descripcion: "Sauce, 14 pulgadas",
        nucleo: "Pelo de unicornio"
      }
    },
    {
      nombre: "Draco Malfoy",
      casa: "Slytherin",
      descripcion: "Rival de Harry y heredero sangre pura",
      emoji: "🐍",
      hechizos: ["Serpensortia", "Tarantallegra", "Crucio"],
      atributos: {
        valentia: 6,
        inteligencia: 8,
        poderMagico: 8
      },
      varita: {
        descripcion: "Espino, 10 pulgadas",
        nucleo: "Pelo de unicornio"
      }
    },
    {
      nombre: "Luna Lovegood",
      casa: "Ravenclaw",
      descripcion: "Excéntrica y sabia soñadora",
      emoji: "🌙",
      hechizos: ["Expecto Patronum", "Stupefy", "Revelio"],
      atributos: {
        valentia: 7,
        inteligencia: 9,
        poderMagico: 8
      },
      varita: {
        descripcion: "Cerezo, 9 pulgadas",
        nucleo: "Pelo de thestrals"
      }
    },
    {
      nombre: "Neville Longbottom",
      casa: "Gryffindor",
      descripcion: "De tímido estudiante a héroe valiente",
      emoji: "🌱",
      hechizos: ["Petrificus Totalus", "Expelliarmus", "Stupefy"],
      atributos: {
        valentia: 9,
        inteligencia: 6,
        poderMagico: 7
      },
      varita: {
        descripcion: "Cerezo, 13 pulgadas",
        nucleo: "Pelo de unicornio"
      }
    },
    {
      nombre: "Severus Snape",
      casa: "Slytherin",
      descripcion: "Profesor de Pociones y espía doble",
      emoji: "🧪",
      hechizos: ["Sectumsempra", "Legilimens", "Protego"],
      atributos: {
        valentia: 8,
        inteligencia: 10,
        poderMagico: 10
      },
      varita: {
        descripcion: "Abedul, 13¼ pulgadas",
        nucleo: "Fibra de corazón de dragón"
      }
    },
    {
      nombre: "Dobby",
      casa: null, // Los elfos domésticos no tienen casa
      descripcion: "Elfo doméstico libre y leal amigo",
      emoji: "🧦",
      hechizos: ["Magia Élfica", "Aparición", "Levitación"],
      atributos: {
        valentia: 10,
        inteligencia: 7,
        poderMagico: 8
      },
      varita: null // Los elfos no usan varitas
    }
  ];

  // Filtros para diferentes criterios
  const estudiantesGryffindor = personajes.filter((p) => p.casa === "Gryffindor");
  const personajesPoderosos = personajes.filter((p) => p.atributos.poderMagico >= 9);
  const personajesConVarita = personajes.filter((p) => p.varita !== null);

  console.log("Estudiantes de Gryffindor:", estudiantesGryffindor);
  console.log("Personajes poderosos:", personajesPoderosos);

  return (
    <div className="min-h-screen bg-gradient-to-br from-purple-900 to-blue-900 p-8">
      <h1 className="text-4xl font-bold text-center mb-2 text-yellow-300">
        ⚡ Harry Potter
      </h1>
      <p className="text-center text-yellow-100 mb-8">El Mundo Mágico de Hogwarts</p>
      
      {/* Todos los personajes */}
      <div className="mb-12">
        <h2 className="text-2xl font-bold text-yellow-300 mb-4 text-center">🏰 Todos los Personajes</h2>
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 max-w-7xl mx-auto">
          {personajes.map((personaje) => (
            <TarjetaPersonaje 
              nombre={personaje.nombre}
              casa={personaje.casa}
              descripcion={personaje.descripcion}
              emoji={personaje.emoji}
              hechizos={personaje.hechizos}
              atributos={personaje.atributos}
              varita={personaje.varita}
            />
          ))}
        </div>
      </div>

      {/* Solo Gryffindor */}
      <div className="mb-12">
        <h2 className="text-2xl font-bold text-red-300 mb-4 text-center">🦁 Casa Gryffindor</h2>
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 max-w-7xl mx-auto">
          {estudiantesGryffindor.map((personaje) => (
            <TarjetaPersonaje 
              nombre={personaje.nombre}
              casa={personaje.casa}
              descripcion={personaje.descripcion}
              emoji={personaje.emoji}
              hechizos={personaje.hechizos}
              atributos={personaje.atributos}
              varita={personaje.varita}
            />
          ))}
        </div>
      </div>

      {/* Personajes poderosos */}
      <div className="mb-12">
        <h2 className="text-2xl font-bold text-purple-300 mb-4 text-center">💫 Magos Poderosos (Poder ≥ 9)</h2>
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 max-w-7xl mx-auto">
          {personajesPoderosos.map((personaje) => (
            <TarjetaPersonaje 
              nombre={personaje.nombre}
              casa={personaje.casa}
              descripcion={personaje.descripcion}
              emoji={personaje.emoji}
              hechizos={personaje.hechizos}
              atributos={personaje.atributos}
              varita={personaje.varita}
            />
          ))}
        </div>
      </div>

      {/* Solo personajes con varita */}
      <div>
        <h2 className="text-2xl font-bold text-amber-300 mb-4 text-center">🪄 Portadores de Varita</h2>
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 max-w-7xl mx-auto">
          {personajesConVarita.map((personaje) => (
            <TarjetaPersonaje 
              nombre={personaje.nombre}
              casa={personaje.casa}
              descripcion={personaje.descripcion}
              emoji={personaje.emoji}
              hechizos={personaje.hechizos}
              atributos={personaje.atributos}
              varita={personaje.varita}
            />
          ))}
        </div>
      </div>
    </div>
  );
}

export default App;
```

### 🚀 Desafío para ti
1. Crea un filtro para mostrar solo personajes de Slytherin
2. Filtra personajes por nivel de inteligencia (≥ 8)
3. Agrega un nuevo personaje con datos complejos
4. Experimenta con renderizado condicional en diferentes propiedades

---

## 🎯 Conceptos Clave Aprendidos

### ✅ Lo que ya dominas

1. **Componentes como funciones:** Crear componentes reutilizables que devuelven JSX
2. **Props:** Pasar datos entre componentes para personalizarlos
3. **Arrays y .map():** Renderizar listas dinámicamente
4. **Objetos anidados:** Acceder a propiedades dentro de propiedades
5. **Arrays dentro de objetos:** Mostrar listas de datos complejos
6. **Filtrado con .filter():** Mostrar solo elementos que cumplen condiciones
7. **Renderizado condicional:** Mostrar elementos solo cuando existen
8. **console.log():** Debuggear y entender el flujo de datos

### 🔄 Flujo de trabajo típico

```jsx
// 1. Datos (array de objetos)
const datos = [...];

// 2. Componente que recibe props
function MiComponente(props) {
  return <div>{props.nombre}</div>;
}

// 3. Renderizado con .map()
function App() {
  return (
    <div>
      {datos.map((item) => (
        <MiComponente nombre={item.nombre} />
      ))}
    </div>
  );
}
```

---

## 🚀 Próximos Pasos

¡Felicitaciones! Ya tienes las bases sólidas para crear aplicaciones React dinámicas. Ahora puedes:

### 🎨 Experimentar más
- Combina diferentes filtros usando && y ||
- Crea componentes más complejos con múltiples niveles de anidación
- Experimenta con diferentes estilos de Tailwind

### 📚 Aprender después
- **useState:** Para crear interactividad (botones, formularios)
- **useEffect:** Para cargar datos de APIs
- **Eventos:** onClick, onChange, etc.
- **Formularios:** Inputs, validación, envío de datos

### 🛠️ Proyectos sugeridos
1. **Catálogo de películas:** Con géneros, puntuaciones y filtros
2. **Lista de tareas:** Agregar, eliminar y marcar como completadas
3. **Galería de fotos:** Con categorías y búsqueda
4. **Dashboard de estadísticas:** Gráficos simples con datos

---

## 💡 Consejos Finales

### 🐛 Para debuggear
- Siempre usa `console.log()` para ver qué datos recibes
- Revisa la consola del navegador regularmente
- Verifica que los nombres de las propiedades coincidan exactamente

### 🎨 Para estilos
- Tailwind CSS es tu amigo: experimenta con colores, espaciado y diseño
- Usa las herramientas de desarrollo del navegador para inspeccionar elementos
- No tengas miedo de probar diferentes combinaciones

### 🚀 Para seguir aprendiendo
- Crea proyectos personales con temas que te interesen
- Modifica los ejercicios de esta guía con tus propios datos
- Busca inspiración en sitios web que uses diariamente

**¡Recuerda:** La programación se aprende programando. ¡No dejes de experimentar y crear!

---

*¡Feliz codificación! 🎉*

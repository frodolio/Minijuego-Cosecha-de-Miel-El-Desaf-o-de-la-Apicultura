# Minijuego-Cosecha-de-Miel-El-Desafio-de-la-Apicultura
# 🍯 Cosecha de Miel - El Desafío de la Apicultura

Bienvenido al minijuego **Cosecha de Miel**, una experiencia estratégica e individual desarrollada en **React**. Representa a tu facción, gestiona tus recursos, defiende tu colmena y recolecta la mayor cantidad de miel para alzarte como el campeón apícola 🐝.

---

## 🎮 ¿Cómo se juega?

### 👥 Participación
- Modo: **Solitario competitivo**, 1 jugador por facción.
- Facciones disponibles:
  - Nightshades
  - Sunflorians
  - Bumpkins
  - Goblins
- Requiere 1 jugador activo por facción para comenzar la partida.
- Entradas:
  - 1 entrada gratuita por jugador.
  - Hasta 2 entradas pagas (3 Flowers c/u).
  - Las Flowers se reintegran al ecosistema de Sunflower.

### 🎯 Objetivo
Recolectar la mayor cantidad de miel posible en un tiempo límite, defendiendo tu colmena y robando a otras. ¡El jugador con más miel al final gana!

---

## ⚙️ Mecánicas Principales

### 🗺️ Mapa y Colmenas
- Colmena propia (genera miel).
- Colmenas neutrales (disputadas).
- Colmenas enemigas (pueden ser saqueadas).

### 🍯 Recolección de Miel
- Cesto limitado (puede mejorar).
- Recolectas de:
  - Tu colmena.
  - Colmenas neutrales.
  - Colmenas enemigas.

### 🛡️ Defensa de la Colmena
- Plagas constantes.
- Herramientas:
  - Trampas, cercas, muros.

### 🐜 Ataques y Plagas
- Envío de plagas a rivales.
- Requiere estrategia y gestión.

### ⚔️ Interacción entre Facciones
- Robo de miel (si la colmena está desprotegida).
- Puedes perder miel si te atrapan.

---

## ⏱️ Fases del Juego

| Fase     | Duración  | Características principales |
|----------|-----------|-----------------------------|
| Inicial  | 0-5 min   | Plagas suaves, herramientas básicas |
| Media    | 5-10 min  | Más plagas, viento molesto, colmenas disputadas |
| Avanzada | 10-15 min | Plagas intensas, viento fuerte, robos agresivos |

---

## 🔧 Herramientas Desbloqueables

| Fase     | Herramientas |
|----------|--------------|
| Inicial  | Cesta pequeña, Trampa básica |
| Media    | Cesta mediana, Trampa avanzada, Cerca |
| Avanzada | Cesta grande, Muro protector, Trampa en área |

---

## 🥇 ¿Cómo se gana?

- El jugador con más miel al finalizar los 15 minutos.
- Desempate: se usan **misiones secundarias**.

### 🧩 Misiones de Desempate

1. **Protección Total**
2. **Colmena Invencible**
3. **Gran Robador de Miel**
4. **Recolección Maestra**

Si persiste el empate: minijuego extra de 1 minuto 🔥.

---

## 🧠 Ventajas del juego

- Competencia directa por recursos 🐝.
- Balance entre defensa, ataque y recolección.
- Participación activa con impacto real.
- Sistema progresivo y rejugabilidad.

---

## 🛠️ Tecnologías Usadas

- [React](https://reactjs.org/)
- [Tailwind CSS](https://tailwindcss.com/)
- [Framer Motion](https://www.framer.com/motion/)
- [Vite](https://vitejs.dev/)

---

## 🚀 ¿Cómo correr el juego localmente?

```bash
git clone https://github.com/tu-usuario/cosecha-de-miel.git
cd cosecha-de-miel
npm install
npm run dev

🤝 Cómo colaborar
Haz un fork del repositorio.

Crea una nueva rama: git checkout -b mejora-x.

Aplica tus cambios.

Haz un Pull Request.

¡Revisaremos y te daremos feedback!





1. Configuración inicial
Asegúrate de tener Node.js instalado en tu máquina. Luego, crea un proyecto de React usando Vite (es rápido y sencillo):

bash
Copiar
Editar
npm create vite@latest cosecha-de-miel --template react
cd cosecha-de-miel
npm install
Después, instala Tailwind CSS:

bash
Copiar
Editar
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init
Configura Tailwind editando el archivo tailwind.config.js para que se vea así:

js
Copiar
Editar
module.exports = {
  content: [
    "./index.html",
    "./src/**/*.{js,jsx,ts,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
Crea un archivo src/index.css con lo siguiente:

css
Copiar
Editar
@tailwind base;
@tailwind components;
@tailwind utilities;
Finalmente, importa el CSS en el archivo src/main.jsx:

javascript
Copiar
Editar
import React from 'react'
import ReactDOM from 'react-dom/client'
import './index.css'
import App from './App'

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
)
2. Código de la aplicación
Crea un archivo src/App.jsx con el siguiente código, que contiene una estructura básica para que puedas jugar al "Desafío de la Apicultura":
import { useState, useEffect } from 'react';

// Facciones
const factions = ["Nightshades", "Sunflorians", "Bumpkins", "Goblins"];

function App() {
  const [playerFaction, setPlayerFaction] = useState(null);
  const [honey, setHoney] = useState(0); // Miel recolectada
  const [plagues, setPlagues] = useState(0); // Plagas en el mapa
  const [basketCapacity, setBasketCapacity] = useState(10); // Capacidad inicial de cesto
  const [phase, setPhase] = useState(1); // Fase actual (1 - Inicial, 2 - Media, 3 - Avanzada)

  // Función para simular la recolección de miel
  const collectHoney = () => {
    if (honey < basketCapacity) {
      setHoney(honey + 1); // Se recolecta 1 unidad de miel
    }
  };

  // Función para simular la aparición de plagas
  const spawnPlagues = () => {
    if (Math.random() < 0.1) {
      setPlagues(plagues + 1); // Aumento de plagas
    }
  };

  // Actualiza las fases con el paso del tiempo
  useEffect(() => {
    const interval = setInterval(() => {
      if (phase === 1 && honey >= 10) {
        setPhase(2); // Avanzamos a la fase media si recolectas suficiente miel
      } else if (phase === 2 && honey >= 20) {
        setPhase(3); // Avanzamos a la fase avanzada
      }

      spawnPlagues();
    }, 1000); // Intervalo de 1 segundo para simular el tiempo de juego

    return () => clearInterval(interval); // Limpiar el intervalo cuando se desmonte el componente
  }, [honey, phase, plagues]);

  // Función para seleccionar la facción
  const handleFactionSelect = (faction) => {
    setPlayerFaction(faction);
  };

  return (
    <div className="min-h-screen flex flex-col items-center justify-center bg-yellow-100">
      <h1 className="text-4xl font-bold text-center text-green-800 mb-4">Cosecha de Miel - El Desafío de la Apicultura</h1>

      {playerFaction ? (
        <div className="text-center">
          <p className="text-xl font-medium mb-2">¡Bienvenido, {playerFaction}!</p>
          <p className="text-lg mb-4">Fase: {phase === 1 ? 'Inicial' : phase === 2 ? 'Media' : 'Avanzada'}</p>
          <p className="text-lg mb-2">Miel recolectada: {honey}</p>
          <p className="text-lg mb-2">Plagas: {plagues}</p>
          <button
            onClick={collectHoney}
            className="bg-green-600 text-white py-2 px-4 rounded mt-4 hover:bg-green-700"
          >
            Recolectar Miel
          </button>
        </div>
      ) : (
        <div className="text-center">
          <p className="text-xl font-medium mb-4">Selecciona tu facción para comenzar:</p>
          {factions.map((faction, index) => (
            <button
              key={index}
              onClick={() => handleFactionSelect(faction)}
              className="bg-blue-600 text-white py-2 px-4 rounded mb-2 hover:bg-blue-700"
            >
              {faction}
            </button>
          ))}
        </div>
      )}
    </div>
  );
}

export default App;

3. Explicación del código
Selección de facción: El jugador selecciona una facción de las disponibles, que luego se guarda en el estado playerFaction.

Recolección de miel: El jugador puede hacer clic en el botón para recolectar miel de su colmena. La cantidad de miel se guarda en honey.

Aparición de plagas: Cada segundo, el juego simula la aparición de plagas, aumentando el contador plagues de forma aleatoria.

Fases del juego: El juego tiene tres fases, que cambian dependiendo de cuánta miel haya recolectado el jugador. La fase se controla con el estado phase.

4. Próximos pasos
Con este código base, puedes expandir el juego agregando:

Defensas para las colmenas (trampas, cercas, muros protectores).

Interacción con otras facciones (robos de miel, defensa, ataques).

Sistema de misiones de desempate.




Código Completo del Juego
Aquí tienes el código completo en React para el juego "Cosecha de Miel". Puedes copiar este código y pegarlo en tu proyecto de React.

Estructura del Proyecto:
index.html (ubicado en la carpeta public)

App.jsx (principal componente del juego)

index.js (punto de entrada para renderizar la aplicación)

styles.css (opcional si deseas personalizar los estilos)

1. App.jsx (Componente Principal)
import React, { useState, useEffect } from "react";

// Facciones
const factions = ["Nightshades", "Sunflorians", "Bumpkins", "Goblins"];

function App() {
  const [playerFaction, setPlayerFaction] = useState(null);
  const [honey, setHoney] = useState(0); // Miel recolectada
  const [plagues, setPlagues] = useState(0); // Plagas en el mapa
  const [basketCapacity, setBasketCapacity] = useState(10); // Capacidad inicial de cesto
  const [phase, setPhase] = useState(1); // Fase actual (1 - Inicial, 2 - Media, 3 - Avanzada)
  const [defenses, setDefenses] = useState({
    trap: false,
    fence: false,
    wall: false,
  }); // Defensas de la colmena
  const [otherFactions, setOtherFactions] = useState({
    Nightshades: 0,
    Sunflorians: 0,
    Bumpkins: 0,
    Goblins: 0,
  }); // Miel de otras facciones
  const [flowers, setFlowers] = useState(0); // Recompensas (Flowers)

  // Función para simular la recolección de miel
  const collectHoney = () => {
    if (honey < basketCapacity) {
      setHoney(honey + 1); // Se recolecta 1 unidad de miel
    }
  };

  // Función para simular la aparición de plagas
  const spawnPlagues = () => {
    if (Math.random() < 0.1) {
      setPlagues(plagues + 1); // Aumento de plagas
    }
  };

  // Función para mejorar las defensas
  const upgradeDefense = (defense) => {
    setDefenses((prevDefenses) => ({
      ...prevDefenses,
      [defense]: true,
    }));
  };

  // Función para robar miel de otras facciones
  const stealHoney = (faction) => {
    if (otherFactions[faction] > 0) {
      const stolenAmount = Math.min(otherFactions[faction], 2);
      setHoney(honey + stolenAmount);
      setOtherFactions((prev) => ({
        ...prev,
        [faction]: prev[faction] - stolenAmount,
      }));
    }
  };

  // Función para obtener recompensas (Flowers)
  const earnFlowers = (amount) => {
    setFlowers(flowers + amount);
  };

  // Actualiza las fases con el paso del tiempo
  useEffect(() => {
    const interval = setInterval(() => {
      if (phase === 1 && honey >= 10) {
        setPhase(2); // Avanzamos a la fase media si recolectas suficiente miel
      } else if (phase === 2 && honey >= 20) {
        setPhase(3); // Avanzamos a la fase avanzada
      }

      spawnPlagues();
    }, 1000); // Intervalo de 1 segundo para simular el tiempo de juego

    return () => clearInterval(interval); // Limpiar el intervalo cuando se desmonte el componente
  }, [honey, phase, plagues]);

  // Función para seleccionar la facción
  const handleFactionSelect = (faction) => {
    setPlayerFaction(faction);
  };

  return (
    <div className="min-h-screen flex flex-col items-center justify-center bg-yellow-100">
      <h1 className="text-4xl font-bold text-center text-green-800 mb-4">
        Cosecha de Miel - El Desafío de la Apicultura
      </h1>

      {playerFaction ? (
        <div className="text-center">
          <p className="text-xl font-medium mb-2">
            ¡Bienvenido, {playerFaction}!
          </p>
          <p className="text-lg mb-4">
            Fase: {phase === 1 ? "Inicial" : phase === 2 ? "Media" : "Avanzada"}
          </p>
          <p className="text-lg mb-2">Miel recolectada: {honey}</p>
          <p className="text-lg mb-2">Plagas: {plagues}</p>

          {/* Botón para robar miel de otras facciones */}
          <div className="my-4">
            {factions
              .filter((faction) => faction !== playerFaction)
              .map((faction) => (
                <button
                  key={faction}
                  onClick={() => stealHoney(faction)}
                  className="bg-red-600 text-white py-2 px-4 rounded mb-2 hover:bg-red-700"
                >
                  Robar miel de {faction}
                </button>
              ))}
          </div>

          {/* Botón para recolectar miel */}
          <button
            onClick={collectHoney}
            className="bg-green-600 text-white py-2 px-4 rounded mt-4 hover:bg-green-700"
          >
            Recolectar Miel
          </button>

          {/* Mejora de defensas */}
          <div className="mt-4">
            <p className="text-lg">Defensas:</p>
            <button
              onClick={() => upgradeDefense("trap")}
              disabled={defenses.trap}
              className={`${
                defenses.trap ? "bg-gray-400" : "bg-yellow-600"
              } text-white py-2 px-4 rounded mb-2`}
            >
              {defenses.trap ? "Trampa de Insectos (Mejorada)" : "Mejorar Trampa"}
            </button>
            <button
              onClick={() => upgradeDefense("fence")}
              disabled={defenses.fence}
              className={`${
                defenses.fence ? "bg-gray-400" : "bg-green-600"
              } text-white py-2 px-4 rounded mb-2`}
            >
              {defenses.fence ? "Cerca de Flores (Mejorada)" : "Mejorar Cerca"}
            </button>
            <button
              onClick={() => upgradeDefense("wall")}
              disabled={defenses.wall}
              className={`${
                defenses.wall ? "bg-gray-400" : "bg-blue-600"
              } text-white py-2 px-4 rounded`}
            >
              {defenses.wall ? "Muro Protector (Mejorado)" : "Mejorar Muro"}
            </button>
          </div>

          {/* Mostrar las Flowers obtenidas */}
          <div className="mt-4">
            <p className="text-lg">Flowers: {flowers}</p>
          </div>

          {/* Ganar Flowers como recompensa */}
          <button
            onClick={() => earnFlowers(5)}
            className="bg-purple-600 text-white py-2 px-4 rounded mt-4 hover:bg-purple-700"
          >
            Ganar 5 Flowers como Recompensa
          </button>
        </div>
      ) : (
        <div className="text-center">
          <p className="text-xl font-medium mb-4">Selecciona tu facción:</p>
          {factions.map((faction, index) => (
            <button
              key={index}
              onClick={() => handleFactionSelect(faction)}
              className="bg-blue-600 text-white py-2 px-4 rounded mb-2 hover:bg-blue-700"
            >
              {faction}
            </button>
          ))}
        </div>
      )}
    </div>
  );
}

export default App;

Que nos falta para completar el código?
Necesitamos la API que se usa para recompensar con Marks a los jugadores
Configuración de la API de Sunflower Land: Primero, asegúrate de que tienes acceso a la API o al SDK de Sunflower Land. De ser necesario, revisa la documentación oficial de la API para obtener las credenciales adecuadas (por ejemplo, una clave de API o método de autenticación). Aquí un ejemplo de cómo podrías hacer una solicitud a una API REST.

Simulación de la funcionalidad de marcas (marks): Suponiendo que quieras agregar marcas a los jugadores que ganen, necesitarás un método para realizar una solicitud a la API y registrar la recompensa. Si los "marks" se otorgan por ganar una partida o al finalizar con éxito en una fase, el código para hacerlo podría lucir como sigue:

Ejemplo de implementación (asumiendo una API de Sunflower Land):
js
Copiar
Editar
import React, { useState, useEffect } from "react";

// Facciones
const factions = ["Nightshades", "Sunflorians", "Bumpkins", "Goblins"];

function App() {
  const [playerFaction, setPlayerFaction] = useState(null);
  const [honey, setHoney] = useState(0);
  const [marks, setMarks] = useState(0); // Marca de recompensa
  const [phase, setPhase] = useState(1);

  const handleVictory = async () => {
    // Suponiendo que la victoria se obtiene al alcanzar fase avanzada
    if (phase === 3) {
      try {
        const response = await fetch("https://api.sunflowerland.com/reward", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            // Agrega aquí cualquier cabecera de autenticación si es necesario
          },
          body: JSON.stringify({
            playerFaction: playerFaction,
            marks: 10, // Cantidad de marks a otorgar
          }),
        });
        
        const data = await response.json();

        if (data.success) {
          setMarks(marks + 10); // Aumenta los marks cuando se haya ganado
          alert("¡Felicidades, has ganado 10 marks!");
        } else {
          alert("Hubo un error al intentar otorgar la recompensa.");
        }
      } catch (error) {
        console.error("Error al otorgar marks:", error);
        alert("Hubo un error al conectarse con el servidor.");
      }
    }
  };

  useEffect(() => {
    if (honey >= 20) {
      setPhase(3); // Cambiar fase a avanzada
    }
  }, [honey]);

  return (
    <div className="min-h-screen flex flex-col items-center justify-center bg-yellow-100">
      <h1 className="text-4xl font-bold text-center text-green-800 mb-4">
        Cosecha de Miel - El Desafío de la Apicultura
      </h1>

      {playerFaction ? (
        <div className="text-center">
          <p className="text-xl font-medium mb-2">
            ¡Bienvenido, {playerFaction}!
          </p>
          <p className="text-lg mb-4">Fase: {phase === 1 ? "Inicial" : phase === 2 ? "Media" : "Avanzada"}</p>
          <p className="text-lg mb-2">Miel recolectada: {honey}</p>
          <p className="text-lg mb-2">Marks: {marks}</p> {/* Mostrar marks */}

          {/* Botón para declarar victoria */}
          <button
            onClick={handleVictory}
            className="bg-purple-600 text-white py-2 px-4 rounded mt-4 hover:bg-purple-700"
          >
            Ganar Marks (Si has alcanzado fase avanzada)
          </button>
        </div>
      ) : (
        <div className="text-center">
          <p className="text-xl font-medium mb-4">Selecciona tu facción:</p>
          {factions.map((faction, index) => (
            <button
              key={index}
              onClick={() => setPlayerFaction(faction)}
              className="bg-blue-600 text-white py-2 px-4 rounded mb-2 hover:bg-blue-700"
            >
              {faction}
            </button>
          ))}
        </div>
      )}
    </div>
  );
}

export default App;
Explicación del flujo:
Selección de facción: El jugador selecciona su facción.

Fase avanzada: Una vez que se recolecta suficiente miel, el jugador llega a la fase avanzada.

Recompensa de marks: Si el jugador llega a la fase avanzada, puede ganar marks como recompensa llamando a la API de Sunflower Land para otorgar los marks.

Llamada a la API: La llamada a la API en el handleVictory se hace con un POST a una URL ficticia de la API que debes reemplazar por la verdadera URL del endpoint de recompensas.

Consideraciones:
Asegúrate de contar con las credenciales necesarias para interactuar con la API.

Si no tienes acceso a un endpoint real, puedes simularlo localmente con una lógica sencilla o crear una API propia que actúe de manera similar.

Personaliza el proceso de otorgamiento de recompensas según las reglas de Sunflower Land.

Decidí hacer una mejora con las recompensas (aún no dispongo de la API)
Paso 1: Medir la eficiencia y dificultad
Para medir la eficiencia de los jugadores, puedes usar parámetros como:

Tiempo: Qué tan rápido completan las fases.

Recursos: Cuántos recursos (como miel) han recolectado en comparación con la capacidad de la canasta.

Plagas controladas: Qué tan bien gestionan las plagas durante el juego.

Para medir la dificultad, podrías usar:

Nivel de fase alcanzado: Fase 1, 2 o 3.

Número de plagas generadas: Más plagas indican un juego más desafiante.

Uso de defensas: El uso y mejora de las defensas podría indicar una mayor dificultad.

Paso 2: Asignar recompensas según estos factores
Basándote en estos parámetros, puedes calcular una cantidad de marks que se otorgan al final de la partida.

Ejemplo de implementación
js
Copiar
Editar
import React, { useState, useEffect } from "react";

// Facciones
const factions = ["Nightshades", "Sunflorians", "Bumpkins", "Goblins"];

function App() {
  const [playerFaction, setPlayerFaction] = useState(null);
  const [honey, setHoney] = useState(0);
  const [marks, setMarks] = useState(0); // Marca de recompensa
  const [phase, setPhase] = useState(1);
  const [startTime, setStartTime] = useState(null); // Tiempo de inicio
  const [plagues, setPlagues] = useState(0); // Plagas generadas
  const [defensesUsed, setDefensesUsed] = useState({ trap: false, fence: false, wall: false });

  // Función para calcular la eficiencia y asignar marks
  const calculateMarks = () => {
    // Ejemplo de lógica para determinar la dificultad
    let difficultyMultiplier = 1;

    if (phase === 3) {
      difficultyMultiplier = 1.5; // Aumento de dificultad en fase avanzada
    }

    // Medir eficiencia: entre menos plagas, más eficiente
    let efficiencyScore = Math.max(0, 10 - plagues); // Menos plagas = más eficiente

    // Medir el tiempo de juego
    const gameDuration = (Date.now() - startTime) / 1000; // Duración en segundos
    let timeMultiplier = gameDuration < 300 ? 1.2 : 1; // Si el juego duró menos de 5 minutos, otorga bonus

    // Calcular marks basados en la eficiencia y dificultad
    const marksGained = Math.round((efficiencyScore * difficultyMultiplier * timeMultiplier) / 2);

    // Asegurarse de que la cantidad de marks no sea negativa
    setMarks((prevMarks) => prevMarks + Math.max(marksGained, 0));
  };

  // Función que maneja la victoria
  const handleVictory = async () => {
    if (phase === 3) {
      calculateMarks(); // Calcular los marks al ganar
      try {
        // Llamada a la API de Sunflower Land para otorgar recompensas (marks)
        const response = await fetch("https://api.sunflowerland.com/reward", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify({
            playerFaction: playerFaction,
            marks: marks, // Cantidad de marks
          }),
        });

        const data = await response.json();

        if (data.success) {
          alert(`¡Felicidades! Has ganado ${marks} marks por tu eficiencia.`);
        } else {
          alert("Hubo un error al intentar otorgar la recompensa.");
        }
      } catch (error) {
        console.error("Error al otorgar marks:", error);
        alert("Hubo un error al conectarse con el servidor.");
      }
    }
  };

  // Actualiza las fases con el paso del tiempo
  useEffect(() => {
    if (!startTime) {
      setStartTime(Date.now()); // Iniciar el cronómetro cuando empiece el juego
    }

    const interval = setInterval(() => {
      if (phase === 1 && honey >= 10) {
        setPhase(2);
      } else if (phase === 2 && honey >= 20) {
        setPhase(3);
      }
    }, 1000);

    return () => clearInterval(interval);
  }, [honey, phase]);

  return (
    <div className="min-h-screen flex flex-col items-center justify-center bg-yellow-100">
      <h1 className="text-4xl font-bold text-center text-green-800 mb-4">
        Cosecha de Miel - El Desafío de la Apicultura
      </h1>

      {playerFaction ? (
        <div className="text-center">
          <p className="text-xl font-medium mb-2">¡Bienvenido, {playerFaction}!</p>
          <p className="text-lg mb-4">Fase: {phase === 1 ? "Inicial" : phase === 2 ? "Media" : "Avanzada"}</p>
          <p className="text-lg mb-2">Miel recolectada: {honey}</p>
          <p className="text-lg mb-2">Plagas: {plagues}</p>
          <p className="text-lg mb-2">Marks: {marks}</p> {/* Mostrar marks */}

          {/* Botón para declarar victoria */}
          <button
            onClick={handleVictory}
            className="bg-purple-600 text-white py-2 px-4 rounded mt-4 hover:bg-purple-700"
          >
            Ganar Marks (Si has alcanzado fase avanzada)
          </button>
        </div>
      ) : (
        <div className="text-center">
          <p className="text-xl font-medium mb-4">Selecciona tu facción:</p>
          {factions.map((faction, index) => (
            <button
              key={index}
              onClick={() => setPlayerFaction(faction)}
              className="bg-blue-600 text-white py-2 px-4 rounded mb-2 hover:bg-blue-700"
            >
              {faction}
            </button>
          ))}
        </div>
      )}
    </div>
  );
}

export default App;
Explicación:
Medición de la eficiencia:

La eficiencia se calcula en base al número de plagas (menos plagas significa mayor eficiencia).

Se mide también el tiempo de juego (si el jugador termina más rápido, obtiene un bono).

Cálculo de los marks:

Usamos un multiplicador para la dificultad basado en la fase (fase avanzada otorga más marks).

También ajustamos los marks basándonos en la eficiencia (menos plagas, más marks) y el tiempo de juego.

Asignación de marks:

Al ganar, el jugador recibe los marks calculados.

Luego, se puede hacer una llamada a la API de Sunflower Land para registrar y otorgar esos marks, similar a la lógica presentada anteriormente.

Me gustaria observar sus comentarios sobre la opinión de este minijuego, el cual es parte de 4 minijuegos que estoy construyendo.
Tambien me gustari indicar que mi conocimiento como Desarrollador es básico.

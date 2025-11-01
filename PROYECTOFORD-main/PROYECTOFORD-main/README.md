# PROYECTOFORD

Este proyecto es una aplicación web fullstack que muestra una lista de carros disponibles.  
Se construyó usando **Node.js y Express** en el backend y **React con Vite** en el frontend, consumiendo una API externa simulada.

---

## Estructura de carpetas

Nombre_carpeta/
├─ backend/ # Servidor Node.js
├─ frontend/ # Aplicación React

yaml
Copiar código

---

## Tecnologías

- Backend: Node.js, Express, CORS, node-fetch  
- Frontend: React, Vite, JavaScript  
- API externa: [Freetest API - Cars](https://freetestapi.com/api/v1/cars)  

---

## Instalación y ejecución

###  Backend

1. Crear la carpeta del backend y entrar a ella:

```bash
mkdir backend
cd backend
Inicializar Node.js:

bash
Copiar código
npm init -y
Instalar dependencias:

bash
Copiar código
npm install express cors node-fetch
Crear server.js con el siguiente contenido:

javascript
Copiar código
import express from "express";
import cors from "cors";
import fetch from "node-fetch";

const app = express();
const PORT = 3000;

app.use(cors());
app.use(express.json());

app.get("/api/saludo", (req, res) => {
  res.json({ mensaje: "Bienvenido al servidor de Venta de Carros 🚗" });
});

app.get("/api/carros", async (req, res) => {
  try {
    const response = await fetch("https://freetestapi.com/api/v1/cars");
    const data = await response.json();
    res.json(data);
  } catch (error) {
    res.status(500).json({ error: "Error al obtener datos de la API" });
  }
});

app.listen(PORT, () => {
  console.log(`Servidor corriendo en http://localhost:${PORT}`);
});
Ejecutar el backend:

bash
Copiar código
node server.js
 Frontend
Crear la carpeta del frontend y entrar a ella:

bash
Copiar código
mkdir frontend
cd frontend
Crear proyecto React con Vite:

bash
Copiar código
npm create vite@latest
Nombre del proyecto: frontend

Framework: React

Variant: JavaScript

Entrar a la carpeta src y editar App.jsx con este código:

javascript
Copiar código
import { useState, useEffect } from "react";

function App() {
  const [mensaje, setMensaje] = useState("");
  const [carros, setCarros] = useState([]);

  useEffect(() => {
    fetch("http://localhost:3000/api/saludo")
      .then((res) => res.json())
      .then((data) => setMensaje(data.mensaje));

    fetch("http://localhost:3000/api/carros")
      .then((res) => res.json())
      .then((data) => setCarros(data));
  }, []);

  return (
    <div style={{ textAlign: "center", padding: "20px" }}>
      <h1 style={{ color: "darkblue" }}>{mensaje}</h1>
      <h2>Lista de Carros Disponibles 🚘</h2>
      <div style={{ display: "flex", flexWrap: "wrap", justifyContent: "center" }}>
        {carros.length > 0 ? (
          carros.map((car, index) => (
            <div
              key={index}
              style={{
                border: "1px solid #ccc",
                borderRadius: "10px",
                margin: "10px",
                padding: "10px",
                width: "250px",
                boxShadow: "2px 2px 10px rgba(0,0,0,0.1)",
              }}
            >
              <img
                src={car.image || "https://via.placeholder.com/200x100"}
                alt={car.make}
                style={{ width: "100%", borderRadius: "10px" }}
              />
              <h3>{car.make} {car.model}</h3>
              <p>Año: {car.year}</p>
              <p>Precio: ${car.price}</p>
            </div>
          ))
        ) : (
          <p>Cargando autos...</p>
        )}
      </div>
    </div>
  );
}

export default App;
Ejecutar el frontend:

bash
Copiar código
npm install
npm run dev
Frontend correrá en http://localhost:5173/

Backend correrá en http://localhost:3000/

 Uso
Abre el navegador en http://localhost:5173/

Verás el mensaje de bienvenida y la lista de carros disponibles.

Cada tarjeta de carro muestra imagen, marca, modelo, año y precio.

Contribuir
Haz un fork del repositorio.

Crea una rama nueva: git checkout -b mi-rama.

Realiza cambios y haz commit: git commit -m "Descripción de cambios".

Haz push a tu fork: git push origin mi-rama.

Abre un Pull Request.




ademas


//Creas carpetas 

mkdir backend
mkdir frontend


//Entrar al backend 
cd backend
//inicializas node.jsç
Inicializa Node.js

//Inicializas las dependencias
npm install express cors node-fetch


//Buscas en l parte izquierda el server.js (NOTA: Este depende de acuerdo a tu ptograma para es)
import express from "express";
import cors from "cors";
import fetch from "node-fetch";

const app = express();
const PORT = 3000;

app.use(cors());
app.use(express.json());

// Rutas básicas
app.get("/api/saludo", (req, res) => {
  res.json({ mensaje: "Bienvenido al servidor de Venta de Carros 🚗" });
});

// Ruta que simula API externa (carros)
app.get("/api/carros", async (req, res) => {
  try {
    const response = await fetch("https://freetestapi.com/api/v1/cars");
    const data = await response.json();
    res.json(data);
  } catch (error) {
    res.status(500).json({ error: "Error al obtener datos de la API" });
  }
});

app.listen(PORT, () => {
  console.log(`Servidor corriendo en http://localhost:${PORT}`);
});


//Ahora en la terminal te aseguras de estar asi y sales de esa carpeta
PS C:\Users\gasr_\Desktop\Nombre_carpeta\backend> cd .. 

//Inicializas el fronted mas bien entras
cd frontend 

//Intalas el React
npm create vite@latest


//Haces estos paso
✔ Project name: frontend
✔ Framework: React
✔ Variant: JavaScript

//Al acabar te dirijes a la subcarpeta src y bnuscas app.jsx (NOTA: También este código depende de tu proyecto lo asemejas a lo tuyo )
import { useState, useEffect } from "react";

function App() {
  const [mensaje, setMensaje] = useState("");
  const [carros, setCarros] = useState([]);

  useEffect(() => {
    fetch("http://localhost:3000/api/saludo")
      .then((res) => res.json())
      .then((data) => setMensaje(data.mensaje));

    fetch("http://localhost:3000/api/carros")
      .then((res) => res.json())
      .then((data) => setCarros(data));
  }, []);

  return (
    <div style={{ textAlign: "center", padding: "20px" }}>
      <h1 style={{ color: "darkblue" }}>{mensaje}</h1>
      <h2>Lista de Carros Disponibles 🚘</h2>
      <div style={{ display: "flex", flexWrap: "wrap", justifyContent: "center" }}>
        {carros.length > 0 ? (
          carros.map((car, index) => (
            <div
              key={index}
              style={{
                border: "1px solid #ccc",
                borderRadius: "10px",
                margin: "10px",
                padding: "10px",
                width: "250px",
                boxShadow: "2px 2px 10px rgba(0,0,0,0.1)",
              }}
            >
              <img
                src={car.image || "https://via.placeholder.com/200x100"}
                alt={car.make}
                style={{ width: "100%", borderRadius: "10px" }}
              />
              <h3>{car.make} {car.model}</h3>
              <p>Año: {car.year}</p>
              <p>Precio: ${car.price}</p>
            </div>
          ))
        ) : (
          <p>Cargando autos...</p>
        )}
      </div>
    </div>
  );
}

export default App;



//SI puedes abres dos terminales en una te metes a backend y el la otra en fronted y los inicializas 

(BACKEND) node server.js

(FRONTEND)npm run dev

//Los resultados esperados al hacer esos comandos es 

 (BACKEND) NO como tal sale esto pero te da una link con el 300  VITE v5.0  ready in 300ms

 (FRONTEND) ➜  Local: http://localhost:5173/


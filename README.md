# 🏆 Prode Mundial 2026 — versión Firebase (tiempo real)

Todos los jugadores comparten la misma base de datos. La tabla de posiciones se actualiza en tiempo real.

---

## 📁 Archivos

```
prode2026-firebase/
├── index.html   ← todo el código (HTML + JS con Firebase)
├── style.css    ← estilos
└── README.md    ← esta guía
```

---

## 🚀 Publicar en Netlify (2 minutos)

1. Entrá a https://app.netlify.com/drop
2. Arrastrá la carpeta `prode2026-firebase` completa
3. ¡Listo! Compartí la URL con tus amigos

---

## ⚽ Cargar resultados reales (cuando termina un partido)

Cuando termina un partido, vos como organizador tenés que cargar el resultado en Firestore.

### Opción A — Desde la consola de Firebase (más fácil)
1. Entrá a https://console.firebase.google.com
2. Tu proyecto → Firestore → pestaña "Datos"
3. Hacé clic en "+ Iniciar colección" → ID: `config`
4. Documento ID: `results`
5. Agregá un campo por partido:
   - Nombre del campo: `1` (el ID del partido)
   - Tipo: **map**
   - Dentro del map: campo `home` (number) y campo `away` (number)

### Opción B — Desde la consola del navegador
Abrí tu prode en el navegador, F12 → Consola, y pegá:

```js
// Ejemplo: partido 1 terminó 2-1 (México 2 - Polonia 1)
import { getFirestore, doc, setDoc } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-firestore.js";
// ... (usar el panel de Firebase es más fácil para esto)
```

### Referencia de IDs de partidos

| ID | Partido |
|----|---------|
| 1  | México vs Polonia |
| 2  | Arabia Saudita vs Argentina |
| 3  | Francia vs Australia |
| 4  | Dinamarca vs Túnez |
| 5  | Argentina vs Polonia |
| 6  | México vs Arabia Saudita |
| 7  | Brasil vs Serbia |
| 8  | Suiza vs Camerún |
| 9  | España vs Costa Rica |
| 10 | Alemania vs Japón |
| 11 | Uruguay vs Corea del Sur |
| 12 | Portugal vs Ghana |
| 13 | Inglaterra vs Senegal |
| 14 | Holanda vs Ecuador |
| 15 | Italia vs Marruecos |
| 16 | Bélgica vs Canadá |
| 17 | Argentina vs México |
| 18 | Francia vs Dinamarca |
| 19 | España vs Alemania |
| 20 | Brasil vs Portugal |

---

## 🏅 Sistema de puntos

| Resultado | Puntos |
|-----------|--------|
| Marcador exacto | **3 pts** |
| Ganador correcto | **1 pt** |
| Incorrecto | **0 pts** |

---

## 🔒 Notas de seguridad

Las reglas de Firestore están abiertas (cualquiera puede leer/escribir).
Para un prode entre amigos esto está bien. Si querés reglas más estrictas, avisale al organizador.

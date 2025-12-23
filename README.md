# 🐢 Guía Definitiva: eMule con ID Alta en LiveBox Fibra

> **¿Te has bajado eMule por nostalgia pero la mula tiene una venda en los ojos y descarga lentísimo?** No te preocupes, no eres el único.

Bienvenido. Este repositorio es una guía **explicada para seres humanos** (no para informáticos) sobre cómo configurar correctamente eMule si tienes un router **LiveBox** (el que suelen poner **Orange, Jazztel o Simyo**).

### 🎯 El Objetivo
Pasar de las flechas amarillas (ID Baja) a las **flechas verdes (ID Alta)** para descargar a la máxima velocidad que permita tu fibra óptica.

### 🧠 ¿Qué necesitas saber antes de empezar?
* **No necesitas ser hacker:** Solo tienes que seguir los pasos uno a uno.
* **Tiempo estimado:** 5 - 10 minutos.
* **Resultado:** Una mula libre, sin vendas y corriendo rápido.

---

# 🚀 Guía Definitiva: Cómo Configurar eMule en Router (ID Alta)

Esta es una guía paso a paso, diseñada para **todos los públicos**, para solucionar el problema de la "venda en los ojos" de la mula (ID Baja) y conseguir que las descargas vuelen en routers.

Si tienes flechas amarillas o tus descargas van lentas, **sigue estos pasos en orden**.

---

## 📋 ¿Qué vamos a conseguir?
1.  **ID Alta:** Flechas verdes en el mundo del eMule 🟢.
2.  **Velocidad:** Optimizar la conexión para fibra óptica.
3.  **Estabilidad:** Que no se desconfigure mañana.

---

## 🛠️ Paso 1: Fijar la "Matrícula" de tu PC
Para que el router sepa a quién abrirle la puerta, necesitamos saber la dirección del ordenador.

1.  En tu teclado, pulsa la tecla `Windows` + `R`.
2.  Escribe `ipconfig` y pulsa **Enter**.
3.  Copia y pega la dirección IP que aparece en **Dirección IPv4**.

---

## 🕵️ Paso 2: Apuntar tus puertos
Necesitamos saber qué "puertas" usa tu eMule.

1.  Abre eMule.
2.  Ve a **Preferencias** > **Conexión**.
3.  Anota los números que salen en:
    * **TCP:** (Ejemplo: `4662`)
    * **UDP:** (Ejemplo: `4672`)
    * *Nota: Tus números pueden ser diferentes, anota los tuyos.*

---

## 🔓 Paso 3: Abrir los puertos en el Router LiveBox
Ahora le diremos al router que deje pasar la información por esas puertas.

1.  Abre un navegador web y entra en: `http://192.168.1.1`
2.  **Usuario:** `admin` | **Contraseña:** Suele ser la misma clave de tu Wi-Fi (mira la pegatina debajo del router).
3.  Ve a **Configuración Avanzada** (engranaje) > **Configuración de la red** > **NAT/PAT**.
4.  Tienes que crear **2 Reglas Nuevas** en la tabla:

| Regla | Aplicación | Puerto Interno | Puerto Externo | Protocolo | Dispositivo / IP |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | EmuleTCP | Tu puerto TCP | Tu puerto TCP | **TCP** | `192.168.1.55` |
| **2** | EmuleUDP | Tu puerto UDP | Tu puerto UDP | **UDP** | `192.168.1.55` |

5.  Asegúrate de marcar la casilla **Habilitar** en ambas y dale a **Guardar**.

---

## 🛡️ Paso 4: El Firewall de Windows (El olvidado)
A veces el router deja pasar los datos pero Windows los bloquea.

1.  Pulsa la tecla `Windows` y escribe: `Permitir una aplicación`.
2.  Abre la opción **Permitir una aplicación a través del Firewall de Windows**.
3.  Pulsa el botón **Cambiar la configuración** (arriba a la derecha).
4.  Busca **eMule** en la lista.
5.  **IMPORTANTE:** Asegúrate de que tiene marcadas las **3 casillas**:
    * [x] La del nombre (eMule)
    * [x] Privada
    * [x] Pública
6.  Si no aparece en la lista, dale a "Permitir otra aplicación" y busca el archivo `emule.exe` en tu PC.

---

## 🚀 Paso 5: Configuración "Turbo" para Fibra
eMule viene configurado para conexiones antiguas. Vamos a actualizarlo.

En eMule, ve a **Preferencias** > **Conexión**:

* **Capacidad Descarga:** `100000`
* **Capacidad Subida:** `10000`
* **Límites:**
    * Límite Descarga: [ ] Desmarcado (Sin límite).
    * Límite Subida: [x] Marcado -> Pon `1000` (Es importante limitar la subida un poco para no saturar el router, pero 1000 es un valor generoso que te dará muchos créditos).
* **Máx. Fuentes/archivo:** `500`
* **Límites de conexión:** `600`

### 🧹 Limpieza de Servidores (Evita servidores espía)
1.  Ve a la pestaña **Servidores**.
2.  Borra todos los que haya (Clic derecho > Eliminar todos).
3.  A la derecha, donde dice "Actualizar server.met desde URL", pega esto:
    `http://upd.emule-security.org/server.met`
4.  Dale a **Actualizar** y conéctate a **eMule Security**.

---

## ⚠️ Solución de Problemas
**¿He hecho todo y sigo con flechas amarillas (ID Baja)?**

Es muy probable que tu compañía te tenga en **CG-NAT**.
* **¿Qué es?** Compartes tu IP pública con muchos vecinos, por lo que abrir puertos no sirve de nada.
* **Prueba:** Entra al router y mira la "IP WAN". Luego entra en [cualesmiip.com](https://www.cualesmiip.com). Si los números son diferentes, tienes CG-NAT.
* **Solución:** Llama a tu operador (Orange/Jazztel/Simyo) y pide que te saquen del CG-NAT. Es gratis y suelen tardar 24h.

---

Disfruta de tus descargas clásicas a máxima velocidad 🐢💨

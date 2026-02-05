# 🖥️ Simulador de Algoritmos de Asignación de Memoria

<div align="center">

![Memory Allocation](https://img.shields.io/badge/Memory-Allocation-0078d4?style=for-the-badge)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

**Una herramienta interactiva para visualizar y comparar algoritmos de gestión de memoria**



</div>

---



## 🎓 Introducción

Este simulador interactivo te permite **visualizar y comparar** los algoritmos **Best Fit** y **Worst Fit** para la asignación de memoria en sistemas operativos. Es una herramienta educativa ideal para:

- 📚 **Estudiantes** de Sistemas Operativos
- 👨‍🏫 **Profesores** que necesitan material didáctico
- 💻 **Desarrolladores** interesados en gestión de memoria
- 🔍 **Investigadores** que estudian rendimiento de algoritmos

---

## 🧠 ¿Qué son los Algoritmos de Asignación de Memoria?

### Contexto

En un sistema operativo, la **memoria RAM** se divide en bloques o particiones. Cuando un programa (proceso) necesita ejecutarse, el SO debe encontrar un espacio adecuado en memoria para cargarlo.

```
┌─────────────────────────────────────┐
│         MEMORIA RAM (1000 KB)       │
├─────────────────────────────────────┤
│  Bloque 1: 200 KB  [LIBRE]         │
│  Bloque 2: 150 KB  [Proceso A]     │
│  Bloque 3: 300 KB  [LIBRE]         │
│  Bloque 4: 100 KB  [Proceso B]     │
│  Bloque 5: 250 KB  [LIBRE]         │
└─────────────────────────────────────┘
```

### El Problema

**¿En qué bloque libre colocamos un nuevo proceso de 180 KB?**

Los algoritmos de asignación resuelven esta pregunta siguiendo diferentes estrategias.

### Fragmentación Externa

Es la **memoria desperdiciada** en bloques libres que son demasiado pequeños para ser utilizados:

```
❌ FRAGMENTACIÓN ALTA (Ineficiente)
┌──────────────────────────────┐
│ [P1: 100KB] [20KB] [P2: 80KB] [15KB] [P3: 50KB] [10KB] │
└──────────────────────────────┘
   Total desperdiciado: 45 KB en fragmentos pequeños

✅ FRAGMENTACIÓN BAJA (Eficiente)
┌──────────────────────────────┐
│ [P1: 100KB] [P2: 80KB] [P3: 50KB] [145KB libre] │
└──────────────────────────────┘
   Total desperdiciado: 145 KB en un solo bloque utilizable
```

---

## 🎯 Algoritmos Implementados

### 1️⃣ **Best Fit (Mejor Ajuste)**

> Asigna el proceso al **bloque más pequeño** que pueda contenerlo

#### 📊 Funcionamiento

```
Proceso a asignar: 150 KB

Bloques disponibles:
  🟢 Bloque A: 200 KB  → Diferencia: 50 KB
  🟢 Bloque B: 180 KB  → Diferencia: 30 KB  ⭐ SELECCIONADO
  🟢 Bloque C: 300 KB  → Diferencia: 150 KB

Resultado: Se elige el Bloque B (menor desperdicio)
```

#### ✅ Ventajas
- Minimiza el espacio desperdiciado por asignación
- Preserva bloques grandes para procesos grandes
- Aprovechamiento óptimo teórico

#### ❌ Desventajas
- Más lento (debe revisar todos los bloques)
- Genera muchos fragmentos muy pequeños
- Puede aumentar la fragmentación externa a largo plazo

---

### 2️⃣ **Worst Fit (Peor Ajuste)**

> Asigna el proceso al **bloque más grande** disponible

#### 📊 Funcionamiento

```
Proceso a asignar: 150 KB

Bloques disponibles:
  🟢 Bloque A: 200 KB  → Diferencia: 50 KB
  🟢 Bloque B: 180 KB  → Diferencia: 30 KB
  🟢 Bloque C: 300 KB  → Diferencia: 150 KB  ⭐ SELECCIONADO

Resultado: Se elige el Bloque C (mayor espacio sobrante)
```

#### ✅ Ventajas
- Los fragmentos resultantes son grandes y reutilizables
- Reduce la cantidad de fragmentos muy pequeños
- Buenos resultados con procesos de tamaño similar

#### ❌ Desventajas
- Más lento (debe revisar todos los bloques)
- Consume rápidamente los bloques grandes
- Puede dejar sin espacio para procesos grandes futuros

---

## 🚀 Cómo Usar el Simulador

### Paso 1: Configurar la Memoria

1. **Establece el tamaño total de memoria** (en KB)
   - Ejemplo: 1000 KB
   
2. **Define el número de particiones iniciales**
   - El sistema creará bloques de tamaño aleatorio
   - Recomendado: 5-8 particiones

3. Haz clic en **🔄 Inicializar Memoria**

```
┌─────────────────────────────────────┐
│  ⚙️ Configuración de Memoria        │
├─────────────────────────────────────┤
│  Tamaño Total: [1000] KB           │
│  Particiones:  [5]                 │
│  [🔄 Inicializar Memoria]          │
└─────────────────────────────────────┘
```

---

### Paso 2: Agregar Procesos

1. **Nombre del proceso** (ej: P1, P2, ProcesoA)
2. **Tamaño del proceso** en KB
3. Clic en **➕ Agregar a Cola**

Repite este paso para agregar múltiples procesos.

```
┌─────────────────────────────────────┐
│  📦 Agregar Proceso                 │
├─────────────────────────────────────┤
│  Nombre: [P1        ]              │
│  Tamaño: [150       ] KB           │
│  [➕ Agregar a Cola]                │
└─────────────────────────────────────┘
```

---

### Paso 3: Ejecutar la Simulación

Tienes 3 opciones de ejecución:

| Botón | Función | Cuándo Usar |
|:---:|:---|:---|
| **▶️ Ejecutar Paso** | Asigna un proceso a la vez | Para análisis detallado |
| **⏩ Ejecutar Todos** | Asigna todos los procesos automáticamente | Para ver resultados finales |
| **🗑️ Reiniciar** | Limpia todo y reinicia | Para comenzar de nuevo |

---

### Paso 4: Analizar Resultados

El simulador muestra en tiempo real:

#### 📊 Visualización de Memoria

```
Best Fit                    Worst Fit
┌─────────────────┐        ┌─────────────────┐
│ Bloque 0 - LIBRE│        │ P1 - 150 KB     │
│ 200 KB          │        │                 │
├─────────────────┤        ├─────────────────┤
│ P1 - 150 KB     │        │ Bloque 1 - LIBRE│
│                 │        │ 200 KB          │
├─────────────────┤        ├─────────────────┤
│ Bloque 2 - LIBRE│        │ Bloque 2 - LIBRE│
│ 300 KB          │        │ 300 KB          │
└─────────────────┘        └─────────────────┘
```

#### 📈 Estadísticas Comparativas

- **Fragmentación Externa**: Memoria libre inutilizable
- **Memoria Utilizada**: Porcentaje de memoria ocupada
- **Procesos Asignados**: Cuántos procesos se pudieron cargar
- **Tabla Comparativa**: Destaca qué algoritmo es mejor en cada métrica

---




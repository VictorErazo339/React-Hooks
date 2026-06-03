# ⚛️Los 10 Hooks de React Más Utilizados en la Web⚛️

## 📖 Introducción

Los **Hooks** son funciones especiales introducidas en React que permiten utilizar características de React dentro de componentes funcionales, como el manejo de estado, efectos secundarios, referencias y optimizaciones.

Antes de los Hooks, muchas de estas funcionalidades solo podían utilizarse mediante componentes de clase. Actualmente, los Hooks son la forma recomendada de desarrollar aplicaciones en React.

---

# 1. useState

## ¿Qué es?

`useState` permite agregar y administrar estado local dentro de un componente.

## Sintaxis

```jsx
const [estado, setEstado] = useState(valorInicial);
```

## Ejemplo

```jsx
import { useState } from "react";

function Contador() {
  const [contador, setContador] = useState(0);

  return (
    <>
      <h1>{contador}</h1>
      <button onClick={() => setContador(contador + 1)}>
        Incrementar
      </button>
    </>
  );
}
```

## Casos de uso

- Formularios
- Contadores
- Modales
- Menús desplegables
- Estados de carga

---

# 2. useEffect

## ¿Qué es?

Permite ejecutar efectos secundarios dentro de un componente.

Un efecto secundario puede ser:

- Llamar una API
- Crear temporizadores
- Escuchar eventos
- Manipular el DOM

## Ejemplo

```jsx
import { useEffect } from "react";

function Usuarios() {
  useEffect(() => {
    console.log("Componente montado");
  }, []);

  return <h1>Usuarios</h1>;
}
```

## Dependencias

### Ejecutar una sola vez

```jsx
useEffect(() => {
  obtenerDatos();
}, []);
```

### Ejecutar cuando cambie una variable

```jsx
useEffect(() => {
  console.log(nombre);
}, [nombre]);
```

---

# 3. useContext

## ¿Qué es?

Permite consumir datos globales sin necesidad de pasar props manualmente entre múltiples componentes.

## Ejemplo

### Crear contexto

```jsx
import { createContext } from "react";

export const TemaContext = createContext();
```

### Consumir contexto

```jsx
import { useContext } from "react";
import { TemaContext } from "./TemaContext";

function Header() {
  const tema = useContext(TemaContext);

  return <h1>Tema actual: {tema}</h1>;
}
```

## Casos de uso

- Autenticación
- Temas (dark/light)
- Idiomas
- Configuración global

---

# 4. useRef

## ¿Qué es?

Permite crear referencias persistentes que sobreviven a los renderizados.

## Ejemplo

```jsx
import { useRef } from "react";

function Formulario() {
  const inputRef = useRef();

  const enfocar = () => {
    inputRef.current.focus();
  };

  return (
    <>
      <input ref={inputRef} />
      <button onClick={enfocar}>
        Enfocar
      </button>
    </>
  );
}
```

## Casos de uso

- Acceder al DOM
- Enfocar elementos
- Almacenar valores sin renderizar

---

# 5. useMemo

## ¿Qué es?

Memoriza el resultado de una operación costosa para evitar recalcularla en cada render.

## Ejemplo

```jsx
import { useMemo } from "react";

function Productos({ productos }) {
  const total = useMemo(() => {
    return productos.reduce(
      (suma, producto) => suma + producto.precio,
      0
    );
  }, [productos]);

  return <h1>Total: {total}</h1>;
}
```

## Ventajas

- Mejora el rendimiento
- Evita cálculos innecesarios

---

# 6. useCallback

## ¿Qué es?

Memoriza funciones para evitar que se creen nuevamente en cada render.

## Ejemplo

```jsx
import { useCallback } from "react";

const manejarClick = useCallback(() => {
  console.log("Botón presionado");
}, []);
```

## Casos de uso

- Componentes optimizados con React.memo
- Listas grandes
- Optimización de rendimiento

---

# 7. useReducer

## ¿Qué es?

Alternativa a `useState` para manejar estados complejos.

## Ejemplo

```jsx
import { useReducer } from "react";

const initialState = { contador: 0 };

function reducer(state, action) {
  switch (action.type) {
    case "incrementar":
      return {
        contador: state.contador + 1
      };

    default:
      return state;
  }
}

function App() {
  const [state, dispatch] = useReducer(
    reducer,
    initialState
  );

  return (
    <>
      <h1>{state.contador}</h1>

      <button
        onClick={() =>
          dispatch({ type: "incrementar" })
        }
      >
        Incrementar
      </button>
    </>
  );
}
```

## Casos de uso

- Carritos de compra
- Formularios complejos
- Gestión de estados grandes

---

# 8. useLayoutEffect

## ¿Qué es?

Funciona igual que `useEffect`, pero se ejecuta antes de que el navegador pinte la interfaz.

## Ejemplo

```jsx
import { useLayoutEffect } from "react";

useLayoutEffect(() => {
  console.log("Antes del render visual");
}, []);
```

## Casos de uso

- Medir elementos del DOM
- Animaciones
- Ajustes visuales

---

# 9. useImperativeHandle

## ¿Qué es?

Permite personalizar qué métodos expone un componente hijo mediante referencias.

## Ejemplo

```jsx
useImperativeHandle(ref, () => ({
  limpiar() {
    setTexto("");
  }
}));
```

## Casos de uso

- Componentes reutilizables
- Inputs personalizados
- Bibliotecas UI

---

# 10. useId

## ¿Qué es?

Genera identificadores únicos y estables.

## Ejemplo

```jsx
import { useId } from "react";

function Formulario() {
  const id = useId();

  return (
    <>
      <label htmlFor={id}>Nombre</label>
      <input id={id} />
    </>
  );
}
```

## Casos de uso

- Formularios
- Accesibilidad
- Componentes reutilizables

---

# 📊 Resumen

| Hook | Uso Principal |
|--------|---------------|
| useState | Manejo de estado |
| useEffect | Efectos secundarios |
| useContext | Estado global |
| useRef | Referencias DOM |
| useMemo | Optimización de cálculos |
| useCallback | Optimización de funciones |
| useReducer | Estados complejos |
| useLayoutEffect | Manipulación previa al render |
| useImperativeHandle | Exponer métodos por referencia |
| useId | IDs únicos |

---

# 🎯 Orden Recomendado para Aprender

Si estás comenzando con React, estudia los Hooks en este orden:

1. useState
2. useEffect
3. useContext
4. useRef
5. useReducer
6. useMemo
7. useCallback
8. useLayoutEffect
9. useImperativeHandle
10. useId

Con los primeros 5 Hooks podrás desarrollar más del 90% de las aplicaciones React modernas.

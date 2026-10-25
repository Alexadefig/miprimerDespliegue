# Actividad: Mi primera contribución con Git y GitHub

## Objetivo

Practicar el flujo de trabajo colaborativo real de un proyecto: **fork → rama → cambios → commit → push → Pull Request**.

Cada alumno agregará una tarjeta con sus datos personales a la página del proyecto y propondrá el cambio al repositorio original mediante un Pull Request.

---

## Repositorio original

```
https://github.com/albertorojas-teacher/miprimerDespliegue
```

---

## Paso a paso

### 1. Hacer fork del proyecto

1. Ingresá al repositorio original con tu cuenta de GitHub.
2. Hacé clic en el botón **Fork** (arriba a la derecha).
3. Dejá las opciones por defecto y confirmá con **Create fork**.

Ahora tenés una copia del proyecto en **tu** cuenta: `https://github.com/TU-USUARIO/miprimerDespliegue`.

> El fork es tu copia personal. Ahí vas a trabajar. Nunca escribas directamente en el repositorio original.

---

### 2. Clonar tu fork

Abrí una terminal y ejecutá (reemplazá `TU-USUARIO`):

```bash
git clone https://github.com/TU-USUARIO/miprimerDespliegue.git
cd miprimerDespliegue
```

Verificá que el remoto apunte a tu fork:

```bash
git remote -v
```

Debe mostrar `TU-USUARIO/miprimerDespliegue`.

---

### 3. Crear tu rama de trabajo

La rama debe seguir la nomenclatura **`feature/suNombre`**, usando tu nombre real en minúsculas, sin espacios ni tildes.

Ejemplos válidos:

- `feature/alberto`
- `feature/maria`
- `feature/juanpablo`

Creala y cambiate a ella:

```bash
git checkout -b feature/TU-NOMBRE
```

Verificá que estás en la rama correcta:

```bash
git branch
```

La rama actual aparece marcada con un asterisco `*`.

> ⚠️ No trabajes sobre `main`. Si lo hacés, el Pull Request no se va a poder revisar correctamente.

---

### 4. Crear tu tarjeta con tu nombre

Abrí el archivo `index.html` y buscá la sección `servicios`:

```html
<section class="servicios" id="servicios">
  <div class="contenedor">
    <h2>Servicios</h2>
    <div class="tarjetas">
      ...
    </div>
  </div>
</section>
```

Justo **debajo** del bloque `<div class="tarjetas"> ... </div>` y **antes** de cerrar el `</div>` del contenedor, agregá un nuevo bloque con tu tarjeta:

```html
<!-- Tarjeta de Nombre Apellido -->
<div class="tarjeta-alumno">
  <h3 class="alumno-nombre">Nombre Apellido</h3>
  <p class="alumno-curso">Curso: 5° Año</p>
</div>
```

Requisitos del contenido:

- **Nombre y apellido** reales del alumno.
- **Curso** al que pertenece.
- Un comentario HTML identificando tu bloque (opcional pero recomendado).
- No borres, muevas ni modifiques el código existente de otros alumnos.

---

### 5. Darle tus propios estilos

Abrí el archivo `styles.css` y agregá tus estilos **al final del archivo**, en una sección claramente identificada:

```css
/* ===== Tarjeta de Nombre Apellido ===== */
.tarjeta-alumno {
  /* tu diseño: fondo, borde, padding, sombra, etc. */
}

.alumno-nombre {
  /* estilos del nombre */
}

.alumno-curso {
  /* estilos del curso */
}
```

Requisitos de los estilos:

- Usar **clases CSS** (no estilos en línea con el atributo `style`).
- Los nombres de clase deben ser propios y no repetir los de otros alumnos (ej.: `.tarjeta-alumno-alberto`).
- El diseño es libre: colores, tipografía, bordes, animaciones, iconos, etc.
- La tarjeta debe verse bien en celular y en escritorio.
- No modificar los estilos existentes de `.tarjeta`, `.hero`, `.header`, etc.

**Sugerencia:** si querés que tu tarjeta se integre al resto de la página, podés reutilizar las variables de color definidas en `:root`:

```css
.tarjeta-alumno {
  background: var(--color-blanco);
  border-radius: var(--radio);
  box-shadow: var(--sombra);
}
```

---

### 6. Probar los cambios

Abrí `index.html` en el navegador (doble clic o arrastrá el archivo a una pestaña) y verificá que:

- Tu tarjeta se vea correctamente.
- El resto de la página siga funcionando igual.
- No haya errores de escritura en las etiquetas HTML.

---

### 7. Guardar los cambios en Git

Revisá qué archivos modificaste:

```bash
git status
```

Agregá los cambios y creá el commit:

```bash
git add index.html styles.css
git commit -m "Agrega tarjeta de Nombre Apellido"
```

Subí tu rama a tu fork:

```bash
git push -u origin feature/TU-NOMBRE
```

> Si es la primera vez que usás Git en esta computadora, puede pedirte configurar tu usuario:
>
> ```bash
> git config --global user.name "Tu Nombre"
> git config --global user.email "tu-correo@ejemplo.com"
> ```

---

### 8. Crear el Pull Request

1. Abrí tu fork en GitHub: `https://github.com/TU-USUARIO/miprimerDespliegue`.
2. Vas a ver un aviso amarillo con el botón **Compare & pull request**. Hacé clic ahí.

   - Si no aparece, andá a la pestaña **Pull requests** → **New pull request** → **compare across forks**.
3. Verificá que la comparación sea:

   | Campo                     | Valor correcto                              |
   | ------------------------- | ------------------------------------------- |
   | **base repository** | `albertorojas-teacher/miprimerDespliegue` |
   | **base branch**     | `main`                                    |
   | **head repository** | `TU-USUARIO/miprimerDespliegue`           |
   | **compare branch**  | `feature/TU-NOMBRE`                       |
4. Completá el título:

   ```
   Agrega tarjeta de Nombre Apellido - Curso
   ```
5. En la descripción escribí brevemente qué hiciste:

   ```markdown
   ## Qué hice
   - Agregué mi tarjeta con nombre, apellido y curso.
   - Agregué estilos propios con clases CSS.

   ## Archivos modificados
   - index.html
   - styles.css
   ```
6. Hacé clic en **Create pull request**.

---

### 9. Revisar el resultado

- Esperá la revisión del docente.
- Si se piden cambios, hacelos en tu rama, volvé a ejecutar `git add`, `git commit` y `git push`. El Pull Request se actualiza solo.
- Una vez aprobado, el PR se fusiona en `main` y tu tarjeta pasa a formar parte del proyecto.

---

## Entregables

| # | Entregable                                                   | Dónde               |
| - | ------------------------------------------------------------ | -------------------- |
| 1 | Fork del repositorio original                                | GitHub, en tu cuenta |
| 2 | Rama `feature/TU-NOMBRE` con al menos un commit            | Tu fork              |
| 3 | Tarjeta con nombre, apellido y curso                         | `index.html`       |
| 4 | Estilos propios con clases CSS                               | `styles.css`       |
| 5 | Pull Request abierto hacia `main` del repositorio original | GitHub               |

Enviá el enlace de tu Pull Request por el canal que indique el docente.

---


## Errores frecuentes

| Error                                          | Cómo evitarlo / solucionarlo                                                                    |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| Trabajé directo en `main`                   | Creá la rama antes de editar: `git checkout -b feature/TU-NOMBRE`                             |
| El PR apunta a mi propio fork y no al original | Al crear el PR, revisá que **base repository** sea `shaka0241/miprimerDespliegue`       |
| Mi tarjeta no se ve                            | Revisá que las etiquetas estén bien cerradas y que la clase en el HTML coincida con la del CSS |
| El CSS no se aplica                            | Verificá que el archivo esté guardado y que la clase en `styles.css` empiece con `.`       |
| Se subió la rama equivocada                   | Creá la correcta y subila: `git push -u origin feature/TU-NOMBRE`                             |
| `git push` pide usuario y contraseña        | Usá un token personal o configurá SSH en tu cuenta de GitHub                                   |
| Aparecen conflictos en el PR                   | No modifiques líneas de otros alumnos; agregá tu código al final de cada archivo              |

---

## Reglas de convivencia del repositorio

1. Cada alumno modifica **solo** su tarjeta y sus estilos.
2. No se borra ni se reescribe el trabajo de otros.
3. Un PR por alumno.
4. Los cambios se agregan al final del archivo, para reducir conflictos.
5. Respetá el código y los nombres de clase existentes.

---

## Glosario rápido

- **Fork:** copia de un repositorio en tu cuenta de GitHub.
- **Rama (branch):** línea de trabajo independiente donde hacés tus cambios sin afectar `main`.
- **Commit:** registro de un conjunto de cambios con un mensaje.
- **Push:** subir tus commits locales a GitHub.
- **Pull Request (PR):** pedido formal para que tus cambios se integren al repositorio original.
- **Merge:** acción de fusionar una rama o PR con `main`.
- **Conflicto:** cuando dos personas modifican las mismas líneas y Git no sabe cuál conservar.

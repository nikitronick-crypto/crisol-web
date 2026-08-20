# Páginas de correo de Crisol

Dos páginas para los correos que envía Supabase. Sin ellas, confirmar una
cuenta lleva a una pantalla en blanco y el usuario no sabe si funcionó.

| Archivo | Para qué |
|---|---|
| `confirmado.html` | Adonde llega el enlace de confirmar cuenta |
| `recuperar.html` | Formulario para poner una contraseña nueva |
| `logo.png` | El ícono de la app |

Las dos usan los colores de la app —pizarra y lima— para que quien llegue
desde el correo reconozca que sigue en el mismo sitio.

---

## Publicarlas en GitHub Pages

Es gratis y no requiere servidor.

**1. Crea el repositorio.** En GitHub, nuevo repositorio llamado `crisol-web`.
Tiene que ser **público**: Pages no funciona con repositorios privados en las
cuentas gratuitas.

**2. Sube los tres archivos.** Arrastra `confirmado.html`, `recuperar.html` y
`logo.png` a la página del repositorio y confirma.

**3. Activa Pages.** En el repositorio, Settings → Pages. En "Source" elige
"Deploy from a branch", rama `main`, carpeta `/ (root)`. Guarda.

**4. Espera un minuto** y comprueba que abra:

```
https://nikitronick-crypto.github.io/crisol-web/confirmado.html
```

Si sale error 404, espera otro par de minutos: la primera publicación tarda.

---

## Autorizar las URL en Supabase

Supabase solo redirige a direcciones que estén en su lista. Sin este paso, los
enlaces seguirán llevando a la página en blanco.

En el panel de Supabase → **Authentication** → **URL Configuration**:

- **Site URL**: `https://nikitronick-crypto.github.io/crisol-web`
- **Redirect URLs**: agrega estas dos, una por línea:
  ```
  https://nikitronick-crypto.github.io/crisol-web/confirmado.html
  https://nikitronick-crypto.github.io/crisol-web/recuperar.html
  ```

---

## Probarlo

Regístrate con un correo que no hayas usado. El enlace debería llevar a una
página con el logo y el tilde verde, no a una en blanco.

Después prueba "¿Olvidaste tu contraseña?" desde el inicio de sesión.

---

## Sobre las claves en `recuperar.html`

Esa página lleva la URL y la clave pública de Supabase escritas en el código.
Es correcto: son las mismas que van dentro de la app y están pensadas para ser
públicas. La protección real está en las políticas de la base de datos, no en
ocultarlas.

La que **nunca** debe aparecer en una página web es la `service_role`.

---

## Lo que viene después

Cuando publiques en Play Store vas a necesitar una **política de privacidad en
una URL pública**. Este mismo repositorio sirve: agregas un
`privacidad.html` y ya tienes dónde alojarla.

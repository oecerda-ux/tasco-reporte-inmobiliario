# Reporte Resultado Inmobiliario — TASCO

Sitio estático (`index.html`) publicado con GitHub Pages. Contiene el reporte de resultado
y deuda inmobiliaria de los 9 proyectos de la división Inmobiliaria de TASCO.

## ⚠️ Confidencialidad

Este repositorio y el sitio publicado son **públicos**: cualquier persona con la URL puede
verlo (no aparece en buscadores, pero no requiere login). Contiene cifras financieras
internas (ingresos, costos, resultados por proyecto). Antes de compartir la URL fuera del
equipo, confirma que ese nivel de exposición es aceptable. Si más adelante se requiere
restringir el acceso, las alternativas son:

- **GitHub Enterprise Cloud + Pages privado**: el sitio solo es visible para miembros
  logueados de la organización (requiere plan Enterprise).
- **Cloudflare Pages + Cloudflare Access**: el repo puede seguir en GitHub (público o
  privado) y Cloudflare agrega una capa de login (ej. con correo corporativo) antes de
  mostrar el sitio, sin depender de un plan Enterprise de GitHub.

## Cómo actualizar el reporte

Cada vez que se regenera `Reporte_Resultado_Inmobiliario_Tasco.html` con datos nuevos:

```bash
cp "../Reporte_Resultado_Inmobiliario_Tasco.html" index.html
git add index.html
git commit -m "Actualizar reporte: <breve descripción del cambio, ej. 'datos julio' o 'fix Remanente IVA ALC'>"
git push
```

GitHub Pages redespliega automáticamente unos segundos/minutos después del push. Todo el
historial de cambios queda disponible con `git log` — permite ver cuándo cambió cada cifra
y revertir (`git revert <commit>`) si una actualización tuvo un error.

## Publicar por primera vez (pendiente de hacer)

1. Crea un repositorio nuevo en GitHub (público), por ejemplo `tasco-reporte-inmobiliario`.
   **No** marques "Add a README" ni ".gitignore" al crearlo (ya los trae esta carpeta).
2. En esta carpeta, conecta el repo remoto y sube el primer commit:

   ```bash
   git remote add origin https://github.com/<tu-usuario-u-org>/tasco-reporte-inmobiliario.git
   git branch -M main
   git push -u origin main
   ```

3. En GitHub: **Settings → Pages** → en "Build and deployment", Source = *Deploy from a
   branch* → Branch = `main` / `/(root)` → Save.
4. Espera 1-2 minutos. La URL queda publicada en la misma pantalla de Settings → Pages,
   con el formato:

   ```
   https://<tu-usuario-u-org>.github.io/tasco-reporte-inmobiliario/
   ```

   Esa URL es fija — no cambia aunque se sobrescriba `index.html` en el futuro.

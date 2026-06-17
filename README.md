# Hub · jaguridi.cl

Landing estática que centraliza mis proyectos y experimentos. Una sola página
(`index.html`) sin dependencias ni build: HTML + CSS y SVG inline. Estilo oscuro
elegante, responsiva y accesible.

🔗 **En producción:** https://hub.jaguridi.cl

## Estructura

```
.
├── index.html    # toda la página (estilos e íconos incluidos)
├── favicon.svg
├── CNAME         # hub.jaguridi.cl  (dominio personalizado de GitHub Pages)
├── .nojekyll     # GitHub Pages sirve el HTML tal cual, sin Jekyll
└── README.md
```

## Editar proyectos

Cada proyecto es un `<li>` dentro de `<ul class="grid">` en `index.html`.
Para agregar uno, copia un bloque de tarjeta (`<a class="card" href="…">…</a>`)
y cambia el `href`, el ícono SVG, el `<h2>` y el `<p>`.

## Despliegue (GitHub Pages + Cloudflare DNS)

Mismo patrón que `dobleclick.jaguridi.cl`.

1. **Repo:** crear un repo público (p. ej. `jaguridi/hub`) y subir estos archivos a `main`.
   ```bash
   git init
   git add .
   git commit -m "Hub inicial"
   git branch -M main
   git remote add origin https://github.com/jaguridi/hub.git
   git push -u origin main
   ```
2. **Pages:** Settings → Pages → *Deploy from a branch* → `main` / `(root)`.
   En *Custom domain* poner `hub.jaguridi.cl` y marcar *Enforce HTTPS*.
   (El archivo `CNAME` ya deja fijado el dominio.)
3. **DNS (Cloudflare):** en el panel DNS de `jaguridi.cl`, agregar un registro
   **CNAME**: nombre `hub` → destino `jaguridi.github.io`. Déjalo en **DNS only**
   (nube gris) hasta que GitHub emita el certificado TLS; después puedes activar el
   proxy (nube naranja) si lo deseas.
4. Esperar la propagación de DNS y la emisión del certificado TLS de GitHub.

> El dominio raíz `jaguridi.cl` ya apunta a la página académica; aquí solo se agrega el
> subdominio `hub`, sin tocar lo existente.

## Desarrollo local

Basta con abrir `index.html` en el navegador, o servirlo:

```bash
python -m http.server 8000   # luego abrir http://localhost:8000
```

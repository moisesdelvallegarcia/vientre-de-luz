# Vientre de Luz — Guía de montaje

Sitio estático (HTML/CSS/JS) → GitHub → dominio de GoDaddy.

---

## Fase 0 — Preparar tu PC y abrir el proyecto en PowerShell

### 0.1 Instalar lo necesario

Abre **PowerShell** (tecla Windows → escribe "PowerShell" → Enter) y verifica qué tienes ya:

```powershell
git --version
node --version
```

Si alguno falla, instálalo. La vía rápida con winget:

```powershell
winget install --id Git.Git -e
winget install --id OpenJS.NodeJS.LTS -e
winget install --id GitHub.cli -e
```

> Después de instalar, **cierra y abre una nueva ventana de PowerShell** para que reconozca los comandos.

### 0.2 Instalar Claude Code

```powershell
npm install -g @anthropic-ai/claude-code
```

Verifica:

```powershell
claude --version
```

### 0.3 Configurar Git (solo la primera vez)

```powershell
git config --global user.name "Moisés Condor"
git config --global user.email "moycondor@gmail.com"
git config --global init.defaultBranch main
```

### 0.4 Crear la carpeta del proyecto y entrar

```powershell
mkdir "$HOME\Proyectos\vientre-de-luz"
cd "$HOME\Proyectos\vientre-de-luz"
```

### 0.5 Lanzar Claude Code dentro del proyecto

```powershell
claude
```

Eso "enlaza" la sesión a esa carpeta: todo lo que Claude cree o edite ocurre ahí. La primera vez te pedirá iniciar sesión en el navegador con tu cuenta.

**Atajos útiles dentro de Claude Code:**

| Comando | Qué hace |
|---|---|
| `/init` | Analiza la carpeta y crea un `CLAUDE.md` con el contexto del proyecto |
| `/clear` | Limpia el contexto de la conversación |
| `Shift+Tab` | Alterna modo plan / auto-aceptar ediciones |
| `/exit` | Salir |

---

## Fase 1 — Crear el repositorio en GitHub

Dentro de la carpeta del proyecto (puedes salir de Claude Code o abrir otra pestaña de PowerShell):

```powershell
git init
```

Crea un `.gitignore` mínimo:

```powershell
@"
node_modules/
.env
.DS_Store
Thumbs.db
"@ | Out-File -Encoding utf8 .gitignore
```

Primer commit:

```powershell
git add .
git commit -m "Primer commit: estructura inicial de Vientre de Luz"
```

Autentícate y crea el repo remoto con GitHub CLI (lo más simple):

```powershell
gh auth login
gh repo create vientre-de-luz --public --source=. --remote=origin --push
```

> Si prefieres hacerlo a mano: crea el repo vacío en github.com/new (sin README), y luego:
> ```powershell
> git remote add origin https://github.com/TU-USUARIO/vientre-de-luz.git
> git branch -M main
> git push -u origin main
> ```

---

## Fase 2 — Publicar el sitio

### Opción A — GitHub Pages (gratis, integrado)

1. En el repo → **Settings → Pages**
2. *Source*: `Deploy from a branch` → rama `main`, carpeta `/ (root)`
3. Guarda. En 1-2 minutos tendrás `https://TU-USUARIO.github.io/vientre-de-luz/`

### Opción B — Netlify (más flexible, previews por rama)

1. netlify.com → *Add new site* → *Import from Git* → elige el repo
2. Build command: vacío. Publish directory: `.` (o `dist` si luego usas un build)
3. Deploy

Ambas dan HTTPS gratis. **Pages** es más simple; **Netlify** te da formularios de contacto, redirects y previews.

---

## Fase 3 — Conectar el dominio de GoDaddy

### Si usas GitHub Pages

**En GitHub:** Settings → Pages → *Custom domain* → escribe `tudominio.com` → Save.
Esto crea un archivo `CNAME` en el repo. Marca también **Enforce HTTPS** (aparece tras validar el DNS).

**En GoDaddy:** Mis Productos → tu dominio → **DNS** → Administrar zonas.

Borra los registros `A` y `CNAME` que GoDaddy pone por defecto (el `A` que apunta a un parking, y el `CNAME www`), y añade:

| Tipo | Nombre | Valor | TTL |
|---|---|---|---|
| A | @ | `185.199.108.153` | 600 |
| A | @ | `185.199.109.153` | 600 |
| A | @ | `185.199.110.153` | 600 |
| A | @ | `185.199.111.153` | 600 |
| CNAME | www | `TU-USUARIO.github.io` | 600 |

Opcional, para IPv6 (recomendado):

| Tipo | Nombre | Valor |
|---|---|---|
| AAAA | @ | `2606:50c0:8000::153` |
| AAAA | @ | `2606:50c0:8001::153` |
| AAAA | @ | `2606:50c0:8002::153` |
| AAAA | @ | `2606:50c0:8003::153` |

### Si usas Netlify

Netlify te da 4 nameservers (tipo `dns1.p03.nsone.net`). En GoDaddy: dominio → **Nameservers** → *Cambiar* → *Usar personalizados* → pega los 4. Netlify gestiona todo el DNS y el certificado.

> Alternativa sin cambiar nameservers: apunta un `CNAME www` al subdominio `.netlify.app` y usa el redirect de apex que Netlify indica.

### Verificar

```powershell
nslookup tudominio.com
nslookup www.tudominio.com
```

La propagación DNS suele tardar de 10 minutos a 2 horas (hasta 48h en el peor caso). El certificado HTTPS se emite automáticamente **después** de que el DNS resuelva bien.

---

## Flujo de trabajo diario

```powershell
cd "$HOME\Proyectos\vientre-de-luz"
claude
```

Y cuando quieras publicar cambios:

```powershell
git add .
git commit -m "Descripción del cambio"
git push
```

El sitio se actualiza solo en 1-2 minutos.

---

## Puntos a decidir antes de escribir código

- Nombre exacto del dominio
- Secciones de la página (inicio, sobre, servicios, contacto…)
- Paleta de colores / tipografía / logo
- ¿Formulario de contacto? ¿Reservas? ¿WhatsApp?
- ¿Idioma único o bilingüe?

# Zona Entreno

Webapp inicial para controlar entrenamiento con fuentes Polar, Strava y Google Sheets.

## Cómo abrirla

Abre `index.html` en tu navegador.

## Cómo probar tu hoja de entrenamiento

Desde Google Sheets:

1. Ve a `Archivo > Descargar > Valores separados por comas (.csv)`.
2. En la app, pulsa `Importar CSV`.

La app reconoce columnas con estos nombres:

- `fecha` o `date`
- `plan`, `entreno` o `workout`
- `real`, `realizado` o `done`
- `rpe` o `esfuerzo`
- `carga` o `load`
- `estado` o `status`

También puedes importar bloques con `plantilla-bloques.csv`:

- `bloque`: umbral z4, z2/tirada larga, series o fuerza
- `marca`
- `km`
- `ritmo`
- `zona`
- `progreso`
- Para fuerza/Jefit: `ejercicio`, `peso`, `reps`, `anterior`, `actual`, `cambio`

Y pruebas cada 4-6 semanas con `plantilla-pruebas.csv`:

- `semana` o `fecha`
- `prueba`
- `resultado`
- `cambio`

Para nutrición puedes importar `plantilla-nutricion.csv`:

- `fecha`
- `calorias`
- `proteina`
- `carbohidratos`
- `grasas`
- `objetivo_calorias`

## Siguiente paso para datos reales

Ya hay un backend preparado en la carpeta `backend/`. Sirve para conectar cuentas reales sin exponer secretos en GitHub Pages:

- Polar AccessLink: sueño, Nightly Recharge, pulso, actividad diaria y entrenamientos.
- Strava API: actividades, ritmo, desnivel, frecuencia cardiaca, potencia y segmentos.
- Google Sheets API: lectura del plan de entrenamiento.
- Jefit: fuerza por exportación CSV mientras no haya API pública oficial disponible.
- MyFitnessPal: calorías y macros por exportación CSV; en Android también puede estudiarse Health Connect como puente.

La app tiene una pantalla `Conectar` con URL de backend, comprobación de estado y botones de conexión.

## Conexión fácil

1. Entra en `backend/`.
2. Copia `.env.example` como `.env`.
3. Rellena las claves de Polar y Strava que tengas.
4. Ejecuta el backend:

```bash
node --env-file=.env server.js
```

5. En la webapp, abre `Conectar`.
6. Pega `http://localhost:8787` como URL del backend.
7. Pulsa `Comprobar`.
8. Pulsa `Conectar` en Polar o Strava.

Cuando lo despliegues en producción, cambia `BACKEND_URL` y `FRONTEND_URL` en el backend.

## Publicarla en GitHub Pages

1. Crea un repositorio en GitHub.
2. Sube todo el contenido de esta carpeta.
3. En GitHub, ve a `Settings > Pages`.
4. En `Build and deployment`, elige `Deploy from a branch`.
5. Selecciona la rama principal y la carpeta raíz.

Para que sea privada con permisos por usuario hace falta usar GitHub privado o añadir autenticación externa. GitHub Pages público no protege por login si el repositorio es público.

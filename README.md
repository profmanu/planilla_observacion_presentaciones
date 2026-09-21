# Planilla de exposiciones

Herramienta para corregir en vivo las presentaciones intermedias de proyectos: cronómetro con marcas en 8, 10 y 12 minutos, check y nivel (4 niveles) por actividad, comentarios, borrador de devolución en bullets y un PDF con todos los equipos.

Es un sitio estático (un solo `index.html` + las librerías de PDF en `vendor/`). No tiene servidor ni base de datos.

## Cómo la usan dos evaluadores

Cada evaluador trabaja en **su propia copia**: los datos se guardan en el navegador de cada persona (`localStorage`) y no se envían a ningún lado.

1. Abrir la URL y escribir el nombre en **Evaluador/a** (sección "Todos los equipos", al final). Figura en el PDF.
2. En la misma sección, **Crear equipos del 1 al…** (por ejemplo 12). Esto también quita el equipo de ejemplo.
3. Por cada equipo: poner el nombre de la app o marca, iniciar el cronómetro y marcar cada actividad (check + nivel; "Sin explicar" y comentarios opcionales).
4. Al terminar el equipo, **Generar borrador** y editar el punteo.
5. **Descargar PDF de todos los equipos**: primera página con el resumen y la escala; después, por equipo, la planilla completa y debajo el punteo de feedback. Si el borrador fue editado, el PDF usa el texto editado.

Recomendaciones:
- Usar siempre el mismo navegador y perfil. Si se borran los datos del sitio, se pierden las planillas.
- Descargar el PDF al terminar cada tanda de exposiciones: es la copia de respaldo.
- Cada evaluador crea los equipos con la misma numeración para poder compararlos.

## Publicar en Vercel vía GitHub

1. Crear un repositorio en GitHub (puede ser privado) y subir el contenido de esta carpeta, incluyendo `vendor/`. Desde la web: **Add file → Upload files** y arrastrar todo.
2. En [vercel.com](https://vercel.com): **Add New → Project → Import Git Repository** y elegir el repositorio.
3. Framework Preset: **Other**. Sin comando de build ni directorio de salida. **Deploy**.
4. Compartir la URL con tu dupla. Cada cambio que se suba al repositorio se publica solo.

`vercel.json` pide a los buscadores que no indexen el sitio (`noindex`) y evita enviar el referrer. Como los datos no salen del navegador, la URL pública no expone ninguna devolución ni nombre de estudiantes.

## Librerías incluidas

- [jsPDF](https://github.com/parallax/jsPDF) 4.2.1 (MIT)
- [jsPDF-AutoTable](https://github.com/simonbengtsson/jsPDF-AutoTable) 5.0.8 (MIT)

Están copiadas en `vendor/` para que el sitio no dependa de un CDN.

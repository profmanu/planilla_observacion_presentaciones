# Planilla de exposiciones

Herramienta para corregir en vivo las presentaciones intermedias de proyectos: cronómetro con marcas en 8, 10 y 12 minutos, check y nivel (4 niveles) por actividad, comentarios, y exportación a PDF y Excel con todos los equipos.

Es un sitio estático (un solo `index.html` + las librerías de exportación en `vendor/`). No tiene servidor ni base de datos.

## Cómo la usan dos evaluadores

Cada evaluador trabaja en **su propia copia**: los datos se guardan en el navegador de cada persona (`localStorage`) y no se envían a ningún lado.

1. Abrir la URL. Arriba de todo, en **Todos los equipos**, escribir el nombre en **Evaluador/a**. Figura en el PDF y el Excel.
2. En la misma sección, **Crear equipos del 1 al…** (por ejemplo 12). Esto también quita el equipo de ejemplo.
3. Por cada equipo: poner el nombre de la app o marca, elegir la cantidad de integrantes (de 2 a 6), iniciar el cronómetro y marcar cada actividad (check + nivel; "Sin explicar" y comentarios opcionales).
4. **Descargar PDF** o **Descargar Excel** de todos los equipos: primero un resumen (o la hoja "Resumen" en el Excel) y después, por equipo, la planilla completa con el punteo de feedback debajo. El punteo se arma solo a partir de los checks, niveles y comentarios cargados.

Recomendaciones:
- Usar siempre el mismo navegador y perfil. Si se borran los datos del sitio, se pierden las planillas.
- Exportar al terminar cada tanda de exposiciones: es la copia de respaldo.
- Cada evaluador crea los equipos con la misma numeración para poder compararlos.

## Publicar en Vercel vía GitHub

1. Crear un repositorio en GitHub y subir el contenido de esta carpeta, incluyendo `vendor/`. Desde la web: **Add file → Upload files** y arrastrar todo.
2. En [vercel.com](https://vercel.com): **Add New → Project → Import Git Repository** y elegir el repositorio.
3. Framework Preset: **Other**. Sin comando de build ni directorio de salida. **Deploy**.
4. Compartir la URL con tu dupla. Cada cambio que se suba al repositorio se publica solo (con el repositorio en público, cualquier colaborador con permiso de escritura puede subir cambios sin necesidad de una cuenta de Vercel).

`vercel.json` pide a los buscadores que no indexen el sitio (`noindex`) y evita enviar el referrer. Como los datos no salen del navegador, la URL pública no expone ninguna devolución ni nombre de estudiantes.

## Librerías incluidas

- [jsPDF](https://github.com/parallax/jsPDF) 4.2.1 (MIT)
- [jsPDF-AutoTable](https://github.com/simonbengtsson/jsPDF-AutoTable) 5.0.8 (MIT)
- [SheetJS / xlsx](https://github.com/SheetJS/sheetjs) 0.18.5 (Apache-2.0)

Están copiadas en `vendor/` para que el sitio no dependa de un CDN.

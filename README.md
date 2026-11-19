# Correlativas · Ingeniería Industrial UTN-FRBA

Mapa interactivo de correlativas del **plan I-23** de Ingeniería Industrial (UTN-FRBA).

**App:** https://thejoresp.github.io/correlativas-utn/

## Qué hace

- Muestra las 43 materias del plan por nivel, con sus correlativas.
- Para cada materia marcás el estado: *No cursada*, *Cursando*, *Regularizada*, *Aprobada por promoción* o *Aprobada por final*.
- Calcula qué podés cursar y qué finales podés rendir:
  - **Para cursar** una materia necesitás sus correlativas *regularizadas* o *aprobadas*, según lo que pida el plan.
  - **Para rendir el final** necesitás todas sus correlativas *aprobadas* (por final o por promoción).
- Al pasar el mouse o tocar una materia se resaltan las que necesitás antes (naranja) y las que te habilita (celeste).
- Es una PWA: se instala en el celular o la compu y funciona sin internet.

## Instalarla

- **Android / Chrome / Edge:** abrí el link y elegí *Instalar app* (o *Agregar a pantalla de inicio*).
- **iPhone (Safari):** Compartir → *Agregar a inicio*.

## Datos

El estado se guarda en el navegador (`localStorage`). Cada dispositivo tiene el suyo.
Para pasarlo de uno a otro, usá **Exportar / importar** (JSON).

La base de materias está en `index.html`, en la constante `M`:

```js
{id:"EdT", n:"Estudio del Trabajo", lv:3, cod:"072523", mod:"Anual 4Hs",
 reg:["AdmGen","PyE"],                          // regularizadas para cursar
 apr:["AM1","SSRR","Info1","PS","AGA","IngSoc"]} // aprobadas para cursar
```

## Correr en local

Es estático: abrís `index.html` y listo. Para probar la parte PWA hace falta servirlo por HTTP:

```bash
docker run --rm -p 8080:80 -v "$PWD":/usr/share/nginx/html:ro nginx:alpine
# http://localhost:8080
```

Si cambiás `index.html`, subí la versión de `CACHE` en `sw.js` para que los dispositivos instalados se actualicen.

## Pendiente

- Cargar las electivas con sus correlativas.
- Verificar los requisitos de la PPS: en el PDF original estaban tapados en parte y se tomaron iguales a Proyecto Final.

> Fuente: cuadro de correlativas del plan I-23 (Franja Morada / UTN-FRBA). Verificá siempre con el plan oficial.

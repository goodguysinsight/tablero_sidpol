# Denuncias policiales – Macrorregión Norte (SIDPOL 2025)

Tablero interactivo y autocontenido (`index.html`) de mapas coropléticos de denuncias policiales registradas en el SIDPOL (PNP–MININTER), enero–octubre 2025, para Áncash, Cajamarca, La Libertad, Lambayeque, Piura y Tumbes. Elaboración: **Good Guys Insight**.

## Contenido
| Sección | Descripción |
|---|---|
| Indicadores | Denuncias únicas, tasa por 100,000 hab., departamento con mayor tasa y % de registros con coordenada real |
| Mapa N° 01 | Tasa por 100,000 hab. por departamento, provincia o distrito (quintiles); en distritos, tasa suavizada por Bayes empírico; ranking de los diez ámbitos con mayor tasa |
| Mapa N° 02 | Mapa bivariado: delitos contra el patrimonio × violencia contra la mujer (terciles) |
| Mapa N° 03 | Cociente de localización por categoría (provincia o distrito) |
| Mapa N° 04 | Puntos calientes y fríos (Getis-Ord Gi*, contigüidad tipo reina, 999 permutaciones) |
| Gráfico N° 01 | Mapa de calor provincia × mes frente al promedio mensual de cada provincia |
| Mapa N° 05 | Calidad de la georreferenciación por provincia |

Categorías: total, violencia contra la mujer e integrantes del grupo familiar, patrimonio, robo, hurto, extorsión, estafa, lesiones, violación de la libertad sexual y delitos informáticos. Botón de tema **claro/oscuro** (respeta la preferencia del sistema y recuerda la elección en el navegador). Los filtros quedan en el enlace (`#cat=...&nivel=...`).

## Publicación en GitHub Pages
Subir el contenido de esta carpeta (`index.html`, `README.md`, `.nojekyll` y `scripts/`) a un repositorio (p. ej. `goodguysinsight/tablero_sidpol`) y activar **Settings → Pages → Deploy from a branch → main / (root)**.

## Regenerar
```
python scripts/procesar_sidpol_tablero.py SIDPOL.csv DISTRITOS/DISTRITOS.shp out
```
El script cuenta denuncias únicas (`ID_DGC`) por ubigeo del hecho y categoría, calcula tasas, Bayes empírico, cociente de localización, Gi* y terciles bivariados, y simplifica las geometrías. Requiere pandas, geopandas, libpysal y esda.

## Notas
- Unidad: denuncia única (`ID_DGC`); un registro del SIDPOL es una combinación de denuncia, persona y modalidad.
- Ubicación por ubigeo del distrito del hecho: la mayoría de coordenadas está forzada al centroide de la comisaría.
- Población: Censo de Población y Vivienda 2017 (capa distrital INEI); puede sobrestimar tasas donde la población creció.
- Las denuncias reflejan hechos reportados a la policía, no la incidencia real del delito.

## Enlace
https://goodguysinsight.github.io/tablero_sidpol/

# Snapshot académico de BeatsCloud

Esta carpeta es una extracción del árbol rastreado del repositorio oficial BeatsCloud en la rama `main`, SHA `3ca1408d86ae66a56d3de9df97f270aaddb9b31e`. El repositorio oficial enlazado abajo es la fuente de verdad; este snapshot es evidencia técnica del corte indicado y no recibe actualizaciones automáticas.

Incluye frontend React/TypeScript, backend Django, migraciones, pruebas automatizadas, configuración versionada y scripts de QA reproducibles. El README y la normalización `.mailmap` corresponden al corte de documentación posterior al baseline funcional `6ff6f55c3233644c1809ae0b807e74476ee5eafd`; no se cambiaron archivos de lógica entre esos cortes.

## Exclusiones

- `.git` y metadatos de ramas/objetos Git: la procedencia está registrada en `SOURCE_COMMIT.txt`.
- `.env`, secretos y credenciales: no forman parte del árbol rastreado fuente. Se conserva `.env.example` con valores vacíos o ficticios.
- Bases de datos locales, medios privados, `node_modules`, entornos virtuales, cachés y archivos temporales: no estaban rastreados en el SHA fuente y no se incluyeron.

`SHA256SUMS` enumera los archivos del snapshot excepto el propio manifiesto de checksums y este manifiesto de exclusiones.

Fuente: https://github.com/felipe-urtubia/BeatsCloud

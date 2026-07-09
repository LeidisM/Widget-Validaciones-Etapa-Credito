# Widget - Validaciones Etapa Crédito

Widget desarrollado para Zoho CRM que realiza la validación integral de un negocio antes de permitir el cambio a la etapa **Crédito**.

## Objetivo

Centralizar las validaciones comerciales, de riesgo y cumplimiento antes de aprobar un negocio, permitiendo identificar excepciones, controlar cupos y generar evidencia de la aprobación mediante una nota automática.

---

## Funcionalidades

- Consulta la información del negocio.
- Consulta información del Emisor y Deudor.
- Calcula disponibilidad de cupos.
- Permite modificar cupos operativos.
- Consulta Control CIFIN y Cámara de Comercio.
- Consulta Validaciones de Cumplimiento.
- Evalúa reglas según el objetivo del negocio.
- Determina si el negocio:
  - Puede continuar.
  - Requiere Gestión de Excepción.
  - Debe solicitar Gestión de Extracupo.
- Genera automáticamente una nota de auditoría al aprobar el negocio.

---

## Validaciones implementadas

### Estado de las entidades

Dependiendo del objetivo del negocio:

- Giro
- Compensación con Giro
- Compensación

se valida el estado del Emisor y/o Deudor.

---

### Cupos

Se valida:

- Cupo aprobado
- Cupo utilizado
- Disponible antes del negocio
- Disponible después del negocio

Cuando existe sobregiro se solicita Gestión de Excepción.

---

### Gestión de Extracupo

El usuario puede solicitar manualmente Gestión de Extracupo.

Al hacerlo:

- se actualiza el negocio
- se revalidan las reglas
- se obliga a registrar Gestión de Excepción

---

### Control CIFIN y Cámara

Se valida:

- Días CIFIN
- Estado CIFIN
- Observaciones CIFIN
- Días Cámara
- Estado Cámara
- Observaciones Cámara

También se detecta cuando no existe registro de Control CIFIN/Cámara.

---

### Cumplimiento

Consulta las validaciones de cumplimiento asociadas al negocio.

Se muestran los resultados de:

- Contraloría
- Procuraduría
- Listas Vinculantes
- Procesos Judiciales
- Observaciones

Si existe al menos una validación en estado **En revisión**, el negocio no podrá continuar a la etapa de Crédito.

Los estados **Finalizada** y **Anulada** permiten continuar normalmente.

Si el negocio no tiene validaciones asociadas, el proceso puede continuar de acuerdo con las reglas de negocio.
---

### Gestión de Excepción

La Gestión de Excepción es obligatoria cuando se presenta alguna de las siguientes situaciones:

- Sobregiro de cupo (Extracupo).
- Solicitud manual de Gestión de Extracupo.
- Estados no válidos del Emisor o Deudor según el objetivo del negocio.

Para continuar es obligatorio registrar:

- Link Gestión de Excepción.
- Comentarios de la excepción.

No es posible continuar a la etapa de Crédito mientras esta información no sea diligenciada.

---

### Evidencia

Al aprobar el negocio el widget crea automáticamente una Nota en Zoho CRM con:

- Información general
- Tasa aprobada
- Cupos utilizados
- Validaciones comerciales
- Validaciones de cumplimiento
- Gestión de excepción
- Estado de aprobación

---

## Tecnologías

- HTML5
- CSS3
- JavaScript (ES6)
- Zoho Embedded App SDK
- Zoho CRM API v7

---

## Estructura

```
app/
│
├── widget.html
├── app.js
├── styles.css
└── translations/

dist/
└── validacionesCredito.zip

plugin-manifest.json
package.json
```

---

## Instalación

```bash
npm install
```

---

## Compilar

```bash
zet pack
```

## Desarrollo

Durante el desarrollo el widget se ejecuta desde Zoho CRM utilizando el entorno de desarrollo del Widget.

Los cambios se realizan sobre los archivos ubicados en:

- app/widget.html
- app/app.js
- app/styles.css

Una vez finalizados, se generar el paquete:

```bash
zet pack
```

El archivo generado se encuentra en:

```
dist/validacionesCredito.zip
```

Este paquete es el que se publica en Zoho CRM.
Subir:

```
dist/validacionesCredito.zip
```

desde:

```
Zoho CRM
Developer Space
Widgets
```

---

## Requisitos

- Zoho CRM
- ZET CLI
- Node.js
- Permisos sobre:
  - Potentials - Negocios
  - Accounts
  - Pagadores
  - Notes

---

## Autor

Leidis
Analista CRM
Factor Dinero
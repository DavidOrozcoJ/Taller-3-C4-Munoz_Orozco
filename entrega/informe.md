# 📄 Informe Técnico del Taller

## 🔖 Nombre del Taller
_Taller 3 - Arquitectura Actual del Sistema con el Modelo C4_

## 👥 Integrantes del equipo
- Nombre 1 (correo o usuario GitHub)
- Nombre 2

## 🧠 Descripción general del trabajo
Este entregable corresponde a la **Parte 1 (Trabajo en Clase)** del taller: la construcción de las vistas C1 (Contexto) y C2 (Contenedores) del modelo C4 sobre el caso base **RedExpress**, siguiendo la metodología de 4 pasos por vista descrita en la guía paso a paso. El objetivo fue practicar la notación C4 y la lógica de descomposición (actores → sistema → contenedores → infraestructura) antes de aplicarla al sistema real del cliente en la Parte 2.

## 🔧 Proceso de desarrollo
Se siguió la guía paso a paso del taller en dos etapas:

1. **Vista de Contexto (C1):** se identificaron los tres actores del caso (Usuario Final, Mensajero, Operador Logístico), se definió la Plataforma RedExpress como sistema en alcance (una sola caja, sin desglosar módulos internos), y se identificaron los dos sistemas externos (API de Notificaciones y Proveedor de Geolocalización), diferenciándolos visualmente del sistema propio con doble borde. Se trazaron y etiquetaron todas las relaciones.
2. **Vista de Contenedores (C2):** se descompuso la Plataforma RedExpress en sus seis contenedores internos (App Móvil, Portal Web Operadores, Módulo de Gestión de Paquetes, Motor de Rutas, Seguimiento GPS, Sistema de Alertas) y se añadió la infraestructura de soporte (Balanceador de Carga, Base de Datos Distribuida). Se retomaron los actores y sistemas externos del C1 para mostrar con qué contenedor específico interactúa cada uno, y se etiquetó cada relación con su protocolo o mecanismo de comunicación.

La herramienta utilizada fue draw.io. El trabajo se validó contra la checklist de autoevaluación de la guía antes de considerarse terminado.

## 🧩 Análisis del modelo propuesto
- **Estructura del modelo:** el C1 mantiene el sistema como una caja negra, cumpliendo el principio de no exponer detalle interno en esta vista; el C2 abre esa caja y expone los contenedores y la infraestructura crítica, sin perder la trazabilidad con los actores y sistemas externos definidos en el C1.
- **Representación de necesidades del caso:** el modelo refleja las tres formas de interacción del caso base (rastreo/agenda desde app móvil, actualización de estado por mensajeros, gestión de rutas por operadores) y las dos integraciones externas (notificaciones y geolocalización).
- **Supuestos tomados:** se asumió que el Balanceador de Carga y la Base de Datos Distribuida son compartidos por ambos contenedores de interfaz (App Móvil y Portal Web); se asumió comunicación push/WebSocket solo para el seguimiento GPS en tiempo real, mientras el resto de relaciones son solicitud/respuesta síncronas.

## 📈 Diagrama final entregado
- Vista C1 (Contexto): `entrega/c1-contexto-final.drawio`
- Vista C2 (Contenedores): `entrega/c2-contenedores-final.drawio`

## 📋 Tabla de actores, entidades o componentes

| Nombre del elemento | Tipo | Descripción | Responsable |
|---|---|---|---|
| Usuario Final | Actor (C1) | Rastrea envíos y agenda recogidas | Cliente |
| Mensajero | Actor (C1) | Actualiza el estado de las entregas | Cliente |
| Operador Logístico | Actor (C1) | Gestiona rutas y despachos | Cliente |
| Plataforma RedExpress | Sistema (C1) | Sistema en alcance del taller | RedExpress |
| API de Notificaciones | Sistema externo (C1) | Envía alertas de estado a los usuarios | Tercero |
| Proveedor de Geolocalización | Sistema externo (C1) | Provee coordenadas para el cálculo de rutas | Tercero |
| App Móvil | Contenedor (C2) | Interfaz de Usuario Final y Mensajero | RedExpress |
| Portal Web Operadores | Contenedor (C2) | Interfaz de Operador Logístico | RedExpress |
| Módulo de Gestión de Paquetes | Contenedor (C2) | Orquesta rutas, ubicación y alertas | RedExpress |
| Motor de Rutas | Contenedor (C2) | Calcula rutas óptimas | RedExpress |
| Seguimiento GPS | Contenedor (C2) | Provee ubicación en tiempo real | RedExpress |
| Sistema de Alertas | Contenedor (C2) | Dispara notificaciones de estado | RedExpress |
| Balanceador de Carga | Infraestructura (C2) | Distribuye el tráfico entrante | RedExpress |
| Base de Datos Distribuida | Infraestructura (C2) | Persiste paquetes, rutas y usuarios | RedExpress |

## 🔍 Investigación complementaria
### Tema investigado:
_No aplica en esta entrega — la investigación complementaria (buenas prácticas y ejemplos reales de arquitecturas C4 en el sector del cliente) corresponde a la Parte 2 del taller, pendiente de desarrollo con el sistema real del cliente._

### Resumen:
_Pendiente para la Parte 2._

## 📚 Referencias
Ver `entrega/referencias.md`.

---

_Este documento hace parte de la entrega de la Parte 1 (Trabajo en Clase) del Taller 3 del curso AREM (Arquitectura Empresarial) - Universidad de La Sabana._

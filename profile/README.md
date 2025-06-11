# SkillTrade

**SkillTrade** es una plataforma diseñada para facilitar el intercambio de servicios entre miembros de una comunidad, usando una moneda digital interna y un sistema de reputación que fomenta la colaboración justa y organizada.

---

## Tabla de Contenidos

1. [Introducción](#introducción)
2. [Características Principales](#características-principales)
3. [Requisitos](#requisitos)

   * [Funcionales](#requisitos-funcionales)
   * [No Funcionales](#requisitos-no-funcionales)
4. [Arquitectura y Módulos](#arquitectura-y-módulos)
5. [Planificación del Proyecto](#planificación-del-proyecto)
6. [Instalación y Uso](#instalación-y-uso)
7. [Contribuir](#contribuir)
8. [Equipo de Trabajo](#equipo-de-trabajo)
9. [Enlaces Útiles](#enlaces-útiles)
10. [Licencia](#licencia)

---

## Introducción

En muchas comunidades, existen individuos con habilidades y conocimientos útiles, así como personas que requieren ayuda en tareas específicas. Sin embargo, la falta de una plataforma que conecte de manera justa y eficiente a quienes ofrecen y solicitan servicios puede desincentivar la colaboración.

**SkillTrade** proporciona:

* Publicación y búsqueda de servicios por categorías.
* Moneda digital interna para transacciones justas.
* Sistema de reputación y comentarios para generar confianza.

---

## Características Principales

* **Gestión de usuarios:** registro, edición de perfil y reputación.
* **Catálogo de servicios:** publicación, búsqueda y filtrado.
* **Transacciones con moneda virtual:** saldo, transferencias automáticas e historial.
* **Comunicación interna:** notificaciones y datos de contacto privado.
* **Moderación y seguridad:** reportes de contenido y gestión de sanciones.

---

## Requisitos

### Requisitos Funcionales

1. **Gestión de Usuarios**

   * Registro con correo, teléfono y contraseña validada por código de barrio.
   * Edición de perfil.
   * Visualización de reputación (puntuaciones y comentarios).

2. **Publicación y Búsqueda de Servicios**

   * Publicar ofertas de servicios.
   * Buscar servicios por categoría o palabras clave.

3. **Transacciones con Moneda Virtual**

   * Visualizar saldo de créditos.
   * Transferencias automáticas al completar servicios.
   * Historial detallado de transacciones.

4. **Acuerdos y Comunicación**

   * Acceso al número de contacto privado del proveedor.
   * Notificaciones de estado: aceptación, finalización y cancelación.

5. **Moderación y Seguridad**

   * Reporte de ofertas o perfiles inapropiados.
   * Suspensión de usuarios que violen normas.

### Requisitos No Funcionales

* **Usabilidad:** interfaz intuitiva; aprendizaje máximo de 10 minutos.
* **Rendimiento:** respuesta en < 1 segundo en el 95% de las peticiones.
* **Seguridad:** autenticación robusta; protección contra inyecciones SQL y XSS.
* **Escalabilidad:** arquitectura modular.
* **Mantenibilidad:** código documentado; uso de estándares (OpenAPI para APIs).

---

## Arquitectura y Módulos

El sistema está organizado en cinco módulos principales:

1. **Gestión de Usuarios**: registro, autenticación, perfiles y reputación.
2. **Catálogo de Servicios**: publicación, búsqueda y filtrado.
3. **Transacciones y Moneda Virtual**: balance, transferencia y historial.
4. **Comunicación y Acuerdos**: notificaciones y datos de contacto.
5. **Moderación y Seguridad**: monitoreo de contenidos y gestión de conflictos.

Además, un componente de **Analytics** agregará métricas clave (usuarios activos, habilidades populares, volumen de transacciones).

---

## Planificación del Proyecto

Cada iteración tendrá una duración de 3 semanas laborales:

* **Incremento 1 (3 semanas):**

  * Registro de usuarios con código (Historia 1.1)
  * Publicación y búsqueda de servicios (Historias 2.1 y 2.3)
  * Visualización de saldo (Historia 3.1)

* **Incremento 2 (3 semanas):**

  * Edición de perfil y reputación (Historias 1.2 y 1.3)
  * Caducidad de ofertas (Historia 2.2)
  * Acceso al número privado y notificaciones (Historias 4.1 y 4.2)

* **Incremento 3 (3 semanas):**

  * Transferencias automáticas e historial (Historias 3.2 y 3.3)
  * Moderación: reportes y suspensión de usuarios (Historias 5.1 y 5.2)

---

## Instalación y Uso

> **Nota:** Requiere Node.js >= 14, base de datos PostgreSQL 12+

1. Clona el repositorio:

   ```bash
   git clone https://github.com/Ornitorrinco/p1-SwEng2-2025i-Ornitorrinco.git
   ```
2. Instala dependencias:

   ```bash
   npm install
   ```
3. Configura variables de entorno en `.env`.
4. Ejecuta migraciones de base de datos:

   ```bash
   npm run migrate
   ```
5. Inicia el servidor:

   ```bash
   npm start
   ```
6. Abre `http://localhost:3000` en tu navegador.

---

## Contribuir

1. Haz un *fork* del repositorio.
2. Crea una rama con tu característica: `git checkout -b feature/nombre-feature`.
3. Realiza *commits* claros y descriptivos.
4. Envía un *pull request* detallando los cambios.

---

## Equipo de Trabajo

* Tatiana Acelas
* Alejandro Argüello
* Nicolás Quezada
* Esteban Rodríguez
* Edinson Sánchez
* Cristian Tovar
* Danny Yaluzán

---

## Enlaces Útiles

* Organización en GitHub: [https://github.com/Ornitorrinco/p1-SwEng2-2025i-Ornitorrinco](https://github.com/Ornitorrinco/p1-SwEng2-2025i-Ornitorrinco)

---

## Licencia

Este proyecto está bajo la licencia MIT. Consulta el archivo [LICENSE](LICENSE) para más detalles.

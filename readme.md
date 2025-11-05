# Sistema de Base de Datos - Mortalidad

## 📋 Descripción del Proyecto

Este proyecto contiene el diseño e implementación de una base de datos relacional para el registro y análisis de información sobre mortalidad accidental. El sistema permite almacenar datos detallados sobre víctimas, ubicaciones geográficas, causas de muerte y circunstancias de los hechos.

La base de datos está diseñada para gestionar información completa sobre muertes accidentales, incluyendo datos demográficos de las víctimas, información geográfica (departamentos y municipios), diagnósticos topográficos, mecanismos causales y detalles específicos de cada evento.

## 🎯 Objetivo 

El objetivo principal de este proyecto es crear un sistema de base de datos normalizado y optimizado que permita:

- Registrar y almacenar información estructurada sobre muertes accidentales
- Gestionar datos demográficos y sociales de las víctimas
- Organizar información geográfica mediante códigos DANE
- Relacionar causas de muerte con diagnósticos topográficos
- Facilitar consultas y análisis estadísticos sobre mortalidad
- Demostrar principios de diseño de bases de datos relacionales, normalización y optimización

Este proyecto forma parte de una actividad educativa sobre introducción al backend y bases de datos.

## ✨ Características Destacadas

- **Normalización Completa**: Base de datos normalizada hasta la Tercera Forma Normal (3FN)
- **Integridad Referencial**: Todas las relaciones están protegidas con claves foráneas y restricciones
- **Optimización**: Índices estratégicos para mejorar el rendimiento de consultas
- **Codificación Universal**: Soporte UTF-8 (utf8mb4) para caracteres especiales
- **Motor Transaccional**: Uso de InnoDB para garantizar transacciones ACID
- **Diseño Relacional**: Estructura que minimiza redundancia y maximiza la integridad de datos
- **Documentación Visual**: Incluye diagramas conceptuales, modelos lógicos y procesos de normalización

## 🛠️ Tecnologías Utilizadas

- **MySQL / MariaDB**: Sistema de gestión de bases de datos relacional
- **SQL**: Lenguaje de consulta estructurado para definición y manipulación de datos
- **InnoDB**: Motor de almacenamiento transaccional
- **UTF-8 (utf8mb4)**: Codificación de caracteres para soporte multilingüe

## 🗂️ Estructura del Sistema

La base de datos `sistema_mortalidad` está compuesta por 6 tablas principales:

### Tablas Principales

1. **DEPARTAMENTO**
   - Almacena información de departamentos
   - Clave primaria: `Codigo_DANE_Departamento`

2. **MUNICIPIO**
   - Almacena información de municipios
   - Clave primaria: `Codigo_DANE_Municipio`
   - Relación con DEPARTAMENTO mediante clave foránea

3. **PERSONA_VICTIMA**
   - Registra información demográfica y social de las víctimas
   - Incluye datos sobre sexo, identidad de género, escolaridad, etnia, etc.
   - Clave primaria: `ID_Victima` (auto-incremental)

4. **DIAGNOSTICO_TOPOGRAFICO**
   - Almacena diagnósticos topográficos y mecanismos causales
   - Clave primaria: `ID_Diagnostico_Topografico` (auto-incremental)

5. **CAUSA_MUERTE**
   - Relaciona las causas de muerte con los diagnósticos topográficos
   - Clave primaria: `ID_Causa` (auto-incremental)
   - Relación con DIAGNOSTICO_TOPOGRAFICO

6. **MUERTE_ACCIDENTAL**
   - Tabla principal que registra los hechos de muerte accidental
   - Relaciona víctimas, causas, ubicaciones y detalles del hecho
   - Clave primaria: `ID` (auto-incremental)
   - Relaciones con PERSONA_VICTIMA, CAUSA_MUERTE y MUNICIPIO

### Relaciones entre Tablas

- `MUNICIPIO` → `DEPARTAMENTO` (Muchos a Uno)
- `MUERTE_ACCIDENTAL` → `PERSONA_VICTIMA` (Muchos a Uno)
- `MUERTE_ACCIDENTAL` → `CAUSA_MUERTE` (Muchos a Uno)
- `MUERTE_ACCIDENTAL` → `MUNICIPIO` (Muchos a Uno)
- `CAUSA_MUERTE` → `DIAGNOSTICO_TOPOGRAFICO` (Muchos a Uno)

### Índices para Optimización

- `idx_municipio_departamento`: Optimiza búsquedas por departamento
- `idx_muerte_victima`: Optimiza búsquedas de muertes por víctima
- `idx_muerte_causa`: Optimiza búsquedas por causa de muerte
- `idx_muerte_municipio`: Optimiza búsquedas por ubicación
- `idx_causa_diagnostico`: Optimiza relaciones causa-diagnóstico

## 📁 Qué Hace Cada Archivo

### `codigo_mysql`
Archivo principal que contiene todos los scripts SQL para la creación de la base de datos. Incluye:
- Creación de la base de datos `sistema_mortalidad`
- Definición de todas las tablas con sus atributos
- Establecimiento de claves primarias y foráneas
- Configuración de restricciones de integridad referencial
- Creación de índices para optimización
- Configuración del motor InnoDB y codificación UTF-8

**Uso**: Ejecutar este archivo en MySQL para crear toda la estructura de la base de datos.

### `diagrama_conceptual.png`
Diagrama que representa el modelo conceptual de la base de datos. Muestra las entidades principales y sus relaciones de alto nivel, sin entrar en detalles técnicos de implementación.

**Propósito**: Visualizar la estructura general del sistema antes de la implementación.

### `modelo logico.jpg`
Modelo lógico de la base de datos que muestra la estructura detallada de tablas, atributos, tipos de datos y relaciones con sus cardinalidades.

**Propósito**: Representación técnica del diseño antes de la implementación física.

### `primera forma.jpg`
Documentación del proceso de normalización mostrando la Primera Forma Normal (1FN). Muestra cómo se eliminaron los grupos repetitivos y se aseguró que cada campo contenga valores atómicos.

**Propósito**: Demostrar el proceso de normalización y mejoramiento del diseño.

### `segunda forma.jpg`
Documentación del proceso de normalización mostrando la Segunda Forma Normal (2FN). Muestra cómo se eliminaron las dependencias parciales, asegurando que todos los atributos no clave dependan completamente de la clave primaria.

**Propósito**: Evidenciar la eliminación de redundancias mediante dependencias funcionales.

### `3 forma.jpg`
Documentación del proceso de normalización mostrando la Tercera Forma Normal (3FN). Muestra cómo se eliminaron las dependencias transitivas, asegurando que los atributos no clave no dependan de otros atributos no clave.

**Propósito**: Completar el proceso de normalización para un diseño óptimo.

### `readme.md`
Este archivo. Contiene toda la documentación del proyecto, incluyendo descripción, objetivos, tecnologías, estructura del sistema y guía de uso.

**Propósito**: Proporcionar documentación completa y accesible del proyecto.

## 🚀 Instalación y Configuración

### Requisitos Previos

- MySQL 5.7 o superior (o MariaDB equivalente)
- Acceso a un servidor MySQL o MariaDB
- Cliente MySQL (MySQL Workbench, phpMyAdmin, o línea de comandos)

### Pasos de Instalación

1. Abre tu cliente MySQL (MySQL Workbench, phpMyAdmin, o línea de comandos)

2. Ejecuta el archivo `codigo_mysql` que contiene todos los scripts de creación:
   ```bash
   mysql -u usuario -p < codigo_mysql
   ```
   
   O copia y pega el contenido del archivo en tu cliente MySQL.

3. Verifica que la base de datos se haya creado correctamente:
   ```sql
   SHOW DATABASES;
   USE sistema_mortalidad;
   SHOW TABLES;
   ```

## 🔒 Integridad Referencial

Todas las claves foráneas están configuradas con:

- **ON UPDATE CASCADE**: Actualizaciones se propagan automáticamente a las tablas relacionadas
- **ON DELETE RESTRICT**: Previene la eliminación de registros que tienen referencias en otras tablas, garantizando la integridad de los datos

## 🛠️ Uso

### Consultas de Ejemplo

```sql
-- Ver todas las muertes accidentales con información completa de víctima
SELECT 
    ma.ID,
    pv.Sexo,
    pv.Grupo_de_edad_quinquenal,
    m.Municipio,
    d.Departamento,
    dt.Diagnostico_Topografico,
    dt.Mecanismo_Causal,
    ma.Anio_del_hecho,
    ma.Mes_del_hecho
FROM MUERTE_ACCIDENTAL ma
JOIN PERSONA_VICTIMA pv ON ma.ID_Victima = pv.ID_Victima
JOIN MUNICIPIO m ON ma.Codigo_DANE_Municipio = m.Codigo_DANE_Municipio
JOIN DEPARTAMENTO d ON m.Codigo_DANE_Departamento = d.Codigo_DANE_Departamento
JOIN CAUSA_MUERTE cm ON ma.ID_Causa = cm.ID_Causa
JOIN DIAGNOSTICO_TOPOGRAFICO dt ON cm.ID_Diagnostico_Topografico = dt.ID_Diagnostico_Topografico;
```

## 👤 Autor
valentina mancilla 

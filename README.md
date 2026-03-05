## TALLER FULL STACK: SISTEMA DE GESTIÓN "COFFEE AROMA"
## OBJETIVO
Diseñar e implementar desde cero un sistema integral para la administración de una tienda de café y su cadena de suministro, permitiendo la gestión de:

Proveedores: Fincas y distribuidores de grano.

Clientes: Consumidores finales de la tienda.

Inventario: Registro de café en grano, molido y bebidas.

Transacciones: Control de compras de materia prima y ventas en barra.

El proyecto debe seguir un flujo de desarrollo profesional: modelado de datos, normalización, implementación de base de datos, desarrollo de API y frontend funcional.

## PARTE 1: ANÁLISIS Y MODELO ENTIDAD RELACIÓN (MER)
ESCENARIO
La cafetería "Coffee Aroma" opera bajo las siguientes reglas de negocio:

La empresa adquiere sacos de café de diferentes fincas (proveedores).

Un producto (ej. Bolsa de Café Arábica) no puede venderse si no existe un registro previo de su compra o ingreso al inventario.

El sistema debe permitir conocer la trazabilidad del grano: de qué finca proviene el café que se está sirviendo en una venta específica.

Una persona puede ser cliente recurrente y tener un historial de compras.

## PARTE 2: NORMALIZACIÓN
El modelo debe someterse a un proceso de normalización para garantizar la integridad de la información:

1FN (PRIMERA FORMA NORMAL)
Eliminación de atributos multivaluados (ej. no guardar varios tipos de tueste en una sola celda).

Asegurar la atomicidad de los valores.

2FN (SEGUNDA FORMA NORMAL)
Eliminación de dependencias parciales.

Los datos de la finca proveedora no deben repetirse en cada registro de bolsa de café.

3FN (TERCERA FORMA NORMAL)
Eliminación de dependencias transitivas.

Regla: No almacenar el total de una venta si este puede ser calculado sumando los precios de los productos individuales.

## PARTE 3: IMPLEMENTACIÓN EN MYSQL (CONSOLA)
REQUISITOS TÉCNICOS
La implementación debe realizarse exclusivamente mediante la interfaz de línea de comandos (CLI).

REGLAS DE INTEGRIDAD
Unicidad de SKU o códigos de barras para cada variedad de café.

Restricción de ventas sobre productos con stock en cero.

Restricción de borrado para proveedores que tengan facturas de compra asociadas.

El documento de identidad del cliente debe ser único.

## PARTE 4: CRUD CON NODE.JS Y EXPRESS
Desarrollo de una API REST enfocada en la entidad principal: PRODUCTO.

OPERACIONES OBLIGATORIAS
Create: Registro de nuevos granos o bebidas.

Read: Listado del menú y búsqueda por origen (ej. "Huila").

Update: Actualización de precios y niveles de stock.

Delete: Eliminación física con validación de dependencias comerciales.

## PARTE 5: INVESTIGACIÓN DE MULTER
Antes de la fase de importación masiva, se debe documentar:

Definición y flujo de un Middleware.

Protocolo multipart/form-data.

Diferencias entre diskStorage y memoryStorage en Multer.

## PARTE 6: IMPORTACIÓN MASIVA (CSV)
Implementación de funcionalidad para la carga de inventario inicial mediante un archivo desorganizado. El sistema debe limpiar los datos e insertarlos en la tabla padre.

DATASET DESORGANIZADO (DATA.CSV)


ID;PRODUCTO;PRECIO;STOCK;PROVEEDOR_INFO
1;Café Caturra;25000;10;Finca La Esperanza - Huila - NIT 900123
2;Espresso Roast;18000;5;Distribuidora Café Sur - Tolima
3;Prensa Francesa;12000;0;Finca La Esperanza - Huila - NIT 900123
4;Café Bourbon;32000;15;Variedades del Eje - Quindío - NIT 800456
5;Capuchino;8500;20;Interno (Preparado)
6;Café Caturra;25000;2;Finca La Esperanza - Huila - NIT 900123

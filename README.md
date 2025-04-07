# Mergofar-proyecto
Proyecto MERGOFAR S.A. - Gestión de base de datos y documentación
1_crear_base_de_datos.sql
CREATE DATABASE IF NOT EXISTS MERGOFAR;
USE MERGOFAR;
2_tablas_clientes.sql
CREATE TABLE Clientes (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50),
    apellido VARCHAR(50),
    telefono VARCHAR(20),
    direccion VARCHAR(100)
);
3_tablas_productos.sql
CREATE TABLE Productos (
    id_producto INT AUTO_INCREMENT PRIMARY KEY,
    nombre_producto VARCHAR(100),
    categoria VARCHAR(50),
    precio DECIMAL(10,2),
    stock INT
);
4_tablas_ventas.sql
CREATE TABLE Ventas (
    id_venta INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT,
    id_producto INT,
    fecha_venta DATE,
    cantidad INT,
    total DECIMAL(10,2),
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente),
    FOREIGN KEY (id_producto) REFERENCES Productos(id_producto)
);
5_insertar_datos.sql
-- Insertar clientes
INSERT INTO Clientes (nombre, apellido, telefono, direccion)
VALUES 
('Carlos', 'Ramírez', '3001234567', 'Cra 10 #20-30'),
('Laura', 'Gómez', '3017654321', 'Cll 45 #12-50');

 Insertar productos
INSERT INTO Productos (nombre_producto, categoria, precio, stock)
VALUES 
('Jarabe Natural de Eucalipto', 'Respiratorio', 15000, 50),
('Té Detox Herbal', 'Digestivo', 12000, 40);

 Insertar ventas
INSERT INTO Ventas (id_cliente, id_producto, fecha_venta, cantidad, total)
VALUES 
(1, 1, '2025-04-06', 2, 30000),
(2, 2, '2025-04-06', 1, 12000);
6_consultas_basicas.sql
 Consultar todos los clientes
SELECT * FROM Clientes;

Consultar productos disponibles
SELECT * FROM Productos WHERE stock > 0;

Ver ventas con detalle de cliente y producto
SELECT V.id_venta, C.nombre, C.apellido, P.nombre_producto, V.fecha_venta, V.cantidad, V.total
FROM Ventas V
JOIN Clientes C ON V.id_cliente = C.id_cliente
JOIN Productos P ON V.id_producto = P.id_producto;
7_actualizar_datos.sql
8_eliminar_datos.sql
-- Eliminar un producto
DELETE FROM Productos WHERE id_producto = 2;



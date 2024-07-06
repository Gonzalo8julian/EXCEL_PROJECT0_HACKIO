# EXPLICACIÓN EJERCICIO EXCEL

1. Abrir archivos .csv desde Excel haciendo: Datos/obtener datos desde archivo de texto.

2. Organización y optimización de los datos (editar errores ortográficos, alinear columnas, etc.)

    #### SALA
    - Utilización de reemplazar para editar las columnas completas.
    - Utilización de CONCAT para unificar la columna ''Platos ordenados''
    - Elección del tipo de dato de cada columna (número, moneda, texto, etc.)

    #### COCINA
    - Consolidación de la columna para unificar el número de orden.
    - También he realizado una tabla dinámica para unificar el número de orden. El resultado es el mismo que al consolidarla.

3. **Funciones** 
    - PARA EL CONJUNTO DE DATOS COCINA
        - Creación de columna ''Ganancia Neta'': Precio unitario Costo unitario x cantidad ordenada  
        - Creación columna '' Ganancia Bruta'': Precio unitario x cantidad ordenada.
        - % ganancia: Ganancia neta / Ganancia bruta x 100

    - PARA EL CONJUNTO DE DATOS SALA
        - Monto total de la cuenta: Precio del total de la comanda (cogido de la tabla cocina consolidada)* Cantidad ordenada. En esta columna he añadido el condicional de que si la columna de factura cobrada es NO, entonces el total es 0€ para no contarlo a la hora de calcular la facturación total.
        - Fecha de factura: Sacado de la columna ''Hora de salida'' donde aparece la fecha.
        - Hora de llegada y de salida: Adaptadas las dos columnas ya creadas y poniéndolo en el horario real para que aparezca en formato 24h.
        - Tiempo de permanencia: Calculado con la fórmula **=SI(K2="Ocupada";(F2-E2)+"00:15";F2-E2)**
        - Tiempo de preparación: A través de la tabla consolidada o tabla dinámica creada, he calculado el tiempo de preparación de los platos de una comanda. **SIN MULTIPLICARLO POR EL TOTAL DE PLATOS REALIZADOS**
        - Tiempo de degustación: Calculado con la fórmula: =SI(F2-E2<0;"0";F2-E2) (hora de salida - hora de entrada)
        - Cuenta cobrada o no: Utilizando fórmula: =SI(R2>0;"SI";"NO")
        - Orden cobrada o no: Creada en función del resultado de la columna Tiempo de degustación con la fórmula: **=SI([@[TIEMPO DEGUSTACIÓN]]<>"0";"SI";"NO")** para que aparezca Si o No en función de lo que haya sucedido.

4. **Tablas dinámicas y visualización** 
    - Creación de una nueva hoja llamada ''Dashboard'' donde aparece a modo resumen y junto con gráficos el análisis de todos los datos recopilados en las tablas anteriores.

        - TABLA 1: Análisis de ingresos por tipo de servicio: Tabla dinámica por la que aparece dividio el tipo de servicio (Almuerzo, comida o cena) y el total de ingresos obtenidos por cada uno. Además, para unificarlo con la TABLA 3, un filtro para poder seleccionar el día de la semana entre el 1 y el 8 de abril de 2023 y así poder saber el número de ingresos que ha habido cada día. Por último se ha añadido un gráfico dinámico donde se muestra la diferencia de ingresos entre los diferentes tipos de servicios.
        - TABLA 2: Análisis del número de transacciones por método de pago: Tabla dinámica donde aparece una primera columna dividia en los métodos de pago (efectivo, tarjeta de crédito y tarjeta de débito) y el recuento de transacciones que se ha hecho por cada método. Además, se añade un gráfico donde se ven las diferencias entre cada método.
        - TABLA 3: Desglose de ingresos por tipo de servicio y día de la semana. Unificada con la TABLA 1 a través del filtro para seleccionar el día de la semana.
        - TABLA 4: Desglose de ingresos por País de Origen: Tabla de dinámica dividida entre una columna con los paises de origen recopilados y el total de ingresos por cada uno de ellos. Acompañada de un gráfico y un filtro para poder interactuar con ello y saber qué paises son los que más y menos ingresos han realizado.
        - TABLA 5: Desglose de impagos: Tabla en la que se muestra el total de cuentas pagadas e impagadas, además del porcentaje de cuentas pagadas vs cuentas no pagadas. 
        - TABLA 6: Desglose de propinas: Una tabla dinámica interactiva, en la que se dividen todas las propinas recibidas por cada cliente y por cada método de pago, además de ver el total de las propinas recibidas.
        - TABLA 7: Desglose de órdentes atendidas por meseros: Tabla dinámica en la que aparece el recuento de órdenes atendidas por cada mesero de la base de datos.

4. **Resumen de resultados** 
    En la misma hoja que el apartado anterior, hemos añadido todos los gráficos para mostrar y explicar cada una de las tablas dinámicas realizadas, incluso donde se puede interactuar para poder ver diferentes datos en función de lo que queramos saber. 

    Además, se han añadido los cálculos requeridos en la parte principal del dashboard para poder tener una visión principal de los números más importantes: 
        - Número total de órdenes: Tabla dinámica en la que se muestra el número total de órdenes realizadas.
        - Número medio de comensales: Tabla dinámica en la que se muestra el promedio de comensales de cada comanda.
        - Ticket medio: Tabla dinámica que calcula el ticket medio en base a las facturas realizadas y cobradas.
        - Facturación total: Tabla dinámica que suma el total de las facturas cobradas. 
        - Coste total: Tabla dinámica que suma el total de costes que han supuesto todos los platos de las comandas **independientemente de que se hayan cobrado o no las comandas**.
        - Margen: Tabla normal realizada calculando la diferencia entre la facturación y los gastos.
        - Margen + propinas: Tabla dinámica en la que se suma el total de ingresos + las propinas recibidas. Realizado la acción campo calculado de la tabla dinámica. 

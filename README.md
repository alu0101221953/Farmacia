# Modelo Entidad/Relación. Farmacia
---

## 1. ***Descripción del Supuesto***
   
La gestión de una farmacia requiere poder llevar control de los medicamentos existentes, así como de los que se van sirviendo, para lo cual se pretende diseñar un sistema acorde a las      siguientes especificaciones:

    ● En la farmacia se requiere una catalogación de todos los medicamentos existentes, para lo cual se almacenará
    un código de medicamento, nombre del medicamento, tipo de medicamento (jarabe,   comprimido, pomada,...) unidades 
    en stock, unidades vendidas y precio. Existen medicamentos de venta libre y otros que sólo se pueden dispensar 
    con receta médica.
    
    ● En la farmacia se requiere una catalogación de todos los medicamentos existentes, para lo cual se almacenará 
    un código de medicamento, nombre del medicamento, tipo de medicamento (jarabe,   comprimido, pomada,...) 
    unidades en stock, unidades vendidas y precio. Existen medicamentos de venta libre y otros que sólo se pueden 
    dispensar con receta médica.
    
    ● La farmacia compra cada medicamento a un laboratorio, o bien los fabrica ella misma. Se desea conocer el 
    código del laboratorio, nombre, teléfono, dirección postal y fax, así como el nombre de la persona de contacto.
    
    ● Los medicamentos se agrupan en familias, dependiendo del tipo de enfermedades a las que dicho medicamento 
    se aplica. De este modo, si la farmacia no dispone de un medicamento concreto, puede vender otro similar 
    aunque de distinto laboratorio.
    
    ● La farmacia tiene algunos clientes que realizan los pagos de sus pedidos a fin de cada mes (clientes con crédito).
    La farmacia quiere mantener las unidades de cada medicamento comprado por los clientes (con o sin crédito)
    así como la fecha de compra. Además, es necesario conocer los datos bancarios de los clientes con crédito,
    así como la fecha de pago de las compras que realizan.
    
## 2. ***Entidades***

   #### 1. Medicamento
   Es la entidad que representa aquellas sustancias que sirven para prevenir, curar o aliviar enfermedades.
   Se encuentra caracterizada por los siguientes atributos:
      1. **Código_Med:** Es el identificador único de cada medicamento.
      2. **Nombre**: ES el nombre cientifico del medicamento.
      3. **Tipo**: Es el tipo del fármaco (jarabe,   comprimido, pomada,...).
      4. **Stock**: Unidades disponibles de ese medicamento.
      5. **Unidades Vendidad**: Ejemplares que se han liquidado.
      6. **Tipo Venta**: Indica si el medicamento es de venta libre o requiere receta.
   
   #### 2. Laboratorio

   
   #### 3. Cliente

   
   #### 4. Compra

   
   #### 5. Familia 

## 3. ***Relaciones***

## 4. ***Restricciones Semánticas***
      
   1. El tipo de venta de un ***Medicamento*** es de venta libre o con receta.
   
   2. En ***Cliente***, el atributo _Crédito_ es de tipo __bool__.
   
   3. En ***Cliente***, los atributos _Datos Bancarios_ y _Fecha de Pagos_ son __null__ si no tiene credito.
   
   4. Suponemos que un ***Medicamento*** pertenece unicamente a un tipo de ***Familia***.

    

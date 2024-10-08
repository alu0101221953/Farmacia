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
   + **Código_Med:** Es el identificador único de cada medicamento. Es el atributo clave.  
   + **Nombre**: ES el nombre cientifico del medicamento.  
   + **Tipo**: Es el tipo del fármaco (jarabe,   comprimido, pomada,...).  
   + **Stock**: Unidades disponibles de ese medicamento.  
   + **Unidades Vendidad**: Ejemplares que se han liquidado.  
   + **Tipo Venta**: Indica si el medicamento es de venta libre o requiere receta.  
   
   #### 2. Laboratorio
   Lugar en el que se desarrollan los medicamentos. Este puede proveer de medicamentos a la farmacia.
   Tiene los siguientes atributos:  
   + **Código_Lab:** Identificador único de cada laboratorio. Es el atributo clave.  
   + **Nombre:** Nombre del laboratorio.  
   + **Teléfono:** Número de teléfono de contacto.  
   + **Dirección Postal:** Identificación completa del destinatario de un correo.  
   + **Fax:** Número de contacto fax.  
   + **Persona Contacto:** Usuario perteneciente al laboratorio con el que se puede contactar.  

   #### 3. Cliente
   Personas que van a comprar a la farmacia. Dispone de los siguientes atributos:  
   + **DNI:** Documento nacional de identificación. Es el atributo clave.  
   + **Nombre:** Nombre del cliente.  
   + **Crédito:** Indica si el cliente tiene pagos con crédito. Es de tipo **bool**.  
   + **Datos Bancarios:** Contiene la información bancaria del cliente. Es **null** si el cliente no tiene crédito.
   + **Fecha de Pagos:** Contiene las fechas de los pagos con crédito. Es **null** si el cliente no tiene crédito.
   
   #### 4. Compra
   Recibos de compra por parte de los clientes.
   + **Código Compra:** Identificar único de cada compra.
   + **Código Medicamento:** Código de los medicamentos adquiridos por el cliente.
   + **Unidades Compradas:** Número de unidades de cada medicamento comprado.
   + **Importe:** Coste total de la compra.
   + **Fecha:** Fecha de realización de la compra.
   + **DNI Cliente:** Identificador del comprador en caso de que sea un cliente con crédito.
   
   #### 5. Familia 
   Agrupamiento de medicamento que sirven para tratar un mismo tipo de enfermedad.
   + **Codigo Fam:** Identificador del tipo de familia.
   + **Tipo:** Enfermedades a las que se aplican los medificamento de la familia.

## 3. ***Relaciones***
   #### Medicamento - Familia (Pertenece)
   
   - **Cardinalidad**: 1:N
   - **Descripción**: Un medicamento pertenece a una única familia (grupo de enfermedades tratadas), pero una familia puede tener múltiples medicamentos asociados.
   
   ---
   
   #### Medicamento - Laboratorio (Suministra)
   
   - **Cardinalidad**: N:M
   - **Descripción**: Cada medicamento puede ser suministrado por varios laboratorios, que pueden ser la misma farmacia u otra entidad externa. Un laboratorio puede proveer varios medicamentos diferentes.
   
   ---
   
   #### Cliente - Compra (Realiza)
   
   - **Cardinalidad**: 1:N
   - **Descripción**: Un cliente puede realizar múltiples compras en la farmacia. Cada compra se asocia a un solo cliente, registrando la información bancaria y la fecha de pago en caso de clientes con crédito.
   
   ---
   
   #### Compra - Medicamento (Involucra)
   
   - **Cardinalidad**: N:M
   - **Descripción**: Una compra puede incluir varios medicamentos, y se almacenan las unidades compradas de cada medicamento en cada compra. Un medicamento en específico se puede ver involucrado en varias compras.

## 4. ***Restricciones Semánticas***
      
   1. El tipo de venta de un ***Medicamento*** es de venta libre o con receta.
   
   2. En ***Cliente***, el atributo _Crédito_ es de tipo __bool__.
   
   3. En ***Cliente***, los atributos _Datos Bancarios_ y _Fecha de Pagos_ son __null__ si no tiene credito.
   
   4. Suponemos que un ***Medicamento*** pertenece unicamente a un tipo de ***Familia***.

    

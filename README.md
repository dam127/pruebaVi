<<<<<<< HEAD
# Web Service : WS CORTES

## Introduccion

## Instalacion
>El codigo fuente se encuentra en la ruta del GIT de Viesgo : **https://gitlab.corp.cic.es/VIESGO/Distribucion/CalidadSuministro/CortesWS**

### Eclipse
>File > New Proyect > Other > Web Dynamic Project
Project name: CortesWS
Definir : Target Runtime - Apache Tomcat v7.0.42 (Jdk 1.6.0.45)
Definir : Jdk 1.6.0.45	
>
En la opcion del proyecto : **Properties for CortesWs >> Project Facets** definir :
>+ Dynamic Web Module 3.0
>+ Java 1.6
>+ JAvaScript 1.0

En la pestaña **Runtimes** es obligatorio marcar en cada opcion el check **Apache Tomcat v7.0.42**
***
En caso de que el proyecto de el sieguiente error: **The annotation @XmlElement is disallowed for this location:**
Click derecho sobre el proyecto>Propiedades>Java Build Path>Order and Export

Reordenamos para que se vea de la siguiente manera:
>+ CortesWS/src
>+ Web App Libraries
>+ Apache Tomcat v7.0.42
>+ JRE System Library [jdk1.6_45]
***
### Requesitos
>+ IDE Eclipse
>+ Java 1.6.0.45
>+ Tomcat 7.0.42

### Anexo
Las coordenadas de los CD's se encuentran definidas en el fichero **CentroidesCts.xml** que se encuentra en el paquete **eon.cortes.centroides.ct**.

Para la regeneracion de este fichero se ha añadido un fichero SQL con un grupo de SQL's que se tienen que ejectuar en PRODUCCION, recogiendo sus datos y editando el fichero CentroidesCts.xml
con la nueva informacion obtenida.
 
Es IMPORTANTE cerrar la conexion contra la B.DD. cada vez que se ejecute la sentencia SQL para evitar colapsar la B.DD. 

### Peticiones / Pruebas
Ruta del fichero WSDL 
>+ LOCAL [http://localhost:8080/CortesWS/CortesWS?wsdl]
>+ PRE [http://10.123.112.137/CortesWS/CortesWS?wsdl]
>+ PRO [http://10.123.112.20/CortesWS/CortesWS?wsdl]

### LOG
Ruta del fichero LOG (Cortes_WS.log) 
>+ PRE [http://10.123.112.137/onlineLogs/] *En PRE el fichero LOG se denomina WSCortes.txt
>+ PRO [http://10.123.112.20/onlineLogs/]

### Properties
| Fichero | Descripcion |
|-------|-------------|

## Entregas
### Version CADI_WS_CORTES_v207
#### Introduccion

| Campo | Descripcion | 
|-------|-------------|
| Version | CADI_WS_CORTES_v207 24/10/2018 | 
| Resumen | Evolutivo WS Cortes para calidad de portal | 
| Incidencia | JIRA [CADIPIT-754](https://corp.app.viesgo.com/JiraIT/browse/CADIPIT-754) | 

>+ Modificacion consultas de periodo actual para notificar unicamente incidentes en estado 'ASIGNADO', 'EN RESOLUCION','RESUELTO' y 'VALIDADO'.
>+ Cambio Fecha inicio incidente getDetalleCT. 
>+ Nuevo metodo getIncidentes. 
>+ Incluir fecha fin prevista en getAllDetalleCT.
>+ Creado nuevo periodo a 7 dias.

#### Contenido

| Carpeta | Fichero | Descripcion |
| ------- | --------- | ----------- |
| 01. BBDD | **Nuevas_Fechas_GDR_CALIDAD_INCIDENCIA_ONLINE.sql** | Crear nuevos campos para las fechas INCIOL_FECHA_PREV_LLEGADA y INCIOL_FECHA_PREV_RESOLUC en tabla GDR_CALIDAD.INCIDENCIA_ONLINE|


### Evolutivo Automatizacion Reclamaciones II - Version CADI_WS_CORTES_vX.X.X
___
### Evolutivo Incidencias AT/MT - Version CADI_WS_CORTES_v2.2.0 (08/01/2019)
Se añaden nuevos campos INCIOL_FECHA_PREV_LLEGADA y INCIOL_FECHA_PREV_RESOLUC en la tabla GDR_CALIDAD.INCIDENCIA_ONLINE
___
### Evolutivo Incidencias abiertas Mapa Calidad - Version CADI_WS_CORTES_v2.2.0
#### Introduccion
| Campo | Descripcion | 
|-------|-------------|
| Version | CADI_WS_CORTES_v208 (01/02/2019) | 
| Resumen | Notificar como incidentes abiertos aquellos con estados ACTIVO, ASIGNADO, EN RESOLUCION | 
| Incidencia | JIRA [CADIPIT-779](https://corp.app.viesgo.com/JiraIT/browse/CADIPIT-779) | 

___
### Version CADI_WS_CORTES_v2.3.0
#### Introduccion
| Campo | Descripcion | 
|-------|-------------|
| Version | CADI_WS_CORTES_v209 (25/02/2019) | 
| Resumen | Modificar el servicio CADI de cortes, para que no notifique como activo los incidentes de BT cuya resolución en campo es "inci_reparación_finalizada" | 
| Incidencia | JIRA [CADIPIT-800](https://corp.app.viesgo.com/JiraIT/browse/CADIPIT-800) | 

Se modifican los siguientes sql's;
>+ select id="select-avisos"
>+ select id="select-cups-detalle"
>+ select id="select-cd-detalle"
___
### Version CADI_WS_CORTES_v2.3.1
#### Introduccion
| Campo | Descripcion | 
|-------|-------------|
| Version | CADI_WS_CORTES_v210 (29/04/2019) | 
| Resumen | Se corrigen nn el mapa de calidad los municipios con Ñ no están bien escritos, donde aparecen con N en lugar de Ñ. | 
| Incidencia | JIRA [CADIPIT-825](https://corp.app.viesgo.com/JiraIT/browse/CADIPIT-825) | 

Modificacion de los siguientes ficheros.
>+ CentroidesMunicipios.xml (Cambio de 19 nombres de municipios)
___
### Version CADI_WS_CORTES_v2.4.0
#### Introduccion
| Campo | Descripcion | 
|-------|-------------|
| Version | CADI_WS_CORTES_v211 (xx/xx/xxxx) | 
| Resumen | Obtener las averias masivas para un CUPS | 
| Incidencia | JIRA [CADIPIT-806](https://corp.app.viesgo.com/JiraIT/browse/CADIPIT-806) | 

Se añade la siguiente sql's:
>+ select-incidentes-averia-masiva

Se modifica el fichero **prj.properties** para añadir un parametro de configuracion:
>+ minimo-numero-suministros=10 

¡MODIFICAR FICHERO **prj.properties** PARA AÑADIR LA NUEVA PROPIEDAD!
DESCOMENTAR EL METODO **getIncidentesAveriaMasica**

=======
<<<<<<< HEAD
# pruebaVi
=======
:memo: toda
# pruebaC
>>>>>>> remotes/origin/develop
>>>>>>> 8f52d482cadfacd1063bd753e64b62e5709ea4ae

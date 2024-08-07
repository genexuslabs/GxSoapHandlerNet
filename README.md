# GxSoapHandler
## Spanish
Componente para reescribir paquete Soap, especialmente sus credenciales. Al llamar a un servicio se pueden sobreescribir los valores del mismo usando el tipo de datos location.

A partir de la versión GeneXus v15 upgrade 11 hay una nueva propiedad (Non Standard), location.Configuration, que permite hacer dinámicos estos parámetros.

En GeneXus se puede programar algo  así: 

```
&location = GetLocation("WS_eFactura")
&location.Configuration= "Nombre;IDENTITY;PATH_CERT_DGI; PATH_ CERT_CLIENTE;PASSWORD;URI"    // Esta es la nueva propiedad,donde se pasa un string  en este caso

//Se carga una consulta como test para DGI
&pWS_eFacturaData.xmlData.FromString("")
&pWS_eFacturaDataResult = &WS_eFactura.EFACRECEPCIONSOBRE(&pWS_eFacturaData)
&longvar = &pWS_eFacturaDataResult.ToXml()
```

Se debe armar un assembly GxSoapHandler.dll con este proyecto que recibe los parámetros y modifica las credenciales.

Además, se debe agregar en el `web.config` la línea:
```
<add key="NativeChannelConfigurator" value="GxSoapHandler" />
```
    
## English
Component to rewrite webservice credential. When calling a service, its values ​​can be overwritten using the location data type.

Starting with the GeneXus v15 upgrade 11 version, there is a new property (Non Standard), location.Configuration, that allows these parameters to be made dynamic. 

In GeneXus, something like this would be programmed:

```
&location = GetLocation("WS_eFactura") 
&location.Configuration= "Name;IDENTITY;PATH_CERT_DGI; PATH_ CERT_CLIENT;PASSWORD;URI" // This is the new property, where It pass a string in this case

//It load a query as a test for DGI
&pWS_eFacturaData.xmlData.FromString("")
&pWS_eFacturaDataResult = &WS_eFactura.EFACRECEPCIONSOBRE(&pWS_eFacturaData)
&longvar = &pWS_eFacturaDataResult.ToXml()
```

A GxSoapHandler.dll assembly must be created with this project, that receives the parameters and modifies the credentials.

Additionally, this line must be added to the `web.config` file:
```
<add key="NativeChannelConfigurator" value="GxSoapHandler" />
```

# Práctica 16 - Creación de recursos a través de Azure Resource Manager

## Innovaccion Virtual (VII Edición) #IAWizards

### Semana 3 - Sesión 7

En esta práctica se creó una cuenta de almacenamiento a través de Azure Resource Manager.

---------------------------------------------------

#### Requerimientos
-  Una cuenta de Azure con suscripción.
- [Visual Studio Code](https://code.visualstudio.com/download).
- Instalar la extensión [Azure Resource Manager (ARM)](https://marketplace.visualstudio.com/items?itemName=msazurermtools.azurerm-vscode-tools) en Visual Studio Code.

----------------------------------------------------

#### Pasos a seguir

1. Abrimos Visual Studio Code y creamos un nuevo archivo llamado “azuredeploy.json” y descargamos la extensión de VSC ‘Azure Resource Manager (ARM) Tools’.

![P16I1](Images\Sesión 7 - P16 01.PNG)

2. Habiendo creado el archivo .json, escribimos el siguiente script:

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "resources": []
}
```

![P16I2](Images\Sesión 7 - P16 02.PNG)

3. Posteriormente, para subir esto a Azure, en la pestaña de ‘Explorer’ desplegamos la plantilla donde se encuentran los proyectos, y buscamos por el archivo “azuredeploy.json” y le damos click derecho y pulsamos sobre ‘Reveal in File Explorer’. Al abrir el explorador de archivos, pulsamos sobre la ruta de ubicación y remplazamos la ruta por “cmd” y damos enter.

![P16I3](Images\Sesión 7 - P16 03.PNG)

![P16I4](Images\Sesión 7 - P16 04.PNG)

4. Una vez abierto el cmd, escribimos los siguientes comandos:

```
az deployment group create \
--name my-first-template \
--resource-group Sesion7 \
--template-file Azuredeploy.json
```

Esperamos a que se termine de implementar.

![P16I5](Images\Sesión 7 - P16 05.PNG)

5. Para comprobar la implementación realizada, podemos ir al grupo de recursos que creamos y clickear en ‘Implementaciones’ y aquí se encontrarán la plantilla que se elaboró con los comandos, con el estado de ‘Correcta’ que quiere decir que se implementó correctamente.

![P16I6](Images\Sesión 7 - P16 06.PNG)

6. Regresamos a VSC y en el apartado del script, donde se escribió “resources”: [] damos un enter entre ambos corchetes para luego escribir los siguientes comandos:

```json
{
      "type": "Microsoft.Storage/storageAccounts",
      "apiVersion": "2021-09-01",
      "name": "mystorageaccount",
      "location": "Central US",
      "sku": {
        "name": "Standard_LRS"
      },
      "kind": "StorageV2",
      "properties": {
        "supportsHttpsTrafficOnly": true
      }
}
```

![P16I7](Images\Sesión 7 - P16 07.PNG)

7. Repetimos los pasos 4 y 5 para encontrarnos con los recursos de almacenamiento que se elaboraron con comandos en VSC.

***Información Adicional:*** Si el paso 4 no funciona en cmd, quitar los \ y dejar todo el script en una sola línea, es decir, sin enter. Los pasos también se encuentran en el acordeón: [https://github.com/josejesusguzman/acordeon-az900-innovaccion/blob/main/res/plantilla_arm.md](https://github.com/josejesusguzman/acordeon-az900-innovaccion/blob/main/res/plantilla_arm.md).
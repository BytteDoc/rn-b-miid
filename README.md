![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/LogoBytte.png)

# Bytte S.A.S

# Documento Integración SDK React Native V2
### CONFIDENCIALIDAD

La información contenida en el presente documento es CONFIDENCIAL, hace parte del secreto comercial e industrial de la empresa e implica transmisión de información cuya propiedad corresponde exclusivamente a BYTTE SAS. En consecuencia, la divulgación o el uso inapropiado de la información aquí contenida por parte del receptor de la misma, implicarán la aplicación de las normas legales pertinentes para su debida protección.

### 1. INTRODUCCIÓN

#### Propósito General del Documento

El presente documento tiene como finalidad dar a conocer el paso a paso de la instalación del SDK provisto por Bytte en una aplicación hibrida generada en React Native.

#### 1.1. Objetivo

El presente documento tiene como objetivo explicar basado en un ejemplo, cómo realizar la integración del SDK Bytte a una aplicación React Native.

#### 1.2. Factores Limitantes

Los factores limitantes para la integración del SDK son:
* El Plugin SDK Bytte, está disponible para plataformas IOS y Android únicamente.
* Se recomiendan cámaras con resolución mayores o iguales a 8 Mega Pixeles para un óptimo rendimiento.
* Se debe verificar la calidad de la cámara, es recomendable utilizar dispositivos con cámara que tengan la característica de “Auto Foco” habilitada.
* El SDK no funciona sobre dispositivos virtuales, únicamente sobre dispositivos físicos IPhone y Android.

### 2. INSTALACIÓN

#### 2.1. Pre requisitos

* General:
    > * NPM (sistema de gestión de paquetes)

* Para la compilación de aplicación en plataforma IOS, se requiere:
    > * XCode 15 o Superior con SDK IOS 15 o superior.

#### 2.2. Instalación Plugin react-native-bytte-bio-lib-miid

#### 2.2.1 Configuración Token

#### 2.2.1.1 MAC

Una vez instalado NPM (sistema de gestión de paquetes). En la ruta por defecto de instalación se debe encontrar el archivo .npmrc, si no se encuentra se debe crear a nivel de usuario.

Una vez detectado el archivo se debe configurar de la siguiente manera.

Copie el siguiente código a su .npmrc.


```
registry=https://byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/RN-B-MIID/npm/registry/ 
                        
always-auth=true

; begin auth token
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/RN-B-MIID/npm/registry/:username=BytteTFS
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/RN-B-MIID/npm/registry/:_password=[BASE64_ENCODED_PERSONAL_ACCESS_TOKEN]
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/RN-B-MIID/npm/registry/:email=npm requires email to be set but doesn't use the value
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/RN-B-MIID/npm/:username=BytteTFS
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/RN-B-MIID/npm/:_password=[BASE64_ENCODED_PERSONAL_ACCESS_TOKEN]
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/RN-B-MIID/npm/:email=npm requires email to be set but doesn't use the value
; end auth token
```
En el espacio (BASE64_ENCODED_PERSONAL_ACCESS_TOKEN) se debe ingresar el password enviado por Bytte s.a.s.

#### 2.2.1.2 WINDOWS

Una vez instalado NPM (sistema de gestión de paquetes). Se debe ejecutar el siguiente comando en la terminal.

``` vsts-npm-auth -config .npmrc```

este comando creará un archivo .npmrc en la ruta por defecto C:\Users\USER\\.npmrc

Una vez detectado el archivo se debe configurar de la siguiente manera.

```
registry=https://byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/RN-B-MIID/npm/registry/ 
                        
always-auth=true
```
                        
# rn-b-miid

#### 2.2.2 Instalación 

`$ npm install rn-b-miid --save`


Una vez instalado el plugin, se debe realizar la consulta a la aplicación para verificar que este quedó correctamente instalado.

### Configuración Plataformas
#### 2.3. Configuración nativo iOS (XCode)
## iOS

######   Adicionar la implementación bytte a su proyecto NPM
para esta implementación se puede generar desde npm integrando de la siguiente forma: 

``` npm install rn-b-miid --save```

Luego de instalar las dependencias npm se ingresa a la carpeta ***ios*** y se ejecuta el comando `pod install`

    $ cd ios
    $ pod install

![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/ReactNative/podinstall.png)


###### Licencia captura dactilar y captura facial

Bytte proporciona archivos de licencia para captura dactilar y facial. Estos archivos deben ser guardado en la raiz del proyecto IOS y embebido como recurso en la aplicación nativa tal como lo muestra la siguiente imagen.

![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/ReactNative/Licencias.png)

El nombre del archivo se envía por parámetro ***(namePath)*** en la captura dactilar y facial.


######   Permisos
Los permisos en runtime deben ser solicitados por la app para el uso de bytte es necesario el siguiente:
configurar en el archivo Info.plist para el uso de la ***Camara***

`Privacy - Camera Usage Description`

#### 2.4. Configuración nativo Android
## Android

* **Se debe verificar la calidad de la cámara, es recomendable utilizar dispositivos con cámara que tengan la característica de “Auto Foco” habilitada**
* **Se recomiendan cámaras con resolución mayores o iguales a 5 Mega Pixeles para un óptimo rendimiento**
* **El SDK no funciona sobre dispositivos virtuales, únicamente sobre dispositivos físicos IPhone y**
* **Sistemas soportados Android 5.0 o superior gradle 4.1.2 o superior arquitecturas x86,64 bits**


### Para compilación de aplicación en plataforma Android, se requiere:
* **Java JDK Versión 1.8**
* **Android SDK** 
* **Funciona con Android 5.0 o superior**
* **Para el uso de la licencia identy es necesario registrar el app Pakage ID**  
* **Para generar la llave safetyNet api key busca los detalles del resgistro**
en https://developer.android.com/training/safetynet/attestation 
* **Desarrollador SHA1 Key. Cada desarrollador necesita un par de claves para firmar aplicaciones: una para debug y otra para el modo de release. Estos HASH también deben estar asociados con la licencia.**

## licencia  Android para el uso de huellas
* **crear una carpeta en el direccorio android llamada assets**
Dentro de esa carpeta depositamos el archivo de licencia que se generara para la implementación en debug y otra para reléase


## Luego vamos a generar la llave safetynet 
https://developer.android.com/training/safetynet/attestation
en la url se muestran los detalles para solicitar la llave safetynet 


## Los permisos en runtime deben ser solicitados por la app
para el uso de bytte es necesario los siguientes:
uso de ***Camara y almacenamiento***
`<uses-permission android:name="android.permission.CAMERA" />`
`<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>`
######   Adicionar la implementación bytte a su proyecto 
``` npm i react-native-rn-bytte-bio-lib-miid --save```

Luego vamos a android en la app, para la configuración en el archivo `build.gradle` del proyecto

`android/build.gradle`:

##### en la etiqueta 
   ``` 
allprojects {
    repositories {
          maven {
        url 'https://multifactorbyttelibrary.pkgs.visualstudio.com/BytteSDKLibraryX/_packaging/BytteSDKIdenty/maven/v1'
        name 'BytteSDKIdenty'
        credentials {
            username ""
            password ""
        }
    }
    }
}

   ``` 

Solicitar a **Bytte lo siguiente:**   ingresarlo dentro de los "" 
- **username**
- **password**


Tener en cuenta que debe estar habilitado multidex para android revisar la documentación para generarlo en react-native
' multiDexEnabled true'
Las librerías bytte soportan las arquitecturas a 32 y 64 bits necesarias para Android
 ndk{
             abiFilters  "armeabi-v7a", 'arm64-v8a'
        }
        

### 2. USO
```javascript
import { NativeModules } from 'react-native';

const { RnBytteBioLibMiid } = NativeModules;

export default RnBytteBioLibMiiD;
```

## Metodos react-native-bytte-bio-lib-miid

* Una vez instalado el plugin, la aplicación destino heredará el Javascript expuesto por este, el cual expone las siguientes operaciones:

#### Captura de la parte frontal del documento 
```javascript
import {NativeModules} from 'react-native'

const btnFront = () => {
  captureType = 'FRONT';
  NativeModules.RnBytteBioLibMiiD.startDocumentPki(
    url,
    ClientID,
    ClientKey,
    sesionId,
    country,
    captureType,
    (response: string) => {
      let res = JSON.parse(response);
      console.log(res);
    },
  );
};
```

| Parámetro          | Tipo       | Descripción                                      |
|--------------------|------------|--------------------------------------------------|
| **url**            | `string`   | Dirección del servidor.                          |
| **ClientID**       | `string`   | Identificador único del cliente.                 |
| **ClientKey**      | `string`   | Clave secreta para la autenticación.             |
| **sesionId**       | `string`   | Llave que encripta la imagen.                    |
| **country**        | `string`   | Código del país: (`CO` Hologramas, `COV2` Digital).                              |
| **captureType**    | `string`   | Tipo de captura (`FRONT` para frontal).          |
| **Callback**       | `function` | Función para manejar la respuesta en JSON.       |


#### Captura de la parte trasera del documento
```javascript
import {NativeModules} from 'react-native'

const btnBackDoc = () => {
  captureType = 'BACK';
  NativeModules.RnBytteBioLibMiiD.startDocumentPki(
    url,
    ClientID,
    ClientKey,
    sesionId,
    country,
    captureType,
    (response: string) => {
      let res = JSON.parse(response);
      Alert.alert(res.MensajeOriginal);
      console.log(res);
    },
  );
};

```

| Parámetro          | Tipo       | Descripción                                      |
|--------------------|------------|--------------------------------------------------|
| **url**            | `string`   | Dirección del servidor.                          |
| **ClientID**       | `string`   | Identificador único del cliente.                 |
| **ClientKey**      | `string`   | Clave secreta para la autenticación.             |
| **sesionId**       | `string`   | Llave que encripta la imagen.                    |
| **country**        | `string`   | Código del país: (`CO` Hologramas, `COV2` Digital).                                |
| **captureType**    | `string`   | Tipo de captura (`BACK` para trasero).           |
| **Callback**       | `function` | Función para manejar la respuesta en JSON.       |



#### Captura de huellas dactilares
```javascript
import {NativeModules} from 'react-native'

 const btnFinger = () => {
  NativeModules.RnBytteBioLibMiiD.startFingerID(
    url,
    licFinger,
    ClientID,
    ClientKey,
    sesionId,
    fingerNumber,
    (response: string) => {
      let res = JSON.parse(response);
      Alert.alert(res.MensajeOriginal);
      console.log(res.MensajeOriginal);
    },
  );
};

```
| Parámetro          | Tipo       | Descripción                                      |
|--------------------|------------|--------------------------------------------------|
| **url**            | `string`   | Dirección del servidor.                          |
| **licFinger**      | `string`   | Licencia para la captura de huellas.             |
| **ClientID**       | `string`   | Identificador único del cliente.                 |
| **ClientKey**      | `string`   | Clave secreta para la autenticación.             |
| **sesionId**       | `string`   | Llave que encripta la imagen.                    |
| **fingerNumber**   | `number`   | Número del dedo a capturar (`2` para derecho, `7` para izquierdo). |
| **Callback**       | `function` | Función para manejar la respuesta en JSON.       |


####  Captura facial

```javascript
import {NativeModules} from 'react-native'

const btnFace = () => {
  NativeModules.RnBytteBioLibMiiD.startFaceID(
    url,
    licFace,
    ClientID,
    ClientKey,
    sesionId,
    (response: string) => {
      let res = JSON.parse(response);
      Alert.alert(res.MensajeOriginal);
      console.log(res);
    },
  );
};

```


| Parámetro          | Tipo       | Descripción                                      |
|--------------------|------------|--------------------------------------------------|
| **url**            | `string`   | Dirección del servidor.                          |
| **licFace**        | `string`   | Licencia para la captura facial.                 |
| **ClientID**       | `string`   | Identificador único del cliente.                 |
| **ClientKey**      | `string`   | Clave secreta para la autenticación.             |
| **sesionId**       | `string`   | Llave que encripta la imagen.                    |
| **Callback**       | `function` | Función para manejar la respuesta en JSON.       |











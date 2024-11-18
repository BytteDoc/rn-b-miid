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

- El Plugin SDK Bytte, está disponible para plataformas IOS y Android únicamente.
- Se recomiendan cámaras con resolución mayores o iguales a 8 Mega Pixeles para un óptimo rendimiento.
- Se debe verificar la calidad de la cámara, es recomendable utilizar dispositivos con cámara que tengan la característica de “Auto Foco” habilitada.
- El SDK no funciona sobre dispositivos virtuales, únicamente sobre dispositivos físicos IPhone y Android.

### 2. INSTALACIÓN

#### 2.1. Pre requisitos

- General:

  > - NPM (sistema de gestión de paquetes)

- Para la compilación de aplicación en plataforma IOS, se requiere:
  > - XCode 15 o Superior con SDK IOS 15 o superior.

#### 2.2. Instalación Plugin react-native-bytte-bio-lib-miid

#### 2.2.1 Configuración Token

#### 2.2.1.1 MAC

Una vez instalado NPM (sistema de gestión de paquetes). En la ruta por defecto de instalación se debe encontrar el archivo .npmrc, si no se encuentra se debe crear a nivel de usuario.

Una vez detectado el archivo se debe configurar de la siguiente manera.

Copie el siguiente código a su .npmrc.

```
registry=https://byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/rn-b-miid/npm/registry/ 
                        
always-auth=true

; begin auth token
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/rn-b-miid/npm/registry/:username=BytteTFS
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/rn-b-miid/npm/registry/:_password=[BASE64_ENCODED_PERSONAL_ACCESS_TOKEN]
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/rn-b-miid/npm/registry/:email=npm requires email to be set but doesn't use the value
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/rn-b-miid/npm/:username=BytteTFS
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/rn-b-miid/npm/:_password=[BASE64_ENCODED_PERSONAL_ACCESS_TOKEN]
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/rn-b-miid/npm/:email=npm requires email to be set but doesn't use the value
; end auth token
```

En el espacio (BASE64_ENCODED_PERSONAL_ACCESS_TOKEN) se debe ingresar el password enviado por Bytte s.a.s.

#### 2.2.1.2 WINDOWS

Una vez instalado NPM (sistema de gestión de paquetes). Se debe ejecutar el siguiente comando en la terminal.

` vsts-npm-auth -config .npmrc`

este comando creará un archivo .npmrc en la ruta por defecto C:\Users\USER\\.npmrc

Una vez detectado el archivo se debe configurar de la siguiente manera.

```
registry=https://byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/rn-b-miid/npm/registry/ 
                        
always-auth=true
```

# rn-b-miid

#### 2.2.2 Instalación

`$ npm install rn-b-miid --save`

Una vez instalado el plugin, se debe realizar la consulta a la aplicación para verificar que este quedó correctamente instalado.

### Configuración Plataformas

#### 2.3. Configuración nativo iOS (XCode)

## iOS

###### Adicionar la implementación bytte a su proyecto NPM

para esta implementación se puede generar desde npm integrando de la siguiente forma:

` npm install rn-b-miid --save`

Luego de instalar las dependencias npm se ingresa a la carpeta **_ios_** y se ejecuta el comando `pod install`

    $ cd ios
    $ pod install

![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/ReactNative/podinstall.png)

###### Licencia captura dactilar y captura facial

Bytte proporciona archivos de licencia para captura dactilar y facial. Estos archivos deben ser guardado en la raiz del proyecto IOS y embebido como recurso en la aplicación nativa tal como lo muestra la siguiente imagen.

![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/ReactNative/Licencias.png)

El nombre del archivo se envía por parámetro **_(namePath)_** en la captura dactilar y facial.

###### Permisos

Los permisos en runtime deben ser solicitados por la app para el uso de bytte es necesario el siguiente:
configurar en el archivo Info.plist para el uso de la **_Camara_**

`Privacy - Camera Usage Description`

#### 2.4. Configuración nativo Android

## Android

- **Se debe verificar la calidad de la cámara, es recomendable utilizar dispositivos con cámara que tengan la característica de “Auto Foco” habilitada**
- **Se recomiendan cámaras con resolución mayores o iguales a 5 Mega Pixeles para un óptimo rendimiento**
- **El SDK no funciona sobre dispositivos virtuales, únicamente sobre dispositivos físicos IPhone y**
- **Sistemas soportados Android 23 o superior arquitecturas arm x86,64 bits**

### Para compilación de aplicación en plataforma Android, se requiere:

- **Java JDK Versión 11**
- **Android SDK**
- **Funciona con Android 23 o superior**
- **Para el uso de la licencia identy es necesario registrar el app Pakage ID**
- **Desarrollador SHA1 Key. Cada desarrollador necesita un par de claves para firmar aplicaciones: una para debug y otra para el modo de release. Estos HASH también deben estar asociados con la licencia. y deben ser compartidos para la generacion de las mismas**

## licencia Android para el uso de huellas

- **crear una carpeta en el direccorio android llamada assets en el caso de react esta android/app/src/main**
  Dentro de esa carpeta depositamos el archivo de licencia que se generara para la implementación en debug y otra para reléase

## Los permisos en runtime deben ser solicitados por la app

para el uso de bytte es necesario los siguientes:
uso de **_Camara y almacenamiento_**
`<uses-permission android:name="android.permission.CAMERA" />`
`<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>`

###### Adicionar la implementación bytte a su proyecto

Luego vamos a android en la app, para la configuración en el archivo `build.gradle` del proyecto

`android/build.gradle`:

##### en la etiqueta

```
allprojects {
 repositories {
       maven {
         url 'https://byttetfs.pkgs.visualstudio.com/BytteSDKLibrarys-Android/_packaging/SdkBytteV2/maven/v1'
         name 'SdkBytteV2'
     credentials {
         username ""
         password ""
     }
 }
 }
}

```

Solicitar a **Bytte lo siguiente:** ingresarlo dentro de los ""

- **username**
- **password**

Tener en cuenta que debe estar habilitado multidex para android revisar la documentación para generarlo en react-native
' multiDexEnabled true'
Las librerías bytte soportan las arquitecturas a 32 y 64 bits necesarias para Android
ndk{
abiFilters "armeabi-v7a", 'arm64-v8a'
}

### licencias de Biometria

Las licencias de biometría deben ir en la carpeta de la plataforma Android: assets como indica a continuacion adicionalmente bytte le suministrara los archivos que estaran registrados por cada name package

`android/app/src/main/assets`

```
file.lic
```

## Configuración colores de la pantalla de huellas

> boxes -> Color de borde del cuadro de la cámara.
> boxes_transparent -> Color del recuadro entre el header y el footer.
> colorPrimary -> Color del footer y el header.

    ```  xml
    <color name="boxes">#FF5722</color>
    <color name="boxes_transparent">#FF5722</color>
    <color name="colorPrimary">#FFC107</color>
    <color name="colorPrimaryDark">#FF5722</color>

    ```

## Configuración en español para mensajes huellas

Vamos a la carpeta res/values/strings.xml

```xml
 <string name="id_searching_left">Buscando dedos izquierdos…</string>
    <string name="id_searching_right">Buscando dedos derechos…</string>




        <string name="id_authentication_retake">INSEGURO VOLVER A TOMAR</string>
        <string name="id_authentication_successful">Autenticado</string>
        <string name="id_authentication_unsuccessful">Autenticación incorrecta</string>
        <string name="id_capture_completed">Captura completada</string>
        <string name="id_captured">Capturado</string>
        <string name="id_capturing">Capturando..</string>
        <string name="id_close">Cerrar</string>
        <string name="id_confirm_exit">Confirmar salida</string>
        <string name="id_continue">SEGUIR</string>
        <string name="id_dshow_again">No me lo muestres de nuevo</string>
        <string name="id_enrollment_completed">INSCRIPCIÓN FINALIZADA</string>
        <string name="id_exit_text">¿Quieres salir de la captura?</string>
        <string name="id_good_quality">Todo de buena calidad</string>
        <string name="id_hand_closer">Por favor acerca la mano</string>
        <string name="id_hand_further_away">Mueva la mano más lejos</string>
        <string name="id_hand_further_away_ff">Mueva la mano más lejos 4F</string>
        <string name="id_hold_0">Por favor sostenga</string>
        <string name="id_hold_1">Por favor sostenga 1</string>
        <string name="id_hold_2">Por favor sostenga 2</string>
        <string name="id_hold_3">Por favor sostenga 3</string>
        <string name="id_hold_4">Por favor sostenga 4</string>
        <string name="id_hold_5">Por favor sostenga 5</string>
        <string name="id_hold_6">Por favor sostenga 6</string>
        <string name="id_hold_still">Asegúrate de mantenerte quieto hasta la captura automática. </string>
        <string name="id_identy_template_format">Formato de plantilla IDENTY</string>
        <string name="id_image_cd_todo">QUE HACER</string>
        <string name="id_in_front_camera">2.Coloque los dedos frente a la cámara</string>
        <string name="id_index">INDICE    </string>
        <string name="id_index_finger">dedo índice</string>
        <string name="id_inside_guide">Por favor, esté dentro de la guía.</string>
        <string name="id_keep_fingers">1.Extiende y mantén los dedos juntos</string>
        <string name="id_keep_fingers_together">mantener los dedos juntos</string>
        <string name="id_left_thumb"> PULGAR IZQUIERDO</string>
        <string name="id_little">PEQUEÑO   </string>
        <string name="id_little_finger">dedo índice</string>
        <string name="id_location_error_off">Algo es extraño APAGADO</string>
        <string name="id_middle">MEDIO   </string>
        <string name="id_middle_finger">dedo medio</string>
        <string name="id_next">SIGUIENTE</string>
        <string name="id_next_detection">Pasar a la siguiente mano ?</string>
        <string name="id_next_hand_confirm">Siguiente detección Confirmar</string>
        <string name="id_no">NO</string>
        <string name="id_no_match">SIN COINCIDENCIA</string>
        <string name="id_not_good_quality">no tiene buena calidad.</string>
        <string name="id_ok">OK</string>
        <string name="id_pic_qc_title">FALLO EN LA CALIDAD DE LA IMAGEN</string>
        <string name="id_processing">Procesando …</string>
        <string name="id_qc_retake">Necesitamos retomar la foto</string>
        <string name="id_quality_failed">Falló la calidad de la imagen</string>
        <string name="id_retake_additional_tip">Consejos adicionales</string>
        <string name="id_retake_match">Se alcanzó el número máximo de intentos, inténtelo de nuevo</string>
        <string name="id_retake_q">volver a tomar?</string>
        <string name="id_retake_string">volver a tomar</string>
        <string name="id_retake_tip_1">Tus dedos miran hacia la cámara</string>
        <string name="id_retake_tip_2">Tus dedos están dentro de la caja azul</string>
        <string name="id_retake_tip_3">Utilice iluminación interior normal</string>
        <string name="id_retry">Procesar de nuevo</string>
        <string name="id_right_thumb">PULGAR DERECHO</string>
        <string name="id_ring">ANILLO     </string>
        <string name="id_ring_finger">dedo anular</string>
        <string name="id_select_hand">por favor seleccione al menos una mano</string>
        <string name="id_spoof">PARODIA</string>
        <string name="id_spoof_additional_tip">Consejos adicionales</string>
        <string name="id_spoof_question">¿Estás usando manos reales para autenticarte?</string>
        <string name="id_spoof_tip_2">Utilice iluminación interior normal  </string>
        <string name="id_spoof_tip_3">Intente intentar una ubicación / fondo diferente</string>
        <string name="id_spoof_title">Spoof detectado</string>
        <string name="id_stable">Por favor sea estable</string>
        <string name="id_stay_still_blue">3.Quédate quieto dentro del rectángulo azul</string>
        <string name="id_success">Éxito</string>
        <string name="id_success_match"> MATCH EXITOSO</string>
        <string name="id_thumb">PULGAR    </string>
        <string name="id_thumb_finger">dedo índice</string>
        <string name="id_try_again">Intentar otra vez</string>
        <string name="id_try_again_in">Inténtelo de nuevo en : </string>
        <string name="id_wait_auto">4.Espere la captura automática (hasta que se apague el flash)</string>
        <string name="id_wsq_compression">Relación de compresión WSQ</string>
        <string name="id_yes">SI</string>
        <string name="id_zero">0</string>
```

## Configuración colores de la pantalla de facial

### Colores para personalizar la vista

Estos colores se toman de la configuración de la app

> id_box -> Color del mensaje
> id_face_boxes -> Color del borde
> colorPrimary -> Color del footer y el header

```

    <color name="id_box">#FF5722</color>
    <color name="id_face_boxes">#8BC34A</color>
```

### 2. USO

```javascript
import { NativeModules } from "react-native";

const { RnBytteBioLibMiid } = NativeModules;

export default RnBytteBioLibMiiD;
```

## Metodos react-native-bytte-bio-lib-miid

- Una vez instalado el plugin, la aplicación destino heredará el Javascript expuesto por este, el cual expone las siguientes operaciones:

#### Captura de la parte frontal del documento

```javascript
import { NativeModules } from "react-native";

const btnFront = () => {
  captureType = "FRONT";
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
    }
  );
};
```

| Parámetro       | Tipo       | Descripción                                         |
| --------------- | ---------- | --------------------------------------------------- |
| **url**         | `string`   | Dirección del servidor.                             |
| **ClientID**    | `string`   | Identificador único del cliente.                    |
| **ClientKey**   | `string`   | Clave secreta para la autenticación.                |
| **sesionId**    | `string`   | Llave que encripta la imagen.                       |
| **country**     | `string`   | Código del país: (`CO` Hologramas, `COV2` Digital). |
| **captureType** | `string`   | Tipo de captura (`FRONT` para frontal).             |
| **Callback**    | `function` | Función para manejar la respuesta en JSON.          |

#### Captura de la parte trasera del documento

```javascript
import { NativeModules } from "react-native";

const btnBackDoc = () => {
  captureType = "BACK";
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
    }
  );
};
```

| Parámetro       | Tipo       | Descripción                                         |
| --------------- | ---------- | --------------------------------------------------- |
| **url**         | `string`   | Dirección del servidor.                             |
| **ClientID**    | `string`   | Identificador único del cliente.                    |
| **ClientKey**   | `string`   | Clave secreta para la autenticación.                |
| **sesionId**    | `string`   | Llave que encripta la imagen.                       |
| **country**     | `string`   | Código del país: (`CO` Hologramas, `COV2` Digital). |
| **captureType** | `string`   | Tipo de captura (`BACK` para trasero).              |
| **Callback**    | `function` | Función para manejar la respuesta en JSON.          |

#### Captura de huellas dactilares

```javascript
import { NativeModules } from "react-native";

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
    }
  );
};
```

| Parámetro        | Tipo       | Descripción                                                        |
| ---------------- | ---------- | ------------------------------------------------------------------ |
| **url**          | `string`   | Dirección del servidor.                                            |
| **licFinger**    | `string`   | Licencia para la captura de huellas.                               |
| **ClientID**     | `string`   | Identificador único del cliente.                                   |
| **ClientKey**    | `string`   | Clave secreta para la autenticación.                               |
| **sesionId**     | `string`   | Llave que encripta la imagen.                                      |
| **fingerNumber** | `number`   | Número del dedo a capturar (`2` para derecho, `7` para izquierdo). |
| **Callback**     | `function` | Función para manejar la respuesta en JSON.                         |

#### Captura facial

```javascript
import { NativeModules } from "react-native";

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
    }
  );
};
```

| Parámetro     | Tipo       | Descripción                                |
| ------------- | ---------- | ------------------------------------------ |
| **url**       | `string`   | Dirección del servidor.                    |
| **licFace**   | `string`   | Licencia para la captura facial.           |
| **ClientID**  | `string`   | Identificador único del cliente.           |
| **ClientKey** | `string`   | Clave secreta para la autenticación.       |
| **sesionId**  | `string`   | Llave que encripta la imagen.              |
| **Callback**  | `function` | Función para manejar la respuesta en JSON. |

# Código de errores

```
<string name="OK">0000</string><string name="TimeOut">0001</string>
<string name="Cancelado_a_proposito">0002</string>
<string name="Error_de_Licencia_MicroBlink">0111</string>
<string name="Error_No_tiene_permisos_camara">0112</string>
<string name="Error_de_Licencia_Biometria">0113</string>
<string name="Error_Captura_de_huellas">0114</string>


<string name="timeOut">TimeOut</string>
<string name="Canceladoproposito">Cancelado a proposito</string>
<string name="ErrorLicencia_MicroBlink">Error de Licencia MicroBlink"</string>
<string name="ErrorLicencia_Biometria">Error de Licencia biometría"</string>
<string name="Error_Capturahuellas">Error en la captura de las huellas"</string>
<string name="ErrorLicenciaBiometria">Error licencia de  biometría"</string>

------------------------------
Control de cambios
------------------------------
```

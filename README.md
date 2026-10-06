# Generador de códigos QR

Proyecto web para generar un código QR que contiene los datos introducidos por el usuario en el formulario.

## Funcionamiento

El usuario introduce:

- Nombre
- Apellidos
- DNI

Al pulsar el botón **Generar el código QR**, la aplicación:

1. Recoge los datos introducidos en el formulario.
2. Los convierte en un texto.
3. Genera un código QR con ese texto.
4. Muestra el código QR en la página.
5. El código QR puede escanearse desde un teléfono movil para obtener los datos que se ha introducido en el formulario y  recibirlos como el texto.

## Tecnologías utilizadas

- HTML5
- CSS3
- JavaScript
- Git y GitHub

## Librería utilizada

Para generar el código QR se utiliza **QRCode-JS**, de Rabbit Company.

La librería se encuentra integrada localmente en:

``` text
lib/qrcode.js
```

Se utiliza mediante un módulo JavaScript:

``` javascript
import { QRCode } from "../lib/qrcode.js";
```

La generación del codigo QR se realiza con la clase QRCode y su método encode:

``` javascript
const qr = QRCode.encode(datos);
```

Después se convierte a SVG:

``` javascript
const svg = qr.toSVG({
    scale:8,
    title: "Código QR con datos personales"
});
```

La documentación de la librería indica que implementa ISO/IEC 18004 y permite generar códigos QR en formato SVG.

Repositorio oficial:

https://github.com/Rabbit-Company/QRCode-JS

## Accesibilidad

El proyecto tiene en cuenta criterios de accesibilidad siguiendo las recomendaciones de **WCAG 2.2**.

Los campos del formulario están asociados a sus etiquetas `label` y `for`.
Además utilizan el atributo required y aria-required="true" (que se suele acompañar con el asterisco).

El código QR siendo un contenido visual, esta complementado con una alternativa textual accesible para las personas que utilizan lectores de pantalla.
Esta información no se muestra visualmente, para no duplicar el contenido de QR, pero esta disponible para las tecnologías de asistencia.

Además, el SVG generado incluye un título accesible.

## Estructura del proyecto

``` text
generador-qr/
│
├── css/
│   └── estilos.css
│
├── js/
│   └── script.js
│
├── lib/
│   └── qrcode.js
│
├── index.html
│
└── README.md
```

## Ejecución

No es necesario instalar dependencias mediante npm.

El proyecto incorpora localmente el archivo `qrcode.js` de la librería QRCode-JS, 
por lo que no es necesario hacer ninguna instalación externa.

Para ejecutar el proyecto se puede abrir `index.html` con un servidor local, 
por ejemplo utilizando la extensión **Live Server** de Visual Studio Code.

## Estandar QR

El proyecto utiliza una librería que declara implementar **ISO/IEC 18004** para la generación de código QR.

La accesibilidad de la página web se aborda de forma independiente según los criterios de **WCAG 2.2**.



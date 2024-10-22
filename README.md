importar { Terminal } desde "@es-js/terminal"
importar { obtenerJson } desde "https://desarrollo-aplicaciones.vercel.app/2024/code/obtener-json.js"
importar { validarSecreto } desde "https://desarrollo-aplicaciones.vercel.app/2024/code/validar-secreto.js"

asincrono funcion inicio() {

  Terminal.escribir("Hola! Ingresa la palabra secreta:")

  var secreto = esperar Terminal.leer()

  var dni = "38678077" 
  var palabrasecreta= "castillo-slawycz-077"

  si (esperar validarSecreto(dni, secreto)) {
    esperar mostrarCotizacion()
  } sino {
    Terminal.escribir("Palabra secreta inválida")
  }

  Terminal.escribir("Presiona ENTER para volver a ingresar")

  esperar Terminal.leerEnter()

  Terminal.limpiar()

  inicio()
}

asincrono funcion mostrarCotizacion() {

const dolarBlue = esperar obtenerJson('https://dolarapi.com/v1/dolares/blue')
Terminal.escribir( "cotizacion de "  + dolarBlue.moneda)  

Terminal.escribir( "el precio  de venta del dolar blue es $ " + dolarBlue.venta)  

Terminal.escribir( "el precio de la compra del dolar  blue es $ " + dolarBlue.compra)  

Terminal.escribir( "el precio promedio es $ " +(dolarBlue.venta/2 + dolarBlue.compra /2))

Terminal.escribir(  "segun fecha de cotización " + dolarBlue.fechaActualizacion)
}

inicio()


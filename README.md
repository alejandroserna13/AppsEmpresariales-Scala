# AppsEmpresariales-Scala
Clase de 03 de Marzo donde explicaron Scala 

GUIA CRUD EN SCALA

Requerimientos: 

Tener instalado el JDK 8 o superior.
Tener instalado sbt.
Tener instalado MySQL.
Y algun editor de código como Sublime o Scala IDE.

Nota: Cuando se escriben pequeños programas que consisten en uno, dos o tres archivos fuente, entonces es bastante fácil compilar dichos archivos fuente escribiendo scalac MyProgram.scala en la línea de comando. Pero cuando se comienza a trabajar en un proyecto más grande con docenas o incluso cientos de archivos fuente, resulta demasiado tedioso compilar todos esos archivos fuente manualmente. Por esta razón, se empezara a considerar el uso de una herramienta de compilación para administrar la compilación de todos esos archivos fuente.

Aquí es donde entra Sbt (Simple build tool), el cual es una herramienta para la construcción de proyectos en Scala y Java parecida a Maven o Ant. Su funcionamiento consiste en crear un archivo de proyecto que describe cómo se ve el proyecto (en sbt, este archivo se llamará build.sbt). Ese archivo enumera todos los archivos fuente en los que se basa el proyecto, junto con otra información sobre el mismo. Sbt leerá tal archivo y luego sabrá qué hacer para compilar el proyecto completo, además sbt puede administrar automáticamente las dependencias del proyecto, esto significa que si se necesita usar algunas bibliotecas escritas por otros, sbt puede descargar automáticamente las versiones correctas de esas bibliotecas e incluirlas en el proyecto.

Creación del proyecto (terminal):

Verificamos que sbt sea un comando conocido en la terminal o consola, para ello ejecute sbt.

Nota: Si estamos en un sistema operativo Windows se deberá configurar también el path en donde se haya instalado el sbt. Para hacer ello, se hace:
Clic derecho sobre Mi PC o Este equipo.
Seleccionar Propiedades.
Configuración Avanzada del Sistema.
Pasamos a la pestaña Opciones avanzadas y hacemos clic en Variables de entorno.
En la nueva ventana agregaremos como variable de sistema, lo siguiente:
SBT_HOME
La ruta donde se instaló sbt (Ej: C:\Program Files (x86)\sbt).
Y agregamos en la variable de sistema path, el siguiente fragmento:
%SBT_HOME%\bin

Finalmente, para corroborar que todo haya quedado bien simplemente en la consola escribimos sbt -si es la primera vez se actualizarán algunos paquetes- y deberemos tener algo como sbt:usuario>, lo cual implica que ya está instalado y configurado el sbt.



[Opcional] Si lo desea puede escribir sbtVersion para saber cual es la versión vigente del sbt.




Ahora para crear el proyecto, volvemos a la consola del sistema operativo y nos desplazamos a la carpeta donde queremos crear el proyecto (por ejemplo: \Documents\ProyectosScala) y escribimos el comando sbt new playframework/play-scala-seed.g8. Esta instrucción lo que hace es que crea un nuevo proyecto bajo una plantilla de Play Framework, el cual es uno de los mejores frameworks para desarrollo web de Scala.



Tras uno o dos minutos, sbt nos solicitará el nombre y el dominio que le vamos a dar al proyecto. En nuestro caso particular, llamaremos al proyecto PetStore y el dominio será: co.edu.udea. Para los demás campos, se pueden ignorar/omitir presionando Enter.




Una vez creado el proyecto, desde la misma consola nos movemos dentro de la carpeta del proyecto y finalmente ejecutamos el comando sbt run, esto hará que se ejecute el servidor Netty (con el cual viene configurado Play) para que podamos desplegar nuestro aplicativo web y así ver los cambios o trabajos que hagamos sobre el proyecto en el navegador.



Como tal esto puede tomar algunos minutos, pero una vez el servidor se ponga en marcha deberíamos obtener algo como:




NOTA: No se debe cerrar esta terminal para que el servidor no deje de ejecutarse.
Creación de la base de datos:

Antes de continuar con el proyecto, se procederá a crear una sencilla base de datos en el MySQL.

Script SQL:
CREATE TABLE `PetsData`.`Pet` ( 
`id` INT NOT NULL,
`name`VARCHAR(30) NOT NULL,
`kind` VARCHAR(10) NOT NULL, 
`gender` CHAR(1)NOT NULL,
`location` VARCHAR(5) NOT NULL,
`state` CHAR(1) NOT NULL ,
PRIMARY KEY (`id`)) ENGINE = InnoDB;
GUIA CRUD EN SCALA

Requerimientos: 

Tener instalado el JDK 8 o superior.
Tener instalado sbt.
Tener instalado MySQL.
Y algun editor de código como Sublime o Scala IDE.

Nota: Cuando se escriben pequeños programas que consisten en uno, dos o tres archivos fuente, entonces es bastante fácil compilar dichos archivos fuente escribiendo scalac MyProgram.scala en la línea de comando. Pero cuando se comienza a trabajar en un proyecto más grande con docenas o incluso cientos de archivos fuente, resulta demasiado tedioso compilar todos esos archivos fuente manualmente. Por esta razón, se empezara a considerar el uso de una herramienta de compilación para administrar la compilación de todos esos archivos fuente.

Aquí es donde entra Sbt (Simple build tool), el cual es una herramienta para la construcción de proyectos en Scala y Java parecida a Maven o Ant. Su funcionamiento consiste en crear un archivo de proyecto que describe cómo se ve el proyecto (en sbt, este archivo se llamará build.sbt). Ese archivo enumera todos los archivos fuente en los que se basa el proyecto, junto con otra información sobre el mismo. Sbt leerá tal archivo y luego sabrá qué hacer para compilar el proyecto completo, además sbt puede administrar automáticamente las dependencias del proyecto, esto significa que si se necesita usar algunas bibliotecas escritas por otros, sbt puede descargar automáticamente las versiones correctas de esas bibliotecas e incluirlas en el proyecto.

Creación del proyecto (terminal):

Verificamos que sbt sea un comando conocido en la terminal o consola, para ello ejecute sbt.

Nota: Si estamos en un sistema operativo Windows se deberá configurar también el path en donde se haya instalado el sbt. Para hacer ello, se hace:
Clic derecho sobre Mi PC o Este equipo.
Seleccionar Propiedades.
Configuración Avanzada del Sistema.
Pasamos a la pestaña Opciones avanzadas y hacemos clic en Variables de entorno.
En la nueva ventana agregaremos como variable de sistema, lo siguiente:
SBT_HOME
La ruta donde se instaló sbt (Ej: C:\Program Files (x86)\sbt).
Y agregamos en la variable de sistema path, el siguiente fragmento:
%SBT_HOME%\bin

Finalmente, para corroborar que todo haya quedado bien simplemente en la consola escribimos sbt -si es la primera vez se actualizarán algunos paquetes- y deberemos tener algo como sbt:usuario>, lo cual implica que ya está instalado y configurado el sbt.



[Opcional] Si lo desea puede escribir sbtVersion para saber cual es la versión vigente del sbt.




Ahora para crear el proyecto, volvemos a la consola del sistema operativo y nos desplazamos a la carpeta donde queremos crear el proyecto (por ejemplo: \Documents\ProyectosScala) y escribimos el comando sbt new playframework/play-scala-seed.g8. Esta instrucción lo que hace es que crea un nuevo proyecto bajo una plantilla de Play Framework, el cual es uno de los mejores frameworks para desarrollo web de Scala.



Tras uno o dos minutos, sbt nos solicitará el nombre y el dominio que le vamos a dar al proyecto. En nuestro caso particular, llamaremos al proyecto PetStore y el dominio será: co.edu.udea. Para los demás campos, se pueden ignorar/omitir presionando Enter.




Una vez creado el proyecto, desde la misma consola nos movemos dentro de la carpeta del proyecto y finalmente ejecutamos el comando sbt run, esto hará que se ejecute el servidor Netty (con el cual viene configurado Play) para que podamos desplegar nuestro aplicativo web y así ver los cambios o trabajos que hagamos sobre el proyecto en el navegador.



Como tal esto puede tomar algunos minutos, pero una vez el servidor se ponga en marcha deberíamos obtener algo como:




NOTA: No se debe cerrar esta terminal para que el servidor no deje de ejecutarse.
Creación de la base de datos:

Antes de continuar con el proyecto, se procederá a crear una sencilla base de datos en el MySQL.

Script SQL:
CREATE TABLE `PetsData`.`Pet` ( 
`id` INT NOT NULL,
`name`VARCHAR(30) NOT NULL,
`kind` VARCHAR(10) NOT NULL, 
`gender` CHAR(1)NOT NULL,
`location` VARCHAR(5) NOT NULL,
`state` CHAR(1) NOT NULL ,
PRIMARY KEY (`id`)) ENGINE = InnoDB;



Nota: El usuario y contraseña de MySQL en el LIS es root para ambos campos.

Ejemplo CRUD con listas:

Antes de realizar las operaciones con la base de datos de MySQL, vamos a realizar un pequeño ejemplo de manejo de datos en colecciones -específicamente listas-. Para empezar, dentro de la estructura del proyecto vamos a buscar la carpeta app, dentro de ella crearemos una carpeta o paquete adicional llamado models.



En esta carpeta models es donde se crearan los POJOs u objetos que se mapearan a la base de datos pero que aquí también nos van a servir. En particular y como solo manejaremos una tabla dentro de la base de datos entonces solo crearemos el archivo Pet.scala.

 

El contenido de dicho POJO se puede ver a continuación y como tal importamos algunos paquetes para añadir funcionalidades básicas y para la conversión de los objetos a JSON y viceversa. El constructor básicamente se define en los parámetros de la clase y los métodos para conversión se definen en un objeto del mismo nombre del POJO.

package models

// Importes necesarios para hacer el modelo Pet
import com.sun.org.apache.xpath.internal.operations.Or
import play.api.libs.json.{JsPath, Json, Reads}
import play.api.libs.functional.syntax._

// Se crea la clase Pet, en la cual los parámetros deben coincidir con los campos de la tabla Pet de la base de datos
case class Pet(id: Int, name: String, kind: String, gender: String, location: String, state: String)

// También se crea un objeto Pet con el fin de implementar los métodos para escribir Pet como si fueran Jsons
object Pet {
  implicit val petWrite = Json.writes[Pet]
  implicit val petRead = Json.reads[Pet]
}

Ya con el modelo pasamos al controlador, el cual es el encargado de manejar toda la lógica del proyecto. Particularmente, ya existe uno desde la creación del mismo proyecto llamado HomeController.scala.

 


En este inicialmente vamos a importar nuestro POJO y la librería para manejo de los Json. Después se creará una lista con datos de prueba e implementaremos el primer método para recuperar todos los datos de la lista y retornarlos/mostrarlos en la interfaz.

// Importes necesarios para que nuestra clase funcione
import play.api.libs.json._
import models.Pet


// Se crea una lista con algunos elementos de prueba
var mascotas = List[Pet](
  Pet(1, "Neron", "Bulldog", "M", "Calle 48 No.48-12", "P"),
  Pet(2, "Bruno", "Beagle", "H", "Carrera 4 No.65-75", "E")
)

// Metodo para recuperar todos los elementos de la lista mascotas
def getMascotas = Action {
  val jsonAux = Json.toJson(mascotas) // Simplemente se toma la lista, se Jsifica
  Ok(jsonAux) // Y se retorna en la lista Jsificada
}

Antes de intentar ver si este metodo si funciona, vamos a agregar (o registrar) el mismo en las rutas aceptadas del aplicativo. Esto se hace por medio del archivo routes que está en la carpeta conf del proyecto. Si no se registra el método le será imposible al servidor de aplicaciones saber a quién acudir para responder a la solicitud del usuario.




En este archivo de rutas, se deben definir qué rutas van a ser responsables de que métodos. Para ello se debe indicar qué método HTTP bajo qué ruta relativa va a responder al método del controlador. Por ejemplo, nuestro método para conseguir todas las mascotas va a responder al método GET de la ruta http://localhost:9000/mascotas.

# Rutas propias del aplicativo PetStore
GET  /mascotas  controllers.HomeController.getMascotas

El resultado se puede apreciar fácilmente escribiendo la ruta en el navegador.





O también se puede hacer con PostMan.



Continuando con lo que hemos hecho, agregamos la ruta de los métodos que hacen el resto de operaciones en la rutas del proyecto.

# Rutas propias del aplicativo PetStore
GET  /mascotas  controllers.HomeController.getMascotas
POST  /insertar  controllers.HomeController.insertarMascota
PUT  /actualizar  controllers.HomeController.actualizarMascota
DELETE  /eliminar/:id  controllers.HomeController.removerMascota(id: Int)

Y definimos los otros métodos en el controlador que tenemos.

// Método para eliminar la mascota indicada de la lista 
def removerMascota(id: Int) = Action {
  // Simplemente se usa el método find de la colección de mascotas y con el match
  // se busca en cual caso cae el resultado. Si encontró ALGO entonces que borre la mascota de la lista y retorna un mensaje de ello
  // O sino (cualquier otro caso) entonces se retorna un mensaje de que no se encontró la mascota a borrar.
  mascotas.find(_.id == id) match {
    case Some(m) => mascotas = mascotas.filter(x => x.id != id)
                    Ok("La mascota ha sido eliminada exitosamente!")
    case _ => Ok("La mascota indicada no existe o ya fue eliminada!")
  }    
}

// Metodo para actualizar la información de la mascota indicada en la lista
def actualizarMascota = Action { implicit request =>
  val cuerpoJson = request.body.asJson.get // En primer lugar se recupera el cuerpo del mensaje el cual debe contener el json con la información a actualizar

  // Luego, se valida que lo que obtuve si es un json que corresponda con un objeto tipo Pet
  cuerpoJson.validate[Pet] match {
    // En caso de éxito entonces
    case success: JsSuccess[Pet] =>

      // Creo un nuevo objeto mascota a partir de la información que me llego
      var nuevaMascota = Pet(success.get.id, success.get.name, success.get.kind, success.get.gender, success.get.location, success.get.state)

      // Ahora, se busca que la mascota a actualizar si exista, por lo que...
      mascotas.find(_.id == success.get.id) match {
        // Si de verdad existe entonces intercambio la mascota que acabo de crear con la mascota que tiene el mismo id
        case Some(m) => mascotas = mascotas.map(aux => if (aux.id == success.get.id) nuevaMascota else aux)
                        Ok("La mascota ha sido actualizada exitosamente!")
        // Sino entonces retorno un mensaje al respecto
        case _ => Ok("No se puede actualizar una mascota que no existe!")
      }
    // En caso de error entonces devuelvo un mensajito
    case e:JsError => BadRequest("No se pudo actualizar porque hay malos parametros!!")
  }
}

// Método para agregar una nueva mascota en la lista
def insertarMascota = Action { implicit request =>
  val cuerpoJson = request.body.asJson.get // En primer lugar se recupera el cuerpo del mensaje el cual debe contener el json con la información de la mascota a ingresar a la lista

  // Luego, se valida que lo que obtuve si es un json que corresponda con un objeto tipo Pet
  cuerpoJson.validate[Pet] match {
    // En caso de exito entonces
    case success: JsSuccess[Pet] =>

      // Creó un nuevo objeto mascota a partir de la información que me llego
      var nuevaMascota = Pet(success.get.id, success.get.name, success.get.kind, success.get.gender, success.get.location, success.get.state)

      // Ahora, se busca que la mascota a insertar no repita id, por lo que...
      mascotas.find(_.id == success.get.id) match {
        // Si ya hay una mascota con tal id entonces se muestra un mensaje al respecto
        case Some(m) => Ok("No se puede insertar la mascota porque la clave indicada ya existe")
        // sino entonces se inserta la mascota y se muestra un mensaje de exito
        case _ =>  mascotas = mascotas :+ nuevaMascota
                   Ok("La mascota ha sido ingresada exitosamente!")
      }

    // En caso de error entonces devuelvo un mensajito
    case e:JsError => BadRequest("No se pudo actualizar porque hay malos parametros!!")
  }
}

Los resultados de los otros métodos se puede apreciar con mayor facilidad en el postman. Por ejemplo, para el eliminar solo debemos indicar el método HTTP de DELETE, la dirección con la cual se eliminan datos y la clave del elemento que se desea borrar.



En el caso de la actualización es muy similar pero se usa el método PUT de HTTP, además en el cuerpo del mensaje se debe inscribir el dato a ingresar con formato JSON y explícitamente se debe definir que el cuerpo del mensaje es JSON(application/json) de lo contrario marcará error.


Para terminar, el insertar es casi exactamente igual al actualizar pero el método HTTP cambia de PUT a POST.





Ejemplo CRUD con BD MySQL:

Ahora, con el fin de realizar las operaciones básicas de manejo de base de datos desde scala, en primer lugar se debe indicar en el archivo build.sbt del proyecto que vamos a emplear las librerías JDBC y MySQL respectivamente. Para hacer esto simplemente agregamos las siguientes instrucciones a dicho archivo. Si no se hace esto nos aparecerán muchos problemas.


// Estas son las dependencias necesarias para trabajar con bases de datos MySQL
libraryDependencies += jdbc
libraryDependencies += "mysql" % "mysql-connector-java" % "5.1.41"

Posteriormente, para configurar la conexión con la base de datos nos desplazamos a la carpeta conf del proyecto. Una vez allí, en el archivo application.conf debemos describir en dónde reside la base de datos, el usuario, la contraseña y cualquier otra configuración que indique cómo deseamos conectarnos con la base de datos. En nuestro caso particular, la configuración básica necesaria para conectarse a una base de datos MySQL es la que se aprecia a continuación.


# Archivo de configuración general de nuestro aplicativo web

# Configuracion basica de conexión a la base de datos MySQL
db {
  default.driver=com.mysql.jdbc.Driver
  default.url="jdbc:mysql://localhost/petsdata"
  default.username=root
  default.password=""
}

Ahora, de la misma forma a como se registraron las operaciones CRUD para las listas también se procederá a registrar las operaciones CRUD para la base de datos en el mismo archivo de rutas del proyecto.

# Rutas propias del aplicativo PetStore para la version con MySQL
GET  /mascotasSQL  controllers.HomeController.getMascotasSQL
POST  /insertarSQL  controllers.HomeController.insertarMascotaSQL
PUT  /actualizarSQL  controllers.HomeController.actualizarMascotaSQL
DELETE  /eliminarSQL/:id  controllers.HomeController.removerMascotaSQL(id: Int)

NOTA: El modelo o POJO que utilizamos en la sección anterior también se puede usar aqui sin ningun cambio.

Con todo lo hecho hasta ahora, solo falta implementar los métodos CRUD en sí mismos, para ello volvemos al controlador de proyecto -o sea, HomeController.scala-. Ya allí, deberemos importar el API DB que play framework tiene diseñado para las bases de datos.

NOTA: Es muy importante escribir(agregar) db: Database como parámetro de la clase HomeController, porque de lo contrario se marcaran una serie de errores como que la variable db no es reconocida, o que no se reconocen ciertos métodos de db, etc.

Adicionalmente, crearemos una lista vacía la cual nos ayudará al manejo de algunos resultados obtenidos de la base de datos.

// Importes necesarios para que nuestra clase funcione
import play.api.libs.json._
import models.Pet
import play.api.db._ // Este es especialmente necesario para conectarse con la BD

// Controlador de la página web
// NOTA: No olvidar poner >>> db: Database como parámetro de la clase. OJO!
@Singleton
class HomeController @Inject()(db: Database, cc: ControllerComponents) extends AbstractController(cc) {
 
  // Se crea una lista vacía para manejar los datos que llegan de la BD
  var mascotas = List[Pet]()
  .
  .
  .

Finalmente implementamos los métodos CRUD para:
Búsqueda:

def getMascotasSQL = Action {
  // En primer lugar creamos una variable para realizar la conexion con la BD
  val conexion = db.getConnection()
  
  // A continuación inicializamos (vaciamos) la lista con la que procesaremos los datos que lleguen de la BD
  mascotas = List[Pet]()
    
  try{
  // Ahora creamos una variable en donde formulamos nuestra query SQL de búsqueda y la ejecutamos
    val query = conexion.createStatement
    val resultado = query.executeQuery("SELECT * FROM pet")
 	 
    // Ya con el resultado de la consulta, creamos objetos mascota y los agregamos a la lista de apoyo
    while (resultado.next()) {
      var p = Pet(resultado.getInt("id"), resultado.getString("name"), resultado.getString("kind"), resultado.getString("gender"), resultado.getString("location"), resultado.getString("state"))
      mascotas = mascotas :+ p
    }
  }
  finally{
    // Antes de retornar los resultados, cerramos la conexión a la BD
    conexion.close()
  }
    
  val jsonAux = Json.toJson(mascotas) // Finalmente, se Jsifican los resultados
  Ok(jsonAux) // Y se retorna la lista de mascotas Jsificada
}

Eliminación:

// Método para eliminar la mascota indicada de la BD
def removerMascotaSQL(id: Int) = Action {
  // En primer lugar creamos una variable para realizar la conexión con la BD
  val conexion = db.getConnection()
    
  try{
    // Después creamos una variable en donde formulamos nuestra query SQL de eliminación y la ejecutamos
    val query = conexion.createStatement
    val resultado = query.executeUpdate("DELETE FROM pet WHERE id = " + id)
  }
  finally{
    // Antes de terminar, cerramos la conexión a la BD
    conexion.close()
  }
    
  // Y para terminar indicamos que se realizó la operación correctamente
  Ok("La mascota ha sido eliminada exitosamente!")
}

Actualización:

// Método para actualizar la información de la mascota indicada en la BD
def actualizarMascotaSQL = Action { implicit request =>
  val cuerpoJson = request.body.asJson.get // En primer lugar se recupera el cuerpo del mensaje el cual debe contener el json con la información a actualizar
  
  // Luego, se valida que lo que se obtuve si es un json que corresponda con un objeto tipo Pet
  cuerpoJson.validate[Pet] match {
    // En caso de éxito entonces
    case success: JsSuccess[Pet] =>
      // Se crea un nuevo objeto mascota a partir de la información que me llego
      var nuevaMascota = Pet(success.get.id, success.get.name, success.get.kind, success.get.gender, success.get.location, success.get.state)
	 
      // También, creamos una variable para realizar la conexión con la BD
      val conexion = db.getConnection()
   	 
      try{
        // Después creamos una variable en donde formulamos nuestra query SQL de actualización y la ejecutamos
        val query = conexion.createStatement
        val resultado = query.executeUpdate("UPDATE pet SET name = '"+nuevaMascota.name+"', kind = '"+nuevaMascota.kind+"', gender = '"+nuevaMascota.gender+"', location = '"+nuevaMascota.location+"',state = '"+nuevaMascota.state+"' WHERE id = "+nuevaMascota.id)
      }
      finally{
        // Posterior , cerramos la conexión a la BD
        conexion.close()
      }
   	 
      // Y para terminar indicamos que se realizó la operación correctamente
      Ok("La mascota ha sido actualizada exitosamente!")
   	 
    // En caso de error entonces devuelvo un mensajito
    case e:JsError => BadRequest("No se pudo actualizar porque hay malos parametros!!")
  }
}

Inserción:

// Método para agregar una nueva mascota en la BD
def insertarMascotaSQL = Action { implicit request =>
  val cuerpoJson = request.body.asJson.get // En primer lugar se recupera el cuerpo del mensaje el cual debe contener el json con la información de la mascota a ingresar a la lista

  // Luego, se valida que lo que se obtuvo si es un json que corresponda con un objeto tipo Pet
  cuerpoJson.validate[Pet] match {
    // En caso de éxito entonces
    case success: JsSuccess[Pet] =>
      // Creó un nuevo objeto mascota a partir de la información que me llego
      var nuevaMascota = Pet(success.get.id, success.get.name, success.get.kind, success.get.gender, success.get.location, success.get.state)
   	 
      // También, creamos una variable para realizar la conexión con la BD
      val conexion = db.getConnection()
   	 
      try{
        // Después creamos una variable en donde formulamos nuestra query SQL de inserción y la ejecutamos
        val query = conexion.createStatement
        val resultado = query.executeUpdate("INSERT INTO pet VALUES("+nuevaMascota.id+",'"+nuevaMascota.name+"','"+nuevaMascota.kind+"','"+nuevaMascota.gender+"','"+nuevaMascota.location+"','"+nuevaMascota.state+"')")
     	 
        // Si todo es correcto mostramos un mensaje de éxito
        Ok("La mascota ha sido ingresada exitosamente!")
      }
      catch
      {
        // En caso que pase algo mostramos un mensaje de error
        case e: Exception => Ok("No se puede insertar la mascota porque la clave indicada ya existe o hubo un error.")
      }
      finally{
        // Finalmente, cerramos la conexión a la BD
        conexion.close()
      }
   	 
    // En caso de error entonces devuelvo un mensajito
    case e:JsError => BadRequest("No se pudo actualizar porque hay malos parametros!!")
  }
}

Ya para evaluar si los metodos estan trabajando correctamente volvemos a utilizar postman para ver si todo está funcionando correctamente.




Ejercicio Propuesto:

Realizar una función que me devuelva una mascota por su id














Nota: El usuario y contraseña de MySQL en el LIS es root para ambos campos.

Ejemplo CRUD con listas:

Antes de realizar las operaciones con la base de datos de MySQL, vamos a realizar un pequeño ejemplo de manejo de datos en colecciones -específicamente listas-. Para empezar, dentro de la estructura del proyecto vamos a buscar la carpeta app, dentro de ella crearemos una carpeta o paquete adicional llamado models.



En esta carpeta models es donde se crearan los POJOs u objetos que se mapearan a la base de datos pero que aquí también nos van a servir. En particular y como solo manejaremos una tabla dentro de la base de datos entonces solo crearemos el archivo Pet.scala.

 

El contenido de dicho POJO se puede ver a continuación y como tal importamos algunos paquetes para añadir funcionalidades básicas y para la conversión de los objetos a JSON y viceversa. El constructor básicamente se define en los parámetros de la clase y los métodos para conversión se definen en un objeto del mismo nombre del POJO.

package models

// Importes necesarios para hacer el modelo Pet
import com.sun.org.apache.xpath.internal.operations.Or
import play.api.libs.json.{JsPath, Json, Reads}
import play.api.libs.functional.syntax._

// Se crea la clase Pet, en la cual los parámetros deben coincidir con los campos de la tabla Pet de la base de datos
case class Pet(id: Int, name: String, kind: String, gender: String, location: String, state: String)

// También se crea un objeto Pet con el fin de implementar los métodos para escribir Pet como si fueran Jsons
object Pet {
  implicit val petWrite = Json.writes[Pet]
  implicit val petRead = Json.reads[Pet]
}

Ya con el modelo pasamos al controlador, el cual es el encargado de manejar toda la lógica del proyecto. Particularmente, ya existe uno desde la creación del mismo proyecto llamado HomeController.scala.

 


En este inicialmente vamos a importar nuestro POJO y la librería para manejo de los Json. Después se creará una lista con datos de prueba e implementaremos el primer método para recuperar todos los datos de la lista y retornarlos/mostrarlos en la interfaz.

// Importes necesarios para que nuestra clase funcione
import play.api.libs.json._
import models.Pet


// Se crea una lista con algunos elementos de prueba
var mascotas = List[Pet](
  Pet(1, "Neron", "Bulldog", "M", "Calle 48 No.48-12", "P"),
  Pet(2, "Bruno", "Beagle", "H", "Carrera 4 No.65-75", "E")
)

// Metodo para recuperar todos los elementos de la lista mascotas
def getMascotas = Action {
  val jsonAux = Json.toJson(mascotas) // Simplemente se toma la lista, se Jsifica
  Ok(jsonAux) // Y se retorna en la lista Jsificada
}

Antes de intentar ver si este metodo si funciona, vamos a agregar (o registrar) el mismo en las rutas aceptadas del aplicativo. Esto se hace por medio del archivo routes que está en la carpeta conf del proyecto. Si no se registra el método le será imposible al servidor de aplicaciones saber a quién acudir para responder a la solicitud del usuario.




En este archivo de rutas, se deben definir qué rutas van a ser responsables de que métodos. Para ello se debe indicar qué método HTTP bajo qué ruta relativa va a responder al método del controlador. Por ejemplo, nuestro método para conseguir todas las mascotas va a responder al método GET de la ruta http://localhost:9000/mascotas.

# Rutas propias del aplicativo PetStore
GET  /mascotas  controllers.HomeController.getMascotas

El resultado se puede apreciar fácilmente escribiendo la ruta en el navegador.





O también se puede hacer con PostMan.



Continuando con lo que hemos hecho, agregamos la ruta de los métodos que hacen el resto de operaciones en la rutas del proyecto.

# Rutas propias del aplicativo PetStore
GET  /mascotas  controllers.HomeController.getMascotas
POST  /insertar  controllers.HomeController.insertarMascota
PUT  /actualizar  controllers.HomeController.actualizarMascota
DELETE  /eliminar/:id  controllers.HomeController.removerMascota(id: Int)

Y definimos los otros métodos en el controlador que tenemos.

// Método para eliminar la mascota indicada de la lista 
def removerMascota(id: Int) = Action {
  // Simplemente se usa el método find de la colección de mascotas y con el match
  // se busca en cual caso cae el resultado. Si encontró ALGO entonces que borre la mascota de la lista y retorna un mensaje de ello
  // O sino (cualquier otro caso) entonces se retorna un mensaje de que no se encontró la mascota a borrar.
  mascotas.find(_.id == id) match {
    case Some(m) => mascotas = mascotas.filter(x => x.id != id)
                    Ok("La mascota ha sido eliminada exitosamente!")
    case _ => Ok("La mascota indicada no existe o ya fue eliminada!")
  }    
}

// Metodo para actualizar la información de la mascota indicada en la lista
def actualizarMascota = Action { implicit request =>
  val cuerpoJson = request.body.asJson.get // En primer lugar se recupera el cuerpo del mensaje el cual debe contener el json con la información a actualizar

  // Luego, se valida que lo que obtuve si es un json que corresponda con un objeto tipo Pet
  cuerpoJson.validate[Pet] match {
    // En caso de éxito entonces
    case success: JsSuccess[Pet] =>

      // Creo un nuevo objeto mascota a partir de la información que me llego
      var nuevaMascota = Pet(success.get.id, success.get.name, success.get.kind, success.get.gender, success.get.location, success.get.state)

      // Ahora, se busca que la mascota a actualizar si exista, por lo que...
      mascotas.find(_.id == success.get.id) match {
        // Si de verdad existe entonces intercambio la mascota que acabo de crear con la mascota que tiene el mismo id
        case Some(m) => mascotas = mascotas.map(aux => if (aux.id == success.get.id) nuevaMascota else aux)
                        Ok("La mascota ha sido actualizada exitosamente!")
        // Sino entonces retorno un mensaje al respecto
        case _ => Ok("No se puede actualizar una mascota que no existe!")
      }
    // En caso de error entonces devuelvo un mensajito
    case e:JsError => BadRequest("No se pudo actualizar porque hay malos parametros!!")
  }
}

// Método para agregar una nueva mascota en la lista
def insertarMascota = Action { implicit request =>
  val cuerpoJson = request.body.asJson.get // En primer lugar se recupera el cuerpo del mensaje el cual debe contener el json con la información de la mascota a ingresar a la lista

  // Luego, se valida que lo que obtuve si es un json que corresponda con un objeto tipo Pet
  cuerpoJson.validate[Pet] match {
    // En caso de exito entonces
    case success: JsSuccess[Pet] =>

      // Creó un nuevo objeto mascota a partir de la información que me llego
      var nuevaMascota = Pet(success.get.id, success.get.name, success.get.kind, success.get.gender, success.get.location, success.get.state)

      // Ahora, se busca que la mascota a insertar no repita id, por lo que...
      mascotas.find(_.id == success.get.id) match {
        // Si ya hay una mascota con tal id entonces se muestra un mensaje al respecto
        case Some(m) => Ok("No se puede insertar la mascota porque la clave indicada ya existe")
        // sino entonces se inserta la mascota y se muestra un mensaje de exito
        case _ =>  mascotas = mascotas :+ nuevaMascota
                   Ok("La mascota ha sido ingresada exitosamente!")
      }

    // En caso de error entonces devuelvo un mensajito
    case e:JsError => BadRequest("No se pudo actualizar porque hay malos parametros!!")
  }
}

Los resultados de los otros métodos se puede apreciar con mayor facilidad en el postman. Por ejemplo, para el eliminar solo debemos indicar el método HTTP de DELETE, la dirección con la cual se eliminan datos y la clave del elemento que se desea borrar.



En el caso de la actualización es muy similar pero se usa el método PUT de HTTP, además en el cuerpo del mensaje se debe inscribir el dato a ingresar con formato JSON y explícitamente se debe definir que el cuerpo del mensaje es JSON(application/json) de lo contrario marcará error.


Para terminar, el insertar es casi exactamente igual al actualizar pero el método HTTP cambia de PUT a POST.





Ejemplo CRUD con BD MySQL:

Ahora, con el fin de realizar las operaciones básicas de manejo de base de datos desde scala, en primer lugar se debe indicar en el archivo build.sbt del proyecto que vamos a emplear las librerías JDBC y MySQL respectivamente. Para hacer esto simplemente agregamos las siguientes instrucciones a dicho archivo. Si no se hace esto nos aparecerán muchos problemas.


// Estas son las dependencias necesarias para trabajar con bases de datos MySQL
libraryDependencies += jdbc
libraryDependencies += "mysql" % "mysql-connector-java" % "5.1.41"

Posteriormente, para configurar la conexión con la base de datos nos desplazamos a la carpeta conf del proyecto. Una vez allí, en el archivo application.conf debemos describir en dónde reside la base de datos, el usuario, la contraseña y cualquier otra configuración que indique cómo deseamos conectarnos con la base de datos. En nuestro caso particular, la configuración básica necesaria para conectarse a una base de datos MySQL es la que se aprecia a continuación.


# Archivo de configuración general de nuestro aplicativo web

# Configuracion basica de conexión a la base de datos MySQL
db {
  default.driver=com.mysql.jdbc.Driver
  default.url="jdbc:mysql://localhost/petsdata"
  default.username=root
  default.password=""
}

Ahora, de la misma forma a como se registraron las operaciones CRUD para las listas también se procederá a registrar las operaciones CRUD para la base de datos en el mismo archivo de rutas del proyecto.

# Rutas propias del aplicativo PetStore para la version con MySQL
GET  /mascotasSQL  controllers.HomeController.getMascotasSQL
POST  /insertarSQL  controllers.HomeController.insertarMascotaSQL
PUT  /actualizarSQL  controllers.HomeController.actualizarMascotaSQL
DELETE  /eliminarSQL/:id  controllers.HomeController.removerMascotaSQL(id: Int)

NOTA: El modelo o POJO que utilizamos en la sección anterior también se puede usar aqui sin ningun cambio.

Con todo lo hecho hasta ahora, solo falta implementar los métodos CRUD en sí mismos, para ello volvemos al controlador de proyecto -o sea, HomeController.scala-. Ya allí, deberemos importar el API DB que play framework tiene diseñado para las bases de datos.

NOTA: Es muy importante escribir(agregar) db: Database como parámetro de la clase HomeController, porque de lo contrario se marcaran una serie de errores como que la variable db no es reconocida, o que no se reconocen ciertos métodos de db, etc.

Adicionalmente, crearemos una lista vacía la cual nos ayudará al manejo de algunos resultados obtenidos de la base de datos.

// Importes necesarios para que nuestra clase funcione
import play.api.libs.json._
import models.Pet
import play.api.db._ // Este es especialmente necesario para conectarse con la BD

// Controlador de la página web
// NOTA: No olvidar poner >>> db: Database como parámetro de la clase. OJO!
@Singleton
class HomeController @Inject()(db: Database, cc: ControllerComponents) extends AbstractController(cc) {
 
  // Se crea una lista vacía para manejar los datos que llegan de la BD
  var mascotas = List[Pet]()
  .
  .
  .

Finalmente implementamos los métodos CRUD para:
Búsqueda:

def getMascotasSQL = Action {
  // En primer lugar creamos una variable para realizar la conexion con la BD
  val conexion = db.getConnection()
  
  // A continuación inicializamos (vaciamos) la lista con la que procesaremos los datos que lleguen de la BD
  mascotas = List[Pet]()
    
  try{
  // Ahora creamos una variable en donde formulamos nuestra query SQL de búsqueda y la ejecutamos
    val query = conexion.createStatement
    val resultado = query.executeQuery("SELECT * FROM pet")
 	 
    // Ya con el resultado de la consulta, creamos objetos mascota y los agregamos a la lista de apoyo
    while (resultado.next()) {
      var p = Pet(resultado.getInt("id"), resultado.getString("name"), resultado.getString("kind"), resultado.getString("gender"), resultado.getString("location"), resultado.getString("state"))
      mascotas = mascotas :+ p
    }
  }
  finally{
    // Antes de retornar los resultados, cerramos la conexión a la BD
    conexion.close()
  }
    
  val jsonAux = Json.toJson(mascotas) // Finalmente, se Jsifican los resultados
  Ok(jsonAux) // Y se retorna la lista de mascotas Jsificada
}

Eliminación:

// Método para eliminar la mascota indicada de la BD
def removerMascotaSQL(id: Int) = Action {
  // En primer lugar creamos una variable para realizar la conexión con la BD
  val conexion = db.getConnection()
    
  try{
    // Después creamos una variable en donde formulamos nuestra query SQL de eliminación y la ejecutamos
    val query = conexion.createStatement
    val resultado = query.executeUpdate("DELETE FROM pet WHERE id = " + id)
  }
  finally{
    // Antes de terminar, cerramos la conexión a la BD
    conexion.close()
  }
    
  // Y para terminar indicamos que se realizó la operación correctamente
  Ok("La mascota ha sido eliminada exitosamente!")
}

Actualización:

// Método para actualizar la información de la mascota indicada en la BD
def actualizarMascotaSQL = Action { implicit request =>
  val cuerpoJson = request.body.asJson.get // En primer lugar se recupera el cuerpo del mensaje el cual debe contener el json con la información a actualizar
  
  // Luego, se valida que lo que se obtuve si es un json que corresponda con un objeto tipo Pet
  cuerpoJson.validate[Pet] match {
    // En caso de éxito entonces
    case success: JsSuccess[Pet] =>
      // Se crea un nuevo objeto mascota a partir de la información que me llego
      var nuevaMascota = Pet(success.get.id, success.get.name, success.get.kind, success.get.gender, success.get.location, success.get.state)
	 
      // También, creamos una variable para realizar la conexión con la BD
      val conexion = db.getConnection()
   	 
      try{
        // Después creamos una variable en donde formulamos nuestra query SQL de actualización y la ejecutamos
        val query = conexion.createStatement
        val resultado = query.executeUpdate("UPDATE pet SET name = '"+nuevaMascota.name+"', kind = '"+nuevaMascota.kind+"', gender = '"+nuevaMascota.gender+"', location = '"+nuevaMascota.location+"',state = '"+nuevaMascota.state+"' WHERE id = "+nuevaMascota.id)
      }
      finally{
        // Posterior , cerramos la conexión a la BD
        conexion.close()
      }
   	 
      // Y para terminar indicamos que se realizó la operación correctamente
      Ok("La mascota ha sido actualizada exitosamente!")
   	 
    // En caso de error entonces devuelvo un mensajito
    case e:JsError => BadRequest("No se pudo actualizar porque hay malos parametros!!")
  }
}

Inserción:

// Método para agregar una nueva mascota en la BD
def insertarMascotaSQL = Action { implicit request =>
  val cuerpoJson = request.body.asJson.get // En primer lugar se recupera el cuerpo del mensaje el cual debe contener el json con la información de la mascota a ingresar a la lista

  // Luego, se valida que lo que se obtuvo si es un json que corresponda con un objeto tipo Pet
  cuerpoJson.validate[Pet] match {
    // En caso de éxito entonces
    case success: JsSuccess[Pet] =>
      // Creó un nuevo objeto mascota a partir de la información que me llego
      var nuevaMascota = Pet(success.get.id, success.get.name, success.get.kind, success.get.gender, success.get.location, success.get.state)
   	 
      // También, creamos una variable para realizar la conexión con la BD
      val conexion = db.getConnection()
   	 
      try{
        // Después creamos una variable en donde formulamos nuestra query SQL de inserción y la ejecutamos
        val query = conexion.createStatement
        val resultado = query.executeUpdate("INSERT INTO pet VALUES("+nuevaMascota.id+",'"+nuevaMascota.name+"','"+nuevaMascota.kind+"','"+nuevaMascota.gender+"','"+nuevaMascota.location+"','"+nuevaMascota.state+"')")
     	 
        // Si todo es correcto mostramos un mensaje de éxito
        Ok("La mascota ha sido ingresada exitosamente!")
      }
      catch
      {
        // En caso que pase algo mostramos un mensaje de error
        case e: Exception => Ok("No se puede insertar la mascota porque la clave indicada ya existe o hubo un error.")
      }
      finally{
        // Finalmente, cerramos la conexión a la BD
        conexion.close()
      }
   	 
    // En caso de error entonces devuelvo un mensajito
    case e:JsError => BadRequest("No se pudo actualizar porque hay malos parametros!!")
  }
}

Ya para evaluar si los metodos estan trabajando correctamente volvemos a utilizar postman para ver si todo está funcionando correctamente.




Ejercicio Propuesto:

Realizar una función que me devuelva una mascota por su id













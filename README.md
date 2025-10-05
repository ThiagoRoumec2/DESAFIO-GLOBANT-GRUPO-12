# DESAFIO-GLOBANT-GRUPO-12
Repositorio donde se encuentra el desafío realizado propuesto por Juan Pablo Pizarro.

# Desarrollo

CanchApp es una app-web destinada a la reserva y gestión de canchas de pádel. Este permite a los usuarios reservar turnos de canchas disponibles, además de crear una petición para ser dueño, la cual será aceptada o rechazada por un admin, donde en caso de ser aceptada, el usuario obtendrá las caracteristicas de un dueño. Un dueño puede tanto reservar como también crear y gestionar sus propias canchas. Estas reservas se representan con un código único por cada una, además de un historial, que permite un manejo más eficiente de estas sin recurrir a planillas físicas.

#Diagramas

*Diagrama de Flujo: Un diagrama de flujo es un diagrama que permite ver paso a paso el flujo de los datos de un programa.
Para este diagrama consideramos las caracteristicas principales donde se ingresa a la aplicación con opción de registrarse o iniciar sesión. Ese inicar sesión es un bucle donde si los datos no coinciden con los registrados nunca podrá ingresar al programa.
Una vez ingresado el sistema obtiene el rol del usuario y dependiendo de su rol, realiza distintas acciones.
Usuario: Opción de ser dueño, reservar cancha y cancelar reserva.
Dueño: Opción de crear cancha.
Admin: Opción de aceptar solicitud de usuario para ser dueño.

Esto nos permitió visualizar antes de realizar el programa como va a ser y como es su flujo de datos.

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////


*Diagrama UML: Un diagrama UML es un diagrama que permite ver como se relacionan las diferentes funcionalidades de los actores del programa entre ellos y con el sistema.
Para este diagrama detectamos tres actores:

•	Usuario: Actor externo que accede a la plataforma para consultar, reservar y gestionar reservas.

Sus casos de uso:

•	Iniciar Sesión
o	(<<extend>>) Registrarse
•	Registrarse
•	Reservar cancha
o	(<<include>>) Notificar cambios de reserva.
•	Buscar canchas
o	(<<extend>>) Ver detalles de cancha.
•	Ver detalles de cancha
o	(<<extend>>) Reservar cancha.
•	Ver perfil
o	(<<extend>>) Ver historial de reservas.
•	Ver historial de reservas
•	Solicitar ser dueño
•	Cancelar reserva
o	(<<include>>) Notificar cambios de reserva.
•	Notificar cambios de reserva
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
•	Dueño: Actor externo que accede a la plataforma para publicar y gestionar canchas.

El actor “Dueño de cancha” se considera una generalización del actor “Usuario”, ya que hereda todas las acciones disponibles para un usuario común y además cuenta con funciones adicionales específicas de su rol.
•	Eliminar cancha
•	Agregar cancha
•	Editar cancha
•	Revisar reservas
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
•	Administrador: Actor interno que administra roles, gestiona la base de datos y consulta estados del sistema.

Sus casos de usos:

•	Iniciar sesión
•	Administrar solicitud
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

*Diagrama de Esquema de Base de Datos: Este diagrama representa la estructura de la base de datos y las relaciones entre las distintas entidades del sistema. Cada entidad refleja un objeto del proyecto, como usuarios, canchas, reservas, valoraciones, etc. Las relaciones muestran cómo interactúan entre sí. Este diseño garantiza la integridad de los datos y facilita la gestión eficiente de la información.

Entidades Principales y sus Campos
•	Usuario: id_usuario, nombre, email, contraseña, foto.

•	Favoritos: id_favorito, id_usuario, id_cancha, fecha_agregado. 

•	Reserva: id_reserva, fecha, hora_inicio, hora_final, id_usuario, id_cancha, espacios_reservados, jugadores_reservados, teléfono, observaciones, estado. 

•	Cancha: id_cancha, id_duenio, nombre, lugar, foto, bio, valoración, precio. 

•	Dueño: id_duenio, id_usuario, nombre, email, contraseña. 

•	Verificación: id_verificacion, estado, fecha, observación, id_usuario, id_admin.

•	Admin: id_admin, nombre, email, contraseña.

• Valoración: id_valoracion, valor, comentario, id_usuario, id_cancha.

Relaciones 
•	Usuario-Reserva: Un solo usuario puede realizar muchas reservas, mientras que cada reserva pertenece a un único usuario. (1: N) 
•	Usuario-Favoritos: Un solo usuario puede añadir muchas canchas a favoritos, mientras que cada favorito pertenece a un único usuario. (1: N) 
•	Usuario-Verificación: Un solo usuario puede solicitar muchas verificaciones, mientras que cada verificación pertenece a un único usuario. (1: N) 
•	Usuario-Dueño: Un usuario puede ser un dueño y cada dueño corresponde a un único usuario. (1:1)
• Usuario-Valoración: Un usuario puede otorgar muchas valoraciones y cada valoración corresponde a un único usuario. (1: N)
•	Dueño-Cancha: Un dueño puede registrar muchas canchas, mientras que cada cancha pertenece a un único dueño. (1: N) 
•	Cancha-Reserva: Una cancha puede tener muchas reservas, mientras que cada reserva está asignada a una única cancha. (1: N) 
•	Cancha-Favoritos: Una cancha puede estar en los favoritos de muchos usuarios, mientras que cada favorito pertenece a una única cancha. (1: N)
• Cancha-Valoración: Una cancha puede tener muchas valoraciones, mientras que cada valoración corresponde a una única cancha. (1: N)
•	Admin-Verificación: Un admin puede revisar muchas verificaciones, mientras que cada verificación es revisada por un único admin. (1: N)
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

*Diagrama de Bloques: Es un diagrama que repesenta en forma de bloques procesos e interacciones y sus relaciones en un sistema.
Este diagrama fue separado en 3. Diagrama de Bloques del Usuario, del Dueño y del Admin donde cada uno contiene sus propios procesos.

Usuario: Este se registra e inicia sesión, donde tiene 2 interacciones:
• Solicitud para ser dueño.
• Búsqueda y selección de cancha. Donde esta en caso de estar disponible:
  • Reservación de cancha.
  • Validación de datos.
  • Generación de código único de reserva.
  • Valorar o comentar cancha.

Dueño: Este se registra e inicia sesión, donde tiene la opción de:
• Creación de cancha.
• Validación de datos.
• Cancha creada.
• Gestión de cancha.

Admin: Este se registra e inicia sesión, donde tiene la opción de:
• Gestión de solicitudes. Donde puede rechazarla o aprobarla:
  • Solicitud rechazada.
  • Solicitud aprobada.
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////  




#Herramientas Utilizadas

Para nuestros diagramas utilizamos MIRO y draw.io.
Utilizamos miro ya que es una herramienta colaborativa que nos permite hacer diagramas muy comodamente pero con desventaja que su versión gratuita no permite modificar o utilizar 3 archivos distintos (Hay que borrarlos para liberar ese tope).
Y utilizamos draw.io ya que al igual que MIRO es una herramienta colaborativa que nos facilita mucho el trabajo a la hora de hacer diagramas.

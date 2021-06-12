# Configuración Básica de Global Protect On-Demand

Esta configuracción de Global Protect es la mas habitual y como su nombre indica se aplica bajo demanda (cunado el usuario quiera). El usuario cuenta con el control sobre cuando conectarse o desconectarse de Global Protect. Esto provoca que cuando el usuario esta conectado a GlobalProtect le aparecera la opeción de "Desconectarse" cuando lo considere necesario.

En este articulo detallo paso a paso como implementar y configurar esta modalidad de Global Protect.

## Prerequistiros


## Antecedentes




## Vamos Paso A Paso
1. Generearemos una CA raíz, una CA intermedia y un Certificado de servidor. De esta dorma contaremos con una ruta de certificación completa.
   
  * **Generacción de los certificados en el Firewall**: Existen muchas opciones diferentes para poder implementar los certificados, no obstante en esta documentacción se ha decido optar por utilizar los certificados auto generados para poder desarollar la estructura de certificación y cifrado de las comunicaciones.
  
    * **Generación del certificado Root:** Devemos de generar un certifcado Raiz con un nombre de comun de cualquier valor unico, esto hace referencia a que sea utilizado para la generación de este IP o FQDN del portal o puerta de enlace.
    
   ![Imagen del certifado RootCA](./GP-Images/GP-01.PNG.png)
    
   * **Generación del certificado Intermedio**: Esta opción no es obligatoria pero es recomendable como Best Practices para poder mantener una estrucutra de 3 nivles. Devemos generar un certificado intermedio firamdo por el certificado raiz anterior, especificado un nombre común como valor unico que como en el punto anterior no sea la IP o el FQDN del portal o puerta de enlace.

   ![Imagen del certifado IntermediateCA](./GP-Images/GP-02.PNG.png)

   * **Generar el certificado de servidore**: Debemos generar el certificado firlado por la CA intermedia, donde los datos deberan de coincidr estricatmetne con la IP o el FQDN del Portal y la puerta de enlace. 
      * **A**: Si el nombre "subj alt name(SAN)" no existira en el certificado. En los firewalls podemos crear estos atributos debajo de los atriburtos obligatorios. Añadiendo 'HostName', IP, 'e-mail', etc. 
      * **B**: Si los atributos SAN existen para poder determinar una entrad, entonces la IP o el FQDN que se utilizara para el portal debera de estar peresente en esta lista de registros.
      * **C**: Este certificado nunca deberia de ser una CA por motivos de seguridad y operativa.
      * **D**: Siempre que sea possible debera de utilizare el FQDN en lugar de la dirección IP.

 ![Imagen del certifado Servidor(./GP-Images/GP-03.PNG.png)
 
 
 Una vez realizada esta configuracción deberaia de haber quedado una configuracción similar a la siguiente.
 
 ![Imagen del certifado Resultado Final](./GP-Images/GP-04.PNG.png)
 


2. Crearemos un perfil SSL/TLS des de **Device > Certificate Management > SSL/TLS Service Profile**, el qual referenciaremos a al certificado de servidor que hemos creado en el punto anterior.

 ![Perfil de SSL/TLS](./GP-Images/GP-05.PNG.png)

4. Crea un perfil de autenticación a partir de **Device > Authentication Profile > Add**.
* **Nombre:** Establecemos el nombre que va ha tener el perfil de autenticación.
* **Type:** Escogemos a partir de que funete de datos vamos a absorver la identidad de los usuarios que vamos a utilizar en la VPN.
* Para finbalizar devemos acceder al apartado **Advanced** donde definiremos el alacance de los usuarios que podran inicar sessión en la VPN, en el caso que nos ocupa para esta prueba de laboratorio utilizaremos el grupo **all**, en caso de necesitar limitarse se podria añadir cualquier otro grupo.


 ![Autentication_profile_1](./GP-Images/GP-06.PNG.png)
 ![Autentication_profile_2](./GP-Images/GP-07.PNG.png)





# Bibliografia 
CONFIGURACIÓN DE CERTIFICADO PARA GLOBALPROTECT - (SSL / TLS, PERFILES DE CERTIFICADO DE CLIENTE, CERTIFICADO DE CLIENTE / MÁQUINA)
* https://knowledgebase.paloaltonetworks.com/KCSArticleDetail?id=kA10g000000ClFoCAK

CONFIGURACIÓN BÁSICA DE GLOBALPROTECT CON ON-DEMAND
* https://knowledgebase.paloaltonetworks.com/KCSArticleDetail?id=kA10g000000ClH2CAK

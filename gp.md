# Configuración Básica de Global Protect On-Demand

Esta configuracción de Global Protect es la mas habitual y como su nombre indica se aplica bajo demanda (cunado el usuario quiera). El usuario cuenta con el control sobre cuando conectarse o desconectarse de Global Protect. Esto provoca que cuando el usuario esta conectado a GlobalProtect le aparecera la opeción de "Desconectarse" cuando lo considere necesario.

En este articulo detallo paso a paso como implementar y configurar esta modalidad de Global Protect.

## Prerequistiros


## Antecedentes




## Vamos Paso A Paso
1. Generearemos una CA raíz, una CA intermedia y un Certificado de servidor. De esta dorma contaremos con una ruta de certificación completa.
   
  * **Generacción de los certificados en el Firewall**: Existen muchas opciones diferentes para poder implementar los certificados, no obstante en esta documentacción se ha decido optar por utilizar los certificados auto generados para poder desarollar la estructura de certificación y cifrado de las comunicaciones.
  
    * **Generación del certificado Root:** Devemos de generar un certifcado Raiz con un nombre de comun de cualquier valor unico, esto hace referencia a que sea utilizado para la generación de este IP o FQDN del portal o puerta de enlace.
    
    
   ![GitHub Logo](/images/logo.png)
    
    
    * **Generación del certificado Intermedio**: Esta opción no es obligatoria pero es recomendable como Best Practices para poder mantener una estrucutra de 3 nivles. 


2. Crearemos un perfil SSL/TLS des de **Device > Certificate Management > SSL/TLS Service Profile**, el qual referenciaremos a al certificado de servidor que hemos creado en el punto anterior.

4.    




# Bibliografia 
CONFIGURACIÓN DE CERTIFICADO PARA GLOBALPROTECT - (SSL / TLS, PERFILES DE CERTIFICADO DE CLIENTE, CERTIFICADO DE CLIENTE / MÁQUINA)
* https://knowledgebase.paloaltonetworks.com/KCSArticleDetail?id=kA10g000000ClFoCAK

CONFIGURACIÓN BÁSICA DE GLOBALPROTECT CON ON-DEMAND
* https://knowledgebase.paloaltonetworks.com/KCSArticleDetail?id=kA10g000000ClH2CAK

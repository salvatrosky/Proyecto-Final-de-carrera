# Seguridad en redes LAN: utilizando Docker para mejorar la navegación web. 

El 14 de mayo de 2021 presenté mi trabajo final de carrera, recibiendo así el título de Ingeniero en Computación. 

Se realizó un trabajo de investigación donde se muestran las consecuencias que tiene utilizar sistemas que no implementan mecanismos de seguridad, además, se desarrollaron posibles soluciones a las problemáticas anteriormente mencionadas. En varios casos, se montaron escenarios de pruebas para un mejor entendimiento del lector.  

El proyecto fue realizado en LaTeX, utilizando versionado con GitHub .

El documento en formato PDF está disponible [aquí](https://github.com/salvatrosky/Proyecto-Final-de-carrera/blob/main/ES/build/Main.pdf "aquí")

**Table of Contents** 

[TOC] 

# Introducción 

A lo largo de la carrera, y, particularmente, en una de mis materias preferidas, Seguridad en Sistemas, nos han explicado la importancia la protección de los datos, como así también la de los canales de comunicación. Al desplegar una red segura, se deben considerar los siguientes aspectos centrales de la seguridad en sistemas, tales como la confidencialidad, la integridad y la disponibilidad (CIA). 

En nuestra corta experiencia hemos observado como las organizaciones abordan los temas de seguridad en sus sistemas informáticos y en las redes de datos. En general, se concentran en los equipos que están expuestos a la red pública, dejando de lado los que se encuentran aislados de la misma. Muchas veces se piensa que es suficiente, sin embargo, puede traer graves inconvenientes. Es por eso que realizaremos un estudio teórico/práctico sobre las consecuencias de la navegación en redes internas sin ningún tipo de cifrado de datos ni certificaciones, lo cual puede traer graves inconvenientes en cuanto a la seguridad interna. Entre las consecuencias podemos ejemplificar con sistemas internos que no proveen conexiones seguras y descuidan la autenticación confidencial de los usuarios. 

# Navegación web en redes internas 

La conexión en red es la tecnología clave para una amplia variedad de aplicaciones dentro de una organización, como, por ejemplo: correo electrónico, transferencia de archivos, sistemas de intranet para gestión de tareas dentro de la organización (departamento de compras, relación con el cliente ERP, departamentos de ventas, gestión de recursos humanos, gestión de seguridad industrial, dashboards, etc.). Sin embargo, existe una falta significativa en la aplicación de métodos de seguridad para estas aplicaciones. 

# Debilidades del protocolo HTTP 

HTTP originalmente no fue un protocolo pensado en la seguridad. Los mensajes HTTP se envían a través de Internet sin cifrar y, por lo tanto, cualquiera puede leer el mismo cuando se dirige a su destino. Internet, como su nombre indica, es una red de computadoras (interconnected computer networks), no un sistema punto a punto. Hablando específicamente de una red interna, no sabemos cómo se enrutan los mensajes y nosotros, como usuarios, no tenemos idea de que otras partes podrían captarlos. Debido a que HTTP va a través de texto plano, los mensajes se pueden interceptar, leer, e incluso alterar en el camino. 

En este capítulo veremos por qué el protocolo HTTP es inseguro, adicionando luego un caso de estudio donde se demuestra un peque ̃no ataque. 

# Soluciones estudiadas 

Luego de haber explicado las debilidades del protocolo HTTP, vamos a explorar las distintas soluciones encontradas, empezando con un peque ̃no marco teórico, el cual nos permitirá probar estas implementaciones y aplicarlas en un escenario de prueba. 

La herramienta utilizada es Docker, con ella es posible simular escenarios sin necesidad de tener cada uno de los servidores de manera física. Para entenderlo un poco mejor, explicaremos lo que es la virtualización y profundizaremos en la virtualización basada en contenedores. 


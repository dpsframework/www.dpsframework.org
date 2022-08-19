---
layout:  proposal
toc:  true
author:  'Aguayo, FJ'
license:  'GNU Lesser General Public License v2.1'
ref:  p40-clipsjni-051
lang:  es
date:  '2022-04-27'
modified:  '2022-08-17'
status:  'Finalizado'
title:  'Propuesta: autoubicación dual de biblioteca nativa de CLIPSJNI-0.51'
subtitle:  'Propuesta de actualización de CLIPS-JNI-0.51 para facilitar la detección de la arquitectura de máquina y ubicación de librería nativa en tiempo de ejecución'
headtitle:  'El componente Java CLIPSJNI-051 permite conectar Java al núcleo de CLIPS desarrollado en C++. Esta propuesta proporciona una solución probada para detectar la arquitectura de la máquina en tiempo de ejecución, además de incorporar otras mejoras de seguridad adicionales. Está orientada a ser utilizada por los Agentes-PS de JADE con capacidad de resolución de problemas. Sin embargo, puede ser útil en cualquier aplicación que requiera conectividada CLIPS 6.31 desde Java.'
imagepath:  'images/clipsjni-051/'
images:
  -  'clips_logo.png'
  
---

##  Lista de Tareas:
- [x]  \(1) Lograr el cumplimiento del componente CLIPJNI con las especificaciones del sistema de módulos[^migra17] de la Plataforma Java (JPMS).
- [x]  \(2) Permitir la compilación desde versiones de Oracle Java[^java] JDK-11 hasta JDK-17 LTS (2022-2029) y superiores. Y además, permitir compilación con versiones de OpenJDK[^openJDK] desde la openJDK-11 hasta la OpenJDK-17.
- [x]  \(3) Optimizar el rendimiento de CLIPSJNI-0.51a en los Comportamientos de los Agentes de la plataforma JADE.
- [x]  \(4) Incorporar archivos de secuencia de pasos de compilación para las diferentes arquitecturas.
- [x]  \(5) Realizar los Test de CLIPS 6.31 sobre una consola de Agentes tipo Nodo.
- [x]  \(6) Preparar como Repositorio GitHub para su descarga y evaluación de la propuesta.











  

##   Sección 1: Identificación
-  Responsable de la propuesta: _FJ Aguayo_.
-  Fecha de la propuesta: Abril, 2022.
-  Ubicación de resultados: GitHub repo.

##   Sección 2: Procesos
-  La interfaz nativa de Java CLIPS-JNI version 0.51 para CLIPS 6.31[^1] ha sido revisada por _Gary Riley_ el pasado 2019-08-06. El código fuente está disponible en Source forge, en <https://sourceforge.net/projects/clipsrules/files/CLIPS/6.31/>.
-  Los agentes JADE[^jade] con capacidades de integrar y ejecutar Sistemas Expertos autónomos sobre la plataforma Multi-Agente, requieren conocer de antemano cuál es la arquitectura de la máquina Java y del hardware donde se ejecutan. 

###  2.1. Descripción de la propuesta:

-  Realizar un desarrollo sobre CLIPS-JNI-0.51 para que esa interfaz detecte cuál es la máquina de Java y la arquitectura hardware de nodo donde se ejecuta el sistema Multi-Agente, y de esa forma, la propia Librería CLIPSJNI asocie y enlace con su librería nativa en C++.
-  El desarrollo de los elementos de seguridad adicionales, se realizó mediante el ajuste de la visibilidad de los Objetos fundamentales que componen la librería CLIPS-JNI-0.51

###  2.2. Plataforma de destino
-  Java JDK-11[^java] hasta JDK-18[^migra17]. OpenJDK-18[^openJDK]. CLIPS 6.31
  
-  Agentes de Resolución de Problemas de JADE, version 1.9 o superior.




###  2.3. ¿Qué necesita la propuesta de para su ejecución?
-  ECLIPSE IDE 2022. 
-  CLIPS 6.31 código-fuente. CLIPS-JNI-0.51 código-fuente.
-  Agentes PS de JADE version 1.9 o superior.
-  CLIPS 6.31 test[^cool]

###  2.4. ¿Por qué esta propuesta?
-  Porque la librería dpsAgents-1.8-full.jar, desarrollada para JAVA 1.8, no es capaz de enlazar los sistemas expertos autónomos de los agentes JADE, con el núcleo de CLIPS 6.31, ni tampoco con CLIPS 6.40.
-  Porque el mecanismo de detección y enlace entre el Agente y CLIPS o Prolog, debe realizarse por parte de la librería nativa, en un enlace temprano, eliminando del agente la necesidad de localizar la ubicación de la Librería Nativa para OS-X, Gnu-Linux, Windows 32bits o Windows 64bits.






###  2.5. Tecnología o tecnologías subyacentes:
-  CLIPS
-  COOL
-  Java
-  Lisp








###  2.6. ¿Nombre de la librería generada?
-    clipsjni-051ps-i586.jar
-    clipsjni-051ps-amd64.jar
etc.












###  2.7. Dependencias en sistemas operativos específicos
-  Ninguna.












###  2.8. Cuestiones de seguridad por el modelo de seguridad actual
-  No se aplica en este proyecto














###  2.9. ¿Problemas de internacionalización o localización?
-  No se han implementado.















###  2.10. ¿Alguna necesidad de revisión como resultado de este trabajo?
-  No se ha previsto. A la espera de revisión.
















###  2.11. Cronograma para el desarrollo de esta propuesta
-   Inicio: **Abril de 2022**
-   Final: **Agosto 2022**
















##   Sección 3: Contribuciones




###  3.1. Documentos, propuestas o implementaciones que describen la tecnología.















###  3.2. Punto de partida de la obra.
-   CLIPSJNI-051 en Source Forge en: https://sourceforge.net/projects/clipsrules/files/CLIPS/6.31/clips_jni_051.tar.gz/download



















##   Sección 4: Información Adicional (Opcional)












###  4.1. Información adicional a incluir en la Propuesta de Mejora
  
  








##  _Bibliografía_

[^1]: CLIPS Rule Based Programming Language Files. Expert System Tool. Gary, Riley D. (Ed. 2022). URL: https://sourceforge.net/projects/clipsrules/.

[^java]: ORACLE Java 17 is the latest long-term support (LTS) release under Java's six-month release cadence and is the result of extensive collaboration between Oracle engineers and other members of the worldwide Java developer community via the OpenJDK Community and the Java Community Process (JCP). Verificada con la versioón jdk-17.0.3.1 (junio, 2022). https://www.oracle.com/news/announcement/oracle-releases-java-17-2021-09-14/.

[^jade]:    JADE Platform. jade - Revision 6867: /trunk. https://jade.tilab.com/svn/jade/trunk/  Login/passwod: jade/jade. Version 4.5.4 (abril, 2022).

[^migra17]: Significant Changes in JDK 17 Release. Notes for additional descriptions of the new features and enhancements, and API specification in JDK 17. Updates in Java SE 17 and JDK 17: https://docs.oracle.com/en/java/javase/17/migrate/significant-changes-jdk-release.html

[^openJDK]: OpenJDK 17 is the open-source reference implementation of version 17 of the Java SE Platform, as specified by by JSR 390 in the Java Community Process. JDK 17 reached General Availability on 14 September 2021. URL for OpenJDK-11 is: https://openjdk.java.net/projects/jdk/11/. URL for OpenJDK-17 is: https://openjdk.java.net/projects/jdk/17/.

[^cool]: COOL is the acronym for CLIPS Object Oriented Language.
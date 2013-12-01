sialop-core
===========

Core Sialop

--Peter
Iniciando instalacion del Servidor, me dio problemas al iniciar el mismo.
Actualicé JBOSS Tools

El siguiente error salió al iniciar Jboss
Wrong arguments. new for target java.lang.reflect.Constructor expected=[java.net.URI].................

El problema se originó por que la versión de Java es diferente a la que uso:
La solución es cambiar en el archivo "profile.xml" de la configuración de Jboss y ponerle en la línea que tiene el tag 
<parameter> cambiar a : <parameter class="java.io.File"> ejemplo a continuación de toda la sección.

<bean name="AttachmentStore" class="org.jboss.system.server.profileservice.repository.AbstractAttachmentStore">
		<constructor><parameter class="java.io.File"><inject bean="BootstrapProfileFactory" property="attachmentStoreRoot" /></parameter></constructor>
		<property name="mainDeployer"><inject bean="MainDeployer" /></property>
		<property name="serializer"><inject bean="AttachmentsSerializer" /></property>
		<property name="persistenceFactory"><inject bean="PersistenceFactory" /></property>
</bean>

--Peter

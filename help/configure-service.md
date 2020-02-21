---
title: Configuración del servicio Conversión automatizada de formularios
description: Listo la instancia de AEM para utilizar el servicio Conversión automatizada de formularios
translation-type: tm+mt
source-git-commit: ef5789dabccc65dcf988b9424b435aa036017691

---


# Configuración del servicio Conversión automatizada de formularios {#about-this-help}

Esta ayuda describe cómo un administrador de AEM puede configurar el servicio de conversión automatizada de formularios para automatizar la conversión de sus formularios PDF a formularios adaptables. Esta ayuda es para administradores de TI y AEM de su organización. La información proporcionada se basa en el supuesto de que cualquiera que lea esta Ayuda está familiarizado con las siguientes tecnologías:

* Instalación, configuración y administración de paquetes de Adobe Experience Manager y AEM,

* Uso de sistemas operativos Linux y Microsoft Windows,

* Configuración de servidores de correo SMTP

>[!VIDEO](https://video.tv.adobe.com/v/29267/)

**Vea el vídeo o lea el artículo para configurar el servicio de conversión automatizada de formularios**

## Incorporación{#onboarding}

El servicio está disponible de forma gratuita para los clientes a plazo local de AEM 6.5 Forms y AEM 6.4 Forms y para los clientes empresariales de servicios gestionados de Adobe. Puede ponerse en contacto con el equipo de ventas de Adobe o con su representante de Adobe para solicitar acceso al servicio.

Adobe habilita el acceso para su organización y proporciona los privilegios requeridos a la persona designada como administrador en su organización. El administrador puede otorgar acceso a los desarrolladores (usuarios) de AEM Forms de su organización para conectarse al servicio.

## Requisitos previos {#prerequisites}

Para utilizar el servicio de conversión de formularios automatizados, debe hacer lo siguiente:

* El servicio Conversión automatizada de formularios está habilitado para su organización
* Una cuenta de Adobe ID con privilegios de administrador para el servicio de conversión
* Una instancia de autor de AEM 6.5 o AEM 6.4 que se esté ejecutando con el último Service Pack de AEM
* Un usuario de AEM (en su instancia de AEM) que es miembro del grupo de usuarios de formularios

## Configuración del entorno {#setuptheservice}

Antes de usar el servicio, prepare la instancia de creación de AEM para conectarse al servicio que se ejecuta en Adobe Cloud. Realice los siguientes pasos en la secuencia indicada para preparar la instancia para el servicio:

1. [Descargar e instalar AEM 6.5 o AEM 6.4](#aemquickstart)
1. [Descargar e instalar el último Service Pack de AEM](#servicepack)
1. [Descargar e instalar el paquete adicional más reciente de AEM Forms](#downloadaemformsaddon)
1. [Creación de plantillas y temas personalizados](#referencepackage)

### Descargar e instalar AEM 6.5 o AEM 6.4 {#aemquickstart}


El servicio Conversión automatizada de formularios se ejecuta en una instancia de creación de AEM. Se requiere AEM 6.5 o AEM 6.4 para configurar una instancia de creación de AEM. Si AEM no está en funcionamiento, descárguelo de las siguientes ubicaciones:

* Si ya es cliente de AEM, descargue AEM 6.5 o AEM 6.4 del sitio web [de licencias de](http://licensing.adobe.com)Adobe.

* Si es un socio de Adobe, utilice [Adobe Partner Training Program](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) para solicitar AEM 6.5 o AEM 6.4.

Después de descargar AEM, para obtener instrucciones sobre cómo configurar una instancia de autor de AEM, consulte [Implementación y mantenimiento](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall).

### Descargar e instalar AEM Service Pack más reciente {#servicepack}

Descargue e instale el último Service Pack de AEM. Para obtener instrucciones detalladas, consulte las Notas [de la versión de](https://helpx.adobe.com/experience-manager/6-5/release-notes/sp-release-notes.html) AEM 6.5 Service Pack o las Notas [de la versión de](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html)AEM 6.4 Service Pack.

### Descargar e instalar el paquete de complementos de AEM Forms {#downloadaemformsaddon}

Una instancia de AEM contiene funciones básicas de formularios. El servicio de conversión requiere todas las funciones de AEM Forms. Descargue e instale el paquete de complementos de AEM Forms para utilizar todas las funciones de AEM Forms. El paquete es necesario para configurar y ejecutar el servicio de conversión. Para obtener instrucciones detalladas, consulte [Instalación y configuración de funciones de captura de datos.](https://helpx.adobe.com/experience-manager/6-5/forms/using/installing-configuring-aem-forms-osgi.html)

>[!NOTE]
> Si ya es usuario del servicio Conversión automatizada de formularios, instale el complemento de AEM Forms más reciente para seguir utilizando el servicio. El paquete de conector se combina con el paquete del complemento AEM Forms. El paquete de conector adicional ya no es necesario.
> Asegúrese de realizar las configuraciones obligatorias posteriores a la instalación después de instalar el paquete de complemento.


### Creación de plantillas y temas personalizados {#referencepackage}

Si inicia AEM en modo [de](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/production-ready.html) producción (nosamplecontent runmode), los paquetes de referencia no se instalan. Los paquetes de referencia contienen temas y plantillas de ejemplo. El servicio Conversión automatizada de formularios requiere al menos un tema y una plantilla para convertir formularios PDF en formularios adaptables. Cree un tema personalizado y una plantilla propios y una configuración [de](#configure-the-cloud-service) servicio de puntos para utilizar plantillas y temas personalizados antes de utilizar el servicio.

## Configurar el servicio {#configure-the-service}

Antes de proceder a configurar el servicio y conectar su instancia local con el servicio que se ejecuta en Adobe Cloud, conozca las personas y los privilegios necesarios para conectarse al servicio. El servicio utiliza dos tipos diferentes de personas, administradores y desarrolladores:

* **Administradores**: Los administradores son responsables de administrar el software y los servicios de Adobe para su organización. Los administradores otorgan acceso a los desarrolladores de su organización para conectarse al servicio de conversión automatizada de formularios que se ejecuta en Adobe Cloud. Cuando se aprovisiona un administrador para una organización, este recibe un correo electrónico con el título **[!UICONTROL 'You now have administrator rights to manage Adobe software and services for your organization']**. Si usted es un administrador, compruebe su buzón de correo electrónico con el título anteriormente mencionado y continúe [concediendo acceso a los desarrolladores de su organización](#adduseranddevs).

![correo electrónico de concesión de acceso de administrador](assets/admin-console-adobe-io-access-grantedx75.png)

* **Desarrolladores**: Un desarrollador conecta una instancia de autor local de AEM Forms con el servicio de conversión automatizada de formularios que se ejecuta en Adobe Cloud. Cuando un administrador concede derechos a un desarrollador para conectarse al servicio de conversión automatizada de formularios, se envía al desarrollador un mensaje de correo electrónico con el título Ahora tiene acceso de desarrollador para administrar las integraciones de API de Adobe para su organización. Si es un desarrollador, compruebe si hay correo electrónico con el título anteriormente mencionado en su buzón y vaya a [conectar la instancia local de AEM al servicio de conversión automatizada de formularios en Adobe Cloud.](#connectafcadobeio)

![correo electrónico de concesión de acceso para desarrolladores](assets/email-developer-accessx94.png)

### (Solo para administradores) Conceder acceso a los desarrolladores de su organización {#adduseranddevs}

Después de que Adobe habilita el acceso para su organización y proporciona los privilegios requeridos al administrador, el administrador puede iniciar sesión en Admin Console (instrucciones detalladas a continuación), crear un perfil y agregar desarrolladores al perfil. Los desarrolladores pueden conectar una instancia local de AEM Forms al servicio de conversión automatizada de formularios en Adobe Cloud.

Los desarrolladores son miembros de su organización designados para ejecutar el servicio de conversión. Solo los desarrolladores que se agreguen al perfil del servicio Conversión automatizada de formularios de Adobe tienen derecho a utilizar el servicio Conversión automatizada de formularios. Siga los pasos a continuación para crear un perfil y agregarle desarrolladores:

1. Inicie sesión en [Admin Console](https://adminconsole.adobe.com/). Utilice el ID **de** Adobe del administrador suministrado para utilizar el servicio de conversión automatizada de formularios para iniciar sesión. No utilice ningún otro ID o Federated ID para iniciar sesión.
1. Haga clic en la **[!UICONTROL Automated Forms Conversion]** opción.
1. Haga clic **[!UICONTROL New Profile]** en la **[!UICONTROL Products]** ficha.
1. Especifique **[!UICONTROL Name]**, **[!UICONTROL Display Name]** y **[!UICONTROL Description]** para el perfil. Haga clic **[!UICONTROL Done]**. Se crea un perfil.

   ![Especifique los detalles del nuevo perfil.](assets/create-new-profile-details.png)

1. Agregue un desarrollador al perfil. Para agregar los desarrolladores:
   1. En la Consola [de](https://adminconsole.adobe.com/enterprise)administración, vaya a la ficha Información general.
   1. Haga clic **[!UICONTROL Assign Developers]** en la tarjeta de producto requerida.
   1. Introduzca la dirección de correo electrónico del programador y, opcionalmente, los nombres y apellidos.
   1. Seleccione perfiles de producto. Tocar **[!UICONTROL Save]**.

Repita los pasos anteriores para todos los usuarios.  Para obtener más información sobre cómo agregar desarrolladores, consulte [Administrar desarrolladores](https://helpx.adobe.com/enterprise/using/manage-developers.html).

Una vez que un administrador agrega desarrolladores al perfil de Adobe I/O, se notifica a los desarrolladores por correo electrónico. Tras recibir el correo electrónico, los desarrolladores pueden [conectar una instancia local de AEM Forms con el servicio de conversión automatizada de formularios en Adobe Cloud](#connectafcadobeio).

### (Solo para desarrolladores) Conecte la instancia local de AEM Forms al servicio de conversión automatizada de formularios en Adobe Cloud {#connectafcadobeio}

Una vez que un administrador le proporcione acceso de desarrollador, puede conectar la instancia local de AEM Forms al servicio de conversión de formularios automatizados que se ejecuta en Adobe Cloud. Siga los pasos que se indican a continuación para conectar la instancia de AEM Forms al servicio:

* [Configurar notificaciones por correo electrónico](configure-service.md#configureemailnotification)
* [Agregar usuario al grupo de usuarios de formularios](#adduserstousergroup)
* [Obtención de certificados públicos](#obtainpubliccertificates)
* [Creación de la integración de Adobe I/O](#createintegration)
* [Configurar el servicio de nube](configure-service.md#configure-the-cloud-service)

#### Configurar notificación por correo electrónico {#configureemailnotification}

El servicio Conversión automatizada de formularios utiliza el servicio de correo de Day CQ para enviar notificaciones por correo electrónico. Estas notificaciones por correo electrónico contienen información sobre conversiones correctas o fallidas. Si elige no recibir notificación, omita estos pasos. Realice los siguientes pasos para configurar el servicio de correo de CQ de día:

1. Vaya al administrador de configuración de AEM en `http://localhost:4502/system/console/configMgr`
1. Abra la configuración de Day CQ Mail Service. Especifique un valor para los campos **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port]** y **[!UICONTROL From address]** . Haga clic **[!UICONTROL Save]**.

   Puede ponerse en contacto con el proveedor de servicios de correo electrónico o con el administrador de TI para obtener información sobre el nombre de host y el puerto del servidor SMTP. Puede utilizar cualquier dirección de correo electrónico válida en el campo de formulario. Por ejemplo, notification@example.com o donotreply@example.com.

1. Abra la **[!UICONTROL Day CQ Link Externalizer]** configuración. En el **[!UICONTROL Domains]** campo, especifique el nombre de host real o la dirección IP y el número de puerto para las instancias locales, de autor y de publicación. Haga clic **[!UICONTROL Save]**.

#### Agregar usuario al grupo de usuarios de formularios {#adduserstousergroup}

Especifique una dirección de correo electrónico en el perfil del usuario de AEM designado para ejecutar el servicio. Asegúrese de que el usuario es el miembro del grupo de usuarios [de](https://helpx.adobe.com/experience-manager/6-4/forms/using/forms-groups-privileges-tasks.html) formularios. Se envían correos electrónicos a la dirección de correo electrónico del usuario que ejecuta la conversión. Para especificar una dirección de correo electrónico para el usuario y agregar el usuario al grupo de usuarios de formularios:

1. Inicie sesión en la instancia de creación de AEM Forms como administrador de AEM. Utilice sus credenciales locales de AEM para iniciar sesión. No utilice el ID de Adobe para iniciar sesión. Tap **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Seleccione un usuario designado para ejecutar el servicio de conversión y toque **[!UICONTROL Properties]**. Se abre la página Editar configuración de usuario.
1. Especifique una dirección de correo electrónico en el **[!UICONTROL Email]** campo y toque **[!UICONTROL Save]**. Los correos electrónicos se envían a la dirección de correo electrónico especificada cuando la conversión se completa correctamente o no se realiza correctamente.
1. Puntee en la ficha **Grupos** . En la ficha Seleccionar grupo, escriba y seleccione el grupo de usuarios **de** formularios. Toque **Guardar y cerrar**. El usuario es ahora miembro del grupo de usuarios de formularios.

#### Obtención de certificados públicos {#obtainpubliccertificates}

Un certificado público le permite autenticar su perfil en Adobe I/O.

1. Inicie sesión en la instancia de creación de AEM Forms. Ir a **[!UICONTROL Tools]**> **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Tocar **[!UICONTROL Create]**. Aparece la **[!UICONTROL Adobe IMS Technical Account Configuration]** página.

   ![Página Configuración de la cuenta técnica de Adobe IMS](assets/adobe-ims-technical-account-configuration.png)

1. Seleccione **[!UICONTROL Automated Forms Conversion Service]** en Cloud Solution.

1. Seleccione la **[!UICONTROL Create new certificate]** casilla de verificación y especifique un alias. El alias sirve como nombre del cuadro de diálogo. Tocar **[!UICONTROL Create certificate]**. Aparece un cuadro de diálogo. Haga clic **[!UICONTROL OK]**. Se crea el certificado.

1. Toque **[!UICONTROL Download Public Key]** y guarde el archivo de certificado *AEM-Adobe-IMS.crt* en el equipo. El archivo de certificado se utiliza para [crear la integración en la consola](#createintegration)de Adobe I/O. Tocar **[!UICONTROL Next]**.

1. Especifique lo siguiente:

   * Título: Especifique un título.
   * Servidor de autorización: [https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)
   Deje el resto de campos en blanco por ahora (se proporcionará más tarde). Mantenga la página abierta.

   <!--
   Comment Type: draft

   <li> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

#### Creación de la integración de Adobe I/O {#createintegration}

Para utilizar el servicio Conversión automatizada de formularios, cree una integración en Adobe I/O. La integración genera la clave de API, el secreto del cliente y la carga útil (JWT).

1. Inicie sesión en [https://console.adobe.io/](https://console.adobe.io/). Utilice su ID de Adobe y su cuenta de desarrollador que el administrador haya proporcionado para iniciar sesión en la consola de Adobe I/O.

1. Tocar **[!UICONTROL View Integrations]**. Aparece una pantalla con todas las integraciones disponibles.
1. Seleccione su organización en la lista desplegable en **[!UICONTROL Integrations]**. Toque **[!UICONTROL New Integration]**, seleccione **[!UICONTROL Access an API]** y toque **[!UICONTROL Continue]**.
1. Seleccione **[!UICONTROL Experience Cloud]** > **[!UICONTROL Automated Forms Conversion]** y toque **[!UICONTROL Continue]**. Si la opción Conversión automatizada de formularios está desactivada, asegúrese de que ha seleccionado la organización correcta en el cuadro desplegable que hay encima de la **[!UICONTROL Adobe Services]** opción. Si no conoce su organización, póngase en contacto con su administrador.

   ![Seleccionar conversión automatizada de formularios](assets/create-new-integration.png)

1. Especifique el nombre y la descripción de la integración. Toque **[!UICONTROL Select a File from your computer]** y cargue el archivo AEM-Adobe-IMS.crt descargado en la sección [Obtener certificados](#obtainpubliccertificates) públicos.
1. Seleccione el perfil creado al [conceder acceso a los desarrolladores de su organización](#adduseranddevs) y toque **[!UICONTROL Create Integration]**. Se crea la integración.
1. Toque **[!UICONTROL Continue to integration details]** para ver la información de integración. La página contiene la clave de API, el secreto del cliente y otra información necesaria para conectar la instancia local de AEM al servicio de conversión automatizada de formularios. La información de la página se utiliza para crear la configuración de IMS en el equipo local.

   ![Clave de API, Secreto de cliente e información de carga útil de una integración](assets/integration-details.png)

1. Abra la página Configuración de IMS en la instancia local. La página se ha mantenido abierta al final de la sección, [Obtención de un certificado](#obtainpubliccertificates)público.

   ![Especifique el título, la clave de API, el secreto del cliente y la carga útil ](assets/ims-configuration-details.png)

1. En la página técnica de Adobe IMS, especifique la clave de API y el secreto del cliente. Utilice los valores especificados en la página de integración.

   **Para la carga útil, utilice el código proporcionado en la ficha JWT de la página de integración.** Tocar  **[!UICONTROL Save]**. Se crea la configuración de IMS. Cierre la página de integración.

   ![Usar valores del campo JWT para el campo de carga útil](assets/jwt.png)

   >[!CAUTION]
   >
   >Cree una sola configuración de IMS. No cree más de una configuración IMS.

1. Seleccione la configuración de IMS y toque **[!UICONTROL Check Health]**. Aparecerá un cuadro de diálogo. Tocar **[!UICONTROL Check]**. Cuando la conexión se ha realizado correctamente, aparece el mensaje *Token recuperado correctamente* .

   ![Cuando la conexión se realiza correctamente, aparece el mensaje token recuperado correctamente. ](assets/health-check.png)

   <br/> <br/>

#### Configurar el servicio de nube {#configure-the-cloud-service}

Cree una configuración de servicio en la nube para conectar la instancia de AEM al servicio de conversión. También permite especificar una plantilla, un tema y fragmentos de formulario para una conversión. Puede crear varias configuraciones de servicio en la nube por separado para cada conjunto de formularios. Por ejemplo, puede tener una configuración independiente para los formularios del departamento de ventas y otra distinta para los formularios de asistencia al cliente. Realice los siguientes pasos para crear una configuración de servicio en la nube:

1. En la instancia de AEM Forms, toque **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]**> **[!UICONTROL Cloud Services]** > **[!UICONTROL Automate Forms Conversion Configuration]**.
1. Toque la **[!UICONTROL Global]** carpeta y toque **[!UICONTROL Create]**. Aparece la página para crear la configuración de conversión de formularios automatizados. La configuración se crea en la carpeta Global. También puede crear la configuración en una carpeta diferente que ya existe o crear una nueva carpeta para sus configuraciones.

1. En la **[!UICONTROL Create Automated Forms Conversion Configuration]** página, especifique el valor de los campos siguientes y toque **[!UICONTROL Next]**.

   | Campo | Descripción |
   |--- |--- |
   | Título | Título único para la configuración. El título se muestra en la IU utilizada para iniciar la conversión. |
   | Nombre | Nombre único para la configuración. La configuración se guarda en CRX-Repository con el nombre especificado. El nombre puede ser idéntico al título. |
   | Ubicación de miniaturas | Ubicación de la miniatura de la configuración. |
   | URL de servicio | URL del servicio de conversión de formularios automatizados en Adobe Cloud. Utilice la `https://aemformsconversion.adobe.io/` URL. |
   | Plantilla | Plantilla predeterminada que se aplicará a los formularios convertidos. Siempre puede especificar una plantilla diferente antes de iniciar la conversión. Una plantilla contiene la estructura básica y el contenido inicial de un formulario adaptable. Puede elegir una plantilla de las plantillas proporcionadas de forma predeterminada. También puede crear una plantilla personalizada. |
   | Tema | Tema predeterminado que se aplicará a los formularios convertidos. Siempre puede especificar un tema diferente antes de iniciar la conversión.  Puede hacer clic en el icono para elegir un tema incluido de forma predeterminada. También puede crear un tema personalizado. |
   | Fragmentos existentes | Ubicación de fragmentos existentes, si los hay. |
   | Meta-model personalizado | Ruta del archivo .schema.json del metamodelo personalizado. |



1. En la **[!UICONTROL Advanced]** ficha de la **[!UICONTROL Create Automated Forms Conversion Configuration]** página, especifique un valor para el siguiente campo:

   <table>
   <thead>
   <tr>
   <th>Campo</th>
   <th>Descripción</th>
   </tr>
   </thead>
   <tbody>
   <tr>
   <td >Generar documento de registro</td>
   <td>Seleccione la opción para generar automáticamente el documento de registro para los formularios convertidos. La opción solo está disponible para formularios basados en XFA (XDP y formularios PDF). Cuando activa la opción, después de enviar un formulario, puede permitir a sus clientes mantener un registro, impreso o en formato de documento, de la información que han rellenado en el formulario para su futura referencia. Esto se denomina documento de registro.</td>
   </tr>
   <tr>
   <td>Activar Analytics</td>
   <td>Seleccione la opción para habilitar Adobe Analytics en todos los formularios convertidos. Antes de utilizar esta opción, asegúrese de que Adobe Analytics está activado para su instancia de AEM Forms.</td>
   </tr>
   </tbody>
   </table>

   * Cuando el origen es un formulario basado en XFA con extensión .XDP y, a continuación, el DOR de salida conserva la presentación XFA, de lo contrario el servicio de conversión utiliza una plantilla lista para generar un DOR para otros formularios basados en XFA.
   * Cuando se envía un formulario XFA, los datos de envío del formulario se guardan como un elemento XML o un atributo. Por ejemplo, `<Amount currency="USD"> 10.00 </Amount>`. La moneda se guarda como un atributo y la cantidad de moneda; 10,00 se guarda como un elemento. Los datos de envío de un formulario adaptable no tienen atributos, solo tienen elementos. Por lo tanto, cuando un formulario basado en XFA se convierte en formulario adaptable, los datos de envío de formulario adaptable contienen un elemento para cada atributo. Por ejemplo,

   ```css
      {
         "Type": "Principal",
   
         "Amount": "10.00",
   
         "currency": "USD"
      }
   ```

1. Tocar **[!UICONTROL Create]**.  Se crea la configuración de nube. La instancia de AEM Forms está lista para empezar a convertir formularios heredados en formularios adaptables.
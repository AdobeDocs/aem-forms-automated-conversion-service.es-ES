---
title: Configuración del servicio de conversión automatizada de formularios (AFCS)
description: Prepare la instancia de AEM para utilizar el servicio de conversión automatizada de formularios (AFCS)
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer, User
level: Beginner, Intermediate
exl-id: 8f21560f-157f-41cb-ba6f-12a4d6e18555
source-git-commit: 54cd2cf2fdc4f9b420125e4c04c87bec1b7f368d
workflow-type: ht
source-wordcount: '2366'
ht-degree: 100%

---

# Configuración del servicio de conversión automatizada de formularios (AFCS) {#about-this-help}

Esta ayuda describe cómo un administrador de AEM puede configurar el servicio de conversión automatizada de formularios (AFCS) para automatizar la conversión de sus formularios PDF a formularios adaptables. Esta ayuda es para los administradores de TI y AEM de su organización. La información proporcionada se basa en la suposición de que cualquier persona que lea este artículo está familiarizado con las siguientes tecnologías:

* Instalación, configuración y administración de paquetes de Adobe Experience Manager y AEM

* Uso de los sistemas operativos Linux® y Windows® de Microsoft®,

<!--- >[!VIDEO](https://video.tv.adobe.com/v/29267/) 

**Watch the video or read the article to configure Automated Forms Conversion service (AFCS)** -->

## Incorporación{#onboarding}

El servicio está disponible de forma gratuita para clientes de duración determinada de AEM 6.5 Forms On-Premise y clientes empresariales de Adobe-Managed Service. Póngase en contacto con el equipo de ventas de Adobe o con su representante de Adobe para solicitar acceso al servicio. El servicio también está disponible de forma gratuita y está prehabilitado para los clientes de AEM Forms as a Cloud Service.

Adobe posibilita el acceso a su organización y otorga los pertinentes privilegios a las personas de su organización designadas como administradores. Estos administradores pueden otorgar acceso a los desarrolladores de AEM Forms (usuarios) de su organización para conectarse al servicio.

## Requisitos previos {#prerequisites}

Para utilizar el servicio de conversión automatizada de formularios (AFCS), necesita lo siguiente:

* Que el servicio de conversión automatizada de formularios (AFCS) esté habilitado para su organización
* Tener una cuenta de Adobe ID con privilegios de administrador para el servicio de conversión
* Tener AEM 6.5 en funcionamiento con el último Service Pack de AEM o la instancia de autor de AEM Forms as a Cloud Service con las últimas actualizaciones.
* Un usuario de AEM (en la instancia de AEM) que sea miembro del grupo de usuarios de formularios

## Configuración del entorno {#setuptheservice}

Antes de utilizar el servicio, prepare la instancia de autor de AEM para conectarse al servicio que se ejecuta en Adobe Cloud. Realice los siguientes pasos en la secuencia indicada para preparar la instancia para el servicio:

1. [Descarga e instalación de AEM 6.5 o incorporación de AEM Forms as a Cloud Service](#aemquickstart)
1. [(Solo para AEM 6.5) Descarga e instalación del último Service Pack de AEM](#servicepack)
1. [(Solo para AEM 6.5) Descarga e instalación del paquete de complementos de AEM Forms](#downloadaemformsaddon)
1. [Creación de temas y plantillas personalizadas](#referencepackage)

### 1. Descarga e instalación de AEM 6.5 o incorporación de AEM Forms as a Cloud Service {#aemquickstart}


El servicio de conversión automatizada de formularios (AFCS) se ejecuta en la instancia de autor de AEM. Necesita AEM 6.5 o AEM Forms as a Cloud Service para configurar la instancia de autor de AEM.

* Si no tiene AEM 6.5 en funcionamiento, descárguelo desde las siguientes ubicaciones. Después de descargar AEM, para obtener instrucciones para configurar una instancia de autor de AEM, consulte [implementación y mantenimiento](https://helpx.adobe.com/es/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall):

   * Si ya es cliente de AEM, descargue AEM 6.5 desde el [sitio web de licencias de Adobe](http://licensing.adobe.com).

   * Si es socio de Adobe, utilice el [Programa de formación para socios de Adobe](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) para solicitar AEM 6.5.

* Si utiliza AEM Forms as a Cloud Service, consulte Incorporación a [AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-forms-cloud-service.html?lang=es#setup-environment) y la [configuración de un entorno de desarrollo local](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-local-development-environment.html?lang=es#setup-environment).

### 2. (Solo para AEM 6.5) Descarga e instalación del último Service Pack de AEM {#servicepack}

Descargue e instale el Service Pack de AEM más reciente. Para obtener instrucciones de instalación, consulte las [Notas de la versión del Service Pack de AEM 6.5](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/release-notes/release-notes).

### 3. (Solo para AEM 6.5) Descarga e instalación del paquete de complementos de AEM Forms  {#downloadaemformsaddon}

La instancia de AEM contiene funciones básicas para los formularios. El servicio de conversión requiere todas las funciones de AEM Forms. Descargue e instale el paquete de complementos de AEM Forms para disponer de todas las funcionalidades de AEM Forms. El paquete es necesario para configurar y ejecutar el servicio de conversión. Para obtener instrucciones detalladas, consulte [Instalación y configuración de las funcionalidades de captura de datos.](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi)
https://adminconsole.adobe.com/
>[!NOTE]
> Asegúrese de realizar las configuraciones obligatorias posteriores a la instalación después de instalar el paquete de complementos.
>

<!-- ### (Optional) Download and install connector package  {#installConnectorPackage}

The connector package provides early access to the [Auto-detect logical sections](convert-existing-forms-to-adaptive-forms.md#run-the-conversion) features and improvements delivered in release AFC-2020.03.1. Do not install the package if you do not require feature and improvements delivered in AFC-2020.03.1.  You can [download the connector package from AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1). -->


### 4. Creación de temas y plantillas personalizadas {#referencepackage}

Los paquetes de referencia contienen muestras de temáticas y plantillas. El servicio de conversión automatizada de formularios (AFCS) necesita al menos un tema y una plantilla para convertir un formulario PDF en un formulario adaptable. Cree una temática y una plantilla personalizadas propias y marque [configuración del servicio](#configure-the-cloud-service) para utilizar plantillas y temáticas personalizadas antes de usar el servicio.

También puede descargar e instalar el paquete de [Activos de referencia de AEM Forms](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) en la instancia de autor. Crea algunas temáticas y plantillas de referencia.

## Configuración del acceso y los permisos

Antes de proceder a configurar el servicio y conectar su instancia con el servicio que se ejecuta en Adobe Cloud, obtenga información sobre las personas y los privilegios necesarios para conectarse al servicio. El servicio utiliza dos tipos de perfiles, administradores y desarrolladores:

* **Administradores**: son responsables de administrar el software y los servicios de Adobe para su organización. Los administradores conceden acceso a los desarrolladores de su organización para que se conecten al servicio de conversión automatizada de formularios (AFCS) que se ejecuta en Adobe Cloud. Cuando se aprovisiona un administrador para una organización, este recibe un correo electrónico con el título **[!UICONTROL 'You now have administrator rights to manage Adobe software and services for your organization']**. Si es administrador, compruebe si hay un correo electrónico en su buzón con el título mencionado anteriormente y proceda a [conceder acceso a los desarrolladores de su organización](#adduseranddevs).

![Correo electrónico de concesión de acceso del administrador](assets/admin-console-adobe-io-access-grantedx75.png)

* **Desarrolladores**: un desarrollador conecta una instancia de autor de AEM Forms al servicio de conversión automatizada de formularios (AFCS) que se ejecuta en Adobe Cloud. Cuando un administrador concede derechos a un desarrollador para que se conecte al servicio de conversión automatizada de formularios (AFCS), se envía al desarrollador un mensaje de correo electrónico con el título “Ahora tiene acceso como desarrollador para administrar las integraciones de API de Adobe para su organización”. Si es un desarrollador, compruebe si tiene un correo electrónico en su buzón con el título mencionado anteriormente y proceda a [Conectar la instancia de AEM local al servicio de conversión automatizada de formularios en Adobe Cloud.](#connectafcadobeio)

![Correo electrónico de concesión de acceso para desarrolladores](assets/email-developer-accessx94.png)

### Concesión del acceso a los desarrolladores de su organización

Una vez que Adobe habilita el acceso para su organización y proporciona los privilegios necesarios al administrador, este puede iniciar sesión en Admin Console (instrucciones detalladas a continuación), crear un perfil y agregar desarrolladores. Los desarrolladores pueden conectar una instancia de AEM Forms al servicio de conversión automatizada de formularios (AFCS) en Adobe Cloud.

Los desarrolladores son miembros de su organización que están designados para ejecutar el servicio de conversión. Solo aquellos desarrolladores que se añaden al perfil del servicio de conversión automatizada de formularios (AFCS) de Adobe tienen derecho a utilizarlo.
Realice los pasos siguientes para crear un perfil y agregarle desarrolladores. Se requiere un perfil como mínimo para conceder el acceso necesario a los desarrolladores de su organización

1. Inicie sesión en [Admin Console](https://adminconsole.adobe.com/). Use el **Adobe ID** del administrador suministrado para utilizar el servicio de conversión automatizada de formularios (AFCS) para iniciar sesión.
1. Haga clic en la opción **[!UICONTROL Automated Forms Conversion]**.
1. Haga clic **[!UICONTROL New Profile]** en la pestaña **[!UICONTROL Products]**.
1. Especifique **[!UICONTROL Name]**, **[!UICONTROL Display Name]** y **[!UICONTROL Description]** para el perfil. Haga clic en **[!UICONTROL Done]**. Por ejemplo, cree un perfil como **AFC_Flamingo_Test_Dev**.

   ![Especifique los detalles del nuevo perfil.](assets/create-new-profile-details.png)

1. Agregue un desarrollador al perfil. Para agregar a los desarrolladores, haga lo siguiente:
   1. En [Admin Console](https://adminconsole.adobe.com/enterprise), vaya a la pestaña Información general.
   1. Haga clic en **[!UICONTROL Assign Developers]** en la tarjeta de producto requerida.
   1. Escriba la dirección de correo electrónico de los desarrolladores y, opcionalmente, los nombres y apellidos.
   1. Seleccione los perfiles del producto. Haga clic en **[!UICONTROL Save]**.

Repita los pasos anteriores para todos los usuarios. Para obtener más información sobre cómo agregar desarrolladores, vea [Administrar desarrolladores](https://helpx.adobe.com/es/enterprise/using/support-for-experience-cloud.html).

Cuando un administrador añade desarrolladores al perfil de Adobe I/O, se les notifica a los desarrolladores por correo electrónico (si se ha configurado).

<!--
### Configure email notification for local AEM Forms instance

Automated Forms Conversion service (AFCS) uses the Day CQ mail service to send email notifications. These email notifications contain information about successful or failed conversions. If you choose not receive notification, skip these steps. Perform the following steps to configure the Day CQ Mail Service:

* **For AEM 6.5 Forms**:

   1. Go to AEM configuration manager at `http://[server]:[port]/system/console/configMgr`
   2. Open the Day CQ Mail Service configuration. Specify a value for the **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port]**, and **[!UICONTROL From address]** fields. Click **[!UICONTROL Save]**.

      You can contact your email service provider or IT administrator for information about host name and port of SMTP server. You can use any valid email address in the from field. For example, notification@example.com or donotreply@example.com.

   3. Open the **[!UICONTROL Day CQ Link Externalizer]** configuration. In the **[!UICONTROL Domains]** field, specify the actual host name or IP address and port number for local, author, and publish instances. Click **[!UICONTROL Save]**.

* For AEM Forms as a Cloud Service, [log a support ticket to enable the email service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=es#sending-email). -->

### Adición de usuarios a grupos de usuarios de los formularios {#adduserstousergroup}

Especifique una dirección de correo electrónico en el perfil de AEM del usuario designado para ejecutar el servicio. Asegúrese de que el usuario sea miembro del grupo de **usuarios de formularios**. Se envían correos electrónicos a la dirección del usuario que ejecuta la conversión. Para especificar una dirección de correo electrónico para el usuario y agregar el usuario al grupo de usuarios de formularios, haga lo siguiente:

1. Inicie sesión en AEM en la instancia de autor de AEM Forms como administrador. Use sus credenciales de AEM locales para iniciar sesión.
1. Haga clic en **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.
1. Seleccione un usuario designado para ejecutar el servicio de conversión y haga clic en **[!UICONTROL Properties]**. Se abre la página **Editar configuración de usuario**.
1. Especifique una dirección de correo electrónico en el campo **[!UICONTROL Email]** y haga clic en **[!UICONTROL Save]**. Se envían correos electrónicos a la dirección especificada si la conversión se realiza correctamente o si no.

   ![Especificar correo electrónico](/help/using/assets/specify-email.png)
1. Haga clic en la pestaña **Grupos**. En la pestaña Seleccionar grupo, escriba y seleccione el grupo de **usuarios de formularios**.
1. Haga clic en **Guardar y cerrar**. El usuario es ahora miembro del grupo de usuarios de formularios.

   ![Añadir grupo de usuarios](/help/using/assets/add-user-group.png)

## Conexión de la instancia de AEM Forms al servicio de conversión automatizada de formularios (AFCS) en Adobe Cloud

Después de que un administrador le proporcione acceso como desarrollador, puede conectar su instancia de AEM Forms al servicio de conversión automatizada de formularios (AFCS) que se ejecuta en Adobe Cloud. 
Siga estos pasos para conectar la instancia de AEM Forms al servicio de conversión automatizada de formularios:

[1. Configuración de las API de servicio en Adobe Developer Console](#configure-the-service-apis-on-adobe-developer-console)

[2. Creación de configuraciones de IMS de Adobe](#2-create-adobe-ims-configurations)

[3. Creación de la configuración de la conversión automatizada de formularios](#3-create-automated-forms-conversion-configuration)

### 1. Configuración de las API de servicio en Adobe Developer Console

Para utilizar el servicio de conversión automatizada de formularios (AFCS) cree un proyecto y añada la API del **servicio de configuración automatizada de formularios** al proyecto en Adobe Developer Console. La integración genera la clave de API, el secreto del cliente, el ID de cuenta técnica, los ámbitos y el ID de organización.
Para configurar la API del servicio de conversión automatizada de formularios en Adobe Developer Console, realice los siguientes pasos:

1. Inicie sesión en https://developer.adobe.com/console . Utilice su cuenta de desarrollador de Adobe ID que el administrador haya aprovisionado para iniciar sesión en la consola de Adobe I/O.
1. Seleccione su organización en la esquina superior derecha. Si no conoce su organización, póngase en contacto con su administrador.
1. Haga clic en **[!UICONTROL Create new project]**. Aparece una pantalla para comenzar con el nuevo proyecto.

   ![Crear nuevo proyecto de API](/help/using/assets/create-new-api-project.png)

1. Haga clic en **[!UICONTROL Add API]**. Aparece una pantalla con una lista de todas las API habilitadas para su cuenta.
   ![Añadir API](/help/using/assets/add-api.png)

1. Seleccione **[!UICONTROL Automated Forms Conversion service]** y haga clic en **[!UICONTROL Next]**. Aparece una pantalla para configurar la API.
   ![Seleccionar API de AFCS](/help/using/assets/select-afcs-api.png)

1. Seleccione el método de autenticación **OAuth Server-to-Server**.
1. Especifique el **[!UICONTROL Credential Name]** y haga clic en **[!UICONTROL Next]**.
   ![Especificar nombre de credencial](/help/using/assets/specify-credential-name.png)
1. Seleccione un **perfil de producto**. Por ejemplo, seleccione un perfil como **AFC_Flamingo_Test_Dev**.
1. Haga clic en **[!UICONTROL Save configured API]**.
   ![Seleccionar perfil](/help/using/assets/select-profile.png)

   >[!NOTE]
   >
   > Seleccione el perfil creado al conceder el acceso a los desarrolladores de su organización. Si no conoce el perfil que desea seleccionar, póngase en contacto con su administrador.

1. Haga clic en **[!UICONTROL OAuth Server-to-Server]** para ver la clave de la API, el secreto del cliente y otra información necesaria para conectar la instancia de AEM al servicio de conversión automatizada de formularios (AFCS).
   ![Seleccionar credencial Oath](/help/using/assets/select-oauth-credential.png)

   La información de la página se usa para crear la configuración de IMS, como se explica en la sección [Crear la configuración técnica de IMS en la instancia de autor de AEM](#2-create-ims-technical-configuration-on-aem-author-instance).

   ![Detalles de credenciales OAuth](/help/using/assets/oauth-credentials-details.png)

### 2. Creación de configuraciones de IMS de Adobe

Inicie sesión en la instancia de autor para crear las configuraciones de IMS de Adobe. Use los **Detalles de credenciales OAuth** para recuperar la clave de API, el secreto del cliente, el identificador de cuenta técnica, los ámbitos y el identificador de organización.

1. Inicie sesión en la instancia de autor de AEM Forms. Navegue hasta **[!UICONTROL Tools]**> **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.
1. Haga clic en **[!UICONTROL Create]**.

   ![Crear la configuración de IMS de Adobe](/help/using/assets/create-ims-conf.png)

1. Se abre la página **[!UICONTROL Adobe IMS Technical Account Configuration]**.

   ![La página Configuración de cuenta técnica de Adobe IMS](assets/adobe-ims-technical-account-configuration.png)
1. Seleccione **[!UICONTROL Automated Forms Conversion Service]** en **Cloud Solution**.
1. Especifique lo siguiente:

   * **Título**: especifique un título.
   * **Servidor de autorización**: [https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)
   * Recupere lo siguiente de la sección [Configuración de las API de servicio en Adobe Developer Console](#1-configure-the-service-apis-on-adobe-developer-console):
      * **Id. de cliente**: copie y pegue **Clave de API (Id. de cliente)**.
      * **Secreto de cliente**: copie y pegue **Secreto de cliente**.
      * **Ámbito**: copie y pegue **Ámbitos**.
      * **ID de organización**: copie y pegue **ID de cuenta técnica**.

     ![Crear la configuración de IMS de Adobe](/help/using/assets/save-ims-configuration.png)

1. Haga clic en **[!UICONTROL Save]**. Se crea la configuración de IMS de Adobe.

   >[!CAUTION]
   >
   > Cree solo una configuración IMS. No cree más de una.

1. Seleccione la **configuración de IMS de Adobe** y haga clic en **[!UICONTROL Check Health]**. Aparece un cuadro de diálogo.
   ![Comprobar estado](/help/using/assets/check-health.png)

   Aparece un cuadro de diálogo **Comprobar**.

1. Haga clic en **[!UICONTROL Check]**.

   ![Comprobar estado](/help/using/assets/check-dialog.png)

   Cuando la conexión se realiza correctamente, aparece el mensaje *Token recuperado correctamente*.

   ![Cuando la conexión se realiza correctamente, aparece el mensaje Token recuperado correctamente. ](/help/using/assets/healthy-dialog.png)

1. Haga clic en **Cerrar**.

### 3. Creación de la configuración de la conversión automatizada de formularios

Cree una configuración de la conversión automatizada de formularios para conectar la instancia de AEM al servicio de conversión. También le permite especificar una plantilla, un tema y fragmentos de formulario para una conversión. Puede crear varias configuraciones de servicios en la nube por separado para cada conjunto de formularios.
Por ejemplo, puede tener una configuración independiente para los formularios del departamento de ventas y otra para los de asistencia al cliente. Siga estos pasos para crear la configuración del servicio en la nube:

1. En la instancia de AEM Forms, haga clic en **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]**> **[!UICONTROL Cloud Services]** > **[!UICONTROL Automate Forms Conversion Configuration]**.
1. Seleccione la carpeta **[!UICONTROL Global]** y haga clic en **[!UICONTROL Create]**.
Aparece la página para **Crear la configuración de la conversión automatizada de formularios**. La configuración se crea en la carpeta **Global**. También puede crear la configuración en una carpeta diferente que ya exista o crear una para las configuraciones.
   ![Seleccionar carpeta Global](/help/using/assets/create-afcs-cloud-conf.png)
1. En la página **[!UICONTROL Create Automated Forms Conversion Configuration]**, especifique el valor de los campos siguientes y haga clic en **[!UICONTROL Next]**.

   ![Configuración de AFCS](/help/using/assets/create-afcs-config.png)

   | Campo | Descripción |
   |--- |--- |
   | Título | Título único para la configuración. El título se muestra en la IU utilizada para iniciar la conversión. |
   | Nombre | Nombre único para la configuración. La configuración se guarda en el repositorio CRX con el nombre especificado. El nombre puede ser idéntico al título. |
   | Ubicación de la miniatura | Ubicación de la miniatura para la configuración. |
   | URL del servicio | URL del servicio de conversión automatizada de formularios (AFCS) en Adobe Cloud. Utilice la URL `https://aemformsconversion.adobe.io/`. |
   | Plantilla | Plantilla predeterminada que se aplica a los formularios convertidos. Puede especificar una plantilla diferente antes de iniciar la conversión. Una plantilla contiene estructura básica y contenido inicial para un formulario adaptable. Puede elegir una plantilla de las proporcionadas de forma predeterminada. También puede crear una plantilla personalizada. |
   | Tema | Tema predeterminado que se aplica a los formularios convertidos. Siempre puede especificar un tema diferente antes de iniciar la conversión.  Puede hacer clic en el icono para elegir un tema que se proporcione de forma predeterminada. También puede crear un tema personalizado. |
   | Fragmentos existentes | Ubicación de los fragmentos existentes, si los hay. |
   | Metamodelo personalizado | Ruta del archivo .schema.json del metamodelo personalizado. Puede crear metamodelos independientes para los idiomas inglés, francés, alemán, español, italiano y portugués. |

1. En la pestaña **[!UICONTROL Advanced]** de la página **[!UICONTROL Create Automated Forms Conversion Configuration]**, especifique el valor para el siguiente campo:
   ![Configuración de AFCS](/help/using/assets/afcs-config.png)

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
   <td>Seleccione la opción para generar automáticamente el documento de registro para los formularios convertidos. La opción solo está disponible para formularios basados en XFA (formularios XDP y PDF). Cuando se activa la opción, después de enviar un formulario, se puede permitir a los clientes mantener un registro, impreso o en formato de documento, de la información que han rellenado en el formulario, para su referencia futura. Este registro se denomina documento de registro.</td>
   </tr>
   <tr>
   <td>Activar Analytics</td>
   <td>(Para AEM 6.5) Seleccione la opción para habilitar Adobe Analytics en todos los formularios convertidos. Antes de utilizar la opción, compruebe que Adobe Analytics esté habilitado para su instancia de AEM Forms.</td>
   </tr>
   </tbody>
   </table>

   * Cuando el origen es un formulario basado en XFA con la extensión .XDP, el DOR de salida conserva el diseño XFA. De lo contrario, el servicio de conversión utiliza una plantilla predeterminada para generar DOR para otros formularios basados en XFA.
   * Cuando se envía un formulario XFA, los datos enviados se guardan como un elemento XML o un atributo. Por ejemplo, `<Amount currency="USD"> 10.00 </Amount>`. La moneda se guarda como un atributo y la cantidad de divisa (10.00), como un elemento. Los datos de envío de un formulario adaptable no tienen atributos, solo tienen elementos. Por lo tanto, cuando un formulario basado en XFA se convierte en formulario adaptable, los datos de envío de formulario adaptable contienen un elemento para cada atributo. Por ejemplo,

   ```css
      {
         "Type": "Principal",
   
         "Amount": "10.00",
   
         "currency": "USD"
      }
   ```

1. Haga clic en **[!UICONTROL Create]**. Se crea la configuración de la nube. Su instancia de AEM Forms está lista para convertir los formularios heredados a formularios adaptables.

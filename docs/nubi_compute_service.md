# Nubi Compute Service
![](https://www.nubi2go.com/static/e1cc3940146d9b2fdf055b976e775ea0/7640e/computer_service_282.webp)

Nubi Compute Service ([NCS](https://nubi2go.com/services/nubi_compute_service)) es un servicio de máquinas virtuales en la nube.

## Crear un servidor NCS
1. Accedé al [Portal](https://portal.nubi2go.com)
2. Seleccioná **"Servicios"** -> **"Contratar Nuevos Servicios"**
![](assets/ncs-screen1-light.png)
3. Seleccioná [Nubi Compute Service](https://portal.nubi2go.com/index.php?rp=/store/nubi-compute-service)
4. Elegí el tamaño de máquina virtual
![](assets/ncs-screen2-light.png)
   5. Configurá:
      * Imagen
      * Tamaño de disco
      * Red
      * Política de backup
      * IP Pública
      * Nombre
   ![](assets/ncs-screen3-light.png)
6. Una vez creado estará disponible en el área de [Servicios](https://portal.nubi2go.com/clientarea.php?action=services)

## Acceso a servidores NCS Linux
1. Obtené la IP pública o la IP privada en caso de acceder por VPN
![](assets/ncs-screen4-light.png)
2. Descargá la clave de SSH
![](assets/ncs-screen5-light.png)
3. Accedé al servidor por SSH
=== "Desde Windows"
    1. Instalá Putty, si es que no lo tenés
    2. Abrí PuttyGen y seleccioná **"Load"**
    ![](assets/ncs-screen6.png)
    3. Seleccioná **"All Files"** y la clave de SSH
    ![](assets/ncs-screen7.png)
    4. Seleccioná **"Save private key"** para guardar el archivo en formato **.ppk**
    ![](assets/ncs-screen8.png)
    5. Abrí Putty y cargá la clave de SSH en **"Connection"** -> **"SSH"** -> **"Auth"**
    ![](assets/ncs-screen9.png)
    6. Colocá **usuario@ip** y seleccioná **"Open"** para conectarte
    ![](assets/ncs-screen10.png)
   
=== "Desde Linux"
    1. Configurá los permisos del archivo
    ``` sh
    chmod 400 key-000218-62s2-rmd4-9g28-28b55bd2b126.txt
    ```
    2. Accedé por SSH al servidor:
    ``` sh
    ssh -i key-000218-62s2-rmd4-9g28-28b55bd2b126.txt ubuntu@190.183.63.121
    ```


!!! nota 
         El usuario default para Ubuntu es ubuntu, pero varía según la distribución.

## Acceso a servidores NCS Windows
1. Obtené la IP pública o la IP privada en caso de acceder por VPN

    ???+ warning "Nota"
        En este ejemplo se accede con IP pública por simplicidad, pero no recomendamos acceder por escritorio remoto con IP pública. Te recomendamos configurar una VPN.

2. Accedé a la consola web
![](assets/ncs-screen11-light.png)
3. Configurá región, lenguaje y teclado
![](assets/ncs-screen12.png)
4. Aceptá los terminos de licencia
![](assets/ncs-screen13.png)
5. Poné una contraseña fuerte para el administrador

    ???+ warning "Nota"
        En este ejemplo es un Windows Server 2016 en inglés, por lo que el usuario es "Administrator". Si es un Windows en español es "Administrador".

    ![](assets/ncs-screen14.png)
6. Esperá hasta que termine de configurar el Windows y estés acá:
   ![](assets/ncs-screen15.png)
7. Accedé al servidor por escritorio remoto
=== "Desde Windows"
    1. Abrí Microsoft Terminal Services Client (mstsc)
    ![](assets/ncs-screen16.png)
    2. Poné la IP del servidor en **"Computer"** y seleccionar **"Connect"**
    ![](assets/ncs-screen17.png)
    3. Poné las credenciales del usuario administrador
    ![](assets/ncs-screen18.png)
    4. Listo, ya estás conectado al servidor!
    ![](assets/ncs-screen19.png)
=== "Desde Linux"
    1. Instalá Remmina, si es que no lo tenés
    2. Abrí Remmina y seleccioná **(+)**
    ![](assets/ncs-screen20.png)
    3. Poné la IP del servidor, las credenciales de administrador y seleccioná **"Connect"**
    ![](assets/ncs-screen21.png)
    4. Listo, ya estás conectado al servidor!
    ![](assets/ncs-screen22.png)

## Grupo de seguridad
Cada servidor se crea con un grupo de seguridad, que son reglas de firewall a nivel máquina virtual. Por defecto, todo el tráfico de salida está habilitado y el tráfico entrante solo ICMP, SSH y RDP.

Para acceder a las reglas del grupo de seguridad, entrá a **"Grupos de Seguridad"**:
![](assets/ncs-screen23-light.png)

Para agregar una nueva regla, seleccioná **"Agregar Regla"**:
![](assets/ncs-screen24-light.png)


## Volúmenes FBS
Podés conectar volumenes [FBS](https://nubi2go.com/services/flexible_block_storage) que tengas contratados a un servidor NCS. Para ver como hacerlo, entrá a la [documentación de FBS](https://nubi2go.com/docs/flexible_block_storage/)

## Resize
Podés cambiar el tamaño de un servidor NCS en cualquier momento, según lo requieras.

???+ warning "Nota"
    Esta acción va a reiniciar el servidor.

1. En la sección **"Acciones del Servidor"** seleccioná **"Redimensionar"**
![](assets/ncs-screen25-light.png)
2. Elegí el nuevo tamaño y seleccioná **"Aceptar"**
![](assets/ncs-screen26-light.png)
3. Una vez que se termine de ejecutar la acción, en la sección **"Detalles del Servidor"** vas a ver el nuevo tamaño.
![](assets/ncs-screen27-light.png)

## Backups

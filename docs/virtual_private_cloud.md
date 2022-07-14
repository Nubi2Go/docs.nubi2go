# Virtual Private Cloud
![](https://www.nubi2go.com/static/2399084848c107e34eebe6e2331358ca/c47b5/vpc-intro_icon.webp)

[vpc-screen1]: assets/vpc-screen1-light.png
[vpc-screen2]: assets/vpc-screen2-light.png
[vpc-screen3]: assets/vpc-screen3.png
[vpc-screen4]: assets/vpc-screen4.png
[vpc-screen5]: assets/vpc-screen5-light.png
[vpc-screen6]: assets/vpc-screen6-light.png
[vpc-screen7]: assets/vpc-screen11-light.png
[vpc-screen8]: assets/vpc-screen12-light.png
[vpc-screen9]: assets/vpc-screen9-light.png
[vpc-screen10]: assets/vpc-screen7-light.png
[vpc-screen11]: assets/vpc-screen8-light.png
[vpc-screen12]: assets/vpc-screen10-light.png

Virtual Private Cloud ([VPC](https://nubi2go.com/services/vpc)) representa un servicio de redes privadas, virtuales y aisladas dentro del entorno en la nube.
Las redes se utilizan para segmentar conjuntos de servidores NCS con la posibilidad de unirlos de forma segura a través de un [Cloud Firewall](https://nubi2go.com/services/cloud_firewall_and_vpn).

Las máquinas virtuales dentro de la misma red tienen IPs privadas del mismo segmento (subnet) y tienen comunicación por capa 2 entre sí.

Las máquinas virtuales de diferentes redes, tienen IPs privadas de distinto segmento y para comunicarse, necesitan un router o un firewall, conectado a ambas redes.

## Tipos de VPCs
### Directa a internet
Una VPC puede estar directamente conectada a internet, lo que implica que las máquinas virtuales dentro de esa red pueden recibir Floating IPs y tener navegación al instante.

!!! nota
        Una Floating IP es una IP pública que está asignada a una máquina virtual y le brinda acceso a internet sin tener que configurar una placa de red adicional en el sistema operativo.

[![vpc-screen3]][vpc-screen3]

Para las máquinas virtuales que son accecibles directamente desde internet, disponés de un recurso de nube para darles seguridad: Security Groups.

!!! nota
        Un Security Group es un conjunto de reglas de firewall que se pueden aplicar a nivel máquina virtual.

### Detrás de firewall
Una VPC puede estar detrás de un firewall virtual y las máquinas virtuales navegan a través del firewall, quien tiene una o más IPs públicas.
Varias VPCs, pueden estar detrás del mismo firewall, para que sus recursos puedan comunicarse de forma segura, con las reglas de seguridad requeridas.

!!! nota
        Las máquinas virtuales dentro de este tipo de red, no pueden recibir Floating IPs.

[![vpc-screen4]][vpc-screen4]

Además, tenés la posibilidad de configurar túneles sitio a sitio y conexión VPN para usuarios, por ejemplo: Open VPN.

## VPC default del proyecto
Todos los proyectos tienen una VPC default, que se crea al momento de contratar el primer [servidor NCS](/docs/nubi_compute_service/#crear-un-servidor-ncs) o el primer Cloud Firewall.

!!! nota
        Si creás primero un servidor NCS la red por defecto va a ser de tipo **"Directa a internet"**.

        Si creás primero un Cloud Firewall la red por defecto va a ser de tipo **"Detrás de firewall"**.

Una vez que tenés disponible la red default, podés crear más servidores en dicha red, o crear nuevas redes.

**Ver la red por defecto:**

1. Accedé al [Portal](https://portal.nubi2go.com/)
2. Seleccioná [Virtual Private Cloud](https://portal.nubi2go.com/vpc.php)
   [![vpc-screen1]][vpc-screen1]
3. Podés visualizar la red por defecto
   [![vpc-screen2]][vpc-screen2]


## Crear una VPC
1. Accedé al [Portal](https://portal.nubi2go.com/)
2. Ingresá a [Virtual Private Cloud](https://portal.nubi2go.com/vpc.php)
3. Seleccioná **"Crear VPC"**

=== "Directa a internet"

    1. Se crea una VPC, para que las máquinas puedan tomar Floating IPs directamente
    [![vpc-screen5]][vpc-screen5]
    2. Listo, ya podes crear máquinas que salgan directo a internet en esa red
    [![vpc-screen6]][vpc-screen6]

=== "Detrás de firewall nuevo"

    1. Se crea una VPC, para luego crear un firewall que quede como gateway de esa red
    [![vpc-screen7]][vpc-screen7]
    2. Listo, seleccioná **"Firewall Creation Pending"** para crear un firewall para esa red
    [![vpc-screen8]][vpc-screen8]
    3. Luego de crear el firewall, podés ver su interfaz en la red creada
    [![vpc-screen9]][vpc-screen9]

=== "Detrás de firewall existente"

    1. Se crea una VPC, detrás de un firewall ya existente
    [![vpc-screen10]][vpc-screen10]
    2. Podés ver la red creada
    [![vpc-screen11]][vpc-screen11]
    3. Podés ver en el firewall, que se agregó una interfaz adicional en esa red
    [![vpc-screen12]][vpc-screen12]
    
## Cambiar tipo de VPC
Para pasar de una VPC de tipo **"Directa a internet"** al tipo **"Detrás de firewall"**, creá un nuevo Cloud Firewall en la red que querés cambiar.
Esta acción va a colocar al nuevo firewall como default gateway de esa red, tomando las IPs públicas de las máquinas virtuales de esa red y eligiendo una de ellas.
Las máquinas virtuales conservan sus IPs privadas.
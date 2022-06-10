# Nubi Monitoring Service
![](https://www.nubi2go.com/static/25ca25d9144991474734558c02f8453b/4ecad/bar-graphics.webp)

  [nms-screen1]: assets/nms-screen1.png
  [nms-screen2]: assets/nms-screen2.png
  [nms-screen3]: assets/nms-screen3.png
  [nms-screen4]: assets/nms-screen4.png
  [nms-screen5]: assets/nms-screen5.png
  [nms-screen6]: assets/nms-screen6.png
  [nms-screen7]: assets/nms-screen7.png
  [nms-screen8]: assets/nms-screen8.png
  [nms-screen9]: assets/nms-screen9.png
  [nms-screen10]: assets/nms-screen10.png
  [nms-screen11]: assets/nms-screen11.png
  [nms-screen12]: assets/nms-screen12.png
  [nms-screen13]: assets/nms-screen13.png
  [nms-screen14]: assets/nms-screen14.png
  [nms-screen15]: assets/nms-screen15.png
  [nms-screen16]: assets/nms-screen16.png
  [nms-screen17]: assets/nms-screen17.png
  [nms-screen18]: assets/nms-screen18.png
  [nms-screen19]: assets/nms-screen19.png
  [nms-screen20]: assets/nms-screen20.png
  [nms-screen21]: assets/nms-screen21.png
  

Nubi Monitoring Service ([NMS](https://www.nubi2go.com/services/nubi_monitoring_service)) es un servicio de monitoreo en tiempo real e histórico sobre los recursos de [Nubi Compute Service](https://nubi2go.com/docs/nubi_compute_service) (NCS). 
El servicio consta de un agente que corre en tu servidor, una base de datos que almacena las métricas y unos paneles de visualización. 
NMS está soportado tanto para Windows como para Linux, y todos los servidores NCS tienen incluído el plan básico gratis con 15 días de retención.

!!! note
	El agente no recaba información sensible ni confidencial sobre el servidor, únicamente métricas sobre el uso de distintos recursos. 

## Instalar el agente
Para que NMS funcione, es necesario que el agente esté corriendo en tu servidor. Para instalarlo:

1. Accedé al [Portal](https://portal.nubi2go.com)

2. Seleccioná "Start" en [Nubi Monitoring Service](https://portal.nubi2go.com/nubi-monitoring-service.php)
[![nms-screen1]][nms-screen1]


3. Instalá el agente así:

	=== "Linux"
		Copiá el comando que figura a la **izquierda** y correlo en una terminal del servidor 
		
		[![nms-screen2]][nms-screen2]

		(Para más info sobre cómo entrar por SSH a tu servidor hacé click [acá](https://nubi2go.com/docs/nubi_compute_service#acceso-a-servidores-ncs-linux))
	
	=== "Windows"
		Copiá el comando que figura a la **derecha** y correlo en un cmd como administrador 
		
		[![nms-screen3]][nms-screen3]

		(Para más info sobre cómo entrar por Escritorio Remoto a tu servidor hacé click [acá](https://nubi2go.com/docs/nubi_compute_service#acceso-a-servidores-ncs-windows))


4. Repetí el procedimiento para cada servidor que vaya a tener monitoreo. 

## Verificar que el agente se esté ejecutando
=== "Linux"
	1. Accedé al servidor por SSH o consola
	2. Corré:
	``` sh
	sudo systemctl status grafana-agent
	```
	3. Verificá que el servicio esté corriendo
	[![nms-screen4]][nms-screen4]

=== "Windows"
	1. Accedé al servidor por RDP o consola
	2. Apretá "Control + R" (run), escribí "services.msc" y entrá
	[![nms-screen5]][nms-screen5]
	3. Busca el servicio "Grafana Agent" y asegurate que esté corriendo
	[![nms-screen6]][nms-screen6]


## Acceder a Nubi Monitoring Service
1. Accedé al [Portal](https://portal.nubi2go.com)
2. Seleccioná "Start" en [Nubi Monitoring Service](https://portal.nubi2go.com/nubi-monitoring-service.php)
[![nms-screen1]][nms-screen1]
3. Hacé click en "monitor.nubi2go.com/dashboards" 
[![nms-screen7]][nms-screen7]
4. En el login de NMS, hacé click en "Sign in with Nubi2Go"
[![nms-screen8]][nms-screen8]
5. En caso de no estar autenticado, ingresá tus credenciales del Portal
[![nms-screen9]][nms-screen9]
6. Autoriza a la aplicación y continuá
[![nms-screen10]][nms-screen10]
7. En el home tendrás los dashboards de Windows o Linux, dependiendo del servidor que desees ver. 
[![nms-screen11]][nms-screen11]

## Visualizar servidores

Si tenés más de un servidor con el mismo sistema operativo, accedé al dashboard que le correponda (Linux o Windows) 

=== "Linux"
	1. Accedé a tu consola de NMS ([explicación acá](#acceder-a-nubi-monitoring-service))
	
	2. Elegí "Linux Nubimon"	
	[![nms-screen12]][nms-screen12]
	3. Podés elegir el servidor desplegando la variable "Host:" 
	[![nms-screen13]][nms-screen13]
=== "Windows"
	1. Accedé a tu consola de NMS ([explicación acá](#acceder-a-nubi-monitoring-service))
	
	2. Elegí "Windows Nubimon"
	[![nms-screen14]][nms-screen14]
	3. Podés elegir el servidor desplegando la variable "Instance"
	[![nms-screen15]][nms-screen15]
	
## Diferencias entre Basic y Full

La versión Full cuenta con 1 año de retención, a diferencia de la versión Basic que tiene 15 días. Adicionalmente, la versión Full muestra múltiples datos adicionales, ideales para equipos de infraestructura o desarrolladores que requieren conocer detalladamente el comportamiento de su aplicación dentro de Nubi2Go para planificar usos, encontrar cuellos de botella o hacer Troubleshooting.

### Linux :fontawesome-brands-linux:

El NMS Full para Linux tiene +70 paneles adicionales en comparación con el Basic

Ejemplo de dashboard Linux Nubimon **Basic**:
[![nms-screen16]][nms-screen16]

Ejemplo de dashboard Linux Nubimon **Full** (notar la cantidad de paneles adicionales que hay):
[![nms-screen18]][nms-screen18]

Algunos paneles de Linux Nubimon **Full** relacionados a la memoria y el acceso a disco:
[![nms-screen19]][nms-screen19]

### Windows :fontawesome-brands-windows:

El NMS Full para WIndows tiene +10 paneles adicionales en comparación con el Basic

Ejemplo de dashboard Windows Nubimon **Basic**: 
[![nms-screen17]][nms-screen17]

Dashboard Windows Nubimon **Full** (primera parte):
[![nms-screen20]][nms-screen20]

Dashboard Windows Nubimon **Full** (primera parte):
[![nms-screen21]][nms-screen21]


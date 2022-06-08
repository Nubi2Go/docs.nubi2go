# Bienvenido a Nubi2Go Docs

:material-tools: En este sitio se encuentra la documentación técnica sobre todos los servicios de Nubi2Go, así como guías, recomendaciones e integraciones.


## Cómo usar esta documentación   :octicons-book-24:

Estas guías contienen instrucciones paso a paso para realizar tareas comunes que podés llegar a necesitar. Para eso, vas a encontrar secciones así:

```sh
echo "hola usuario" | grep "usuario" >> usuario.txt
```

Esa sección es un fragmento de código o comandos que podés copiar directamente haciendo click en el ícono ":material-content-copy:". ¡Probalo!


También vas a encontrar secciones así:
=== "Para Windows - cmd"

	```cmd
	netstat -a -b | findstr "443"
	```

=== "Para Windows - PowerShell"
	```powershell
	Get-Process -Id (Get-NetTCPConnection -LocalPort 443).OwningProcess
	```

=== "Para Linux"
	```bash
	ss -tulpn | grep 443
	```

En este caso, hay varias maneras de hacer lo mismo y hasta hay dos opciones para el mismo sistema operativo. Por eso, dividimos los casos. ¡Probá entrar a cada título!



## ¿Encontraste un error?   :octicons-bug-24:

Todo nuestro sitio de Nubi2Go Docs está público. Si encontraste algo que está mal o requiere revisión, por favor, [abrinos un issue](https://github.com/Nubi2Go/docs.nubi2go/issues/new).



## ¿Necesitás soporte?

### ¡No te preocupes, estamos para ayudarte!   :material-lifebuoy:

Escribinos a [soporte@nubi2go.com](mailto:soporte@nubi2go.com) o abrinos un ticket [desde el Portal](https://portal.nubi2go.com/submitticket.php).


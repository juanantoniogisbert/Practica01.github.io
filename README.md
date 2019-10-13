## Crear y gestionar nuestro servidor de Git

Primeramente vamos a proceder a instalar [GitLab](https://about.gitlab.com/install/#ubuntu) en nuestro sistema, en este caso como estamos trabajando con [Ubuntu](https://ubuntu.com/) instalaremos la versión para el mismo.

Con los siguientes comandos instalamos y configuramos la dependencias necesarias.

### 1. Instalar y configurar las dependencias necesarias

```markdown
$ sudo apt-get update
$ sudo apt-get install -y curl openssh-server ca-certificates
```

Instalamos Postfix para enviar correos electrónicos de notificación, despues en su configuracion podremos "sin configuracion" para luego poner nuestra direccion en localhost.

```markdown
$ sudo apt-get install -y postfix
```

### Agregar el repositorio de paquetes de GitLab e instalar los paquetes

El siguente paso es añadir los repositorios de GitLab.
```markdown
curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh | sudo bash
```

En el siguiente comando podremos nuestra direccion de localhost para poder accerder atraves del navegador.

```markdown
$ sudo EXTERNAL_URL="http://localhost:4006" apt-get install gitlab-ee
```

Una vez realiza esta instalacion en nuestro navegadores escribiremos "http://localhost:4006" 

![Alt text](images/captura1.png?raw=true "Title") 

Despues vamos siguiendo los pasos hasta que accedemos a GitLab.

![Alt text](images/captura2.png?raw=true "Title")

### Realizar labores de administración inicial como por ejemplo:

- Cambiar el puerto de acceso.

Para cambiar el puerto de acceso tenemos que camviar esta linea "external_url 'http://localhost:4004'" para ello tendremos que ir al siguiente fichero y modificarlo.

```markdown
$ sudo -e /etc/gitlab/gitlab.rb
```

despues tendremos que hacer el siguiento comando para reconfigurar.

```markdown
$ sudo gitlab-ctl reconfigure
```

![Alt text](images/captura3.png?raw=true "Title")

- Impedir que usuarios nuevos puedan modificar su identificador.
<!------------------------------------------------------------------------------------------------->

- Modificar el tiempo de expiración de la sesión.

Por defecto el tiempo esta en 60000 segundos nostros vamos a cambiarlo a 60 segundos para ello editos el siguiente fichero y modificamos la siguiente linea:

```markdown
$ sudo nano /etc/gitlab/gitlab.rb
postgresql['idle_in_transaction_session_timeout'] = "60"
```
![Alt text](images/captura4.png?raw=true "Title")

### Detallar ejemplos de procesos (vía llamadas a la API) como:

- Alta, modificación y borrado de usuarios.
- Bloqueo/desbloqueo de usuarios.
- Establecer usuario como administrador.
- Creación de proyectos.


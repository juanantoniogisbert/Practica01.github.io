## Crear y gestionar nuestro servidor de Git

Primeramente vamos a proceder a instalar [GitLab](https://about.gitlab.com/install/#ubuntu) en nuestro sistema, en este caso como estamos trabajando con [Ubuntu](https://ubuntu.com/) instalaremos la versión para el mismo.

Con los siguientes comandos instalamos y configuramos la dependencias necesarias.

```markdown
$ sudo apt-get update
$ sudo apt-get install ca-certificates curl openssh-server postfix
```
### Repositories en GitLab

El siguente paso es añadir los repositorios de GitLab.
```markdown
$ curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh | sudo bash
```

<!---------------------CAPTURA1----------------------------->

Ahora, descargamos el script de GitLab que agregará los repositorios a nuestro sistema y lo ejecutamos.
```markdown
$ curl -LO https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh
$ sudo bash /tmp/script.deb.sh
```

<!---------------------CAPTURA2----------------------------->


Una vez terminado estos dos pasos anteriores porcedemos a instalar GitLab.
```markdown
$ sudo apt-get install gitlab-ce
```
<!---------------------CAPTURA3----------------------------->

El siguiente paso vamos a revisar que nuestro cortafuegos no bloquee las conexión de GitLab.

Si en la salida nos dice que no está inactivo, no debemos hacer nada más pues no está bloqueando nada. Si está activo, debemos asegurarnos de que el servicio SSH y los puertos 80 y 443 estén permitidos.
```markdown
$ sudo ufw status
$ sudo ufw allow http
$ sudo ufw allow https
$ sudo ufw allow OpenSSH
```
<!---------------------CAPTURA4----------------------------->

Una vez comprobado esto, ya podemos proceder a configurar GitLab. 
```markdown
$ sudo nano /etc/gitlab/gitlab.rb
```
Aquí vamos a buscar external_url y pondremos el nombre del dominio o IP de la máquina donde lo hemos instalado

<!---------------------CAPTURA5----------------------------->

En caso de que hayamos especificado un dominio, vamos a buscar y editar de la siguiente forma:
```markdown
letsencrypt['enable'] = true
letsencrypt['contact_emails'] = ['mi@dominio.com']
```

Una vez terminado, salimos y vamos a reconfigurar GitLab:
```markdown
$ sudo gitlab-ctl reconfigure
```












```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/juanantoniogisbert/Practica01.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

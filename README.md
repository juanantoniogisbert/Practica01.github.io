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

<!----CAPTURA1-------->

![Alt text](images/captura1.png?raw=true "Title") 












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

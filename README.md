# Automatización Jenkins Pipeline con Ansible usando Secret Manager

El objetivo de este repositorio es compartir un Jenkins Pipeline que permite  automatizar la configuración mediante **Ansible** una  instancia EC2 que se encuentra instalada y corriendo en AWS.

El código empleado en el Pipeline utiliza los comandos descriptos en el repositorio  https://github.com/ezequiellladoce/Ansible_EC2_con_Secret_Manager.git, en este ejemplo obtuvimos la clave privada almacenada en AWS Secrets Manager y la ip publica almacenada en con terraform backend en un Bucket S3.-

## Pre-requisitos 📋

- JENKINS SERVER con los siguientes componentes instalados
  - TERRAFORM .12 o superior
  - AWS CLI
  - Ansible
- CUENTA FREE TIER AWS 
  
## Comenzando 🚀

### Preparamos el ambiente:

1) Creamos cuenta free tier en AWS  https://aws.amazon.com/
2) Creamos usuario AWS en la sección IAM con acceso Programático y permisos de administrador https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html  
3) En el servidor de Jenkis instalamos:
   1) Terrafom https://learn.hashicorp.com/tutorials/terraform/install-cli
   2) AWS CLI https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html
   3) Configuramos el AWS CLI https://docs.aws.amazon.com/polly/latest/dg/setup-aws-cli.html 
   4) Ansible https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-ubuntu
   5) Jenkins https://www.jenkins.io/doc/book/installing/linux/
   6) Terraform plugin https://medium.com/appgambit/terraform-with-jenkins-pipeline-439babe4095c
   7) CloudBees AWS Credentials https://plugins.jenkins.io/aws-credentials/

## Despliegue 📦

### Consideraciones Iniciales

  - Para la realización de este despliegue tenemos ya desarrollado y probado el código terraform en git.
  - Verificamos que el Jenkins tenga instado el plugin te terraform y este correctamente configurado https://medium.com/appgambit/terraform-with-jenkins-pipeline-439babe4095c
  - Configuramos las claves AWS en Jenkins https://www.cyberark.com/resources/threat-research-blog/configuring-and-securing-credentials-in-jenkins

### Creamos el pipeline

  - Creamos una Nueva Tarea / Pipeline
  - Vamos a la sección pipeline
  - En Pipeline elegimos:
    - Definition : Pipeline script from SCM
    - SCM: GIT
    - Repository URL:  https://github.com/ezequiellladoce/JenkinsFile_for_Ansible.git
    - Credentials : none
    - Branch Specifier (blank for 'any') : */main
    - Ansible_config.jenkinsfile
    - Guardamos 
  
### Construimos el Job





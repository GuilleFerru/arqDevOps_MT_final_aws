# Proyecto DevOps - Infraestructura en AWS

Este proyecto implementa una infraestructura automatizada en AWS utilizando **Terraform** para el aprovisionamiento de recursos y **Ansible** para la configuración de servicios clave sobre una instancia EC2.

## Descripción General

La infraestructura creada en AWS incluye una instancia EC2 sobre la cual se instalan los siguientes servicios mediante **Ansible**:

- **Jenkins**: Para la gestión de pipelines de CI/CD.
- **SonarQube**: Para el análisis de la calidad de código.
- **Artifactory**: Para la gestión de artefactos.

## Estructura del Proyecto

La estructura principal del proyecto incluye los siguientes archivos y carpetas:

- **ansible/**: Contiene los playbooks de Ansible para la instalación y configuración de Jenkins, SonarQube y Artifactory.
- **jcasc.yaml**: Archivo de configuración para Jenkins Configuration as Code (JCasC).
- **plugins.txt**: Lista de plugins requeridos para Jenkins.
- **provider.tf**: Define el proveedor de AWS para Terraform.
- **resources.tf**: Contiene la definición de los recursos de AWS, como la instancia EC2, incluyendo:
    - **Instancias EC2**: Se crea una instancia EC2 para alojar los servicios de Jenkins, SonarQube y Artifactory. Se especifica el tipo de instancia, la imagen AMI y las claves SSH necesarias para el acceso.
    - **Grupos de seguridad**: Se configuran reglas de seguridad para permitir el acceso a los puertos necesarios:
        - **Puerto 8080**: Para Jenkins.
        - **Puerto 9000**: Para SonarQube.
    - **Puerto 8081**: Para Artifactory.
    - **Red**: Si es necesario, se definen recursos de red como subredes o VPC.
- **variables.tf**: Almacena las variables utilizadas por Terraform para parametrizar la infraestructura.

## Configuración

1. **Terraform**: Utiliza **Terraform** para crear la infraestructura en AWS, que incluye la creación de una instancia EC2, junto con la configuración de red y seguridad necesarias.

   ```bash
   terraform init
   terraform apply -auto-approve
```
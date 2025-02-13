# Hosting Estático en AWS con S3 y CloudFront

## Descripción del Proyecto
Este proyecto implementa un sitio web estático en AWS utilizando **Amazon S3** para el almacenamiento de archivos y **CloudFront** como CDN para mejorar la entrega global con HTTPS. La infraestructura se despliega automáticamente con **AWS CloudFormation**.

## Arquitectura
![Arquitectura del Proyecto](ruta-a-tu-imagen-diagrama.png)

## Servicios Utilizados
- **Amazon S3**: Almacenamiento de archivos y configuración de hosting estático.
- **AWS CloudFront**: CDN para mejorar el rendimiento y seguridad con HTTPS.
- **AWS CloudFormation**: Automatización de la infraestructura.

## Requisitos Previos
- Tener configurada la **CLI de AWS** con un perfil autorizado.
- Contar con una cuenta de AWS activa.

## Pasos de Implementación
1. **Descargar el archivo YAML** de CloudFormation desde este repositorio.
2. **Ejecutar el siguiente comando** en la terminal para desplegar la infraestructura:
   ```bash
   aws cloudformation create-stack --stack-name HostingEstaticoS3 \
     --template-body file://s3-cloudfront-hosting.yaml \
     --capabilities CAPABILITY_NAMED_IAM
   ```
3. **Esperar unos minutos** hasta que la infraestructura se cree correctamente.
4. **Obtener las URLs de salida** desde la consola de AWS CloudFormation o ejecutar:
   ```bash
   aws cloudformation describe-stacks --stack-name HostingEstaticoS3 --query "Stacks[0].Outputs"
   ```

## Subir Archivos al Bucket S3
Para que el sitio web funcione, es necesario subir los archivos HTML al bucket S3:
```bash
aws s3 cp index.html s3://nombre-del-bucket --acl public-read
aws s3 cp error.html s3://nombre-del-bucket --acl public-read
```

## Acceder al Sitio Web
Una vez completado el despliegue, puedes acceder al sitio web mediante la URL proporcionada por CloudFront:
```bash
https://xxxxxx.cloudfront.net
```

## Conclusión
Este laboratorio muestra cómo desplegar de manera automatizada un hosting estático en AWS con S3 y CloudFront. En futuros pasos, se podrá agregar un dominio personalizado con **Route 53** y mejorar la seguridad con certificados SSL personalizados.

---
📌 **Autor**: Codemaker 
📌 **Fecha**: [FEB, 2025]  


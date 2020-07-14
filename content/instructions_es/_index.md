---
title: "Instrucciones"
weight: 1
---

<br>
<br>
<br>
<br>
<br>

Completa los pasos en la siguiente lista y compartire tu CV con la mayor cantidad de gente posible en mi red. Echa un vistazo a las FAQ para entender mejor por que esta lista especificamente.

## 1. Certificación

  Tu CV debe incluir la certificación AWS [Cloud Practitioner](https://aws.amazon.com/es/certification/certified-cloud-practitioner/). AWS Cloud Practitioner es una certification de introduccion a Amazon Web Services, el proveedor cloud lider. Si tienes una certification de nivel superior a AWS Cloud Practitioner perfecto, pero no es necesario. Nada de trampas! Incluye el codigo de validacion que AWS emite con la certificacion. El examen cuesta $100 US y se puede hacer on-line desde casa. Si el coste del examen es una barrera dimelo y vere si puedo echar una mano. [A Cloud Guru ofrece recursos de ayuda para preparar el examen](https://acloud.guru/learn/aws-certified-cloud-practitioner).

## 2. HTML

  Tu CV debe estar escrito en formato [HTML](https://developer.mozilla.org/es/docs/Web/HTML). Nada de documentos de Word, nada de PDF. [Aqui hay un ejemplo de lo que quiero decir](https://codepen.io/emzarts/pen/OXzmym).

## 3. CSS

  Tu CV debe tener diseño via [CSS](https://www.w3schools.com/css/). Si lo tuyo no es el diseño no te preocupes, tampoco lo soy yo. No se trata de crear un diseño elegante, pero si queremos ver algo mas que HTML cuando carguemos la Web. Pero necesitamos ver algo más que HTML sin formato cuando abrimos la página web.

## 4. Web Site estática en Amazon S3

  Tu CV en HTML debe debe desplegarse on-line en forma de una [Web Site estatica en Amazon S3](https://docs.aws.amazon.com/es_es/AmazonS3/latest/dev/WebsiteHosting.html). Servicios como Netlify y GitHub Pages son geniales y normalmente los recomendaría para desplegar Web Sites personales estaticas, pero hacen las cosas muy abstractas para el proposito que tenemos entre manos. Usa Amazon S3.

## 5. HTTPS 

  El sitio web deberia usar [HTTPS](https://www.cloudflare.com/es-es/learning/ssl/what-is-ssl/) por seguridad. [Amazon CloudFront](https://aws.amazon.com/blogs/networking-and-content-delivery/amazon-s3-amazon-cloudfront-a-match-made-in-the-cloud/) te ayudara con esto.

## 6. DNS

  Utiliza un dominio DNS personalizado y dirigelo a la Distribución Web de CloudFront, de manera que se pueda acceder a tu CV con una URL parecida a mi-cv-website.com. Puedes usar [Amazon Route 53](https://aws.amazon.com/es/route53/) o cualquier otro proveedor de DNS para esto. El registro de un  dominio generalmente cuesta alrededor de diez euros anuales.

## 7. Javascript

  La Web de tu CV debe incluir un contador de visitas de manera que se muestre cuanta gente ha visitado la Web. Para esto te hara falta escribir un poco de codigo [Javascript](https://developer.mozilla.org/es/docs/Web/JavaScript). Este [tutorial](https://www.codecademy.com/learn/introduction-to-javascript) te situara en la dirección correcta.

## 8. Base de datos

  El contador de visitas deberá recuperar y actualizar el contador en una base de datos en algún sitio. Te recomiendo que uses [Amazon DynamoDB](https://aws.amazon.com/es/dynamodb/). (Utilica el modelo de pago on-demand para la base de datos y no pagarás prácticamente nada, a menos que almacenes o recuperes una cantidad de datos mucho mayor de lo requerido para este proyecto). [Aquí hay un gran curso gratuito sobre DynamoDB](https://linuxacademy.com/course/dynamo-db-deep-dive/).

## 9. API

  No accedas a DynamoDB directamente desde el código Javascript. En lugar de eso, crea una [API](https://medium.com/@perrysetgo/what-exactly-is-an-api-69f36968a41f) que acepte solicitudes desde tu Web y se comunique con la base de datos DynamoDB. API Gateway y Lambda de AWS son una buena solucion para lograr esto, y sera absoluta o practicamente gratis el uso requerido para este proyecto.

## 10. Python

  Vas a necesitar escribir un poco de código en la función Lambda; Esto se puede haer con Javascript, pero es una buena idea para el proyecto probar Python, un lenguaje común utilizado en programacion de backend y scripts, y la [libreria boto3 para AWS](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html). Aquí hay un buen [tutorial gratuito de Python](https://www.learnpython.org/).

## 11. Tests

  También debes incluir algunos tests para validar el código Python. [Aquí hay algunos recursos](https://realpython.com/python-testing/) para escribir buenos tests de Python.

## 12. Infraestructura como código

  No configures todos los recursos necesarios para la API (tabla de DynamoDB, API Gateway, la función Lambda) a mano haciendo clic en la consola de AWS. En lugar de eso, define los recursos en un [template SAM (Modelo de aplicación sin servidor) de AWS](https://aws.amazon.com/es/serverless/sam/) e impleméntalos usando la CLI de AWS SAM. Esto se llama ["infraestructura como código"](https://www.hashicorp.com/resources/what-is-infrastructure-as-code/) o IaC. Te ahorrara tiempo a largo plazo.

## 13. Control de codigo fuente

  No es ideal actualizar la API ni la Web haciendo llamadas desde tu portátil. Lo ideal es que el codigo de la API y la Web se actualicen automáticamente cada vez que hagas un cambio en el código. (Esto se denomina [integración y despliegue continuo, o CI / CD](https://help.github.com/en/actions/building-and-testing-code-with-continuous-integration/about-continuous-integration)). Crea un [repositorio privado en GitHub](https://docs.github.com/es/github/creating-cloning-and-archiving-repositories/creating-a-new-repository) para el código de la API que forma el back-end.

## 14. CI / CD (back end)

  Configura las [GitHub Actions](https://docs.github.com/es/actions/getting-started-with-github-actions/about-github-actions) de modo que cuando actualices la template SAM o el código Python, se ejecuten los tests de Python. Si pasan los tests, la aplicación SAM debería empaquetarse y desplegarse en AWS.

## 15. CI / CD (front end)

  Crea otro repositorio privado en GitHub para el código de la Web. Crea GitHub Actions de modo que cuando actualices el código de la Web, el S3 se actualice automáticamente. (Muy probablemente tambien debas [invalidar la caché de CloudFront](https://docs.aws.amazon.com/es_es/AmazonCloudFront/latest/DeveloperGuide/Invalidation.html) en el código de GutHub Actions). Importante: ¡NO almacenes credenciales de AWS en el control de codigo fuente! ¡Alguien con malas intenciones puede encontrarlos y usarlos contra ti!

## 16. Publicación de blog

  Finalmente, en el texto de su currículum, debes incluir in link a una breve publicación que describa algunas de las cosas que has aprendido mientras trabajabas en este proyecto. [Dev.to](https://dev.to/) es un gran lugar para publicar si no tienes tu propio blog.

Y esto es todo. Cuando hayas hecho todo esto, agregua mi usuario de GitHub [@forrestbrazeal](https://github.com/forrestbrazeal) como colaborador a tus repositorios. Si necesitas un trabajo en Cloud y has cumplido con las condiciones enumeradas anteriormente, te revisare personalmente el código, y despues hare todo el ruido posible sobre ti para cualquiera que quiera escuchar (¡incluso compartir su increíble publicación en el blog! )

Para obtener más información, puedes leer la [publicación original en el blog de Cloud Resume Challenge](https://forrestbrazeal.com/2020/04/23/the-cloud-resume-challenge/).

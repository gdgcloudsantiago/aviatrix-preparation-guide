# aviatrix-preparation-guide

Guía de preparación en español para la certificación ACE de la solución Multicloud de Aviatrix

# 1) Qué es Aviatrix

Apuntes tomados desde la documentación de Aviatrix: https://community.aviatrix.com/t/h7h3sta

Créditos Documentación Original: Nabeeha Ali - Solutions Engineer Intern at Aviatrix


Aviatrix es un software que provee una plataforma para la construcción de redes y seguridad en las nubes públicas.
Permite una implementación tanto simple como multinube.
Soporta AWS, Azure, GCP y OCI.
Pionero en la implementación de MCNA, Arquitectura de Red Multicloud.

MCNA promueve el Control y gestiona no solamente los componentes nativos de las nubes, sino componentes propios de Aviatrix.

Aviatrix posee un panel de control centralizado.

La seguridad es implementada mediante segmentación de red, encriptación, reglas de entrada y de salida y servicios de seguridad propios.

La Arquitectura es valida tanto para soluciones Cloud de simple región, Multi-región y soluciones MultiCloud y aplica para múltiples negocios, creando una abstracción para el usuario de todas las complejidades de los proveedores Cloud, siendo agnóstica a las nubes.

## Capas MCNA:

### Cloud Core: 

### Application Layer:

En este capa se implementa la aplicación, pudiendo estar en VPC o VNets dependiendo del proveedor Cloud y corriendo como instancias o VMs utilizando los componentes nativos de los proveedores Cloud.

### Global Transient Layer: 

Este es el punto principal para cada componente de esta arquitectura, permitiendo la inserción de servicios en la plataforma mediante el service insertion framework. Esta capa es la que provee alta disponibilidad, una red Multi cloud, encriptación de punta a punta, encriptación de alto rendimiento, dominios de seguridad Multi cloud y herramientas de telemetría para los equipos de operaciones.


### Cloud Security:

Esta capa se asegura de que las capas de aplicación, acceso y transito sean seguras. La capa de seguridad asegura conexiones seguras tanto para conexiones desde Onpremise a Cloud, conexiones de entrada, salida y entre nubes mediante encriptación y segmentación.


### Cloud Access: Cloud Ingress / Egress

Esta capa se asegura de que todos los componentes del negocio estén disponibles permitiendo un acceso seguro a empleados, socios, clientes y datacenters legados hacia la nube de una manera centralizada. 

### Cloud Operations:

Esta capa es la encargada de entregar visibilidad total de todas las otras capas mediante un panel de operaciones centralizado permitiendo realizar troubleshooting, entregando visibilidad y automatización.

En resumen, MCNA se entiende como una solución de arquitectura que permite administrar tanto soluciones de una sola nube o multinube de una manera distribuida y unificada mediante un panel de control centralizado.

### Panel de Control:

Aviatrix ofrece un panel de control que no requiere una base de conocimiento específico para su utilización el cual puede ser implementado mediante un asistente de instalación llamado Application Programming Interface o como Infraestructura como Código mediante Terraform.

El panel de control está basado en una aplicación de navegador que permite orquestar tanto los servicios nativas de las nubes como los sevicios propios de Aviatrix.

Este controlador centralizado también se encarga del despliegue de Aviatrix Gateway para multi-cloud, on premise y conexiones en los extremos.

Aviatrix además promueve la utilización de componentes nativos de las nubes extendiendo sus funcionalidades mediante Aviatrix Controller y Gateway.

### Aviatrix Gateway:

Se considera como un servicio de nodo para una simple nube o multinube.

La responsabilidad de este servicio es ofrecer rutas de transito, encriptación de alto rendimiento, control de ingreso y egreso, conectividad a los extremos, conexión con ambientes onpremise y el uso de soluciones de VPN.

### CoPilot:

CoPilot es una solución de Aviatrix que permite tener una visiblidad total de la operación en la red, permitiendo estar al tanto de cualquier problema en la red.

### Soporte Multicuentas:

Aviatrix permite la integración de las cuentas de los diferentes proveedores Cloud en su plataforma con el fin de tener un solo punto de acceso.

### Seguridad y Compliance:

Aviatrix permite manejar dominios de seguridad diferente tanto para ambientes de desarrolo y producción, además de conexión a VPC utilizando políticas específicas de conexión, habilitación de reglas de firewall basadas en tags, rangos de IP mediante notación CIDR, protocolos y puertos.

Además Aviatrix permite la extención del servicio de AWS GuardDuty con el fin de tomar acción proactiva de amenazas de seguridad a nivel de VPC.

# 2) Nube Pública y Redes:

Apuntes tomados desde la documentación de Aviatrix: https://community.aviatrix.com/t/q6hx19y/an-introduction-to-the-public-cloud-and-public-cloud-networking

Créditos Documentación Original: Nabeeha Ali - Solutions Engineer Intern at Aviatrix

### Nube Pública:

Datacenter gestionando por un proveedor Cloud como AWS, Azure, GCP, OCI donde la infraestructura es compartida por multiples clientes.

### Nube Privada:

La nuble privada con una capa de software que intenta replicar las funcionalidas de una nube pública pero utilizando una infraestructura propia y gestionada generalmente por el cliente.

### OnPremise:

Infraestructura propia gestionada generalmente cliente.

### Datacenter:

Lugar donde se encuentra la infraestructura tanto para soluciones OnPremise, de Nube Privada y Nube Pública.

### Región:

Los Datacenters se agrupan en regiones para entregar disponibilidad de servicio.

### Zona de Disponibilidad (Availability Zone):

Distintas ubicaciones de red separadas de forma que una falla evite la caida de otra zona.

# 3) Nube Pública y Redes:

Apuntes tomados desde la documentación de Aviatrix: https://community.aviatrix.com/t/x2hxjdv/public-cloud-networking

Créditos Documentación Original: Alizah Nauman - Aviatrix Employee

### OnPremise

Los despliegues de aplicaciones OnPremise eran lentos, por eso el equipo de DevOps comenzó con la iniciativa de mover sus cargas de trabajo a la nube.

### Reinventando las redes y la seguridad para los arquitectos en la nube

- Con VMware fue posible virtualizar los servidores, pero aún corrian onPremise. Esto hizo que los clientes comenzaran a moverse a la nube pero con un gap a nivel de arquitectura. Aviatrix con su solución de MCNA ayuda a desplegar aplicaciones en la nube.

### OnPremise, IaaS, PaaS, SaaS

- OnPremise: Toda la responsabilidad de hardware, software y operaciones son responsabilidad del usuario.

- IaaS: El usuario es responsable de correr máquinas virtuales y actualizar el Sistema Operativo, lo demás lo ve el proveedor Cloud.

- PaaS: El usuario gestiona la aplicación y los datos, lo demás lo ve el proveedor Cloud.

- SaaS: El usuario consume el servicio. Todo lo demás lo ve el proveedor Cloud.

### Nube Híbrida

- Conexión entre la nube y un datacenter onPremise.

### Principios de la Nube Pública

- La Nube pública es conocida por tener multiples regiones, poseer alta disponibilidad y ser confiable, aún así como todo tiene problemas algunas veces, pero los usuarios no tienen control ni visibilidad de estos problemas.

### Data Center

- Los proveedores cloud usan datacenter para almacenar sus servicios y recursos.

### Región

- Los Datacenters se agrupan en regiones y áreas geográficas para entregar una disponibilidad a nivel regional.

### Zona de Disponibilidad

- Distintas ubicaciones de la red del proveedor cloud que se encuentran separadas a nivel de ingeniería con el fin de evitar propagación de fallas.

### OnPremise V/S La Nube

- El concepto de red padre de la nube es la VPC (Virtual Private Cloud).

- La parte más importante de la VPC son las aplicaciones y máquinas virtuales.

- Las máquinas virtuales se pueden encontrar en diferentes subredes, es por eso que necesitan una entidad de routing.

- Algunos componentes de seguridad son facilitados, pero son muy primitivos.

- Las VPCs requiere poder enviar tráfico a internet.

- En caso de conectarse a un datacenter, es necesario una conexión privada.

- Limitaciones existentes: 

- Límite de 100 BGP route en AWS-TGW
- No existen controles de ruteo.
- No existe inserción de servicios
- Pobre visibilidad

# 4) AWS Networking 101:

Apuntes tomados desde la documentación de Aviatrix: https://community.aviatrix.com/t/h7hxphg/aws-networking-and-security-101

Créditos Documentación Original: Nabeeha Ali Solutions Engineer Intern at Aviatrix

Cómputo: EC2

Control de Acceso: IAM

Red: VPC (regional)

Seguridad: AWS Security Group

Storage: S3

Nube Híbrida: Direct Connect

DNS: Route 53

CDN: Cloud Front

Gateways:

- Internet Gateway
- Virtual Private Gateway
- NAT Gateway
- Transit Gateway
- VPN Gateway
- Customer Gateway
- Direct Connect Gateway

- Aviatrix permite gestionar y controlar el AWS TGW los cuales permiten remover el límite de routing
- Aviatrix toma la responsabilidad de la configuración inicial y de las futuras actualizaciones en las rutas.
- Permite simplificar el BGP mediante Direct Connect.
- Aviatrix entrega correciones de red y propaga las rutas OnPremise hacia los VPCs.

# 5) Azure Networking 101:

Apuntes tomados desde la documentación de Aviatrix: https://community.aviatrix.com/t/h7hxdf6/an-introduction-to-microsoft-azure

Créditos Documentación Original: Nabeeha Ali Solutions Engineer Intern at Aviatrix

Organización Top-Level: AD Tenant -> Suscripciones -> Resource Group

Red: VNET

Seguridad: Network Security Group

Gateways:

- VPN Gateway (Conexión mediante internet pública, debe ser desplegada en una Gateway Subnet, similar a VGW de AWS, en OnPremise existe el Network Gateway que es similar al GGW en AWS).

- Express Route Gateway (Conexión mediante enlace privado desde la nube a OnPremise)

Transit:

- ExpressRoute Edge Router
- Network Virtual Applicance (NVA)
- VNet Peering

Azure Virtual WAN: Solución propuesta por Microsoft para afrontar las limitantes de la solución nativa Transit.

# 6) GCP Networking 101:

Apuntes tomados desde la documentación de Aviatrix: https://community.aviatrix.com/t/h7hxb19/gcp-networking

Créditos Documentación Original: Alizah Nauman Aviatrix Employee

Organización: Organización -> Carpetas -> Proyectos -> Componentes.

VPC y routing es global a diferencia de AWS y Azure.

Opciones de conexión entre VPCs:

- Shared VPC
- VPC Network Peering

Gateway:

- VPN Gateway

Rutas:

- Rutas por defecto
- Subnet gateway

- Definidas por el usuario
- Static Routing
- Dynamic Routing

Transit:

No existe una solución nativa para interconectar VPCs.
VPC peering es lo más cercano.

Cloud Interconnect (Conexión desde la nube hacia onPremise)

# 7) Operaciones, Visibilidad y Resolución de Problemas en la Nube Pública:

Apuntes tomados desde la documentación de Aviatrix: https://community.aviatrix.com/t/q6hxbm1/operations-visibility-and-trouble-shooting-in-the-public-cloud

Créditos Documentación Original: Alizah Nauman Aviatrix Employee

### Desafíos enfrentados en la nube pública

- Data de evidencia
- Herramientas no familiares como ping, capturador de paquetes y trace route
- Caja negra
- Creación de un problema de soporte para tier-1 con IaaS
- Falta de jerarquías en la nube para seguridad, control y visiblidad
- Soporte Nivel 3 OnPremise se transforma en Sporte Nivel 1 en la nube necesitando soporte de ingenieros seniors de redes.
- Problemas con el crecimiento de la solución, volviendo la resolución de problemas más compleja.

### ¿Cómo Aviatrix soluciona estos problemas?

- Co-Pilot: Dashboard para Operaciones. (Disponibilida de Gateways, % de Gateways desplegados por nube, Visualización de Topología, )

- Flow IQ: (Categoriza y Filtra el Tráfico, Gráfico para revisar problemas específicos, Visualización mediante geo-localización)

- FlighPath: Resolución de Problemas mediante reportes.

-Capturador de Paquetes.

- Control de Acceso basado en Roles.

-Multi Nube y Multi Cuenta.

# 8) Funcionalidades de Aviatrix:

Apuntes tomados desde la documentación de Aviatrix: https://community.aviatrix.com/t/x2hxjd1/aviatrix-platform-component-feature-summary

Créditos Documentación Original: Alizah Nauman Aviatrix Employee

- Aviatrix Controller.
- Aviatrix Gateway. 
- Native Cloud Constructs.

- Características Principales de Aviatrix Controller:

- Solamente 1 controlador por red es necesario
- Puede ser desplegado en cualquier marketplace

- Controller
- Red Avanzada Multiregión y Multicloud
- Encriptación de alto rendimiento
- Site 2 Cloud/OnPrem
- Cloud WAN
- Smart SAML User VPN
- Ingress y Egress seguro
- FireNet (Red de Firewall)
- Herarmientas para la Operación: (Flight Path, Packet Capture, Trace Route, etc) 


# BONUS) Preguntas y Respuestas del Curso de Preparación Aviatrix ACE (No son las preguntas del examen):

Video Original del compilado de preguntas creado por Lokman Shrestha: https://www.youtube.com/watch?v=rRfeop2y_Ps

### ¿Cuál es el centro de gravedad del nuevo modelo de cómputo?

R: Nube Pública

### ¿Qué fue lo que generó un movimiento acelerado hacia la Nube Pública?

R: La necesidad de aumentar la velocidad en los despliegues

### ¿Si una aplicación es migrada a la Nube Pública, su cercanía con internet es?

R: Más cercana

### ¿Cuáles son los desafíos más comunes en la nube?

R:

- Falta de arquitecturas de referencia
- Falta de visibilidad y troubleshooting
- Falta de soporte multinube

### ¿Cómo ayuda Aviatrix a sus clientes en las Nubes Públicas?

R: Aviatrix es una plataforma multinube que permite la implementación de una arquitectura consistente y ofrecer tanto operaciones como visibilidad desde el primer día.

### ¿Cuál fue el grupo que inicio el movimiento hacia la nube?

R: DevOps

### ¿Cuando ocurre un problema de red, los equipos de DevOps generalmente pueden corregirlo sin las necesidad de solicitar ayuda al equipo de redes?

R: Falso

### ¿Un problema que los ingenieros de redes enfrentan en la nube que no exite en ambientes OnPremise es?

R: La gestión de cuentas y suscripciones

### ¿Cuando las organizaciones implementan sus soluciones en la nube, los proveedores cloud generalmente siguen el siguiente modelo?

R: Nosotros te entregamos las piezas y tu las utilizas para construir tus aplicaciones.


### ¿Pueden generalmente los proveedores cloud ayudar facilmente a sus clientes en despliegues multicloud?

R: Falso

### ¿Cuál es la definición de una solución PaaS?

R: Tu como cliente gestionas solamente la aplicación y la data.

### ¿Qué es una nube híbrida?

R: Una combinación entre una nube pública y una nube privada.

### ¿Cuál no es un componente válido de la nube?

R: Zona Geográfica

### ¿Es el concepto de Zona de Disponibilidad igual para todos los clientes en los ambientes cloud?

R: Falso

### ¿Existe actualmente un gap en la nube debido a que no existe un framework consistente entre redes y seguridad para soluciones multinube?

R: Verdadero

### ¿Que servicio más se parece al mundo OnPremise?

R: IaaS

### ¿Office 365 es un ejemplo de que servicio?

R: SaaS

### ¿Una región corresponde al mismo concepto que un datacenter para un proveedor cloud?

R: Falso

### ¿Cuando un proveedor cloud despliega una región, siempre existen distintas zonas de disponibilidad en esa región?

R: Falso

### ¿Una de las ventajas de las zonas de disponibilidad es?

R: Los recursos que se encuentren desplegados en zonas de disponibilidad pueden soportar un apagón de un datacenter.

### ¿Que servicio de AWS representa una máquina virtual?

R: EC2

### ¿Para conectar una VPC, AWS usa un router el cual los clientes deben configurar para permitir comunicaciones entre VPCs?

R: Falso

### ¿Qué servicio de AWS mejor representa tu red virtual?

R: VPC

### ¿Son las subnets de AWS un recurso global que se despliega mediante zonas de disponibilidad?

R: Falso

### ¿Qué componente de seguridad de AWS tiene un filtro stateless?

R: NACL

### ¿Los grupos de seguridad en AWS no pueden ser compartidos mediante VPCs a menos que estén en modo peering?

R: Verdadero

### ¿Cuál gateway no existe en AWS?

R: Virtual Network Gateway

### ¿Los Transient Gateway automatizan de forma total el routing?

R: Falso

### ¿En AWS, una conexión mediante Direct Connect puede terminar en cual de las siguientes opciones?

R: Direct Connect Gateway

### ¿Usando componentes nativos de AWS, cuál es el máximo ancho de banda que se puede lograr mediante un tunel IPSEC?

R: 1.25G

### ¿Existe algún límite en la cantidad de routes soportadas por AWS Transit Gateway?

R: Falso

### ¿Cuál es la diferencia entre las zonas de disponibilidad en Azure frente a otros proveedores?

R: Azure solamente tiene zonas de disponibilidad en algunas regiones.

### ¿Para qué sirven las Network Gateways?

R: Para implementar un termino de conexión híbrida para una VPN o Express Route.

### ¿Que componente de Azure se utiliza para agrupar items?

R: Resource Group

### ¿Cuál es el nivel más alto de organización en la estructura de Azure?

R: AD Tenant

### ¿Las subnets en Azure pueden ser creadas tanto públicas o privadas?

R: Falso

### ¿Algunos desafíos con la WAN Virtual de Azure como plataforma son?

R:

- No hay encriptación en la nube
- No hay una arquitectura multicloud
- No se soportan soluciones HUB de externos

### ¿Un ExpressRoute de Azure puede terminar en que componente?

R: 

- Express Route Gateway
- Virtual Network Gateway

### ¿Usar ExpressRoute hairpinning para trafico spoke to spoke es una opción recomendada para el transito en Azure?

R: Falso

### ¿Qué es NVA en Azure?

R: 

- Cualquier componente de terceros en el Azure Marketplace
- Network Virtual Appliance

### ¿Desafíos de usar NVA para una comunicación spoke to spoke en Azure incluyen?

R: 

- Definir la gestión de rutas a escala.
- SNAT es requerido para la simetría de tráfico

### ¿La conexión privada dedicada de GCP es llamada?

R: Cloud Interconnect

### ¿Todos los recursos en GCP son o Global o Regionales?

R: Falso

### ¿Una máquina virtual es un ejemplo de un recurso?

R: Un recurso Zonal

### ¿Una VPC es un ejemplo de un recurso?

R: Un recurso Global

### ¿Los recursos de GCP son organizados de acuerdo a que estructura?

R: Proyectos

### ¿GCP recomienda el despliege de multiples VPCs para manejar tus cargas de trabajo?

R: Falso

### ¿Que singnifica el concepto de Auto Mode en GCP?

R: Para una red son creadas subredes en cada región.

### ¿GCP soporta rutas dinámicas en la nube?

R: Verdadero

### ¿VPC peering en GCP permite que las VPC sean transitivas?

R: Falso

### ¿Puede un proyecto acceder a los recursos de otro proyecto en GCP mediante?

R: 

- Shared VPC
- VPC Peering

### ¿Cómo se llaman las redes virtuales en Oracle Cloud (OCI)?

R: VCN

### ¿Están las subredes de OCI atadas a un dominio de disponibilidad?

R: Falso

### ¿Cuantos DRGs puedes tener en una región OCI?

R: 5

### ¿Realizar overlapping de IPs está permitido cuando se realiza peering VCNs en OCI?

R: Falso

### En OCI es necesario especificar un XXXXX cuando se crea un recurso.

R: Comparment ID

### ¿En OCI es simple tener una visibilida completa y control de toda la red mediante la consola de OCI?

R: Falso

### ¿El partnership de redes entre Oracle y Azure está disponiblee en todas las regiones de OCI y Azure?

R: Falso

### Los Service Gateway entregan acceso XXXXX desde las VCNs hacia los servicios de Oracle.

R: Privado

### ¿La metadata de un IAM Tenancy está atado a XXXX?

R: home region

### ¿Usar los componentes nativos de redes de OCI te permite facilmente configurar una conexión segura con otros proveedores de nube y a escala?

R: Falso

### ¿Cuáles son los pilares principales del MCNA?

R: Cloud Core, Cloud Access, Cloud Operations.

### ¿La seguridad y la visibilidad son parte del MCNA?

R: Verdadero

### ¿Cuales son ejemplos de beneficios de tener una arquitectura de red multicloud?

R: 

- Tener un Panel de Datos Normalizado
- Tener un Panel de Control centralizado
- Tener un patrón replicable para los proveedores cloud.

### ¿Los desafíos más comunes de los clientes en la nube  son?

R:

- Construcción de Aplicaciones
- Lock In
- Caja negra

### ¿Cuál es el aspecto más importante de una red multicloud?

R: Transit

### ¿La función de la capa de operaciones incluye?

R: 

- Visibilidad Centralizada
- Control Centralizado
- Orquestación Centralizado

### ¿La capa core de MCNA entrega?

R: Panel de datos normalizado sobre nubes.

### ¿Con MCNA, la seguridad debe ser configurada por cada proveedor de nube para mantener la consistencia en el gobierno?

R: Falso

### ¿El acceso cloud en MCNA entrega acceso común a?

R:

- SDWAN
- Opciones de Direct Connect de los proveedores cloud
- VPN connectivity

### ¿El core principal del MCNA es?

R: Un framework de seguridad y redes multicloud para despliegues consistentes en las nubes.

### ¿Cuál de estas opciones describe de mejor manera las Transit Solutions de Aviatrix?

R: Solución construida usando Aviatrix IPSEC para encriptación por defecto con la opción de alto rendimiento.

### ¿Aviatrix Transit debe ser construido por cada nube y no soporta comunicación multicloud por defecto?

R: Falso

### ¿Cual es el desafío con la encriptación nativa en la nubes?

R:

- Los ambientes cloud no están nativamente encriptados.
- La encriptación nativa está limitada a 1.25G.
- Los túneles IPSEC están atados a un solo nucleo de cómputo. 

### ¿Cuáles son los componentes de la plataforma de Aviatrix?

R:

- Controller
- Gateway
- CoPilot

### ¿Por qué cloud IPSEC está limitado a 1.25G?

R: Las soluciones nativas implementa túneles utilizando solamente 1 core.

### ¿La solución de Aviatrix FQDN Egress Filter soporta tanto métodos distribuidos como centralizados de egreso?

R: Verdadero

### ¿Puede Aviatrix extender las funcionalidades de AWS Guard Duty para entregar aplicación de alertas?

R: Verdadero

### ¿Cuáles son las ventajas de Aviatrix Transit en la nube?

R:

- Encriptación de punta a punta
- Replicable entre nubes
- Visión y Control completo

### Con Aviatrix HPE (High Performance Encryption) los clientes pueden:

R:

- Aumentar la velocidad de encriptación en la nube.
- Aumentar la velocidad de encriptación entre nubes.
- Aumentar la velocidad de encriptación entre onPremise y la nube.

### ¿Aviatrix puede filtrar "partner route advertisements" mediante un proceso de aprobación de BGP?

R: Verdadero

### ¿Cuáles son los desafíos más comunes al implementar firewalls en la nube?

R:

- Mover las reglas desde OnPremise a la nube
- Las soluciones de firewall nativas son principalmente L4.
- El cliente tiene que configurar y gestionar el routing.

### ¿Cuanto rendimiento puede alcanzar Aviatrix Firenet?

R: sobre los 70G

### ¿Cuáles son algunas ventajas de la solución de Aviatrix Site to Cloud?

R:

- Soporte para NAT (Network Adress Translation)
- Soporte de túneles TCP y UDP
- Utiliza una plantilla para su configuración

### ¿Aviatrix Firenet puede orquestar el despliegue y routing de firewall, además del routing para VNET/VPC para implmenetación de NGFW?

R: Verdadero

### ¿La solución de User VPN no permite crear perfiles específicos de control de acceso?

R: Falso

### ¿Qué integración de terceros está disponible para Aviatrix User VPN?

R:

- DUO
- Okta
- AD
- SAML

### ¿Aviatrix Firenet requiere que los clientes usen Gateways en los spokes (radios) ya que no está soportado usando constructores nativos para transit (EJ: AWS TGW o Azure Peering) ?

R: Falso

### ¿Que funcionalidad de Aviatrix permite a los clientes agrupar VCP/VNETs con políticas de acceso comunes?

R: Security Domains

### ¿Puede Aviatrix Site 2 Cloud ser usado para soluciones IoT?

R: Verdadero

### ¿Qué problema soluciona Aviatrix Private S3?

R:

- Data exfiltration
- Acceso privado (solamente RFC1918) para buckets en S3 sin la necesidad de tener una dirección pública.

### ¿Es Aviatrix un provider de Terraform?

R: Verdadero

### ¿Aviatrix no puede entregar captura de paquetes en tráfico en vivo?

R: Falso

### ¿VCP tracker está solamente disponible para AWS?

R: Falso

### ¿Qué utiliza Aviatrix para el Controller HA en AWS?

R:

- Lamba Script
- S3 Bucket
- Autoscaling Group

### ¿Cómo facilita la resolución de problemas de conexión Flight Path?

R: Entrega una visualización basada en la fuente y el destino para resaltar problemas en las rutas.

### ¿Cuáles son algunos de los cambios operacionales que los clientes enfrentan en la nube?

R:

- Tier 3 se convierte en Tier 1 para resolución de problemas
- Visibilidad limitada en componentes nativos
- Falta de estándares en herramientas de resolución de problemas (ping, traceroute, etc)

### ¿Aviatrix Controller puede realizar auditoria de componentes para asegurarse que ninguna nueva ruta se agregue afectando al funcionamiento correcto de la red?

R: Verdadero

### ¿Herramientas de resolución de problema comunes como ping y traceroute pueden ser utilizadas utilizando Aviatrix Gateway?

R: Verdadero

### ¿Qué pasa cuando un componente necesita actualización?

R: Las actualizaciones no tienen impacto

### ¿Cuál de las siguientes afirmaciones es correcta?

R: Los clientes pueden lanzar un "single controller" e integrar multiples cuentas cloud para gestionar.

### ¿CoPilot debe ser desplegado en cada nube para obtener la visibilidad mediante todas las nubes?

R: Falso

### ¿La topología de Co-Pilot puede entregar?

R: 

- Opciones personalizadas de visualización 
- Etiqueta personalizada de recursos
- Diagnóstico de funciones desde gateways

### ¿Co-Pilot no entrega ninguna opción de geo-localización para el tráfico de data?

R: Falso

### ¿Aviatrix FlowIQ entrega?

R: Información de la red mediante toda la red multicloud para todo el tráfico que pasa por los gateways

### ¿FlowIQ entrega un resumen de la data de la red pero para registros específicos se deben realizar tareas en los gateways?

R: Verdadero

### ¿Qué es Aviatrix Co-Pilot?

R: Aviatrix Co-Pilot entrega una visibilidad inteligente en las redes cloud mediante una topología dinámica, flujo de red, resolución de problemas y más.

### ¿Co-Pilot permite personalizar los filtros de límite de datos a recursos, aplicaciones y flujos definidos?

R: Verdadero

### ¿En que Nubes puedes desplegar Aviatrix Controller?

R:

- AWS
- Azure
- OCI

### ¿Cuantros Controllers necesitas normalmente para correr un ambiente multicloud consistente entre OCI, Azure y GCP?

R: 1

### ¿Para AWS, cual es el método recomendado o más fácil paara desplegar Aviatrix Controller?

R: Con la plantilal de CloudFormation desde doc.aviatrix.com

### ¿Puedes desplegar Aviatrix Controller en tu datacenter onPremise?

R: Falso

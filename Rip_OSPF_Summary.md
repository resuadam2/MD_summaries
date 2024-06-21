Configurar protocolos de enrutamiento como RIP (Versiones 1 y 2) y OSPF (Open Shortest Path First) implica definir cómo los routers intercambian información de enrutamiento para determinar las rutas óptimas en una red. Aquí tienes un resumen de la sintaxis y ejemplos básicos para configurar RIP v1, RIP v2 y OSPF en routers Cisco:

### RIP v1 (Routing Information Protocol - Version 1)

#### Configuración Básica

1. **Activar RIP v1:**

   ```bash
   Router(config)# router rip
   Router(config-router)# version 1
   ```

   Esto activa RIP v1 en el router.

2. **Agregar Redes a RIP:**

   ```bash
   Router(config-router)# network <dirección_de_red>
   ```

   Ejemplo:

   ```bash
   Router(config-router)# network 192.168.0.0
   ```

   Esto agrega la red 192.168.0.0 a RIP v1 para que el router anuncie esta red.

### RIP v2 (Routing Information Protocol - Version 2)

#### Configuración Básica

1. **Activar RIP v2:**

   ```bash
   Router(config)# router rip
   Router(config-router)# version 2
   ```

   Esto activa RIP v2 en el router.

2. **Agregar Redes a RIP:**

   ```bash
   Router(config-router)# network <dirección_de_red> 
   ```

   Ejemplo:

   ```bash
   Router(config-router)# network 192.168.0.0
   ```

   Esto agrega la red 192.168.0.0 a RIP v2 para que el router anuncie esta red.

### OSPF (Open Shortest Path First)

#### Configuración Básica

1. **Activar OSPF:**

   ```bash
   Router(config)# router ospf <número_de_proceso>
   ```

   Ejemplo:

   ```bash
   Router(config)# router ospf 1
   ```

   Esto activa OSPF con el proceso número 1 en el router.

2. **Agregar Redes a OSPF:**

   ```bash
   Router(config-router)# network <dirección_de_red> <máscara_de_red> area <número_de_area>
   ```

   Ejemplo:

   ```bash
   Router(config-router)# network 192.168.0.0 0.0.255.255 area 0
   ```

   Esto agrega la red 192.168.0.0 con una máscara de red de 255.255.0.0 al área 0 en OSPF.

### Ejemplos Completos de Configuración

#### Ejemplo 1: Configuración Básica de RIP v1

```bash
Router(config)# router rip
Router(config-router)# version 1
Router(config-router)# network 192.168.0.0
```

Esto configura RIP v1 en el router y anuncia la red 192.168.0.0.

#### Ejemplo 2: Configuración Básica de RIP v2

```bash
Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# network 192.168.0.0
```

Esto configura RIP v2 en el router y anuncia la red 192.168.0.0.

#### Ejemplo 3: Configuración Básica de OSPF

```bash
Router(config)# router ospf 1
Router(config-router)# network 192.168.0.0 0.0.255.255 area 0
```

Esto configura OSPF con el proceso número 1 en el router y anuncia la red 192.168.0.0 con una máscara de red de 255.255.0.0 en el área 0.

### Consideraciones Adicionales

- **Autenticación**: Tanto RIP como OSPF permiten la configuración de autenticación para asegurar la integridad de las actualizaciones de enrutamiento.
  
- **Métricas**: RIP utiliza el número de saltos como métrica, mientras que OSPF utiliza un coste basado en la velocidad del enlace.

- **Áreas OSPF**: OSPF organiza las redes en áreas para mejorar la escalabilidad y el rendimiento del enrutamiento.

Estos ejemplos proporcionan una introducción básica a la configuración de RIP v1, RIP v2 y OSPF en routers Cisco. La configuración exacta puede variar dependiendo del fabricante y del modelo del router, así como de la versión específica del protocolo de enrutamiento utilizada.
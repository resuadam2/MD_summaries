Configurar routers es esencial para dirigir el tráfico entre diferentes redes en una infraestructura de red. Aquí te proporciono un resumen básico de la sintaxis y ejemplos para configurar routers Cisco utilizando comandos CLI (Command Line Interface):

### Configuración Básica de Routers Cisco

#### Acceso a la Configuración

Para acceder al modo de configuración de un router Cisco desde la CLI:

```bash
Router> enable
Router# configure terminal
```

Esto te lleva al modo de configuración global del router, donde puedes ingresar comandos de configuración.

#### Asignación de Nombre al Router

```bash
Router(config)# hostname <nombre_del_router>
```

Ejemplo:

```bash
Router(config)# hostname Router1
```

Esto establece el nombre del router como "Router1".

#### Configuración de Interfaces

1. **Configurar una Interfaz Ethernet:**

   ```bash
   Router(config)# interface FastEthernet0/0
   Router(config-if)# ip address <dirección_ip> <máscara_de_red>
   Router(config-if)# no shutdown
   ```

   Ejemplo:

   ```bash
   Router(config)# interface FastEthernet0/0
   Router(config-if)# ip address 192.168.1.1 255.255.255.0
   Router(config-if)# no shutdown
   ```

   Esto configura la interfaz FastEthernet0/0 con la dirección IP 192.168.1.1 y la máscara de red 255.255.255.0, y habilita la interfaz.

2. **Configurar una Interfaz Serial:**

   ```bash
   Router(config)# interface Serial0/0/0
   Router(config-if)# ip address <dirección_ip> <máscara_de_red>
   Router(config-if)# clock rate <velocidad>
   Router(config-if)# no shutdown
   ```

   Ejemplo:

   ```bash
   Router(config)# interface Serial0/0/0
   Router(config-if)# ip address 10.0.0.1 255.255.255.252
   Router(config-if)# clock rate 64000
   Router(config-if)# no shutdown
   ```

   Esto configura la interfaz Serial0/0/0 con la dirección IP 10.0.0.1, la máscara de red 255.255.255.252, establece la velocidad del reloj a 64 kbps y habilita la interfaz.

#### Configuración de Enrutamiento

1. **Configurar Rutas Estáticas:**

   ```bash
   Router(config)# ip route <red_destino> <máscara_de_red> <próximo_salto>
   ```

   Ejemplo:

   ```bash
   Router(config)# ip route 192.168.2.0 255.255.255.0 10.0.0.2
   ```

   Esto configura una ruta estática hacia la red 192.168.2.0/24 a través del próximo salto 10.0.0.2.

2. **Configurar Protocolos de Enrutamiento Dinámico (OSPF):**

   ```bash
   Router(config)# router ospf <número_de_proceso>
   Router(config-router)# network <dirección_de_red> <máscara_de_red> area <número_de_area>
   ```

   Ejemplo:

   ```bash
   Router(config)# router ospf 1
   Router(config-router)# network 192.168.1.0 0.0.0.255 area 0
   ```

   Esto configura OSPF con el proceso número 1 en el router y anuncia la red 192.168.1.0/24 en el área 0.

#### Guardar Configuraciones

Para guardar la configuración actual en la memoria no volátil del router:

```bash
Router# copy running-config startup-config
```

Este comando asegura que los cambios realizados en la configuración se mantengan después de reiniciar el router.

### Ejemplo Completo de Configuración

#### Ejemplo: Configuración Básica de Router con Interfaces y Rutas Estáticas

```bash
Router(config)# hostname Router1
Router(config)# interface FastEthernet0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config)# interface Serial0/0/0
Router(config-if)# ip address 10.0.0.1 255.255.255.252
Router(config-if)# clock rate 64000
Router(config-if)# no shutdown
Router(config)# ip route 192.168.2.0 255.255.255.0 10.0.0.2
Router(config)# end
Router# copy running-config startup-config
```

Este ejemplo configura un router con nombre "Router1", asigna direcciones IP a las interfaces FastEthernet0/0 y Serial0/0/0, configura una ruta estática hacia la red 192.168.2.0/24 a través del próximo salto 10.0.0.2, y guarda la configuración para que sea persistente.

### Consideraciones Adicionales

- **Seguridad**: Configurar correctamente las interfaces y asegurar las rutas para proteger la red contra accesos no autorizados.
  
- **Monitoreo y Gestión**: Utilizar herramientas de monitoreo para supervisar el tráfico de red y la administración de routers de manera eficiente.

Estos ejemplos proporcionan una introducción básica a la configuración de routers Cisco utilizando comandos CLI. La configuración exacta puede variar dependiendo del modelo y la versión del router, así como de los requisitos específicos de la red.
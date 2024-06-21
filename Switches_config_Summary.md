Configurar switches en redes informáticas es fundamental para asegurar la conectividad eficiente y segura de los dispositivos. Aquí tienes un resumen de la sintaxis y ejemplos básicos para la configuración de switches Cisco utilizando comandos CLI (Command Line Interface):

### Configuración Básica de Switches Cisco

#### Acceso a la Configuración

Para acceder al modo de configuración de un switch Cisco desde la CLI:

```bash
Switch> enable
Switch# configure terminal
```

Esto te lleva al modo de configuración global del switch, donde puedes ingresar comandos de configuración.

#### Asignación de Nombre al Switch

```bash
Switch(config)# hostname <nombre_del_switch>
```

Ejemplo:

```bash
Switch(config)# hostname Switch1
```

Esto establece el nombre del switch como "Switch1".

#### Configuración de Puertos

1. **Configurar un Puerto de Acceso:**

   ```bash
   Switch(config)# interface FastEthernet0/1
   Switch(config-if)# switchport mode access
   Switch(config-if)# switchport access vlan <id_vlan>
   ```

   Ejemplo:

   ```bash
   Switch(config)# interface FastEthernet0/1
   Switch(config-if)# switchport mode access
   Switch(config-if)# switchport access vlan 10
   ```

   Esto configura el puerto FastEthernet0/1 como un puerto de acceso asignado a la VLAN 10.

2. **Configurar un Puerto Troncal (Trunk):**

   ```bash
   Switch(config)# interface GigabitEthernet0/1
   Switch(config-if)# switchport mode trunk
   Switch(config-if)# switchport trunk allowed vlan <lista_de_vlans>
   ```

   Ejemplo:

   ```bash
   Switch(config)# interface GigabitEthernet0/1
   Switch(config-if)# switchport mode trunk
   Switch(config-if)# switchport trunk allowed vlan 10,20,30
   ```

   Esto configura el puerto GigabitEthernet0/1 como un puerto troncal que permite el tráfico de las VLANs 10, 20 y 30.

#### Guardar Configuraciones

Para guardar la configuración actual en la memoria no volátil del switch:

```bash
Switch# copy running-config startup-config
```

Este comando asegura que los cambios realizados en la configuración se mantengan después de reiniciar el switch.

### Ejemplos Completos de Configuración

#### Ejemplo 1: Configuración Básica de VLAN y Puertos

```bash
Switch(config)# hostname Switch1
Switch(config)# interface FastEthernet0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config)# interface GigabitEthernet0/1
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk allowed vlan 10,20,30
Switch(config)# end
Switch# copy running-config startup-config
```

Este ejemplo configura un switch con nombre "Switch1", asigna el puerto FastEthernet0/1 a la VLAN 10 como un puerto de acceso, y configura el puerto GigabitEthernet0/1 como un puerto troncal que permite el tráfico de las VLANs 10, 20 y 30.

#### Ejemplo 2: Configuración de Puertos y Guardado de Configuración

```bash
Switch(config)# hostname Switch2
Switch(config)# interface FastEthernet0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20
Switch(config)# interface GigabitEthernet0/1
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk allowed vlan 20,30,40
Switch(config)# end
Switch# copy running-config startup-config
```

Este ejemplo configura un switch con nombre "Switch2", asigna el puerto FastEthernet0/1 a la VLAN 20 como un puerto de acceso, y configura el puerto GigabitEthernet0/1 como un puerto troncal que permite el tráfico de las VLANs 20, 30 y 40. Finalmente, guarda la configuración para que sea persistente.

### Consideraciones Adicionales

- **Seguridad**: Configurar adecuadamente los puertos para minimizar riesgos de seguridad, como evitar el acceso no autorizado a puertos troncales.

- **Monitoreo y Gestión**: Utilizar herramientas de monitoreo para supervisar el tráfico de red y la administración de switches de manera eficiente.

Estos ejemplos proporcionan una introducción básica a la configuración de switches Cisco utilizando comandos CLI. La configuración exacta puede variar dependiendo del modelo y la versión del switch, así como de los requisitos específicos de la red.
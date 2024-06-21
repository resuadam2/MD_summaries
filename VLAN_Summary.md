Configurar una VLAN (Virtual Local Area Network) implica dividir una red física en varias redes lógicas separadas, lo que permite mejorar la seguridad y la eficiencia en la gestión de la red. Aquí tienes un pequeño resumen de la sintaxis y ejemplos básicos para configurar una VLAN en un switch administrable:

### Sintaxis Básica para Configurar VLANs en Switches

1. **Crear una VLAN:**
   
   Para crear una VLAN, necesitas acceder al modo de configuración del switch y usar comandos específicos según el fabricante del switch. A continuación, se muestra un ejemplo genérico:

   ```bash
   Switch(config)# vlan <id_vlan>
   ```

   Ejemplo:

   ```bash
   Switch(config)# vlan 10
   ```

   Este comando crea una VLAN con identificador 10.

2. **Asignar un Puerto a una VLAN:**
   
   Para asignar un puerto físico a una VLAN específica:

   ```bash
   Switch(config-if)# switchport mode access
   Switch(config-if)# switchport access vlan <id_vlan>
   ```

   Ejemplo:

   ```bash
   Switch(config-if)# interface FastEthernet0/1
   Switch(config-if)# switchport mode access
   Switch(config-if)# switchport access vlan 10
   ```

   Esto configura el puerto FastEthernet0/1 para que sea un puerto de acceso a la VLAN 10.

3. **Configurar un Puerto Troncal (Trunk):**
   
   Un puerto troncal (trunk) permite transportar tráfico de múltiples VLANs a través de un solo cable. La configuración típica incluye especificar qué VLANs deben transportarse a través del puerto troncal:

   ```bash
   Switch(config-if)# switchport mode trunk
   Switch(config-if)# switchport trunk allowed vlan <lista_de_vlans>
   ```

   Ejemplo:

   ```bash
   Switch(config-if)# interface GigabitEthernet0/1
   Switch(config-if)# switchport mode trunk
   Switch(config-if)# switchport trunk allowed vlan 10,20,30
   ```

   Esto configura el puerto GigabitEthernet0/1 como un puerto troncal que permite el tráfico de las VLANs 10, 20 y 30.

### Ejemplos de Configuración Completa

#### Ejemplo 1: Crear y Asignar un Puerto a una VLAN

```bash
Switch(config)# vlan 10
Switch(config)# interface FastEthernet0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
```

Esto crea la VLAN 10 y asigna el puerto FastEthernet0/1 a esa VLAN como puerto de acceso.

#### Ejemplo 2: Configurar un Puerto Troncal

```bash
Switch(config)# interface GigabitEthernet0/1
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk allowed vlan 10,20,30
```

Esto configura el puerto GigabitEthernet0/1 como un puerto troncal y permite el tráfico de las VLANs 10, 20 y 30 a través de ese puerto.

### Consideraciones Adicionales

- **Etiquetado (VLAN Tagging)**: En entornos donde se utilizan múltiples VLANs a través de un solo enlace, es común usar etiquetado VLAN (VLAN tagging) para distinguir entre diferentes VLANs.
  
- **Consistencia de Configuración**: Es crucial mantener la consistencia en la configuración de VLANs en todos los switches de la red para asegurar la conectividad adecuada entre los dispositivos.

Estos ejemplos proporcionan una introducción básica a la sintaxis utilizada para configurar VLANs en switches administrables. La configuración exacta puede variar según el fabricante y el modelo del switch, por lo que es importante consultar la documentación específica del dispositivo utilizado.
iptables es una herramienta de administración de paquetes de red en Linux que permite configurar reglas de filtrado de paquetes. Se utiliza para implementar políticas de firewall, traducir direcciones de red (NAT) y redirigir puertos. A continuación, te proporcionaré un resumen de la sintaxis y ejemplos de uso de iptables.

### Sintaxis Básica

La estructura general de un comando iptables es:

```bash
iptables [opciones] [cadena] [condiciones de coincidencia] [acción]
```

- **[opciones]**: Especifican detalles como la tabla a usar (`-t`), la política por defecto (`-P`), o la adición/eliminación de reglas (`-A`, `-D`).
- **[cadena]**: Especifica la cadena en la que se va a trabajar, como `INPUT`, `FORWARD`, `OUTPUT`, `PREROUTING`, `POSTROUTING`.
- **[condiciones de coincidencia]**: Especifican los criterios para que una regla coincida, como la dirección IP de origen o destino (`-s`, `-d`), el protocolo (`-p`), el puerto (`--dport`).
- **[acción]**: Especifica lo que se debe hacer con los paquetes que coinciden, como `ACCEPT`, `DROP`, `REJECT`, `LOG`.

### Ejemplos de Uso

#### Ver Reglas Actuales

```bash
iptables -L
```

Muestra todas las reglas actuales en la tabla de filtros.

#### Aceptar Todo el Tráfico en la Interfaz `lo`

```bash
iptables -A INPUT -i lo -j ACCEPT
```

Acepta todo el tráfico que entra por la interfaz de loopback `lo`.

#### Permitir el Tráfico SSH (Puerto 22)

```bash
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

Permite las conexiones entrantes al puerto 22 (SSH).

#### Bloquear Todo el Tráfico desde una IP Específica

```bash
iptables -A INPUT -s 192.168.1.100 -j DROP
```

Bloquea todo el tráfico entrante desde la IP `192.168.1.100`.

#### Permitir el Tráfico HTTP y HTTPS

```bash
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT
```

Permite las conexiones entrantes a los puertos 80 (HTTP) y 443 (HTTPS).

#### Bloquear Todo el Tráfico Excepto SSH y HTTP/HTTPS

```bash
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

Configura políticas predeterminadas para bloquear todo el tráfico entrante y de reenvío, excepto para las conexiones SSH, HTTP y HTTPS, y permite todo el tráfico saliente.

#### Registrar Paquetes Descargados

```bash
iptables -A INPUT -j LOG --log-prefix "Paquete caído: "
```

Registra todos los paquetes descargados con el prefijo "Paquete caído: ".

#### Eliminar una Regla Específica

```bash
iptables -D INPUT -s 192.168.1.100 -j DROP
```

Elimina la regla que bloquea todo el tráfico desde la IP `192.168.1.100`.

### NAT y Redirección de Puertos

#### Redirigir el Tráfico de un Puerto a Otro

```bash
iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8080
```

Redirige el tráfico entrante al puerto 80 al puerto 8080.

#### Traducción de Direcciones de Red (NAT)

```bash
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

Habilita el enmascaramiento de IP para permitir la compartición de la conexión a internet en la interfaz `eth0`.

### Guardar y Restaurar Reglas

#### Guardar Reglas

```bash
iptables-save > /etc/iptables/rules.v4
```

Guarda las reglas actuales en un archivo.

#### Restaurar Reglas

```bash
iptables-restore < /etc/iptables/rules.v4
```

Restaura las reglas desde un archivo.

### Ejemplo Completo de Configuración de Firewall

```bash
#!/bin/bash

# Limpiar todas las reglas anteriores
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X

# Establecer políticas predeterminadas
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

# Permitir tráfico de loopback
iptables -A INPUT -i lo -j ACCEPT

# Permitir tráfico entrante relacionado y establecido
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Permitir SSH, HTTP y HTTPS
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT

# Bloquear todo el tráfico entrante por defecto
iptables -A INPUT -j DROP

# Guardar reglas
iptables-save > /etc/iptables/rules.v4
```

Este script configura un firewall básico, permite el tráfico de loopback y las conexiones SSH, HTTP y HTTPS, y bloquea todo el tráfico entrante no especificado. Luego guarda las reglas en un archivo para su restauración posterior.

Este resumen proporciona una base sólida para trabajar con iptables, cubriendo la sintaxis básica, ejemplos de uso común y configuración avanzada para NAT y redirección de puertos.

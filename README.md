# Informe técnico de Seguridad en Redes – Módulo 6

Este repositorio contiene el archivo de simulación en **Cisco Packet Tracer** y el informe técnico asociado al proyecto **Prueba Módulo 6 – Seguridad en redes corporativas**.  
El objetivo fue implementar servicios y configuraciones avanzadas de capa 2, capa 3, firewall ASA, VPN y políticas de control de acceso.

---

## 📂 Contenido del repositorio

- `Prueba modulo 6.pdf` → Informe técnico con la descripción detallada de la implementación.  
- `Prueba modulo 6.pkt` → Archivo de simulación en Packet Tracer.  

---

## 🛠️ Requerimientos implementados

### 1. Implementación de Capa 3
- Direccionamiento de toda la topología con **IPv4**.  
- Configuración de **protocolo de enrutamiento OSPF** (estado de enlace) en área backbone.  
- Uso de **interfaces pasivas** en los routers correspondientes.  
- Autenticación en OSPF a nivel de interfaz.  

### 2. Implementación de Capa 2 y seguridad
- Apagado de interfaces no utilizadas y traslado a **VLAN 99** para seguridad.  
- **Port Security** en interfaces con máximo de 2 MAC, desactivando la interfaz al exceder.  
- Estabilización de STP en interfaces de acceso (**PortFast / BPDU Guard**).  
- Configuración de **DHCP Snooping** en el switch designado.  
- Protección contra **ataque de hambruna DHCP**, limitando a 2 IP por minuto.  

### 3. Firewall ASA y VPN de acceso remoto
- Definición de **zonas de seguridad** en ASA:
  - Inside → nivel máximo.  
  - DMZ → 40% de Inside.  
  - Outside → 50% de DMZ.  
- **DHCP** en zona Inside, con máximo 16 direcciones IPv4.  
- Configuración de **PAT** para salida de Inside hacia Outside.  
- Inclusión de ICMP en **MPF** para permitir pruebas de conectividad.  
- **NAT estático** para que PC-DMZ pueda salir hacia Outside y recibir respuesta.  
- Acceso por **Telnet** al ASA desde el servidor de servicios.  
- Implementación de **VPN Site-to-Site** entre RA y RC.  

### 4. Política de control de acceso – Desafío Latam
Se implementó una política para el **uso eficiente de la VPN site-to-site** entre RA y RC.  

- **Objetivo:** Asegurar que solo el tráfico relevante use el túnel VPN, optimizando el ancho de banda y garantizando seguridad.  
- **Tráfico permitido:**  
  - Solo el de **172.16.10.0/24 ↔ 172.16.250.0/24** será considerado “interesante” y cifrado.  
- **Tráfico no permitido:**  
  - Todo lo demás (ejemplo: 172.16.15.0/24 → 172.16.250.0/24 o tráfico a internet) se enviará por la red pública.  
- **ACLs:** Definición explícita en RA y RC del tráfico permitido por la VPN.  
- **Protocolos:** Prioridad al uso de protocolos seguros.  
- **Monitoreo:** Implementación de herramientas de supervisión para validar uso correcto de la VPN.  

---

## 📸 Evidencias
El informe incluye capturas de:
- Configuración de OSPF y autenticación en interfaces.  
- Port Security y DHCP Snooping en switches.  
- Traducciones PAT y NAT estático en ASA.  
- Conectividad entre zonas Inside, Outside y DMZ.  
- Pruebas de conectividad y uso de la VPN site-to-site.  

---

## 🚀 Uso del archivo `.pkt`
1. Abrir el archivo `Prueba modulo 6.pkt` en **Cisco Packet Tracer (v8.x o superior)**.  
2. Verificar las configuraciones en routers, switches y ASA.  
3. Probar conectividad entre VLANs, zonas de ASA y a través de la VPN.  
4. Validar la aplicación de políticas de acceso mediante ACLs y pruebas de tráfico.  

---

## 👤 Autor
- **Daniel Dávila**  

---

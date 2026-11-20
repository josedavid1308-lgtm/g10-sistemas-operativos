# Ficha de verificación de versión – Grupo 10

Fecha de consulta: 19/11/2026

## VM gráfica: Lubuntu

| Campo | Valor | Fuente / cómo se verificó |
|---|---|---|
| Distribución | Lubuntu | Tabla del proyecto (Grupo 10) |
| Versión elegida | 26.04.1 LTS "Resolute Raccoon" | cdimage.ubuntu.com/lubuntu/releases/resolute/release/ |
| Tipo | LTS | lubuntu.me, anuncio del lanzamiento |
| Fecha de lanzamiento | 23/04/2026 (punto 26.04.1 en agosto de 2026) | lubuntu.me |
| Fin de soporte | Abril de 2029 (3 años) | lubuntu.me |
| Instalador | Calamares | Guía de instalación de la clase |
| Particionado manual | "Particionado manual" | Guía de instalación de la clase |
| ¿Permite LVM? | Sí, botón "New Volume Group" | Guía de instalación de la clase |
| Sistema de archivos por defecto | ext4 | Se confirmará con `lsblk -f` o `df -T` en nuestra VM |
| Gestor de paquetes | apt | Documentación de Ubuntu |
| Firewall | ufw (inactivo por defecto) | Documentación de Ubuntu; se confirma en la VM |
| Arranque de la VM | Pendiente | `ls /sys/firmware/efi` tras instalar |
| Kernel | Pendiente | `uname -a` tras instalar |

## VM de consola: CentOS Stream

| Campo | Valor | Fuente / cómo se verificó |
|---|---|---|
| Distribución | CentOS Stream | Tabla del proyecto (Grupo 10) |
| Versión elegida | CentOS Stream 10 | centos.org/download |
| Tipo | Versión mayor continua (sin versiones menores) | centos.org |
| ¿Es la más reciente? | Sí, Stream 10 es la rama más nueva | centos.org |
| Fecha de lanzamiento | 12/12/2024 | Wikipedia (CentOS Stream) |
| Fin de soporte | 31/05/2030 | centos.org/download |
| Kernel base | 6.12 | Wikipedia; se confirma con `uname -a` |
| Instalador | Anaconda | Documentación de CentOS / Red Hat |
| Particionado manual | "Custom" (personalizado) | Se confirmará al instalar |
| ¿Permite LVM? | Sí | Documentación de Red Hat |
| Sistema de archivos por defecto | XFS | Documentación de Red Hat; se confirma con `lsblk -f` o `df -T` |
| Gestor de paquetes | dnf | Documentación de CentOS |
| Firewall | firewalld | Documentación de CentOS / Red Hat |
| Arranque de la VM | Pendiente | `ls /sys/firmware/efi` tras instalar |

## Imagen base del Dockerfile: Rocky Linux

| Campo | Valor | Fuente / cómo se verificó |
|---|---|---|
| Distribución | Rocky Linux | Tabla del proyecto (Grupo 10) |
| Versión | Rocky Linux 10 | Docker Hub / rockylinux.org |
| Imagen oficial | rockylinux/rockylinux:10 | Docker Hub (confirmar nombre exacto al escribir el Dockerfile) |
| Gestor de paquetes | dnf | Documentación de Rocky Linux |

## Notas
- Las filas "Pendiente" se completan en el Sprint 1 con comandos en las VM.
- Los datos marcados "se confirma" son de documentación y los contrastaremos con la instalación real, porque los valores por defecto pueden cambiar según la versión.

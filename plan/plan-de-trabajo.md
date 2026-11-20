# Plan de trabajo – Grupo 10

## Integrantes
| Nombre completo | Rol | Usuario GitHub |
|---|---|---|
| José David López González | Creador del repositorio; trabajo compartido | josedavid1308-lgtm |
| Sebastián Herrera Suniga | Colaborador; trabajo compartido | [pendiente] |

Ambos participan en todas las actividades. Cada tarea tiene un responsable principal y el otro la revisa.

## Distribución asignada
| Componente | Distribución |
|---|---|
| Linux gráfico (g10-grafica) | Lubuntu 26.04.1 LTS |
| Linux consola (g10-consola) | CentOS Stream 10 |
| Imagen base del Dockerfile | Rocky Linux 10 |

## Decisiones técnicas
| Tema | VM gráfica | VM de consola |
|---|---|---|
| Disco virtual | 25 GB | 25 GB |
| RAM / CPU | 4 GB / 2 CPU | 2 GB / 2 CPU |
| Tabla de particiones | MBR si la VM arranca con BIOS (se confirma con `ls /sys/firmware/efi`) | Igual |
| Particiones | /, swap, /home | /, /var, swap, /home |
| Tamaños propuestos | / 15 GB, swap 2 GB, /home 8 GB | / 6 GB, /var 14 GB, swap 2 GB, /home 3 GB |
| Mínimos del proyecto | Los justifica el equipo | / 5, /var 10, swap 1, /home 1 (suman 17 GB) |

### Justificación
- **VM de consola:** de los 8 GB sobrantes, 4 van a /var porque Docker guarda imágenes y contenedores en /var/lib/docker. 1 GB va a / (margen), 1 a swap y 2 a /home. En total: 6 + 14 + 2 + 3 = 25 GB.
- **VM gráfica:** la raíz lleva más espacio porque el escritorio y las aplicaciones (dos navegadores y dos editores) ocupan bastante. /home de 8 GB guarda archivos de usuario. Swap de 2 GB es suficiente para 4 GB de RAM.
- **Sistema de archivos en la consola:** CentOS Stream usa XFS por defecto, que solo se puede ampliar, no reducir. Por eso dimensionamos con margen desde el inicio.
- Si el instalador impide cumplir un mínimo, documentaremos el intento y la limitación.

## Cronograma
| Sprint | Actividad | Responsable principal | Revisa |
|---|---|---|---|
| 0 | Repositorio, plan de trabajo y ficha de versión (vence 20/nov/2026) | José David y Sebastián | Ambos |
| 1 | 1.1 VM gráfica: instalación manual y capturas | José David | Sebastián |
| 1 | 1.2 VM de consola: particionado con /var propio y capturas | Sebastián | José David |
| 1 | 1.3 Instantánea `instalacion-limpia` en cada VM | Cada uno en su VM | Cruzada |
| Siguiente | Docker en la VM de consola | Sebastián | José David |
| Siguiente | Sitio web: cuadro comparativo del instalador | José David | Sebastián |

Las fechas de cada sprint se ajustan al calendario del documento del proyecto.

## Evidencias que recolectaremos
- Capturas de terminal con prompt (usuario@equipo) y `date` en pantalla.
- Captura del resumen del instalador con el esquema de particiones.
- `lsblk`, `df -h`, `cat /etc/fstab`, `free -m`, `ip a`, `uname -a`, `swapon --show`.

## Riesgos y mitigación
- ISO vencida: descargar solo del sitio oficial y verificar que sea la versión estable más reciente.
- CentOS Stream 10 exige CPU x86-64-v3: si la VM no arranca en VirtualBox, documentar el intento y probar Stream 9.
- Anaconda propone LVM por defecto: usaremos particionado personalizado para crear /var propio.
- Pantalla azul en VirtualBox (Lubuntu): controlador VBoxSVGA y 128 MB de vídeo.
- /var sin espacio para Docker: dimensionar bien al particionar.
- Error en fstab: probar con `sudo mount -a` antes de reiniciar.
- Cambios irreversibles de particiones: instantánea antes de cada cambio grande.

## Forma de trabajo
- Trabajo en pareja; ambos hacen commits.
- Comunicación: grupo de WhatsApp para coordinación diaria; GitHub (Issues y commits) para el seguimiento del trabajo.
- Reuniones: una reunión virtual semanal de 1 hora (Google Meet), más una revisión rápida antes de cada cierre de sprint.
- Acuerdos: cada tarea tiene un responsable principal y el otro la revisa antes de entregar; las decisiones importantes se escriben en el repositorio.

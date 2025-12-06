# Sofa_Cluster

SOFA HPC Workflow – Ejecución de SOFA en Singularity dentro del Cluster HTPC

## Requisitos

- Singularity

    - https://sylabs.io/guides/3.5/user-guide/quick_start.html



## Instalación

### Instalación de Singularity
- correr archivo de instalación de singularity wue sintala 

1. Introducción

Este proyecto entrega una guía completa para ejecutar SOFA dentro de una imagen Singularity en el cluster HTPC, incluyendo:

Conexión al cluster

Copia de scripts

Descarga y uso de imágenes Singularity

Ejecución de SOFA

Ejecución de trabajos SLURM

Flujo de trabajo reproducible para cualquier usuario

## Estructura del repositorio
sofa-hpc-workflow/
│
├── scripts/
│   ├── build_image.sh
│   ├── run_sofa.sh
│   └── test_slurm.sh
│
├── slurm/
│   └── job_test.slurm
│
└── README.md


## Requisitos previos

Cuenta activa en el HTPC

Contraseña del correo institucional

Terminal (Linux/macOS/WSL)

Git

Conexión estable a internet

Singularity disponible en el cluster


## Acceso al HTPC


Acceso SSH
ssh usuario@IP_DEL_CLUSTER


Salir:

exit



Clonar el repositorio
git clone https://github.com/usuario/sofa-hpc-workflow.git
cd sofa-hpc-workflow
 


 Qué es una imagen Singularity?

Una imagen Singularity (.sif) es un contenedor diseñado para HPC:
portátil, seguro, reproducible y compatible con SLURM.

Ejemplo:

singularity exec sofa_image.sif python3 script.py



. Descargar o construir la imagen
bash scripts/build_image.sh


Este script descarga o construye la imagen sofa_image.sif.

🧪 9. Verificar SOFA

Entrar a la imagen:

singularity shell sofa_image.sif


Ejecutar SOFA:

runSofa

📄 10. Ejecutar un job SLURM

Enviar:

sbatch slurm/job_test.slurm


Ver estado:

squeue -u $USER


Cancelar:

scancel JOBID

🔧 11. Comandos útiles

Singularity

singularity shell image.sif
singularity exec image.sif comando
singularity run image.sif


SSH

ssh usuario@ip
exit


SCP

scp archivo usuario@ip:/path/
scp -r carpeta usuario@ip:/path/


SLURM

sbatch archivo.slurm
squeue -u usuario
scancel jobid

🧭 12. Flujo de trabajo recomendado

Clonar el repositorio

Copiar scripts al cluster

Descargar o construir la imagen

Verificar ejecución de SOFA

Ejecutar run_sofa.sh

Enviar job SLURM

Revisar resultados
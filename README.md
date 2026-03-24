Aquí tienes **todo el README en un solo archivo**, ya en **formato Markdown**, listo para copiar y pegar directamente en GitHub.
Sin comentarios extras, sin explicaciones: **solo el archivo final**.

---

```markdown
# SOFA_Cluster
SOFA HPC Workflow – Ejecución de SOFA en Singularity dentro del Cluster HTPC

Este repositorio contiene un flujo de trabajo mínimo para ejecutar **SOFA** dentro de un contenedor **Singularity** en un **cluster HPC (High-Performance Computing)** utilizando **SLURM**.

---

## 📌 Requisitos
- Cuenta con acceso al **cluster HTPC**
- Ubuntu u otra distribución Linux
- Acceso SSH
- Imagen Singularity con SOFA

---

## 📁 Estructura del repositorio

```

sofa-hpc-workflow/
│
├── slurm/
│   └── job_test.slurm        # Archivo SLURM de ejemplo
│
└── README.md                 # Documentación del proyecto

````

---

# 1. Acceso al Cluster HTPC

Para conectarse al cluster:

```bash
ssh usuario@IP_DEL_CLUSTER
````

Ejemplo:

```bash
ssh username@172.16.105.194
```

Para salir:

```bash
exit
```

---

# 2. Descargar la imagen de Singularity (SOFA)

Descargar la imagen `.sif` desde:

🔗 [https://drive.google.com/file/d/1CjY5nmMsOa7L5yRpA7l9OavdkGsw66-S/view?usp=sharing](https://drive.google.com/file/d/1CjY5nmMsOa7L5yRpA7l9OavdkGsw66-S/view?usp=sharing)

Subir la imagen al cluster:

```bash
scp sofa_hpc.sif usuario@172.16.105.194:/home/usuario/
```

---

# 3. Clonar el repositorio

```bash
git clone https://github.com/usuario/sofa-hpc-workflow.git
cd sofa-hpc-workflow
```

---

# 4. ¿Qué es un Cluster HPC?

Un **cluster HPC (High-Performance Computing)** es un conjunto de computadores (nodos) conectados entre sí que funcionan como un único sistema de alto rendimiento.

Permite:

* Ejecutar simulaciones grandes
* Usar cientos o miles de núcleos de CPU
* Acceder a GPUs de alto rendimiento
* Compartir almacenamiento y recursos

Se utiliza para tareas que exceden las capacidades de un computador personal.

---

# 5. ¿Qué es Singularity y por qué se usa en el cluster?

**Singularity** es un sistema de contenedores diseñado específicamente para HPC.

### Ventajas:

* No requiere permisos de administrador
* Seguro (no eleva privilegios)
* Portátil y reproducible
* Compatible con SLURM
* Estándar en centros HPC (Docker está prohibido)

Permite empaquetar **SOFA + dependencias** en una sola imagen `.sif`.

---

# 6. ¿Qué es CUDA / GPU?

### GPU

Unidad de procesamiento gráfico optimizada para cálculos paralelos masivos.
En HPC se usa para simulaciones físicas, FEM, machine learning, etc.

### CUDA

Framework de NVIDIA para usar la GPU desde programas C++, Python, etc.

Para usar GPU dentro del contenedor:

```bash
singularity exec --nv sofa_hpc.sif runSofa
```

---

# 7. Ejecutar SOFA dentro del contenedor

Ejecutar SOFA:

```bash
singularity exec sofa_hpc.sif runSofa
```

Con soporte GPU:

```bash
singularity exec --nv sofa_hpc.sif runSofa
```

---

# 8. Enviar un trabajo con SLURM

Enviar el archivo de ejemplo:

```bash
sbatch slurm/job_test.slurm
```

Ver trabajos en ejecución:

```bash
squeue -u usuario
```

Cancelar un trabajo:

```bash
scancel JOB_ID
```

---

# 9. Créditos

Repositorio mantenido por **Benjamín Pichun** para ejecución de simulaciones **SOFA en ambiente HPC** utilizando Singularity y SLURM.

```

---


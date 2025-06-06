# Stack de Chatwoot_Nestor para Traefik by DigitAllFran

Este stack despliega Chatwoot, una plataforma de comunicación con clientes, y la configura para ser gestionada y asegurada por un ecosistema de servicios preexistente.

## Arquitectura y Dependencias

Este stack requiere de un ecosistema funcional para operar.

#### **Prerrequisitos Indispensables:**

1.  **El Guardián (Traefik):** [Stack de Traefik de DigitAllFran](https://github.com/bicibikes15/Traefik)
2.  **El Arsenal (Bases de Datos):** [Stack Global de Bases de Datos de DigitAllFran](https://github.com/bicibikes15/Globals-Databases)
3.  **La Red Compartida:** Todos los stacks deben usar la red externa `digitallfran_net`.

## El Ritual de Invocación (Instalación)

**1. Clonar el Repositorio**
```bash
git clone [https://github.com/tu-github/Chatwoot-Nestor-Stack.git](https://github.com/tu-github/Chatwoot-Nestor-Stack.git)
cd Chatwoot-Nestor-Stack

2. Verificar la Red Externa
Asegúrate de que la red digitallfran_net existe. Si no, créala:

Bash

docker network create digitallfran_net

3. Preparar la Base de Datos (Paso Crítico)

Chatwoot requiere un usuario y una base de datos dedicados en tu PostgreSQL.

A. Elige una contraseña segura para el nuevo usuario.

B. Ejecuta los Comandos SQL:
En la terminal de tu servidor, entra a tu PostgreSQL global:

Bash

docker exec -it postgres_global psql -U postgres
Una vez dentro (postgres=#), ejecuta estos comandos. Reemplaza 'TU_NUEVA_CLAVE_SEGURA' con la contraseña que elegiste.

SQL

CREATE USER chatwoot_nestor_prod WITH PASSWORD 'TU_NUEVA_CLAVE_SEGURA';
ALTER USER chatwoot_nestor_prod WITH SUPERUSER;
CREATE DATABASE chatwoot_nestor_production OWNER chatwoot_nestor_prod;
Sal de psql con \q.

4. Configurar los Secretos

Bash

cp .env.example .env
Edita el archivo .env (nano .env) y rellena todas las variables, especialmente la POSTGRES_PASSWORD con la clave que acabas de asignar en el paso anterior.

5. Desplegar Chatwoot

Bash

docker compose up -d

---
El `gitignore` no requiere cambios. La nueva identidad ha sido forjada en todos los pergaminos.













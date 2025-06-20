<div align="center">
  <img src="https://cdn.jsdelivr.net/gh/simple-icons/simple-icons/icons/chatwoot.svg" alt="Chatwoot Logo" width="120"/>
  <h1 align="center">Stack de Chatwoot_Nestor para Traefik by DigitAllFran</h1>
  <p>
    <img src="https://img.shields.io/badge/Chatwoot-Production-green?style=for-the-badge&logo=chatwoot&logoColor=white" alt="Chatwoot"/>
    <img src="https://img.shields.io/badge/Traefik-v3-blueviolet?style=for-the-badge&logo=traefikproxy&logoColor=white" alt="Traefik v3"/>
    <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL"/>
    <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white" alt="Redis"/>
    <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker"/>
  </p>
</div>

> [!NOTE]
> **Chatwoot listo para producción**  
> Plataforma de comunicación con clientes, gestionada y asegurada por el ecosistema DigitAllFran, con Traefik, SSL automático y base de datos dedicada.

> [!TIP]
> **Arquitectura y dependencias**
> - **Traefik v3** como proxy inverso ([Stack recomendado](https://github.com/bicibikes15/Traefik))
> - **Bases de datos globales:** PostgreSQL y Redis ([Stack recomendado](https://github.com/bicibikes15/Globals-Databases))
> - **Red Docker externa:** `digitallfran_net`

> [!IMPORTANT]
> **El Ritual de Invocación (Instalación)**
> 1. **Clona el repositorio:**
>    ```
>    git clone https://github.com/bicibikes15/Chatwoot-Nestor-Stack-Traefik.git
>    cd Chatwoot-Nestor-Stack-Traefik
>    ```
> 2. **Verifica o crea la red externa:**
>    ```
>    docker network create digitallfran_net
>    ```
> 3. **Prepara la base de datos y usuario:**
>    ```
>    docker exec -it postgres_global psql -U postgres
>    ```
>    Y dentro de psql:
>    ```
>    CREATE USER chatwoot_nestor_prod WITH PASSWORD 'TU_NUEVA_CLAVE_SEGURA';
>    ALTER USER chatwoot_nestor_prod WITH SUPERUSER;
>    CREATE DATABASE chatwoot_nestor_production OWNER chatwoot_nestor_prod;
>    \q
>    ```
> 4. **Configura los secretos:**
>    ```
>    cp .env.example .env
>    # Edita .env y rellena todas las variables, especialmente POSTGRES_PASSWORD
>    ```
> 5. **Despliega Chatwoot:**
>    ```
>    docker compose up -d
>    ```
> 6. **Prepara la base de datos Chatwoot (dentro del stack):**
>    ```
>    docker compose run --rm rails bundle exec rails db:chatwoot_prepare
>    ```

> [!WARNING]
> **Verificación y acceso**  
> Traefik asignará el certificado SSL y expondrá Chatwoot en tu subdominio configurado.  
> Accede a `https://<TU_DOMINIO_CHATWOOT>` y crea tu usuario administrador.

> [!NOTE]
> **¿Todo funcionando?**  
> Si puedes acceder al panel y comunicarte con clientes, ¡listo!  
> Tienes tu plataforma de atención multicanal lista para producción, segura y gestionable.

---

<div align="center">
  <a href="https://digitallfran.co" target="_blank">
    <img src="https://digitallfran.co/logo.svg" alt="DigitAllFran Logo" width="90"/><br>
    <b>¿Necesitas soporte, consultoría o quieres llevar tu comunicación al siguiente nivel?</b><br>
    <span style="font-size:1.1em;">
      <strong>¡Visita <u>digitallfran.co</u> y agenda tu consulta!</strong>
    </span>
  </a>
</div>

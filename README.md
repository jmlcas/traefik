# Traefik

Ver en "localhost:8080"

y en "tudominio.com"

Debes poner un email válido en docker-compose.yml línea 18

Debes poner un dominio válido en docker-compose.yml línea 39 ( Y con DNS redireccionados ) 

### Para añadir otras aplicaciones:
```
    networks:
      - traefik_proxy
    labels:
      - traefik.enable=true
      - traefik.http.services.nombre-app.loadbalancer.server.port=80   # Poner el puerto interno que corresponda 
      - traefik.http.routers.nombre-app.rule=Host(`tudominio.com`)     # Poner un dominio válido y redirigir los DNS
      - traefik.http.routers.nombre-app.entrypoints=web,websecure
      - traefik.http.routers.nombre-app.tls=true
      - traefik.http.routers.nombre-app.tls.certresolver=myresolver

networks:
  traefik_proxy:
    external: true 
```
Cambiar "nombre-app" por el que corresponda al servicio.

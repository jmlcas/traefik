# Traefik

Ver en "localhost:8080"

y en "tudominio.com"

Debes poner un email válido en docker-compose.yml línea 18

Debes poner un dominio válido en docker-compose.yml línea 39 ( Y con DNS redireccionados ) 

### Para añadir otras aplicaciones:
```
    networks:
      - proxy
    labels:
      - traefik.enable=true
      - traefik.port=8000       # Poner el puerto que corresponda 
      - traefik.http.routers.nombre-app.rule=Host(`tudominio.com`)    # Poner un dominio válido y redirigir los DNS
      - traefik.http.routers.nombre-app.entrypoints=websecure
      - traefik.http.routers.nombre-app.tls=true
      - traefik.http.routers.nombre-app.tls.certresolver=myresolver

networks:
  proxy:
```
Cambiar "nombre-app" por el que corresponda al servicio.

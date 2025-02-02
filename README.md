# traefik

Ver en "localhost:8080"

y en "tudominio.com"

Debes poner un email válido en /traefik/traefik.yml (líneas 22 y 30)

Debes poner un dominio válido en docker-compose.yml ( Y con DNS redireccionados a tu servidor) línea 29

Para añadir otras aplicaciones:
    networks:
      - proxy 
    labels:
      - 'traefik.enable=true'      
      - 'traefik.http.routers.nombreapp.entrypoints=web,websecure'   # ATENCION -Cambiar nombreapp por el nombre de la aplicación
      - 'traefik.http.routers.nombreapp.rule=Host("tudominio.com")'  # ATENCION -Cambiar por tu dominio ó subdominio correcto
      - 'traefik.http.services.nombreapp.loadbalancer.server.port=9000' # ATENCION -Cambiar por puerto aplicación
      - 'traefik.http.routers.nombreapp.tls.certresolver=production'      
      - 'traefik.http.routers.nombreapp.tls=true'       
networks:
  proxy:
    external: true 


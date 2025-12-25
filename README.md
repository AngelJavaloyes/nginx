# nginx
Trabajo HTTP IV

# Estudio de Nginx y realizar un informe

## Introducción
Nginx es un servidor web de código abierto creado en 2004 por Igor Sysoev. Inicialmente diseñado para resolver el problema C10K (10,000 conexiones simultáneas), se ha convertido en una alternativa popular a Apache gracias a su arquitectura asíncrona y eficiente.

## Comparativa Técnica: Nginx vs Apache

### Rendimiento
- **Apache**: Excelente para contenido dinámico con .htaccess
- **Nginx**: Superior para contenido estático y alta concurrencia
- **Benchmarks**: Nginx puede servir hasta 4x más solicitudes con los mismos recursos

### Casos de Uso
**Apache es mejor para:**
- Hosting compartido con .htaccess
- Entornos con muchos módulos personalizados
- Aplicaciones legacy

**Nginx es mejor para:**
- Sitios de alto tráfico
- Servir archivos estáticos
- Como proxy inverso
- Microservicios y APIs modernas

## Conclusión para Servicios Web RC, S.A.
Dado el crecimiento esperado de la empresa y la necesidad de optimizar recursos, se recomienda la migración gradual a Nginx. La inversión en formación del equipo se verá compensada por:
1. Reducción del 40-60% en uso de recursos
2. Mayor capacidad para picos de tráfico
3. Arquitectura más moderna y mantenible

# Procedimiento

## 1. Instalar Nginx
sudo apt install nginx -y

## 2. Configurar Página por Defecto
sudo nano /var/www/html/index.nginx-debian.html
y lo personalizamos

## 3. Configurar Virtual Hosting

### Crear directorios:
sudo mkdir -p /var/www/web1
sudo mkdir -p /var/www/web2

### Crear páginas de prueba:
sudo nano /var/www/web1/index.html
sudo nano /var/www/web2/index.html

### Crear archivos de configuración:

**web1.conf:**
sudo nano /etc/nginx/sites-available/web1.conf
server {
    listen 80;
    server_name www.web1.org;
    root /var/www/web1;
    index index.html;
}

**web2.conf:**
sudo nano /etc/nginx/sites-available/web2.conf
server {
    listen 80;
    server_name www.web2.org;
    root /var/www/web2;
    index index.html;
    
    # Solo acceso desde red interna
    allow 10.0.3.0/24;
    deny all;
}

## 4. Habilitar los Sitios (creando enlaces simbólicos)
sudo ln -s /etc/nginx/sites-available/web1.conf /etc/nginx/sites-enabled/
sudo ln -s /etc/nginx/sites-available/web2.conf /etc/nginx/sites-enabled/

## 5. Configuración en Cliente Interno
sudo nano /etc/hosts
10.0.3.25 www.web1.org www.web2.org

## 6. Configuración en Cliente Externo
sudo nano /etc/hosts
10.0.2.15 www.web1.org www.web2.org

## Notas Importantes:
1. Asegúrate de reiniciar Nginx después de realizar cambios:
sudo systemctl restart nginx

2. Verifica la sintaxis de configuración:
sudo nginx -t

3. El sitio web2 solo será accesible desde la red interna (10.0.3.0/24)

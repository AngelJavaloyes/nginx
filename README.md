# nginx
Trabajo HTTP IV

# Estudio Técnico: Migración de Apache a Nginx

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

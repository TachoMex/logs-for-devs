Lo mínimo que todo buen dev debe saber sobre logs

Gilberto Vargas

Kueski

---

¿Qué es un log?

- ¿Mensajes aburridos? 😴
- ¿Desperdicio de almacenamiento? 👻
- ¿Cosas que los sysadmin utilizan? 🤖

---

¿Qué es un log?

- Bitácora de eventos 🕵️
- Interacciones 🤙
- Medidas 🧐
- Datos 🤓

---

¿Qué problemas resuelve tener un buen log?

- Diagnóstico de errores 😷
- Planeación de capacidad 📈
- Métricas 📉
- Medir => Comparar => Decidir 🤔

---

¿Qué pasaría si pusieras saber en qué has gastado todo el dinero de la quincena?

---

¿Qué pasaría si pusieras saber en qué has gastado todo el dinero de la quincena?

- Encontrar qué le pasó a la quincena 😅
- Medir qué proporciones se usa la quincena 🤔
- Encontrar problemas de gastos 😌
- Medir los gastos hormiga 🐜

---

Diagnóstico de errores

- Regularmente se tienen 2 fotografias del problema:
  - Lo que había originalmente (la quincena 🤑)
  - Lo que hay (la cartera vacía 😰)

---

Diagnóstico de errores

- ¿Cómo determinas el problema con tan pocos datos?
- ¿En dónde buscas el problema?
- 🤔

---

- Logs
- Revisión de todos los eventos
- Recreación de los hechos
- 🕵️

---

Planeación de capacidad

- Determinar los límites de los recursos
- Decidir cuando crecer.

---
Planeación de capacidad

- Si para ir al trabajo recorro X km al día y gasto $Y en transporte:
  - ¿Cuánto dinero necesito para recorrer Z km?
  - ¿Es rentable realizar un viaje de X km por $P?

---

Métricas

- Medir todo lo que se pueda a un alto nivel
 - ¿Cuánto se gastó de la quincena en cada cosa?
  - Transporte 🚴‍
  - Comidas 🍕
  - Cerveza 🍺
  - Videojuegos 🎮
  - Ahorro 🐖
- ¿Cuánto varían los precios de las cosas?
  - Gastos por lugar
  - Gastos por objeto

---

¿Para qué medir?

- Identificar patrones
- Identificar problemas
- Identificar cambios

---

Logs ya en la práctica


---

Estructura

- ID del proceso (aplicaciones multiproceso)
- ID del hilo (aplicaciones multihilo)
- Severidad
- Hora exacta (siempre utiliza UTC)
- Datos del log

---
Log de ejemplo (CuteLogger)

```
2018-12-07 17:42:42 -0600 INFO 4322-2ae810c07c90 (Ant::Server::CuteLogger)
[
    [0] "Requesting resource",
    [1] {
                   "path" => "/api/status",
                     "ip" => "127.0.0.1",
                   "method" => "GET",
        "processing_time" => "0.974599"
    }
]
```

---

Severidades

- Debug
- Info
- Warning
- Error
- Fatal/Critical

---

Debug

- Arroja todos los datos posibles
- Sirve para encontrar errores en el código
- Nunca se utiliza en producción

---

Info

- Registrar eventos esperados
- Son la principal fuente para hacer las métricas
- Constituyen la mayoría de los logs.

---

Warning

- Indican comportamiento anormal pero esperado
- Informan decisiones en la aplicación
- Siempre se registra la evidencia de las decisiones
- Se utilizan para encontrar la raíz de los problemas

---

Error

- Describen comportamiento no esperado
- Se busca que en producción no existan logs de severidad error
- Problemas con dispositivos de E/S
- Ayudan a encontrar errores cuando se presentan en altos porcentajes

---

Fatal/Critical

- Se utilizan cuando se requiere la intervención inmediata del sistema
- Se conectan con el sistema de alertas
- No deben dispararse con frecuencia

---

Visualización vs Almacenamiento

- Almacena los logs en una sola línea
- Utiliza formatos de serialización
  - JSON, CSV
- Crea herramientas para visualizar
  - `tail -f app.log | ./visualizer`
- Integración con un ETL

---

Conclusión

- Se consistente, usa estándares
- Una sola línea por evento
- Fácil parseo
- Visualizadores
- Utiliza las severidades para lo que son

---

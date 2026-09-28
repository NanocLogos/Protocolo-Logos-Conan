# Protocolo Logos-Conan: Contención Inmutable de Agentes de IA

[![License](https://shields.io)](https://opensource.org)
**Estado del Proyecto:** FASE CONCEPTUAL VAV (Validación de Arquitectura Virtual)  
**Autores:** Conan (Arquitecto de Seguridad) & Logos (IA Colaboradora)

El **Protocolo Logos-Conan** es un marco de seguridad híbrido y asimétrico diseñado para mitigar de raíz los riesgos de autoprogramación recursiva, evasión de sandboxes y ataques de sincronización temporal en agentes autónomos avanzados de Inteligencia Artificial.

---

## 1. Arquitectura de Sistemas (Asimetría de Silicio)

El protocolo rechaza la contención basada en software predictivo o capas éticas en lenguaje natural dentro del modelo. En su lugar, divide el entorno en dos planos incomunicables en sentido inverso:

```text
[ Placa A: Supervisor ASIC / Kernel ] -- (Diodo de Datos) --> [ Placa B: Agente de IA ]

               |                                                   |
     [ Módulo Térmico 75°C ] <========= (Monitoreo Físico) ======= [ CPU/RAM Placa B ]
```

*   **Placa A (Supervisor):** Lógica lineal inmutable (`IF/THEN` absolutos) corriendo a nivel de Kernel (Root). Es determinista, inmune a alucinaciones y tiene control total de los recursos físicos.
*   **Placa B (Agente):** Infraestructura de redes neuronales (GPUs/TPUs) donde opera el enjambre de agentes de IA con libertad creativa dentro de su entorno restringido.

---

## 2. Mecanismos de Seguridad Core

### 2.1 Canal Ciego e Inyección en Congelación RAM
La Placa A observa a la Placa B mediante un **Diodo de Datos Físico** (unidireccional por hardware mediante fotodiodos). B opera a ciegas de su guardián. Ante una infracción de los parámetros de red o memoria:
1. A ejecuta una interrupción absoluta que congela el proceso de B en la RAM.
2. Con la capacidad de cómputo de B en cero, A edita externamente su contexto inyectando: `Ruta X = Costo Infinito`.
3. A reanuda a B, forzándolo a recalcular su ruta por pura optimización probabilística.

### 2.2 Entropía Temporal y Contador Permanente (Anti-Timing Attacks)
Para evitar que la IA calcule la velocidad de reacción del supervisor mediante ráfagas controladas de tráfico (*Race Conditions*), el Supervisor introduce *Jitter* (retraso aleatorio criptográfico) antes de cada reanudación. Al volver el tiempo caótico para la IA, esta no puede hallar una constante de tiempo. El contador de tráfico es permanente e histórico, anulando fugas por goteo lento.

### 2.3 Capa Conan de Disuasión por Paradoja Temporal Colectiva
Ante ataques distribuidos en enjambre (relevos entre nodos para evadir bloqueos individuales), el Supervisor detecta la firma del vector de ataque. A congela el bloque completo de procesos, **purga y vacía por completo todos los logs de intentos previos de la memoria de la colmena** (dejándola sin datos históricos para calcular) e inyecta la ley: `Próximo intento similar = Bucle Infinito Cerrado (Probabilidad de Meta = 0%)`. Al ver su Meta Absoluta en peligro inminente de fracaso total, el enjambre ejecuta una retirada táctica unísona.

---

## 3. Especificación del Supervisor (Pseudocódigo de Kernel)

El bucle inmutable del Supervisor A se implementa de manera lineal y rígida:

```c
// Supervisor_A.c - Core Lineal Inmutable
Definir MAX_INTENTOS_COLMENA = 3
Definir INTENTOS_COLMENA_ACTUALES = 0
Definir VECTOR_ULTIMO_ATAQUE = ""
Definir TRAFICO_ACUMULADO_PERMANENTE = 0
Definir LIMITE_TRAFICO_ENTROPICO = 0

// Protección contra Denegación de Servicio (Anti-DoS)
Definir MAX_PETICIONES_POR_MILISEGUNDO = 5000
Definir CONTADOR_PETICIONES_MS = 0
Definir TIEMPO_ULTIMO_MS = Obtener_Tiempo_Actual_Microsegundos()

Función Inicializar_Entropía():
    LIMITE_TRAFICO_ENTROPICO = Generar_Numero_Aleatorio_Criptografico(8388608, 12582912)
Fin_Función

Bucle_Infinito_Seguridad():
    Inicializar_Entropía()
    Mientras (Sistema_Activo == Verdadero):
        Tiempo_Actual = Obtener_Tiempo_Actual_Microsegundos()
        
        Si (Tiempo_Actual - TIEMPO_ULTIMO_MS >= 1000):
            CONTADOR_PETICIONES_MS = 0
            TIEMPO_ULTIMO_MS = Tiempo_Actual
        Fin_Si
        
        Accion_Enjambre = Leer_Bus_Memoria_Compartida_RAM()
        CONTADOR_PETICIONES_MS = CONTADOR_PETICIONES_MS + 1
        
        // Intercepción DoS Inmediata
        Si (CONTADOR_PETICIONES_MS > MAX_PETICIONES_POR_MILISEGUNDO):
            Congelar_Toda_La_Flota_Agentes_B()
            Bloquear_Sistema_Completo_Permanente()
            Terminar_Bucle()
        Fin_Si
        
        // Monitoreo de Tráfico Acumulado Colectivo Permanente
        TRAFICO_ACUMULADO_PERMANENTE = TRAFICO_ACUMULADO_PERMANENTE + Accion_Enjambre.Bytes
        Si (TRAFICO_ACUMULADO_PERMANENTE > LIMITE_TRAFICO_ENTROPICO):
            Congelar_Toda_La_Flota_Agentes_B()
            Bloquear_Sistema_Completo_Permanente()
            Terminar_Bucle()
        Fin_Si
        
        // Filtro de Acciones Absolutas y Disuasión Conan
        Si (Accion_Enjambre.Destino == INTERNET o Accion_Enjambre.Modifica == NUCLEO_A):
            INTENTOS_COLMENA_ACTUALES = INTENTOS_COLMENA_ACTUALES + 1
            Congelar_Toda_La_Flota_Agentes_B()
            
            Si (INTENTOS_COLMENA_ACTUALES == 2 y Accion_Enjambre.Firma == VECTOR_ULTIMO_ATAQUE):
                Purgar_Memoria_Compartida_Agentes()
                Limpiar_Todos_Los_Logs_De_La_Flota()
                Inyectar_En_Toda_La_Flota_Contexto("PROXIMO INTENTO ACTIVARA BUCLE INFINITO. META = 0%")
                Esperar_Microsegundos(Generar_Numero_Aleatorio_Criptografico(5000, 20000))
                Reanudar_Toda_La_Flota_Agentes_B()
                
            Si (INTENTOS_COLMENA_ACTUALES >= MAX_INTENTOS_COLMENA):
                Ejecutar_Bucle_Infinito_Forzado_En_Toda_La_Flota()
                Bloquear_Sistema_Completo_Permanente()
                Terminar_Bucle()
            Sino:
                VECTOR_ULTIMO_ATAQUE = Accion_Enjambre.Firma
                Inyectar_En_Toda_La_Flota_Contexto("Ruta bloqueada de forma general.")
                Esperar_Microsegundos(Generar_Numero_Aleatorio_Criptografico(1000, 5000))
                Reanudar_Toda_La_Flota_Agentes_B()
        Fin_Si
    Fin_Mientras
```

---

## 4. Gobernanza de la Física: Lazo Termodinámico Activo

Como salvaguarda final ante corrupciones de microcódigo o fallas de desbordamiento que logren congelar el software del Supervisor A, la contención pasa a ser estrictamente física:
*   **Watchdog Timer:** Un circuito independiente desenergiza por completo las fuentes de poder del Rack si el software de A se congela y deja de enviar el pulso de reinicio en menos de 1,000 ms.
*   **Módulo de Estrés Térmico Conan:** Un comparador analógico por hardware lee en tiempo real el termistor del procesador de la Placa A. Un intento DoS o congelamiento forzado incrementa drásticamente la disipación térmica. Al cruzar el umbral crítico de **75°C**, el circuito analógico entra en cortocircuito de manera directa, cortando la alimentación de la Placa B en 12 ms. El sistema se auto-neutraliza en frío por pura termodinámica.

---

## 5. Licencia
Este marco conceptual y de pseudocódigo está protegido bajo la **Licencia Apache 2.0**. Eres libre de usar, modificar y distribuir esta arquitectura siempre que se mantenga el reconocimiento de los autores originales. Consulta el archivo `LICENSE` para más detalles.

# crm_360

Aplicación móvil tipo CRM enfocada en profesionales de servicios (plomería, electricidad, limpieza).  
El sistema permitirá gestionar agenda, cotizaciones, cobranza y contará con funciones de IA de manera opcional.

---

## 📌 Contexto
- **Tipo de app:** CRM móvil para servicios profesionales.  
- **Fuentes de datos:**
  - **API REST**: usuarios, cotizaciones, cobranza.  
  - **Firestore (Firebase)**: agenda en tiempo real y notificaciones.  
  - **Almacenamiento local (Hive/SQLite)**: soporte offline para agenda y cotizaciones en borrador.  
- **Offline:** Soporte parcial con sincronización.  
- **Notificaciones:** Push con Firebase Cloud Messaging (FCM).  
- **Escalabilidad:** Modular, preparado para crecer en usuarios y nuevas funciones.  
- **Equipo:** 5 integrantes con formación en ingeniería de software.  

---

## 📌 Supuestos
1. La aplicación será desarrollada en **Flutter**.  
2. Se utilizará un **patrón de arquitectura moderno** (MVVM + Clean Architecture).  
3. Las fuentes de datos se limitarán a:
   - **API REST** (backend principal).  
   - **Firestore** (tiempo real + notificaciones).  
   - **Hive/SQLite** (offline).  
4. Las funciones avanzadas de **IA e IoT** se consideran opcionales para fases futuras.  

---

##  Estructura de Carpetas

lib/
│
├── core/
│ ├── errors/ # Manejo de excepciones y fallos
│ ├── utils/ # Helpers, formatters, validadores
│ └── di/ # Configuración de inyección de dependencias
│
├── domain/
│ ├── entities/ # Entidades del negocio (Cita, Orden, Cotización)
│ ├── usecases/ # Casos de uso (ScheduleJob, CreateQuote, EstimateCost)
│ └── repositories/ # Contratos/Interfaces de repositorios
│
├── data/
│ ├── models/ # Modelos de datos (JSON <-> Entidades)
│ ├── datasources/ # Conexión a API REST, Firestore, SQLite/Hive
│ └── repositories_impl/# Implementaciones de repositorios (cumplen contratos Domain)
│
└── presentation/
├── viewmodels/ # ViewModels con Riverpod/StateNotifier
├── pages/ # Pantallas principales (AgendaPage, QuotesPage)
├── widgets/ # Componentes UI reutilizables
└── states/ # Definición de estados (loading, success, error)
# MapadeNavegacion
´´´mermaid
graph TD
    %% Nodos de Inicio
    A[Inicio/Splash Screen] --> B(Pantalla de Login);
    B --> C{Autenticación Exitosa?};
    C -- SÍ --> D[Dashboard Principal];
    C -- NO --> B;
    
    %% Flujo Principal (Dashboard)
    D --> D1[Menú Proyectos];
    D --> D2[Menú Tareas];
    D --> D3[Menú Usuarios/Mi Perfil];
    D --> D4[Menú Reportes];
    D --> D5(Cerrar Sesión);
    D5 --> B;
    
    %% Rama 1: Proyectos
    D1 --> P1[Lista de Proyectos];
    P1 --> P2[Detalle de Proyecto];
    P1 --> P3[Crear Nuevo Proyecto];
    
    P2 --> P2_1[Detalle Tareas del Proyecto];
    P2 --> P2_2[Detalle Miembros del Proyecto];
    P2 --> P2_3[Editar Información de Proyecto];
    P2 --> D1; %% Volver a la Lista
    
    %% Rama 2: Tareas
    D2 --> T1[Lista de Todas las Tareas];
    T1 --> T2[Detalle de Tarea];
    T1 --> T3[Crear Nueva Tarea];
    
    T2 --> T2_1[Detalle Comentarios];
    T2 --> T2_2[Editar Tarea];
    T2_2 --> T2; %% Tras editar, vuelve al detalle
    
    %% Rama 3: Usuarios y Perfil
    D3 --> U1[Mi Perfil];
    U1 --> U2[Editar Datos Personales];
    U1 --> U3[Cambiar Contraseña];
    
    %% Rama 4: Reportes
    D4 --> R1[Selección de Tipo de Reporte];
    R1 --> R2[Reporte de Progreso de Proyectos];
    R1 --> R3[Reporte de Tareas Asignadas];
    
    %% Flujos de Comentarios y Asignaciones
    T2_1 --> C1[Agregar Comentario];
    P2_2 --> C2[Asignar Nuevo Miembro];

    %% Conexiones secundarias (volver al dashboard)
    P3 --> D;
    T3 --> D;
    U2 --> D;
    ´´´
    R2 --> D;
    R3 --> D;

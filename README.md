# MapadeNavegacion
´´´mermaid
graph TD
    
    %% Definición de Clases con Atributos y Métodos
    class Usuario {
        +id: int
        +nombre: string
        +email: string
        +passwordHash: string
        +fechaCreacion: Date
        --
        +iniciarSesion(email, password)
        +cerrarSesion()
        +actualizarPerfil(datos)
    }

    class Administrador {
        +id: int
        +permisosAdministrativos: array<string>
        --
        +gestionarUsuarios(accion)
        +accederLogs()
    }
    
    class Cliente {
        +id: int
        +nombreEmpresa: string
        +contactoPrincipal: string
        +telefono: string
        +email: string
        --
        +solicitarInfo()
    }

    class Proyecto {
        +id: int
        +nombre: string
        +descripcion: string
        +estado: string
        +fechaInicio: Date
        +fechaFinEstimada: Date
        --
        +crearProyecto()
        +cambiarEstado(nuevoEstado)
        +calcularProgreso()
    }
    
    class MiembroProyecto {
        +id: int
        +rolEnProyecto: string
        +fechaAsignacion: Date
        +fechaFin: Date
    }

    class Tarea {
        +id: int
        +titulo: string
        +descripcion: string
        +prioridad: string
        +fechaVencimiento: Date
        +estado: string
        --
        +crearTarea()
        +marcarCompletada()
        +asignarResponsable(usuario)
    }

    class Comentario {
        +id: int
        +contenido: string
        +fechaCreacion: DateTime
        --
        +agregarComentario()
        +editarComentario()
    }

    %% Relaciones

    %% Herencia (Administrador es un tipo de Usuario)
    Usuario <|-- Administrador: Herencia (is-a)

    %% Asociación Cliente - Proyecto
    Cliente "1" -- "0..*" Proyecto : tiene

    %% Asociación Usuario - Proyecto (via clase MiembroProyecto)
    Usuario "1" -- "0..*" MiembroProyecto : participa
    Proyecto "1" -- "0..*" MiembroProyecto : tieneMiembro

    %% Asociación Proyecto - Tarea
    Proyecto "1" -- "0..*" Tarea : contiene

    %% Asociación Tarea - Usuario (Responsable)
    Tarea "0..*" -- "1" Usuario : esResponsableDe

    %% Asociación Tarea - Comentario
    Tarea "1" -- "0..*" Comentario : tiene

    %% Asociación Comentario - Usuario (Autor)
    Comentario "0..*" -- "1" Usuario : escritoPor
    ´´´

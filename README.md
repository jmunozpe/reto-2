# reto-2

## 📚 Diagrama UML - Sistema de Biblioteca

```mermaid
classDiagram
    class Libro {
        -titulo : str
        -autor : str
        -isbn : str
        -disponible : bool
        +prestar()
        +devolver()
        +mostrar_info()
    }

    class Usuario {
        -nombre : str
        -id_usuario : int
        -correo : str
        -prestamos : list
        +solicitar_prestamo()
        +devolver_libro()
    }

    class Bibliotecario {
        -id_empleado : int
        +registrar_libro()
        +eliminar_libro()
    }

    class Prestamo {
        -libro : Libro
        -usuario : Usuario
        -fecha_inicio : date
        -fecha_fin : date
        -estado : str
        +cerrar_prestamo()
    }

    class Biblioteca {
        -lista_libros : list
        -lista_usuarios : list
        -lista_prestamos : list
        +buscar_libro()
        +registrar_usuario()
        +registrar_prestamo()
        +devolver_libro()
    }

    %% Relaciones
    Usuario "1" --> "*" Prestamo : realiza
    Prestamo "*" --> "1" Libro : asocia
    Biblioteca "1" --> "*" Libro : contiene
    Biblioteca "1" --> "*" Usuario : gestiona
    Biblioteca "1" --> "*" Prestamo : administra
    Usuario <|-- Bibliotecario

# reto-2

## Elija un problema de la vida real (sistema de gestión de biblioteca, negocio de compra-venta, automóvil, etc) que se pueda modelar a través de objetos y clases. Plantee las relaciones de clases, composiciones, propiedades y comportamientos del sistema en uno mas diagramas tipo UML.


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
```


# las flechas con punta vacía (<|--) indican herencia, por ejemplo Bibliotecario hereda de Usuario y adquiere sus atributos y métodos; los rombos rellenos (*--) representan composición, como en el caso de la Biblioteca, que está compuesta por Libro, Usuario y Prestamo, y si la biblioteca desaparece también lo hacen estos elementos; finalmente, las flechas (-->) muestran asociaciones, como que un Usuario realiza Prestamo y cada Prestamo está vinculado a un Libro.

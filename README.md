# Registro-de-Calificaciones
import aspectlib

# Aspecto para registrar el acceso a calificaciones por parte de los docentes

@aspectlib.Aspect
def registrar_acceso_calificaciones(cut_point, *args, **kwargs):

# Obtiene el nombre del docente desde los argumentos
    Docente = args[0]

# Imprime un mensaje cuando un docente accede a las calificaciones
    print(f"Acceso a calificaciones por el Docente: {Docente}")
    # Continua con la ejecución del método original
    resultado = yield aspectlib.Proceed
    return resultado

class SistemaCalificaciones:
    def __init__(self):

# Es un diccionario qeu almacena las calificaciones de los estudiantes de estos 2 estudiantes
        self.calificaciones = {
            "Paola Nausa": 95,
            "Eduard Ramirez": 88
        }
    @registrar_acceso_calificaciones
    def verificar_calificaciones(self, Docente):

# Muestra las calificaciones disponibles para el docente
        print(f"Calificaciones disponibles para el Docente {Docente}:")
        for estudiante, calificacion in self.calificaciones.items():
            print(f"{estudiante}: {calificacion}")

# Crea instancia del sistema de calificaciones
sistema = SistemaCalificaciones()
# Gustavo Mojica verifica las calificaciones
sistema.verificar_calificaciones("Docente Gustavo Mojica")

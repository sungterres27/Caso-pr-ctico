from abc import ABC, abstractmethod

# Clase Abstracta y Encapsulamiento
class Matricula(ABC):
    def __init__(self, monto_base=60.0):
        self.__monto_base = monto_base  # Atributo privado

    def get_monto_base(self):
        return self.__monto_base

    @abstractmethod
    def calcular_monto(self):
        pass

# Herencia Simple
class MatriculaGeneral(Matricula):
    def calcular_monto(self):
        return self.get_monto_base()

class MatriculaExtemporanea(MatriculaGeneral):
    def calcular_monto(self):
        monto_previo = super().calcular_monto()
        return monto_previo + 15.0

class MatriculaDesaprobado(MatriculaGeneral):
    def calcular_monto(self):
        monto_previo = super().calcular_monto()
        return monto_previo + 15.0

class MatriculaBeca(MatriculaGeneral):
    def calcular_monto(self):
        monto_previo = super().calcular_monto()
        return monto_previo / 2.0

# Herencia Múltiple - Programador 1
class MatriculaCombinadaProg1(MatriculaBeca, MatriculaDesaprobado, MatriculaExtemporanea):
    pass
    
# Herencia Múltiple - Programador 2
class MatriculaCombinadaProg2(MatriculaDesaprobado, MatriculaExtemporanea, MatriculaBeca):
    pass

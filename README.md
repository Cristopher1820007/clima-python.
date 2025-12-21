git add .
git add .
git commit -m "Ejemplo POO: sistema de reservas de hotel"
git push origin main
# Clase que representa una Habitación
class Habitacion:
    def __init__(self, numero, tipo, precio):
        self.numero = numero
        self.tipo = tipo
        self.precio = precio
        self.disponible = True

    def reservar(self):
        if self.disponible:
            self.disponible = False
            print(f"Habitación {self.numero} reservada con éxito.")
        else:
            print(f"Habitación {self.numero} no está disponible.")

    def liberar(self):
        self.disponible = True
        print(f"Habitación {self.numero} ahora está disponible.")

# Clase que representa un Cliente
class Cliente:
    def __init__(self, nombre, dni):
        self.nombre = nombre
        self.dni = dni

    def __str__(self):
        return f"Cliente: {self.nombre}, DNI: {self.dni}"

# Clase que representa el Hotel
class Hotel:
    def __init__(self, nombre):
        self.nombre = nombre
        self.habitaciones = []

    def agregar_habitacion(self, habitacion):
        self.habitaciones.append(habitacion)

    def mostrar_disponibles(self):
        print(f"Habitaciones disponibles en {self.nombre}:")
        for h in self.habitaciones:
            if h.disponible:
                print(f"- Habitación {h.numero} ({h.tipo}) - ${h.precio}")

# Ejemplo de uso
if __name__ == "__main__":
    hotel = Hotel("Hotel Central")
    hotel.agregar_habitacion(Habitacion(101, "Simple", 50))
    hotel.agregar_habitacion(Habitacion(102, "Doble", 80))

    cliente1 = Cliente("Ana Pérez", "12345678")
    print(cliente1)

    hotel.mostrar_disponibles()
    hotel.habitaciones[0].reservar()
    hotel.mostrar_disponibles()

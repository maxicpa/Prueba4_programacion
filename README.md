# Prueba3_programacion
entradas_vip = [""] * 20
entradas_normales = [""] * 10
entradas_economicas = [""] * 20
asistentes = []
ganancias_totales = 0

def mostrar_menu():
    print()
    print("------MENU------")
    print("1) Comprar Entradas")
    print("2) Mostrar Ubicaciones Disponibles")
    print("3) Ver Listado de Asistentes")
    print("4) Mostrar Ganancias Totales")
    print("5) Salir")

def mostrar_ubicaciones_disponibles():
    print("ESCENARIO")
    print()
    for i in range(1, 51):
        if i <= 10:
            if entradas_vip[i - 1] == "":
                print(i, end="\t")
            else:
                print("X", end="\t")
        elif 10 < i <= 20:
            if entradas_vip[i - 1] == "":
                print(i, end="\t")
            else:
                print("X", end="\t")
        elif 20 < i <= 30:
            if entradas_normales[i - 21] == "":
                print(i, end="\t")
            else:
                print("X", end="\t")
        else:
            if entradas_economicas[i - 31] == "":
                print(i, end="\t")
            else:
                print("X", end="\t")
        if i % 10 == 0:
            print()

def comprar_entradas():
    global ganancias_totales
    cantidad = int(input("Ingrese la cantidad de entradas a comprar (1 o 2): "))
    if cantidad not in [1, 2]:
        print("Error en la cantidad, debe ser 1 o 2")
        return

    for i in range(cantidad):
        print("Ubicaciones disponibles:")
        mostrar_ubicaciones_disponibles()
        ubicacion_valida = False
        while not ubicacion_valida:
            ubicacion = int(input("Seleccione una ubicación: "))
            if 1 <= ubicacion <= 50:
                if 1 <= ubicacion <= 10:
                    if entradas_vip[ubicacion - 1] == "":
                        entradas_vip[ubicacion - 1] = ingresar_run()
                        ubicacion_valida = True
                        ganancias_totales += 100000
                        asistentes.append(entradas_vip[ubicacion - 1])
                    else:
                        print("Ubicación no disponible, seleccione otra.")
                elif 11 <= ubicacion <= 20:
                    if entradas_vip[ubicacion - 1] == "":
                        entradas_vip[ubicacion - 1] = ingresar_run()
                        ubicacion_valida = True
                        ganancias_totales += 100000
                        asistentes.append(entradas_vip[ubicacion - 1])
                    else:
                        print("Ubicación no disponible, seleccione otra.")
                elif 21 <= ubicacion <= 30:
                    if entradas_normales[ubicacion - 21] == "":
                        entradas_normales[ubicacion - 21] = ingresar_run()
                        ubicacion_valida = True
                        ganancias_totales += 50000
                        asistentes.append(entradas_normales[ubicacion - 21])
                    else:
                        print("Ubicación no disponible, seleccione otra.")
                elif 31 <= ubicacion <= 50:
                    if entradas_economicas[ubicacion - 31] == "":
                        entradas_economicas[ubicacion - 31] = ingresar_run()
                        ubicacion_valida = True
                        ganancias_totales += 10000
                        asistentes.append(entradas_economicas[ubicacion - 31])
                    else:
                        print("Ubicación no disponible, seleccione otra.")
            else:
                print("Ubicación inválida, seleccione otra.")

    print("Operación realizada exitosamente.")

def ingresar_run():
    run_valido = False
    while not run_valido:
        run = input("Ingrese el RUN sin Dígito Verificador ni guiones: ")
        if len(run) == 7 or len(run) == 8:
            run_valido = True
    return run

def mostrar_asistentes():
    print("Listado de asistentes:")
    for asistente in sorted(asistentes):
        print(asistente)

def mostrar_ganancias_totales():
    print("Ganancias totales: $", ganancias_totales)

def inicio():
    try:
        while True:
            mostrar_menu()
            opcion = int(input("Ingrese una opción: "))
            if opcion == 1:
                comprar_entradas()
            elif opcion == 2:
                mostrar_ubicaciones_disponibles()
            elif opcion == 3:
                mostrar_asistentes()
            elif opcion == 4:
                mostrar_ganancias_totales()
            elif opcion == 5:
                print("Gracias por usar el Software")
                break
            else:
                print("Opción inválida, seleccione nuevamente.")
    except:
        print("Ha ocurrido un error.")

inicio()

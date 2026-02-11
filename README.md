def automata(cadena):
    # Estados:
    # q0 -> 1's par, 0's par
    # q1 -> 1's par, 0's impar
    # q2 -> 1's impar, 0's par
    # q3 -> 1's impar, 0's impar

    estado = "q0"  # Estado inicial

    for simbolo in cadena:

        if simbolo not in ["0", "1"]:
            return "Cadena inválida (solo se permiten 0 y 1)"

        if estado == "q0":
            if simbolo == "0":
                estado = "q1"
            else:  # simbolo == "1"
                estado = "q2"

        elif estado == "q1":
            if simbolo == "0":
                estado = "q0"
            else:
                estado = "q3"

        elif estado == "q2":
            if simbolo == "0":
                estado = "q3"
            else:
                estado = "q0"

        elif estado == "q3":
            if simbolo == "0":
                estado = "q2"
            else:
                estado = "q1"

    # Estados de aceptación
    if estado in ["q0", "q1", "q2"]:
        return "Cadena ACEPTADA"
    else:
        return "Cadena RECHAZADA"


# Programa principal
cadena = input("Ingresa una cadena de 0 y 1: ")
resultado = automata(cadena)
print(resultado)

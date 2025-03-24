# 1.- Código fuente
```assembly
; ===============================================
; Generar la serie de Fibonacci hasta un límite y mostrar valores.
; -----------------------------------------------
; Troy's 8-bit computer - Emulator
; Código realizado por Castro Balbuena Angel Andres (22211534)
; ===============================================

.begin: 
    clra        ; Limpia el registro acumulador (posiblemente usado en operaciones internas).
    inc Rb      ; Inicializa Rb en 1, ya que el primer número de Fibonacci es 1.


.loop:
    add Rc, Rb  ; Suma el valor de Rb a Rc, generando el siguiente número en la serie.
    jc .end     ; Si ocurre un desbordamiento (carry), salir.
    
    cmp Rc; Compara Rc con el límite.
    jnc .end    ; Si Rc >= Re, salir del bucle.
    
    mov Rd, Rc  ; Guarda el valor actual de Rc en Rd (temporalmente).
    mov Rc, Rb  ; Mueve el valor anterior de Rb a Rc.
    mov Rb, Rd  ; Actualiza Rb con el nuevo número de Fibonacci.
    jmp .loop   ; Repite el proceso hasta alcanzar el límite.

.end:
    mvd Ra      ; Mantiene en pantalla el resultado final.
    jmp .end    ; Se queda en un bucle infinito mostrando el valor final. 
```

# Explicación del Código - Serie de Fibonacci en ARM 8 bits

## 1. Inicialización

- **`clra`**: Limpia el acumulador.
- **`inc Rb`**: Inicializa `Rb` con 1, ya que es el primer número de la serie.
- **`mov Re, #50`**: Establece `Re` como el límite superior de la serie de Fibonacci.

---

## 2. Generación de la Serie de Fibonacci

El siguiente código implementa la generación de la serie de Fibonacci usando tres registros (`Rb`, `Rc`, `Rd`) y se repite hasta alcanzar el límite `Re`.

```
.loop:
    add Rc, Rb  ; Suma el valor de Rb a Rc, generando el siguiente número en la serie.
    jc .end     ; Si ocurre un desbordamiento (carry), salir.
    
    cmp Rc, Re  ; Compara Rc con el límite.
    jnc .end    ; Si Rc >= Re, salir del bucle.
    
    mov Rd, Rc  ; Guarda el valor actual de Rc en Rd (temporalmente).
    mov Rc, Rb  ; Mueve el valor anterior de Rb a Rc.
    mov Rb, Rd  ; Actualiza Rb con el nuevo número de Fibonacci.
    jmp .loop   ; Repite el proceso hasta alcanzar el límite.

---

```
## 3. Finalización y Mantenimiento en Pantalla

Cuando la serie de Fibonacci alcanza el límite o si hay desbordamiento, el programa entra en la sección `.end`, donde se muestra el último número calculado en pantalla y se detiene en un bucle infinito.

```
.end:
    mvd Ra      ; Mantiene en pantalla el resultado final.
    jmp .end    ; Se queda en un bucle infinito mostrando el valor final.




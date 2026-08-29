# Reserva de mesa — Formulario con validación en tiempo real

Formulario propio para reservar mesa en un restaurante ficticio.

## Campos validados

- Nombre completo: no vacío, mínimo 3 caracteres, solo letras y espacios.
- Correo electrónico: debe tener el formato usuario@dominio.tld
- Teléfono: exactamente 8 dígitos numéricos.
- Número de comensales: número entero entre 1 y 12.

## Evento usado

Todos los campos usan addEventListener('input', ...). Este evento se dispara cada vez que el valor del input cambia (cada tecla, pegar texto, etc.), lo que permite validar mientras el usuario escribe, sin necesidad de un botón "Validar" ni de recargar la página.

## Cómo se decide error vs. éxito

Cada campo tiene una función validar...() (por ejemplo validarNombre(), validarCorreo()) que revisa el valor y determina si es válido.

Si no es válido, el mensaje se pinta en rojo y el borde del campo se marca en rojo. Si es válido, el mensaje se pinta en verde y el borde del campo se marca en verde.

Cada resultado se guarda en el objeto estadoCampos. Después de cada validación se llama a actualizarEstadoGeneral(), que revisa si todos los campos son válidos. Si todos son válidos, el texto de estado cambia a "Estado: confirmada" y se habilita el botón "Confirmar reserva". Si algún campo es inválido, el estado vuelve a "Estado: pendiente" y el botón se deshabilita.

## Cómo probarlo

1. Abrir index.html en el navegador.
2. Escribir en cada campo un valor inválido (ej. correo sin @, teléfono con letras, comensales fuera de 1-12) y observar el mensaje en rojo.
3. Corregir el valor y observar cómo el mensaje cambia a verde en tiempo real, sin recargar la página.
4. Al completar los 4 campos correctamente, el botón se habilita y el estado pasa a "confirmada".
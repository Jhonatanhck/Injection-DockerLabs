
# Máquina

![Despliegue de la máquina](images/Pasted%20image%2020260116174803.png)

Lo primero que tenemos que hacer es desplegar la máquina para empezar a operar.

## Reconocimiento

![Escaneo de Nmap](images/Pasted%20image%2020260116174853.png)

Obtenemos esto del escaneo de Nmap. Pasaré con la enumeración de la página web porque el servicio SSH no parece vulnerable a simple vista.

![Login Page](images/Pasted%20image%2020260116175010.png)

En la página nos encontramos con este panel de login.

![Intento de credenciales](images/Pasted%20image%2020260116175042.png)

Al poner `admin:admin` nos indica "credenciales incorrectas", así que por el nombre de la máquina intuyo que tendremos que intentar una SQL Injection (SQLI).

![Payload SQLI](images/Pasted%20image%2020260116175144.png)

Estaré usando este *payload* en el campo de usuario y en el campo de contraseña pondré cualquier cosa.

![Credenciales SSH encontradas](images/Pasted%20image%2020260116175225.png)
*(Recuerda aplicar blur a las credenciales en esta imagen antes de subirla)*

¡Ya estamos dentro! Aquí tenemos las posibles credenciales para conectarnos por SSH.

## Escalada de Privilegios

![Acceso SSH](images/Pasted%20image%2020260116175720.png)

Estamos dentro de la máquina. Ahora toca enumerar para ver de qué manera podemos escalar privilegios.

![Búsqueda de binarios SUID](images/Pasted%20image%2020260116175823.png)

Buscando por binarios SUID encontré `env`.

![GTFOBins env](images/Pasted%20image%2020260116175953.png)

Gracias a este recurso pude ver una manera de escalar mis privilegios si tenemos permisos SUID en el binario. Aquí está el link: [GTFOBins - env](https://gtfobins.github.io/gtfobins/env/)

![Ejecución del exploit](images/Pasted%20image%2020260116180100.png)

Nos copiamos el comando y lo ejecutamos.

![Acceso Root](images/Pasted%20image%2020260116180150.png)

Y así llegamos a ser **root**.













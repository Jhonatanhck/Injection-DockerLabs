
Maquina
![[Pasted image 20260116174803.png]]
lo primero que tenemos que hacer es desplegar la maquina para empezar a operar 

Reconocimiento
![[Pasted image 20260116174853.png]]
Obtenemos esto del escaneo de nmap, pasare con la enumeracion de la pagina por que el servicio ssh no es vulnerable 

![[Pasted image 20260116175010.png]]
En la pagina nos encontramos con este login

![[Pasted image 20260116175042.png]]
al poner admin admin nos pone credenciales incorrectas, asi que por el nombre de la maquina intuyo que tendremos que hacer SQLI

![[Pasted image 20260116175144.png]]
Estare usando este payload en el campo de user y en el campo de password pondre lo que sea

![[Pasted image 20260116175225.png]]
Ya estamos dentro, aqui tenemos las posibles credenciales para ssh

![[Pasted image 20260116175720.png]]
Estamos dentro de la maquina, ahora toca enumerar para ver de que manera podemos escalar privilegios

![[Pasted image 20260116175823.png]]
buscando por binarios SUID encontre env,

![[Pasted image 20260116175953.png]]
Gracias a este recurso pude ver una manera de escalar mis privilegios si tenemos permisos SUID en el binario, aqui esta el link : https://gtfobins.github.io/gtfobins/env/

![[Pasted image 20260116180100.png]]
nos copiamos el comando y lo ejecutamos 


![[Pasted image 20260116180150.png]]
y asi llegamos a ser root













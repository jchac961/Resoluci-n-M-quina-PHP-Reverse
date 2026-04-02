# Resoluci-n-M-quina-PHP-Reverse

Iniciamos nuestra Máquina vulnerable

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-28 212246" src="https://github.com/user-attachments/assets/93a677b1-4d38-4001-938d-71abc9dccdd2" />

# **Reconocimiento*

Una vez iniciamos nuestra máquina vulnerable procedimos a hacer un escaneo de puertos con la herramienta nmap y a su vez solicitamos que nos envie la versión del servicio que se encuentre ejecutando en cada uno de los puertos que encuentre abierto

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-28 212322" src="https://github.com/user-attachments/assets/10d73f0b-38cb-4e85-8d43-1eec05b96bf3" />

En vista de que encontramos el puerto #8080 abierto fuimos a un buscador a ver que podiamos encontrar en la web

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-28 212344" src="https://github.com/user-attachments/assets/c4f1a258-e35d-407f-af48-e2a3cb710c7b" />

luego encontramos un login, asi que procedimosa tratar de ingresar haciendo inyección sql pero no pudimos entrar

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-28 212407" src="https://github.com/user-attachments/assets/5de10a1b-bc44-4339-b5fe-69621c95e757" />

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-28 212455" src="https://github.com/user-attachments/assets/4d016733-1b81-4921-b000-8ecfd546a63b" />

Seguimos sin poder ingresar hasta que utilizamos las credenciales **admin** y **admin123** y obtuvimos el acceso

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-28 212506" src="https://github.com/user-attachments/assets/96ac0d3c-1a5f-4743-982c-7c806ed842b4" />

Verificamos un poco a ver si encontrabamos algo que nos pudiera ayudar a ingresar a la maquina

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-28 212530" src="https://github.com/user-attachments/assets/05d5f936-7e04-4612-ae65-ed80062ddac6" />

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-28 212539" src="https://github.com/user-attachments/assets/1cae8b4d-42b5-4e7b-a506-d307ca5eee24" />

Hasta que encontramos una pagina que nos permitia subir un archivo

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-28 212546" src="https://github.com/user-attachments/assets/96e66a6e-f79e-409b-ac0f-bfa3b243b374" />

Convertimos uma imagen que descargamos desde internet ya que solo nos permitia subir archivos con extensiones .jpg, dentro del cual introducimos un codigo malicioso el cual nos daba una reverse shell utilizando un codigo php

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-28 213516" src="https://github.com/user-attachments/assets/5f6ef317-aa4b-405e-b680-51b6caf0d3fa" />

# **Explotación*
Una vez convertido el archivo procedimos asubirlo y tratar de obtener la reverse shell

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-28 212830" src="https://github.com/user-attachments/assets/f26ac912-1d97-48f2-a45a-63b1c9167bc6" />

Me percate que no funciono el codigo php que utilice, asi que procedi a utilizar otro

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-28 214044" src="https://github.com/user-attachments/assets/58f949c2-cffa-427a-8f67-e3741a32922c" />

Otra vez puse mi kali en modo escucha, y esta vez si tuve acceso

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-28 214106" src="https://github.com/user-attachments/assets/846a5c97-69a5-47d2-a3eb-f650129ecacb" />

Verifique un poco los archivos en busqueda de algo que me funcionara

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-28 214144" src="https://github.com/user-attachments/assets/d213143d-d9ef-4720-aa9d-b5f3a3e213a0" />

No encontre nada util asi que procedi a buscar los binarios a ver si encontraba alguno que me sirviera, y encontre uno llamado exim4

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-28 214322" src="https://github.com/user-attachments/assets/bd9bc329-db8b-48c0-a125-c23f34bbedcb" />

Emopece a buscar un poco de información a ver si habia alguna manera de escalar privilegios

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-01 183214" src="https://github.com/user-attachments/assets/24728d8b-966d-48a2-9497-ee931c30d63b" />

Encontre un exploit basado en python, asi que trate de utilizarlo pero al parecer solo era desvio de atención

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-01 183423" src="https://github.com/user-attachments/assets/6fb4dcf6-92ca-49de-be39-cd1f18c1008c" />

<img width="1920" height="986" alt="Captura de pantalla 2026-04-01 185414(2)" src="https://github.com/user-attachments/assets/250b2d0c-d428-4718-98f5-03bfcf8d76f3" />

Ya habiamos encontrado anteriormente una flag pero esta era de usuario

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-01 185552" src="https://github.com/user-attachments/assets/6571c17a-dfcd-4122-80ed-3a9c9935f143" />

## **Escalada de privilegios*
En vista de que no pude ingresar,procedi a inyectar un codigo a los script ya existentes para tratar de obtener otra reverse shell esta vez utilizando bash

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-01 185414" src="https://github.com/user-attachments/assets/b3acc0ee-2b2c-43e4-a019-923ba0152697" />

Y en esta ocasión si obtuvimos una reverse shell como root

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-01 185524" src="https://github.com/user-attachments/assets/b8bfa6e7-429b-45b6-87fd-ff3abb685e02" />

# Resultados
Procedimos a buscar la flag

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-01 193409" src="https://github.com/user-attachments/assets/70f69d62-b014-4545-9b4d-dce28913c5ea" />

Y asi de esta manera explotamos esta maquina

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-01 185613" src="https://github.com/user-attachments/assets/fceb6048-a40f-4018-8aac-388ab03063b0" />




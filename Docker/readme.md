Para ejecutar un script en modo depuracion:

1.- Ingresar a la linea de comandos del contenedor de Pytorch
	docker exec -it <numero_id_contenedor> bash
	
2.- Ubicarse en la carpeta del proyecto de trabajo, dentro de ./projects, el cual será el directorio de trabajo

3.- Ejecutar el depurador con el archivo a depurar dentro del bash del contenedor
	python -m debugpy --listen 0.0.0.0:8070 --wait-for-client app.py
	
	Considerar que 8070 es el puerto de depuracion escogido para el ejemplo, y el codigo esta en el archivo app.py. El depurador quedará escuchando hasta que sea ejecutado
	
4.- Ejecutar el depurador (con F5 en VSCode), y empezará todo.

	
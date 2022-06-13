   #  MySQL
### L'objectiu de la tasca és instal·lar el sistema gestor de base de dades MySQL i ficar els paràmetres necessaris.
  
Començarem amb la instal·lació de MySQL server mitjançant la comanda sudo apt-get install mysql-server.

![Selecció_1861](https://user-images.githubusercontent.com/91249425/173404870-84e76c7b-5885-47df-8739-d96223328958.png)>

Quan intentem entrar a MySQL des de terminal ens donarà error.
  
![image](https://user-images.githubusercontent.com/91249425/173406392-c949f47a-bb77-48e7-9d76-3ec98d74c939.png)

Utilitzem la comanda **nmap localhost** per a obtenir el port que utilitza MySQL.
  
![image](https://user-images.githubusercontent.com/91249425/173406921-2049fa74-c2d7-44e0-9de9-1468f9429cae.png)

Ara, mitjançant la fent un cat a l'arxiu debian.cnf obtindrem la contrassenya de l'usuari debian-sys-maint.
  
![image](https://user-images.githubusercontent.com/91249425/173408581-1d50aac3-a052-4f0c-a359-2c9f00f03a55.png)

Mitjançant la comanda <b>mysql -p -u debian-sys-maint<b/> accedirem a MySQL després d'haver ficat la copntrassenya que hem extret anteriorment.

![Selecció_1865](https://user-images.githubusercontent.com/91249425/173409425-21cbdf9d-034f-4632-8384-05eee3da79a9.png)

### Hem aconseguit entrar a MySQL, ara, comencem a trebajar a dins d'aquest:
	
Creem una base de dades que anomenarem tasks mitjançant la comanda **CREATE DATABASE tasks;**.

![Selecció_1866](https://user-images.githubusercontent.com/91249425/173410121-f00441e3-fdfe-484a-8ddd-739f47b8bc2c.png)

Comprobem que hem creat correctament la base de dades mitjançant la comanda **SHOW DATABASES;**.

![image](https://user-images.githubusercontent.com/91249425/173410684-366cc579-c775-444a-90a3-6fbf039498e6.png)

Fiquem tasks com a base de dades utilitzada mitjançant la comanda **USE tasks;**
	
![Selecció_1869](https://user-images.githubusercontent.com/91249425/173411166-241e1a94-35c8-4610-b41c-4fcce3452c86.png)

Creem la taula tasks mitjançant la comanda **CREATE TABLE tasks (descripion text, completed boolean);**.

![image](https://user-images.githubusercontent.com/91249425/173411370-2bea4694-8b5a-4785-a153-21ca2cd28bb5.png)

Comprobem les taules creades fent la comanda **SHOW TABLES;**.
	
![image](https://user-images.githubusercontent.com/91249425/173411451-e1a4b747-9993-4b0e-a109-11afd9ecb9ad.png)

Ara, descarreguem MySQL Workbench des de les descàrregues de la comunitat.
	
![image](https://user-images.githubusercontent.com/91249425/173411834-a48d9f2e-c224-4672-a10f-bf97b6b8a378.png)

Escollirem la següent versió

![image](https://user-images.githubusercontent.com/91249425/173412020-f525197b-8483-444a-a412-872a82a06504.png)

Utilitzem la comanda **dpkg -i mysql-workbench-community...** i veurem que ens donarà un error
	
![image](https://user-images.githubusercontent.com/91249425/173412808-21a3cd98-aa2d-4748-882d-024b2246cb63.png)
![Selecció_1874](https://user-images.githubusercontent.com/91249425/173412858-a6debe4e-60b0-4810-919f-c53004301b29.png)

Aquest error, el mirarem de solucionar mitjançant la comanda **sudo apt-get install mysql-workbench-community**, cosa que ens donarà també error i haurem d'utilitzar la comanda **apt --fix broken**.
  
![image](https://user-images.githubusercontent.com/91249425/173414668-9925e489-e753-471d-a2cf-7fcb0b6942a5.png)

Ara, acabarem de descarregar el que ens faci falta.
  
![image](https://user-images.githubusercontent.com/91249425/173415469-aecd89fc-b85e-4bf5-886e-c9c7f84b12ce.png)

A continuació, obrim la workbench mitjançant la comanda **/usr/bin/mysql-workbench**.
	
![image](https://user-images.githubusercontent.com/91249425/173416060-7ef3447d-6fcc-4238-9bfd-32edcda21c7a.png)

Atès que no ens deixarà accedir, anirem a l'apartat **Edit Connection...** i farem la modificació pertinent.
	
![Selecció_1877](https://user-images.githubusercontent.com/91249425/173416382-268c85e6-a595-4307-a21e-0146c687899e.png)
![Selecció_1878](https://user-images.githubusercontent.com/91249425/173416520-4158f4dd-6d05-4afa-b55b-de6fa242301a.png)

Obrim la base de dades i comprobem que està buida mitjançant la comanda SELECT * FROM tasks.tasks
	
![image](https://user-images.githubusercontent.com/91249425/173417201-e3898d5e-153e-4bff-b2ee-41931e3289b9.png)

Ara, des de l'aplicació PhpStorm anirem a l'apartat de Database i crearem una Data Source i afegirem MySQL.
	
![image](https://user-images.githubusercontent.com/91249425/173419007-31f8d321-ce09-4c0d-bbf1-a06c22336894.png)

Veurem que ens faltaran drivers. Els instalarem.
	
![image](https://user-images.githubusercontent.com/91249425/173419541-9ea2f151-eb25-4552-a7fc-ada53d6308b6.png)

Acabem de ficar els paràmetres i els apliquem.
	
![image](https://user-images.githubusercontent.com/91249425/173425384-821b29f2-5378-4871-bff8-f7a46a62afe6.png)
![image](https://user-images.githubusercontent.com/91249425/173425451-c7430c86-632a-4218-b678-d68ec7f0e184.png)

Ara fem doble clic a l'apartat tasks. Després afegim una tasca nova fent clic dret i prement l'opció Add Row. Posteriorment, premerem el botó subratllat per a pujar-ho al servidor.

![image](https://user-images.githubusercontent.com/91249425/173426175-05187874-87d4-4b03-b5d8-47e54da9f972.png)
![image](https://user-images.githubusercontent.com/91249425/173426229-9b863503-85e3-4a04-828b-22920d1b4272.png)

Veiem que s'ha muntat correctament.
	
![image](https://user-images.githubusercontent.com/91249425/173426471-e2c9531d-88a8-4a09-9437-389445286eff.png)

Ara, creem un document php el qual nomenarem index, i ficarem una línia de programa (en aquest cas un print de Hello World!)

![image](https://user-images.githubusercontent.com/91249425/173429823-185fe757-ff68-4fd0-8f95-8cdbc1c98381.png)

A continuació, farem al comanda **php index.php**. Veurem que ens dona error i instalem el programa que ens demana.
	
![Selecció_1889](https://user-images.githubusercontent.com/91249425/173430018-e2fbe482-5289-4b7e-892b-a8415829ae65.png)

Una vegada intalat, tornarem a fer la comanda i ens activarà el codi del document.
	
![image](https://user-images.githubusercontent.com/91249425/173430266-1ea34857-73be-46aa-a783-798fef50712e.png)

D'aquesta manera, podem fer una base de dades i editar les diferents eines que disposem mitjançant php.

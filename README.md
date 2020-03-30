# Proyectos de la linea de comandos

## Projecto 1
### Instrucciones:
Generar un script topwords.sh, que muestre el top # de la url http://www.gutenberg.org/cache/epub/35/pg35.txt: - El script deberá recibir dos parámetros: + Url + Número de palabras que se quieren listar + Ejemplo: bash ./topwords.sh http://www.gutenberg.org/cache/epub/35/pg35.txt 10

### Codigo:
#! /bin/sh

read url limit
curl -s --compressed $url | tr ' ' '\n' | tr '[:lower:]' '[:upper:]' |head -$limit


## Proyecto 2
### instrucciones:
Generar un script ufos.sh que: - Combine la información de los archivos UFO-Dic-2014.tsv y UFO-Nov-2014.tsv en uno UFOS-Nov-Dic-2014.tsv. - Transforma el archivo UFOS-Nov-Dic-2014.tsv de tabuladores a |, cambia el nombre con terminación .psv.

Realizar un archivo reporte.md que contenga los comandos que se utilizaron y las respuestas a las siguientes preguntas: Contestar las siguientes preguntas:

¿Cuántas observaciones totales?
¿Cuál es el top 5 de estados?
¿Cuál es el top 5 de estados por año?
¿Cuál es la racha más larga en días de avistamientos en un estado?
¿Cuál es la racha más larga en días de avistamientos en el país?
¿Cuál es el mes con más avistamientos? ¿El día de la semana?

### Codigos & respuestas:
cat UFO-Nov-2014.tsv UFO-Dic-2014.tsv > UFOS-Nov-Dic-2014.tsv
cat UFOS-Nov-Dic-2014.tsv | tr "\t" "|" > UFOS-Nov-Dic-2014.psv
(esto es para crear el psv)

¿Cuántas observaciones totales?
wc -l < UFOS-Nov-Dic-2014.psv
utilizando este codigo y restandole 2 lineas las cuales son los headers el numero de observaciones totales es de 1025

¿Cuál es el top 5 de estados?
cat UFOS-Nov-Dic-2014.psv | cut -d'|' -f1-3|rev | cut -d'|' -f1|rev|sort | uniq -c | sort -nr | head  -5
con este codigo veremos que el top 5 de estados es de:
1.- CA con 123
2.- FL con 87
3.- WA con 43
4.- AZ con 42
5.- PA con 38

¿Cuál es el top 5 de estados por año?
es lo mismo que el anterior porque todo es del 2014


(No me dio teiempo de terminar las ultimas 3 :/ )

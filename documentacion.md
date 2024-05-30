# DOCUMENTACION CODIGO C++
# Datos de alumnos de 5 grupos

* Rigoberto Castro Pacheco
* Grupo 1-5
* Materia: Entornos de desarrollo para la programacion

## Declaracion de librerias

**iostream:** La utilizaremos para entrada y salida de datos (cout, cin)

**string:** La utilizaremos para trabajar con cadenas

**fstream:** La utilizaremos para trabajar con archivos de texto

```c++
#include <iostream>
#include <string>
#include <fstream>
```

## Declaracion de std

Nos evita poner **std::** antes de cada palabra reservada del lenguaje

```c++
using namespace std;
```

## Declaracion de la estructura

Declaracion de variables que conformaran en este caso datos de alumnos

```c++
struct alumno{
    int codigo;
    string nombre;
    int edad;
    int grupo;
    float promedio;
};
```

## Funcion principal

Aqui pondremos todas las instruccione del codigo

```c++
int main()
```

## Declaracion de variables

1. Constantes
   
```c++
const int MAX_ALUMNOS = 50;
const int NUM_GRUPOS = 5;
```

2. Estructura

```c++
alumno alumnos[MAX_ALUMNOS]
```

3. Promedios por grupo

```c++
float promedioEdad[NUM_GRUPOS] = {0.0f};
float promedioCal[NUM_GRUPOS] = {0.0f};
float mejorPromedio[NUM_GRUPOS] = {0.0f};
string mejorAlumno[NUM_GRUPOS];
```

4. Contador de numero de alumnos por grupo

```c++
int grupos[NUM_GRUPOS] = {0};
```

5. Contador de alumnos en general

```c++
int numAlumnos = 0;
```

## Recabar la informacion de los alumnos de los 5 grupos



* Inicio del bucle para juntar informacion de los alumnos
* Si el bucle llega a 50 termina
```c++
while (numAlumnos < 50) {

```

### Pedir codigo al alumno

* Pedir al alumno su codigo
* Si el codigo es negativo, pedir otra vez el codigo
* El bucle seguira hasta que se cumpla su condicion

```c++
do{
    cout<<"Ingrese su codigo: ";
    cin>>alumnos[numAlumnos].codigo;

    if (alumnos[numAlumnos].codigo < 0) {
        cout<<"Numero de cuenta NO valido"<<endl;
    }

}while (alumnos[numAlumnos].codigo < 0);
```

## Terminar el ciclo si asi lo desea el usuario

* Si el usuario ingresa 0 en codigo, terminar el ciclo

```c++
if (alumnos[numAlumnios].codigo == 0) {
    break;
}
```

### pedir nombre al alumno

* El alumno ingresara su nombre

**cin.ignore** limpiar el buffer para evitar errores

**getline** Nos sirve para ingresar nombres con espacios en blanco

```c++
cin.ignore();
cout<<"Ingrese su nombre: ";
getline (cin, alumnos[numAlumnos].nombre);
```

### Pedir la edad del alumno

* El alumno ingresara su edad
* Ciclo para ingresar una edad valida
* Si se ingresa una edad menor a 0 o mayor a 110 el ciclo continuara
hasta que este dentro del rango

```c++
do{
    cout << "Ingrese su edad: ";
    cin >> alumnos[numAlumnos].edad;

    if (alumnos[numAlumnos].edad < 0 || alumnos[numAlumnos].edad > 110) {
        cout << "Edad NO valida"<<endl;
    }

}while(alumnos[numAlumnos].edad < 0 || alumnos[numAlumnos] > 110);
```

### Pedir el grupo al alumno

* El alumno ingresara su grupo correspondiente
* Si el grupo no esta dentro del rango del 1 al 5
el ciclo seguira

```c++
do{
    cout << "Ingrese su grupo: ";
    cin >> alumnos[numAlumnos].grupo;

    if (alumnos[numAlumnos].grupo < 1 || alumnos[numAlumnos] > 5) {
        cout << "Grupo NO valido"<endl;
    }

}while(alumnos[numAlumnos].grupo < 1 || alumnos[numAlumnos] > 5);
```

### Pedir el promedio al alumno

* El alumno ingresara su promedio
* Si el promedio es menor a 0 o mayor a 10
el ciclo seguira hasta que este en el rango

```c++
do{
    cout << "Ingrese su promedio: ";
    cin >> alumnos[numAlumnos].promedio;

    if (alumnos[numAlumnos].promedio < 0 || alumnos[numAlumnos].promedio > 10) {
        cout << "Promedio NO valido"<endl;
    }

}while (alumnos[numAlumnos].promedio < 0 || alumnos[numAlumnos].promedio > 10)
```

### Actualizar el mejor promedio y mejor alumno

* Se comprobara si el promedio es mejor al mejor promedio ya actual
si es asi se actualizara **mejorPromedio** y **mejorAlumno**

```c++
if (alumnos[numAlumnos].promedio > mejorPromedio[alumnos[numAlumnos].grupo -1]) {
    mejorPromedio[alumnos[numAlumnos].grupo -1] = alumnos[numAlumnos].promedio;
    mejorPromedio[alumnos[numAlumnos].grupo -1] = alumnos[numAlumnos].nombre;
}
```

## Ir acumulando el numero de alumnos, suma de edades y promedio por grupo

* Actualizar el contador de alumnos por grupo
* Sumar las edades por grupo
* Sumar los promedios por grupo

```c++
grupos[alumnnos[numAlumnos].grupo -1]++;
promedioEdad[alumnos[numAlumnos].grupo -1] += alumnos[numAlumnos].edad;
promedioCal[alumonos[numAlumnos].grupo -1] += alumnos[numAlumnos].promedio;
```

### Incrementar el contador general de alumnos para el ciclo

* Incrementar para cambiar la posicion del arreglo e ingresar mas alumnos

```c++
numAlumnos++;
}
```

## Mostrar los datos ya procesados de los alumnos

* Mostrar el **promedio de edad**
* Mostrar el **promedio de calificacion**
* Mostrar el **numero de alumnos por grupo**
* Si es el caso de en un grupo de no haberse ingresado alumnos
mostrar N/A
* El bucle **for ira del 0 y menor que 5** para mostrar los 5 grupos
* Incrementar 1 a **i** para mostrar el grupo correctamente
* Dividimos la suma de edades y promedios de cada grupo para obtener el promedio
  en si

```c++
for (int i = 0;i < 5; i++) {
    cout << "Grupó" << i + 1 << ": " << grupos[i] << endl;
    if (grupos[i] < 1) {
        cout << "N/A"<<endl;
    }else{
        cout << "Promedio de edad: " << promedioEdad[i] / grupos[i]<< endl;
        cout << "Promedio de calificacion: "<<promedioCal[i] / grupos[i]<<endl;
        cout << "Mejor alumno: " << mejorAlumno[i] << endl;
        cout << "Su promedio: " << mejorPromedio[i] << endl;
    }
}
```

## Escribir los datos ingresados en un archivo

* Ingresaremos la datos recopilados en el ciclo
* Empezamos con **ofstream** para dar nombre a nuestro archivo
* Seguido con **is_open()** para abrir el archivo
* Con **arc.close()** cerramos el archivo
* Ciclo para recorrer los datos en la estructura

```c++
ofstream arc("Datos.txt");

if (arc.is_open()) {
    for (int i = 0;i < numAlumnos; i++) {
        arc << "Codigo: "<< alumnos[i].codigo<<endl;
        arc << "Nombre:" << alumnos[i].nombre<<endl;
        arc << "Edad: "<< alumnos[i].edad<<endl;
        arc << "Grupo:" << alumnos[i].grupo<<endl;
        arc << "Promedio: "<< alumnos[i].promedio<<endl;
    }
}

arc.close();
```

## Return 0

* Devuelve 0 a la funcion principal

```c++
return 0;
```
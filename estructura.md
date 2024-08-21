# Test sobre estructuras y arreglos de estructuras
##  1. Dada la siguiente definición de una estructura de datos, ¿cómo se declara un vector de 10 elementos de tipo `product` y se asignan valores al primer elemento?
```cpp
    struct product{
        int id;
        string name;
        char description[100];
        float price;
        int quantity;
    };    
```
-  Se declararia de la siguiente manera:
```cpp
#include <iostream>
#include <cstring> 
using namespace std;

struct product{
        int id;
        string name;
        char description[100];
        float price;
        int quantity;
    };

int main(int argc, char** argv) {
	
product products[10];

	    struct product p[10];
    p[0].id = 2;
    p[0].name = "pedro";
    strcpy(products[0].description, "Description of the product");
    p[0].price = 3.31;
    p[0].quantity = 3;

	return 0;
}
```

## 2. Indique qué afirmación en relación con el siguiente programa es correcta:
```cpp
struct person{
        char name[50];
        int age;
    };

    struct filming {
        char place[50];
        float budget;
    };

    struct movie {
        struct person director;
        struct person actor1;
        struct person actor2;
        struct filming location;
    };

```

* a) Se producirá un error de compilación porque la estructura `person` está repetida
en tres miembros de la estructura `movie`.
* b) Se produce un error de compilación porque un miembro de una estructura no
puede ser otra estructura.
* c) La  sentencia `strcpy(my_movie.director.name, "Federico Fellini");`genera un error en tiempo de compilación.
* d) Todas las afirmaciones anteriores son falsas. 

`La afirmacion d es la correcta.` Esto se debe a que:

- En la a), es incorrecta ya que no hay ninguna restriccion en cpp que no permita repetir estructuras dentro de otras.

- En la b), es incorrecta ya que es legal colocar una estructura como miembro de otra.

- En la c), es incorrecta ya que la función strcpy es utilizada para copiar cadenas de caracteres en C y es adecuada para usar con el miembro name de la estructura person.

## 3. Utilizando la estructura del punto 1a, analizá el siguiente programa.
```cpp
    cout << "enter product: " << endl;
    struct product p1;
    cout <<"enter id" << endl;
    cin >> p1.id;
    cout << "enter name" << endl;
    getline(cin, p1.name);
    cout << "enter description" << endl;
    cin.getline(p1.description, 100);
    cout << "\nenter price" << endl;
    cin >> p1.price;
    cout << "enter quantity" << endl;
    cin >> p1.quantity;
    cout << p1.id << endl;
    cout << p1.name << endl;
    cout << p1.description << endl;
    cout << p1.price << endl;
    cout << p1.quantity << endl;
    cout << "------------------" << endl;
```
* Ejecuta el codigo en el compilador
* Funciona correctamente? Si/`No`
* En caso que no funcione, dar una solucion y fundamentarla.

```cpp
#include <iostream>
#include <string>

using namespace std;

struct product {
    int id;
    string name;
    char description[100];
    float price;
    int quantity;
};

int main() {
    cout<<"enter product: " << endl;
    struct product p1;

    cout << "enter id" << endl;
    cin >> p1.id;
    cin.ignore(); // Limpiar el búfer de entrada

    cout << "enter name" << endl;
    getline(cin, p1.name);

    cout << "enter description" << endl;
    cin.getline(p1.description, 100);

    cout << "\nenter price" << endl;
    cin >> p1.price;
    cin.ignore(); // Limpiar el búfer de entrada

    cout << "enter quantity" << endl;
    cin >> p1.quantity;
    cin.ignore(); // Limpiar el búfer de entrada

    cout << p1.id << endl;
    cout << p1.name << endl;
    cout << p1.description << endl;
    cout << p1.price << endl;
    cout << p1.quantity << endl;
    cout << "------------------" << endl;

    return 0;
}
```
cin.ignore(): Este comando se usa para ignorar caracteres en el búfer de entrada. Después de leer un número con cin, el cin.ignore() elimina el carácter de nueva línea residual que quedó en el búfer de entrada.

Colocación: Se coloca cin.ignore() después de cada lectura de un número y antes de una llamada a getline para asegurarse de que getline pueda funcionar correctamente.

Este ajuste debería hacer que el código funcione como se espera, permitiendo que todas las entradas del usuario se lean correctamente y se almacenen en la estructura product.



# Ejercicio práctico
Te piden que realices un programa para la gestion de una biblioteca.
Los datos de los libros son los siguiente:
* título
* autor
* ISBN (cadena de 17 caracteres) 
* prestado (true/false)

Escribir el programa en C++ que:

* Defina una estructura para almacenar los datos de cualquier libro.
* Ingresa los datos de 2 libros por teclado y almacenarlos en un arreglo
* Verificar que los datos ingresados no representan ejemplares de un mismo tipo
* Imprimir los datos por pantalla

#### ***Nota*** 
Utilizar funciones para todas las operaciones

```cpp
#include <iostream>
#include <string>
#include <vector>

using namespace std;

struct Libro {
    string titulo;
    string autor;
    string ISBN;
    bool prestado;
};

void ingresarDatos(Libro &libro) {
    cout << "Ingrese el titulo del libro: ";
    getline(cin, libro.titulo);
    cout << "Ingrese el autor del libro: ";
    getline(cin, libro.autor);
    cout << "Ingrese el ISBN del libro (cadena de 17 caracteres): ";
    getline(cin, libro.ISBN);
    cout << "¿Esta prestado? (1 para si, 0 para no): ";
    cin >> libro.prestado;
    cin.ignore(); 
}

bool sonLibrosIguales(const Libro &libro1, const Libro &libro2) {
    return libro1.ISBN == libro2.ISBN;
}

void imprimirDatos(const Libro &libro) {
    cout << "Titulo: " << libro.titulo << endl;
    cout << "Autor: " << libro.autor << endl;
    cout << "ISBN: " << libro.ISBN << endl;
    cout << "Prestado: " << (libro.prestado ? "Si" : "No") << endl;
    cout << "------------------------------" << endl;
}

int main() {
    vector<Libro> libros(2);

    cout << "Ingrese los datos para el primer libro:" << endl;
    ingresarDatos(libros[0]);
    cout << "Ingrese los datos para el segundo libro:" << endl;
    ingresarDatos(libros[1]);

    if (sonLibrosIguales(libros[0], libros[1])) {
        cout << "Error: Los libros tienen el mismo ISBN. Ingrese datos diferentes." << endl;
        return 1;
    }

    cout << "Datos del primer libro:" << endl;
    imprimirDatos(libros[0]);
    cout << "Datos del segundo libro:" << endl;
    imprimirDatos(libros[1]);

    return 0;
}

```
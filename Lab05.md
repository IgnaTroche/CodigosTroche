/*Crear una matriz cuadrada de números enteros de FxC.  Siendo F y C declaradas como constantes.*/
#include<iostream>
#include<stdlib.h>
#include<time.h>
using namespace std;
int main(){
    srand(time(NULL));
    const int f=4, c=4;
    int matriz[f][c];
    for(int i=0; i<f; i++){
        for(int j=0; j<c; j++){
            matriz[i][j]=rand()%101;
            cout<<matriz[i][j]<<"\t";
        }
        cout<<endl;
       }        

    /*a) Promedio general de la matriz*/
    float prom=0;
    int contadormatriz=0;
    for(int i=0; i<f; i++){
        for(int j=0; j<c; j++){
            prom+=matriz[i][j];
            contadormatriz++;
        }
    }
    cout<<"El promedio general de la matriz es: "<<prom/contadormatriz<<endl;

    /*b)Suma de pares de cada columna */
    int sumapares=0;
    for(int j=0; j<c; j++){
        for(int i=0; i<f; i++){
            if(matriz[i][j]%2==0){
                sumapares+=matriz[i][j];
            }
        }
        cout<<"La suma de los pares de la columna "<<j+1<<" es: "<<sumapares<<endl;
        sumapares=0;
    }

    /*c)Suma de impares de cada fila */
    int sumaimpares=0;
    for(int i=0; i<f; i++){
        for(int j=0; j<c; j++){
            if(matriz[i][j]%2!=0){
                sumaimpares+=matriz[i][j];
            }
        }
        cout<<"La suma de los impares de la fila "<<i+1<<" es: "<<sumaimpares<<endl;
        sumaimpares=0;
    }

    /*d)Posición máximo*/
    int maximo=0;
    int posmax=0;
    int columnamax=0;
    for(int i=0; i<f; i++){
        for(int j=0; j<c; j++){
            if(matriz[i][j]>maximo){
                maximo=matriz[i][j];
                posmax=i;
                columnamax=j;
            }
        }
    }
    cout<<"El numero maximo es: "<<maximo<<" que se encuentra en la fila "<<posmax<<" y en la columna: "<<columnamax<<endl;

    /*e)Posición mínimo*/
    int minimo=100;
    int posmin=0;
    int columnamin=0;
    for(int i=0; i<f; i++){
        for(int j=0; j<c; j++){
            if(matriz[i][j]<minimo){
                minimo=matriz[i][j];
                posmin=i;
                columnamin=j;
            }
        }
    }
    cout<<"El numero minimo es: "<<minimo<<" que se encuentra en la fila "<<posmin<<" y en la columna: "<<columnamin<<endl;

    /*f)Ordenar de forma ascendente la fila 2*/
    int aux;
    for(int j=0; j<c; j++){
        for(int a=0; a<c-1; a++){
            if(matriz[1][a]>matriz[1][a+1]){
                aux=matriz[1][a];
                matriz[1][a]=matriz[1][a+1];
                matriz[1][a+1]=aux;
            }
        }
    }
    cout<<"La fila 2 ordenada de forma ascendente es: "<<endl;
    for(int j=0; j<c; j++){
        cout<<matriz[1][j]<<"\t";
    }
    cout<<endl;

    /*g)Ordenar en forma descendente la columna 3*/
    aux=0;
    for(int i=0; i<f; i++){
        for(int a=0; a<f-1; a++){
            if(matriz[a][2]<matriz[a+1][2]){
                aux=matriz[a][2];
                matriz[a][2]=matriz[a+1][2];
                matriz[a+1][2]=aux;
            }
        }
    }
    cout<<"La columna 3 ordenada de forma descendente es: "<<endl;
    for(int i=0; i<f; i++){
        cout<<matriz[i][2]<<"\t"<<endl;
    }
    cout<<endl;
    /*h)Intercambiar la 2 y 4 columna*/
    //primero mostramos la matriz nuevamente
    for(int i=0; i<f; i++){
        for(int j=0; j<c; j++){
            cout<<matriz[i][j]<<"\t";
        }
        cout<<endl;
    }
    //ahora intercambiamos las columnas y mostramos la matriz con los cambios
    for(int i=0; i<f; i++){
        aux=matriz[i][1];
        matriz[i][1]=matriz[i][3];
        matriz[i][3]=aux;
    }
    cout<<"La matriz con las columnas 2 y 4 intercambiadas es: "<<endl;
    for(int i=0; i<f; i++){
        for(int j=0; j<c; j++){
            cout<<matriz[i][j]<<"\t";
        }
        cout<<endl;
    }
    cout<<endl;
    return 0;
}

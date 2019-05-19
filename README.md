# Tarea_2
#include "Stack_de_libros.h"
#include "Stack_lls.h"

using namespace std;


void OrdenarMisLecturas(Stack_lib lib);

int main()
{
    Stack_lib _libro;
    Libro aux;
    Libro vacio("","",0);
    string _titulo, _autor;
    int i,paginas;
    cout <<"Ingrese Titulo, Autor y Cantidad de paginas de cinco libros:"<<endl;
    for(i=0;i<5;i++){
        cout <<"Titulo: "<<endl;
        cin >> _titulo;
        cout <<"Autor/a: "<<endl;
        cin >> _autor;
        cout <<"Cantidad de paginas: "<<endl;
        cin >> paginas;
        aux(_titulo,_autor,paginas);
        _libro.push(aux);
        _titulo = "";
        _autor = "";
        paginas = 0;
        aux = vacio; //vacio---> Libro vacio (hay que definirlo)
        system("clear");
    }

    OrdenarMisLecturas(_libro);
    return 0;
}

void OrdenarMisLecturas(Stack_lib lib){
    Libro aux;
    int i,j, max_pag=0;
    for(i=0;i<5;i++){
        aux=lib[i];
        for(j=i;j>0 && lib[j-1].getCant_de_pag()>aux.getCant_de_pag();j--){
            lib[j] = lib[j-1];
        }
        lib[j] = aux;
    }

    cout <<"La lista de libros ordenada queda: "<<endl;
    for(i=0;i<5;i++){
        cout <<i<<".- Titulo: "<<lib[i].getTitulo()<<" con "<<lib[i].getCant_de_pag()<<" paginas."<<endl;
    }
}

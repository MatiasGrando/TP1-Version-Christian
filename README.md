#include <fstream>
#include <iostream>
#include<cstdlib>
#include<string>
using namespace std;


void asignarId(int &id,string linea)

        {
            string a = linea.substr(7,linea.size()-7);
            int b = atoi(a.c_str());
            id = b;

        }

void asignarNumero(string &numero,string linea)

        {
                numero = linea.substr(7,linea.size()-7);
        }
void asignarTitular(string &titular,string linea)

        {
                titular = linea.substr(8,linea.size()-8);
        }


void imprimirDatos(int id,string numero,string titular)
        {

        cout<<"Identificador: "<<id<<endl;
        cout<<"Numero de telefono: "<<numero<<endl;
        cout<<"Titular de la linea: "<<titular<<endl;
        cout<<" "<<endl;

        }



struct rec{
    int id;
    string titular;
    string numero;
};


int main ()
{
    const int maximo=10;
    rec vec[maximo];
    char ruta[40];
    cout<<"Ingrese la ruta donde esta el archivo de texto."<<endl;
    cin>>ruta;
    ifstream celulares (ruta);
    int i=0;
    string linea;
    if (celulares)
    {
        while(getline(celulares,linea))
        {
            if (linea.compare(0,6,"Inicio") == 0)
                {asignarId(vec[i].id,linea);}
            else if (linea.compare(0,6,"Numero") == 0)
                {asignarNumero(vec[i].numero,linea);}
            else if (linea.compare(0,7,"Titular") == 0)
                {asignarTitular(vec[i].titular,linea);}
            else if (linea.compare(0,3,"Fin") == 0)
                {i++;}
            }
          int ml=i;
          for (i=0;i<ml;i++){

                imprimirDatos(vec[i].id,vec[i].numero,vec[i].titular);

            }
    }
    else cout<<"No se pudo abrir el archivo"<<endl;
    celulares.close();
    return 0;
}

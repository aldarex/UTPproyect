# UTPproyect
Solve a problem with c++ or JS

#include <iostream>
#include <fstream>
#include <string>
#include <conio.h>
#include <windows.h>
#define CONTRA "0000"
#define USEREST "user"
using namespace std;
int guardartexto();
int imprimir_texto();
int function_ingresa();
fstream ficheroEntrada;
ofstream ficheroSalida;
string frase;
string nombre;
int result, cont=0;
string user_estudiante, pass_estudiante;
bool ingresa=false;

int main () {

function_ingresa();

 return 0;
}
 
 
guardartexto(){
 
result = MessageBox(NULL, "DESEA GUARDAR SUS CREDITOS? \n", "CREDITOP", MB_YESNO);
	if(result==IDYES){
ficheroEntrada.open ( nombre.c_str() , ios::in);
 ficheroSalida.open ("archivocreditos.txt");
 while (! ficheroEntrada.eof() ) {
            getline (ficheroEntrada,frase);
            ficheroSalida<<""<<frase<<endl;
        }
 ficheroEntrada.close();
 ficheroSalida.close();
 
 MessageBox(NULL, "EL ARCHIVO archivocreditos.txt\n HA SIDO GUARDADO", "CREDITOP", MB_OK);
 system("cls");
}
else{
	system("cls");
	cout<<"PRESIONA CUALQUIER TECLA PARA SALIR"<<endl;
}
cout<<"PRESIONA CUALQUIER TECLA PARA SALIR"<<endl;
return 0;
}

imprimir_texto(){
	
	cout<<"ingrese su nombre sin espacios y en minusculas (Ej: pepitoconde.txt): ";
 getline(cin, nombre);
 system("cls");
 cout<<nombre<<" CARGANDO SUS CREDITOS..."<<endl;
 
 
    ficheroEntrada.open ( nombre.c_str() , ios::in);
    if (ficheroEntrada.is_open()) {
    	cout<<"\n\n";

        while (! ficheroEntrada.eof() ) {
            getline (ficheroEntrada,frase);
            cout << frase << endl;
        }

        ficheroEntrada.close();
    }
    else cout << "Fichero inexistente o faltan permisos" << endl;  
}

function_ingresa(){

do{
system("cls");
cout<<"\n\t\t\tCREDITOP"<<endl;
cout<<"INICIA SESION"<<endl;
cout<<"\n\t USUARIO: ";
getline(cin, user_estudiante);
cout<<"\t CONTRASEÑA: ";
getline(cin, pass_estudiante);

if(user_estudiante==USEREST && pass_estudiante==CONTRA){
ingresa=true;

	system("cls");
	imprimir_texto();
	guardartexto();
	
}//fin if principal
else{
	ingresa=false;
	cont++;
	cout<<"CONTRASEÑA O USUARIO INVALIDOS"<<endl;
	cout<<"PRESIONE CUALQUIER TECLA..."<<endl;
	getch();
}//fin else principal 
}//fin do 
while(ingresa==false && cont!=3);
	cin.get();
}//fin funcion ingresa

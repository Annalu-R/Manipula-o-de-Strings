# Manipula-o-de-Strings
Trabalho de algoritmos.
#include <algorithm>
#include <iostream>
#include <fstream>
#include <vector>
#include <ctype.h>

using namespace std;

void lista_tarefas();
void leitura();
void apagar_lista();

int main()
{
    cout << endl << " ~~~Bem vindo a sua lista de tarefas!~~~" << endl;
    cout << endl << "Escreva uma tarefa: " << endl;
    
    char resp;
    cout << endl << "Deseja escrever mais? S ou N?"<< endl;
    cin >> resp;
    cin.ignore();

if(resp == 'S'){
    lista_tarefas();
    
}

cout << endl << "Deseja ler a lista? S ou N?" << endl;
cin >> resp;
cin.ignore();

if( resp == 'S'){
    
    leitura();
    
}

cout << endl << "Deseja apagar alguma tarefa? S ou N?" << endl;
cin >> resp;
cin.ignore();

if(resp == 'S'){
    apagar_lista();   
}


    return 0;
}


void lista_tarefas(){
    
    ofstream arquivo;
    ifstream arquivoLeitura;
    string tarefa;
    
    vector<string> tarefasExistentes;
    
    arquivoLeitura.open("tarefas.txt");
    
    
    do{
     
     getline(arquivoLeitura,tarefa);
     tarefasExistentes.push_back(tarefa);
     
     }while(!arquivoLeitura.eof());
    
    arquivoLeitura.close();
    
    arquivo.open("tarefas.txt");
    
    getline(cin, tarefa);
    
    tarefasExistentes.push_back(tarefa);
    
    vector <string> tarefasOrganizadas;
    
    for(string t: tarefasExistentes){
        
        tarefasOrganizadas.push_back(t);
    }
 
    sort(begin(tarefasOrganizadas), end(tarefasOrganizadas));
    
    for(string p : tarefasOrganizadas){
        arquivo << p << endl;
    }
    
    
    arquivo.close();
}

void leitura(){
    
    ifstream arquivo;
    
     arquivo.open("tarefas.txt");
     
     vector <string> palavras;
     
     string tarefa;
     
     do{
     
     getline(arquivo,tarefa);
     palavras.push_back(tarefa);
     
     }while(!arquivo.eof());
     
     for (int i = 0 ; i < palavras.size() ; i++ ){
         
         cout << palavras[i] << endl;
         
         
     }
     
     arquivo.close();
    
}
void apagar_lista(){
    
    
    ifstream arquivoLer;
    ofstream arquivoDevolver;
    int pos;
    string tarefa;
    
    vector<string> tarefas;
    
    arquivoLer.open("tarefas.txt");
    

    do{
     
     getline(arquivoLer,tarefa);
     tarefas.push_back(tarefa);
     
     }while(!arquivoLer.eof());
    
    arquivoLer.close();
    arquivoDevolver.open("tarefas.txt");
    
    for (int j = 0 ;j < tarefas.size() ; j++ ){
        
        cout << j + 1 << tarefas[j] << endl ;
        
    }
    
    cout << endl << "Em qual posição deseja apagar?" << endl;
    cin >> pos;
    cin.ignore();
    
    for (int i = 0 ;i < tarefas.size() ; i++ ){
        
        if(pos == i){
            tarefas.erase(tarefas.begin()+(i-1));
        }
        
    }
    
     for(string p : tarefas){
        arquivoDevolver << p << endl;
    }
    
    arquivoDevolver.close();
}


#include <iostream>
#include <vector>

using namespace std;
//una estructura que representa una ciudad 
struct NodoCiudad {
//nombre del nodo puede ser pair o ciudad
    string nombre;
//vector que contiene los punteros de los vectores
    vector<NodoCiudad*> hijos;
//constructor que señala el nombre del nodo
    NodoCiudad(string nombre) : nombre(nombre) {}
};
// funcion que imprime el arbol de nodos en forma jerarquica
void imprimirArbol(NodoCiudad* nodo, int nivel = 0) {
    if (!nodo) return;// si el nodo  es nulo sale de la funcion con esta return
//imprimir el nombre del nodo 
    for (int i = 0; i < nivel; i++) cout << " ";
    cout << nodo->nombre << endl;//imprimir el nombre del nodo
//imprimir cada uno de los nodos hijos
    for (auto hijo : nodo->hijos) {
        imprimirArbol(hijo, nivel + 1);
    }
}

int main() {
//crear el nodo raiz para representar el pais 
    NodoCiudad* pais = new NodoCiudad("pais");
//crear nodos que representen los estados
    NodoCiudad* estado1 = new NodoCiudad("estado1");
    NodoCiudad* estado2 = new NodoCiudad("estado2");
    
//agregar ciudades en el primer estado  
    estado1->hijos.push_back(new NodoCiudad("Ciudad A"));
    estado1->hijos.push_back(new NodoCiudad("Ciudad B"));
//agregar ciudades en el segundo estado   
    estado2->hijos.push_back(new NodoCiudad("Ciudad C"));
    estado2->hijos.push_back(new NodoCiudad("Ciudad D"));
    estado2->hijos.push_back(new NodoCiudad("Ciudad E"));
//agregar los estados al nodo raiz    
    pais->hijos.push_back(estado1);
    pais->hijos.push_back(estado2);
// imprimir la estructura del arbol    
    imprimirArbol(pais);
    
    return 0;// fin del programa
}

 







#include <iostream>
#include <vector>

using namespace std;
//definimos el numeros de ciudades
const int NUM_CIUDADES = 5;

//funcion para imprimir el grafo en forma de matriz
void imprimirGrafo(const vector<vector<int>>& grafo) {
    cout << "martinez de adyacencia:\n";//mensaje que indica que se mostrara en la matriz
    for (int i = 0; i <NUM_CIUDADES; ++i) {//recorremos cada fila
        for (int j = 0; j <NUM_CIUDADES; ++j) {//recorremos cada columna
            cout << grafo[i][j] << " ";//imprimimos el valor de la matriz
        }
        
        cout <<endl;//nueva linea al final de cada fila
    }
}

int main() {
//creamos un grafo con 5 ciudades inicializado en cero
    vector<vector<int>> grafo(NUM_CIUDADES, vector<int>(NUM_CIUDADES, 0));
    
    //definimos las conexiones entre las ciudades c
    
    grafo[0][1] = grafo[1][0] = 1;// ciudad 0 y 1 estan conectadas
    grafo[1][2] = grafo[2][1] = 1;// ciudad 1 y 2 estan conectadas
    grafo[2][3] = grafo[3][2] = 1;// ciudad 2 y 3 estan conectadas
    grafo[3][4] = grafo[4][3] = 1;// ciudad 3 y 4 estan conectadas
    grafo[4][5] = grafo[5][4] = 1;// ciudad 4 y 5 estan conectadas
    
//llamamos a la funcion para imprimir el grafo    
    imprimirGrafo(grafo);
    return 0;//fin del programa
    
}




#include <iostream>
#include <map>
#include <utility>

using namespace std;

int main() {
//creamos un mapa para almacear distacias entre ciudades
    map<pair<string, string>, int> distancias;

//asignamos distacias entre pares de ciudades
    distancias[{"ciudad A", "ciudad B"}] = 100;//distacia entre ciudad A y ciudad B
    distancias[{"ciudad B", "ciudad C"}] = 150;//distacia entre ciudad B y ciudad C
    distancias[{"ciudad C", "ciudad D"}] = 200;//distacia entre ciudad C y ciudad D
    distancias[{"ciudad E", "ciudad F"}] = 250;//distacia entre ciudad E y ciudad F
    distancias[{"ciudad G", "ciudad H"}] = 300;//distacia entre ciudad G y ciudad H

//imprimimos las distacias entre las ciudades    
    cout << "Distancias entre ciudades:\n";
    for (const auto& par : distancias) { //iteramos sobre el mapa
        //mostramos la distancia entre cada par de ciudad
        cout << par.first.first << " - " << par.first.second << ": "
             << par.second << " KM\n";//formato de salida
    }

    return 0;//fin del programa
}

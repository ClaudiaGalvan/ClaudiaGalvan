#include <iostream>

// Función para ordenar el arreglo utilizando el método de inserción
void insertionSort(int arr[], int n, bool ascending) {
    for (int i = 1; i < n; ++i) {
        int key = arr[i];
        int j = i - 1;

        // Si se quiere ordenar en orden ascendente
        if (ascending) {
            // Insertar el elemento actual en la posición correcta en el arreglo ordenado
            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                --j;
            }
        } 
        // Si se quiere ordenar en orden descendente
        else {
            // Insertar el elemento actual en la posición correcta en el arreglo ordenado
            while (j >= 0 && arr[j] < key) {
                arr[j + 1] = arr[j];
                --j;
            }
        }
        arr[j + 1] = key;
    }
}

// Función para imprimir los elementos del arreglo
void printArray(int arr[], int n) {
    for (int i = 0; i < n; ++i) {
        std::cout << arr[i] << " ";
    }
    std::cout << std::endl;
}

int main() {
    const int size = 10;
    int arr[size];
    
    // Inicio del programa: Se solicita al usuario ingresar los valores del arreglo
    std::cout << "Ingrese los valores del arreglo (separados por espacio): ";
    for (int i = 0; i < size; ++i) {
        std::cin >> arr[i];
    }

    // Mostrar el arreglo original
    std::cout << "Arreglo original: ";
    printArray(arr, size);

    char order;
    // Preguntar al usuario si desea ordenar en orden ascendente o descendente
    std::cout << "¿Desea ordenar en orden ascendente (a) o descendente (d)? ";
    std::cin >> order;

    bool ascending;
    // Si la opción del usuario es 'a' o 'A', se establece el orden ascendente como verdadero
    if (order == 'a' || order == 'A') {
        ascending = true;
    } 
    // Si la opción del usuario es 'd' o 'D', se establece el orden ascendente como falso
    else if (order == 'd' || order == 'D') {
        ascending = false;
    } 
    // Si la opción del usuario no es válida, se establece el orden ascendente como verdadero
    else {
        std::cout << "Opción no válida. Ordenando en orden ascendente por defecto." << std::endl;
        ascending = true;
    }

    // Llamar a la función insertionSort() para ordenar el arreglo
    insertionSort(arr, size, ascending);

    // Mostrar el arreglo ordenado
    std::cout << "Arreglo ordenado: ";
    printArray(arr, size);

    // Final del programa
    return 0;
}

#include <stdio.h>
#include <stdlib.h>

void printVetor(float *vet, int n) {
    printf("[ ");
    for(int i=0; i < n; i++) {
        printf("%f ", vet[i]);
    }
    printf(" ]\n");
}

// Função compara
int compara(const void * a, const void * b) {
  return ( *(float*)a - *(float*)b );
}

int main() {
    // ler a quantidade de itens para o vetor
    int n;
    printf("entre com o numeros de itens: ");
    scanf("%d", &n);

    // Aloca o array na memória
    float *vet = (float *)malloc(n * sizeof(float));

    // ler os elementos do vetor
    printf("Insira os valores do vetor: ");
    for(int i = 0; i < n; i++) {
        scanf("%f", vet + i);
    }

    // Mostra o vetor inserido
    printVetor(vet, n);

    void (*pont_qsrot)(void *vet, size_t n, size_t size, int(*comp)(const void *, const void *));
    pont_qsrot = qsort;

    // Imprime e ordena o vetor
    printf("\nVetor ordenado: ");
    qsort(vet, n, sizeof(float), compara);
    printVetor(vet, n);

    free(vet);
    
    return 0;
}

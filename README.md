# Fila
repositório GitHub
//FILA SEQUENCIAL
#include <stdio.h>
#include <stdlib.h>
#define MAX 100

typedef struct{
	int v[MAX];
	int inicio;
	int final;
}Fila;

int empty(Fila *f);
void inserir(Fila *f, int x);
int size(Fila *f);
int primeiro(Fila *f);
int remover(Fila *f);

int main(void){	
	Fila fila;

	fila.inicio=0;
	fila.final=0;
	inserir(&fila,1);
	inserir(&fila,2);
	inserir(&fila,3);
	inserir(&fila,4);
	
	printf("\nFila vazia %d",empty(&fila));
	printf("\nTamanho da Fila %d",size(&fila));
	printf("\nProximo da Fila %d",primeiro(&fila));
	printf("\nTirando da Fila %d",remover(&fila));
	printf("\nTirando da Fila %d",remover(&fila));
	printf("\nTirando da Fila %d",remover(&fila));
	printf("\nProximo da Fila %d",primeiro(&fila));
	printf("\nTirando da Fila %d",remover(&fila));
	printf("\nFila vazia %d",empty(&fila));
	
	printf("\n");
	return 0;
}

int empty(Fila *f){
	if(f->inicio == f->final){//se inicio igual final, fila vazia
		return 1;
	}
	else{
		return 0;
	}
}

void inserir(Fila *f, int x){
	if(f->final+1 >= MAX){
		printf("Estouro da capacidade da fila.");
		exit(1);
	}
	f->v[f->final] = x;
	f->final++;
	return;
}

int size(Fila *f){
	return f->final;
}

int primeiro(Fila *f){
	return f->v[0];
}

int remover(Fila *f){
	int i,x;
	
	if(empty(f)){
		printf("Fila vazia.");
		exit(1);
	}
	x=f->v[0];
	for(i=0;i<(f->final);i++){
		f->v[i] = f->v[i+1];
	}
	f->final--;
	return x;
}

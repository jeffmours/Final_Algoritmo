#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <iostream>


using namespace std; 

struct matricula{
int RA;
char nome[81];
char turma;
};

typedef struct matricula MatAluno;
#define tam 100
typedef MatAluno* Hash[tam];

int funcao_Esp (int RA) {
 return (RA % tam);
}

MatAluno* insere_Esp (Hash tab, int RA, char* nome, char turma) {
int h = funcao_Esp(RA);
while (tab[h] != NULL) {
 if (tab[h] -> RA == RA)
 break;
 h = (h + 1) % tam;
}

if (tab[h] == NULL) {
 tab[h] = (MatAluno*) malloc(sizeof(MatAluno));
 tab[h] -> RA = RA;
}

strcpy(tab[h] -> nome, nome);
tab[h] -> turma = turma;
return tab[h];
}

void remove_Esp(Hash tab, int RA) {
int h = funcao_Esp(RA);
if(tab[h] -> RA == RA) {

 tab[h] = NULL;

 printf("\nRA excluido!");
 }else{

 printf("\nRA nao encontrado");
 }

}

MatAluno* busca_Esp (Hash tab, int RA) {
int h = funcao_Esp(RA);
while (tab[h] != NULL){

 if (tab[h] -> RA == RA);
 return tab[h];
 h = (h + 1) % tam;

}
return NULL;

}

int main() {
	int matr, contar, busca;
	char turma;
	char nome[81] = "Número";
	printf("Informe o número: ");
	scanf("%c" ,&turma);
	Hash alunos; //inicializando tabela Hash
	for (int i=0; i<= 101; i++){
		alunos[i] = NULL;
	}
	
	for (int count = 1; count <=100; ++count){
		matr = count;
		std::cout<<matr<<"\t";
		if (count% 5 == 0)
			std::cout << "\n";
		insere_Esp(alunos, matr, nome, turma);
	}
	
}

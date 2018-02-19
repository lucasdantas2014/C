 #include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>
#include<ctype.h>

typedef struct
{
  int top;
  int elementos[500];
  int qtvElem[500];
  int tamMax;
} Pilha;


int contadorNodo(char *arvore,int contador){
  int abertos = 1;
  int fechados = 0;
  int nodos = 0;
  while(1){
    if(arvore[contador] == '(')
    {
      abertos++;
      contador++;
    }
    
     

    
    else if(arvore[contador] == ')')
    {
      
    
      if(arvore[contador -1] == ')')
      {
        nodos+=1;
      }
      
      else if(arvore[contador -1] == '(')
      {
        nodos+=1;
      }
      
      fechados++;
      contador++;

    

    }
    else
    {
      contador++;
    }
    if(abertos == fechados)
    {

      //printf("\n-----------\nNodos: %d\n-------------\n", nodos -1 );
            /*
      printf("\n-----------\nAbertos: %d\n-------------\n", abertos);

      printf("\n-----------\nFechados: %d\n-------------\n", fechados);
      */
      break;
    }
  }
}

void
initPilha (Pilha * p, int max)
{
  p->top = 0;
  p->tamMax = max;
}

int
verificar (char *arvore, int direcao, int contador, Pilha * pais)
{
  
  
  
  /*
  printf("\n\n-----------");
  printf("\nO CARACTER desta rodada E o: %c",arvore[contador]);
  printf("\no PAI DESTA RODADA E O: %d\n",pais->elementos[pais->top]);
  printf("--------------------\n");
  */
  //printf("\n O tam: %d  O cont: %d\n",pais->tamMax, contador);

  if(pais->tamMax - 1 <= contador && pais->top > -1){
    return 1;
  }

  if (direcao == 1 || direcao == 2)
    {

      //SE O CARACTER FOR UM PARENTESE ABERTO ADIANTE 1 CARACTER
      if (arvore[contador] == '(')
	{
	  contador++;
	  verificar (arvore, direcao, contador,
	  pais);
	}

      //SE O CARACTER FOR UM PARENTESE FECHADO ADIANTE 1 CARACTER E MUDE A DIRECAO
  else if (arvore[contador] == ')')
	{
	  
	  if (arvore[contador -1] == ')'){
	    
	    pais->qtvElem[pais->top] += 1;

  	  //printf("\nELE APARECEU: %d", pais->qtvElem[pais->top]);
  	  if(pais->qtvElem[pais->top] > 10)
  	  {
  	    //printf("FOi por Nodo");
  	    return 0;
  	  }
  	    
	  }
	  else if(arvore[contador - 1] == '('){
	    pais->qtvElem[pais->top] += 1;
  	  //printf("\nELE APARECEU: %d", pais->qtvElem[pais->top]);
  	  if(pais->qtvElem[pais->top] > 10)
  	  {
  	    //printf("FOi por Nodo");
  	    return 0;
  	  }
	  }
	 

	  if (direcao == 1)
	    {
	      direcao = 2;
	    }
	  else
	    {
	      direcao = 1;
	      pais->top -= 1;
	    }
	 
	  
	  
	  contador++;


	  verificar (arvore, direcao, contador, pais);
	}
  
  else if(arvore[contador] == ' '){
    direcao = 2;
    contador++;
    verificar (arvore,direcao,contador,pais);
  }
      //Valor identificado
      else
	{
	  char numeroSTR[20];
	  int addNumC = 0;
	  int valor;
	  int pai;
	  while (isdigit(arvore[contador]))
	    {
	      
	      
	      //N
	      numeroSTR[addNumC] = arvore[contador];
	      contador++;
	      addNumC++;
	    }
	  valor = atoi(numeroSTR);
	  pais->top++;
	  pais->elementos[pais->top] = valor;
	  pai = pais->elementos[pais->top - 1];
	  //printf("\nELE APARECEU: %d", pais->qtvElem[pais->top]);

	  // CASO ENTRE NESSES CASOS VAO RETORNAR 1 E VAI SER FALSO
	  if (direcao == 1 && pai < valor && pais->top > 0)
	    {
	      //printf("FOi POr valor!\n");
	      return 0;
	    }
	  else if (direcao == 2 && pai > valor && pais->top > 0)
	    { 
	      //printf("FOi POr valor!\n");
	      return 0;
	    }
	    
	  if(arvore[contador] == '('){
	        direcao = 1;
	   }
	   
	  contadorNodo(arvore, contador);
	  verificar (arvore, direcao, contador, pais);
	}
    }

}


int main (void)
{
  int resp;
  char arvore[5000];
  Pilha pais;
  

  fgets(arvore,5000,stdin);
  pais.top = -1;
  pais.tamMax = strlen(arvore);
  int cont;
  for (cont = 0; cont <= pais.tamMax; cont++)
  {
    pais.qtvElem[cont] = 0;
  }
  
  resp = verificar (arvore, 1, 0, &pais);
	//printf("Resposta");
	if(resp == 0){
	  printf("FALSO");
	}
	else{
	  printf("VERDADEIRO");
	}
  return 0;
}


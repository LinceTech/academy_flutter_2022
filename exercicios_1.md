# Praticando lógica de programação

Utilize a ferramenta da sua preferência para realizar os exercicios abaixo.  
Caso não tenha acesso a um ambiente com a Dart SDK instalada, todos os exercicios podem ser implementados utilizando o
ambiente online [DartPad](https://dartpad.dev/?).

[Lista de respostas](/exercicios_1_respostas.md)

### 1 — Escreva um programa que receba uma lista de raios de círculos e com base nos raios, calcule o area e o perimetro de cada círculo e exiba no console. Utilize a biblioteca dart:math.

**Tempo estimado**: 10m  
**Raios**: 5, 8, 12, 7.3, 18, 2, 25  
**Saida esperada no console:**
> Raio: 5, área: 78.54, perímetro: 31.42.  
> Raio: 8, área: 201.06, perímetro: 50.27.  
> Raio: 12, área: 452.39, perímetro: 75.40.  
> Raio: 7.3, área: 167.42, perímetro: 45.87.  
> Raio: 18, área: 1017.88, perímetro: 113.10.  
> Raio: 2, área: 12.57, perímetro: 12.57.  
> Raio: 25, área: 1963.50, perímetro: 157.08.  

### 2 — Escreva um programa que converta uma lista temperaturas de celcius para Fahrenheit e Kelvin.

**Tempo estimado**: 10m   
**Temperaturas (C)**: 0.0, 4.2, 15.0, 18.1, 21.7, 32.0, 40.0, 41.0   
**Saida esperada no console:**
> Celcius: 0.00, fahrenheit: 32.00, kelvin: 273.15  
> Celcius: 4.20, fahrenheit: 39.56, kelvin: 277.35  
> Celcius: 15.00, fahrenheit: 59.00, kelvin: 288.15  
> Celcius: 18.10, fahrenheit: 64.58, kelvin: 291.25  
> Celcius: 21.70, fahrenheit: 71.06, kelvin: 294.85  
> Celcius: 32.00, fahrenheit: 89.60, kelvin: 305.15  
> Celcius: 40.00, fahrenheit: 104.00, kelvin: 313.15  
> Celcius: 41.00, fahrenheit: 105.80, kelvin: 314.15  

### 3 — Escreva um programa que receba um parágrafo, e imprima no console as seguintes informações:

1. Texto do paragrafo;
2. Número de palavras;
3. Tamanho do texto;
4. Número de frases;
5. Número total de vogais;
6. Consoantes presentes no texto;

**Tempo estimado**: 40m   
**Paragrafo**: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam venenatis nunc et posuere vehicula. Mauris
lobortis quam id lacinia porttitor.
**Saida esperada no console:**
> Paragrafo: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam venenatis nunc et posuere vehicula. Mauris
> lobortis quam id lacinia porttitor.  
> Número de palavras: 20  
> Tamanho do texto: 139  
> Número de frases: 3  
> Número de vogais: 50  
> Consoantes encontradas: b, c, d, g, h, l, m, n, p, q, r, s, t, v  

### 4 — Escreva um programa que some 18 dias de semana (ignorar sabado e domingo) partindo da data atual, e imprima a data atual e data calculada formatada no padrão dia/mes/ano (ex.: 01/01/2022).

Ex: Considerando a data atual como 05/09/2022

**Tempo estimado**: 20m   
**Saida esperada no console:**
> Data atual: 05/09/2022  
> Data calculada: 29/09/2022

### 5 — Escreva um programa que gere sugestões de nomes, com base em listas pré-definidas de nomes e sobrenomes.

**Lista de nomes:** Ana, Maria, Francisco, João, Pedro, Gabriel, Rafaela, Marcio, Jose, Carlos, Patricia, Helena,
Camila,
Mateus, Gabriel, Samuel, Karina, Antonio, Daniel, Joel, Cristiana, Sebastião, Paula

**Lista de sobrenomes:** Silva, Souza, Almeida, Azevedo, Braga, Barros, Campos, Cardoso, Costa, Teixeira, Santos,
Rodrigues, Ferreira, Alves, Pereira, Lima, Gomes, Ribeiro, Carvalho, Lopes, Barbosa

**Tempo estimado**: 10m

### 6 — Escreva um programa que receba uma lista de números inteiros e imprima no console em ordem crescente os números representados na forma decimal, binaria, octal e hexadecimal.

**Tempo estimado**: 10m  
**Números**: 3, 17, 23, 49, 328, 1358, 21, 429, 12, 103, 20021  
**Saida esperada no console:**
> decimal: 3, binario: 11, octal: 3, hexadecimal: 3  
> decimal: 12, binario: 1100, octal: 14, hexadecimal: c  
> decimal: 17, binario: 10001, octal: 21, hexadecimal: 11  
> decimal: 21, binario: 10101, octal: 25, hexadecimal: 15  
> decimal: 23, binario: 10111, octal: 27, hexadecimal: 17  
> decimal: 49, binario: 110001, octal: 61, hexadecimal: 31  
> decimal: 103, binario: 1100111, octal: 147, hexadecimal: 67  
> decimal: 328, binario: 101001000, octal: 510, hexadecimal: 148  
> decimal: 429, binario: 110101101, octal: 655, hexadecimal: 1ad  
> decimal: 1358, binario: 10101001110, octal: 2516, hexadecimal: 54e  
> decimal: 20021, binario: 100111000110101, octal: 47065, hexadecimal: 4e35  

### 7 — Escreva um programa que receba uma lista de números inteiros, e retorne o somatorio dos números na lista. Implemente essa função em três modelos:
1. Utilizando o comando for;
2. Utilizando o comando while;
3. Utilizando um metodo recursivo; 
4. Utilizando metodos de lista;

**Tempo estimado**: 10m  
**Números**: 10, 35, 999, 126, 95, 7, 348, 462, 43, 109
**Saida esperada no console:**
> for: 2234  
> while: 2234  
> recursão: 2234  
> lista: 2234  

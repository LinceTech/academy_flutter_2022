# Praticando orientação a objetos

Utilize a ferramenta da sua preferência para realizar os exercicios abaixo.  
Caso não tenha acesso a um ambiente com a Dart SDK instalada, todos os exercicios podem ser implementados utilizando o
ambiente online [DartPad](https://dartpad.dev/?).

[Lista de respostas](EXERCICIOS_2_RESPOSTAS.md)

### 1 — Utilizando os conceitos de orientação a objetos, complete o programa sem alterar o código já existente, para que o programa imprima aleatoriamente no console uma das tres saidas abaixo.

**IMPORTANTE**: para a realização desse exercicio, não deve ser utilizado dynamic.

**Tempo estimado**: 15m  
**Saidas esperadas no console:**

> [TELEFONE] Ligando para (47) 99876-5432...

> [CELULAR] Ligando para (47) 99876-5432...

> [ORELHAO] Ligando para (47) 99876-5432...


Código base:

```dart
// NÃO PODE SER MODIFICADO
// -------------------------------------------------------------
import 'dart:math' as math;

void main() {
  final meioDeComunicacao = aleatorio();
  meioDeComunicacao.fazerLigacao('(47) 99876-5432');
}

MeioDeComunicacao aleatorio() {
  final meiosDeComunicacao = <MeioDeComunicacao>[
    Telefone(),
    Celular(),
    Orelhao(),
  ];

  final random = math.Random();

  return meiosDeComunicacao[random.nextInt(
    meiosDeComunicacao.length,
  )];
}

// -------------------------------------------------------------
// ADICIONAR IMPLEMENTAÇÃO RESTANTE ABAIXO DESSA LINHA
// -------------------------------------------------------------
```

### 2 — Trabalhando com refatoração de programas, iniciante

**IMPORTANTE**: para a realização desse exercicio, não deve ser utilizado dynamic.

**Objetivo do programa**: fazer a simulação de uma **pessoa** que consome **calorias** provenientes de **produtos**, os
produtos são fornecidos por **fornecedores**.

Considerando o objetivo do programa, efetue uma refatoração utilizando os conceitos de orientação a objetos, completando
os requisitos especificados abaixo, utilizando comentarios para demarcar no código onde os objetivos foram atingidos.

1. Criar novos fornecedores: sanduiches, bolos, saladas, petiscos, ultra-caloricos
2. Alterar o programa para escolher um novo fornecedor aleatoriamente para cada "refeição"
3. Nas informações da pessoa, adicione uma lógica "status" do nivel de calorias (dica: utilizar um enum)
    1. Calorias <= 500 : Deficit extremo de calorias;
    2. 500 > Calorias <= 1800 : Deficit de calorias;
    3. 1800 > Calorias <= 2500 : Pessoa está satisfeita;
    4. Calorias > 2500 : Excesso de calorias;
4. Altere o programa para definir um nivel inicial de calorias aleatoriamente ao instanciar uma pessoa;
5. Altere o programa para se basear no nivel de calorias para definir se a pessoa precisa de refeições
6. Imprima o número de refeições realizadas nas informações da pessoa;

**Tempo estimado**: 60m

```dart
import 'dart:math';

void main() {
   final pessoa = Pessoa();
   final fornecedor = FornecedorDeBebidas();

   // Consumindo produtos fornecidos
   for (var i = 0; i < 5; i++) {
      pessoa.refeicao(fornecedor);
   }

   pessoa.informacoes();
}

class Produto {
   Produto(this.nome, this.calorias);

   /// Nome deste produto
   final String nome;

   /// Total de calorias
   final int calorias;
}

class FornecedorDeBebidas {
   final _random = Random();
   final _bebidasDisponiveis = <Produto>[
      Produto('Agua', 0),
      Produto('Refrigerante', 200),
      Produto('Suco de fruta', 100),
      Produto('Energetico', 135),
      Produto('Café', 60),
      Produto('Cha', 35),
   ];

   /// Retorna um produto que pode ser consumido por um consumidor
   Produto fornecer() {
      return _bebidasDisponiveis[_random.nextInt(_bebidasDisponiveis.length)];
   }
}

class Pessoa {
   // Acumulador de calorias
   int _caloriasConsumidas = 0;

   /// Imprime as informações desse consumidor
   void informacoes() {
      print('Calorias consumidas: $_caloriasConsumidas');
   }

   /// Consome um produto e aumenta o numero de calorias
   void refeicao(FornecedorDeBebidas fornecedor) {
      final produto = fornecedor.fornecer();
      print('Consumindo ${produto.nome} (${produto.calorias} calorias)');

      _caloriasConsumidas += produto.calorias;
   }
}

```

### 3 — Biblioteca de musicas

**IMPORTANTE**: para a realização desse exercicio, não deve ser utilizado dynamic.

Crie um programa para controlar uma biblioteca de músicas, a biblioteca terá uma **lista de músicas** disponiveis.
O programa deverá imprimir no console as músicas cadastradas, o número de músicas e o **tempo total** em **horas** das
músicas da biblioteca.

**As músicas devem ter as seguintes informações:**

1. Titulo da musica
2. Nome do artista
3. Nome do album
4. Duração em segundos

A biblioteca deve permitir buscar música pelo título, nome dor artista e nome do album. Deve ser incluido no 
programa a execução de todas essas buscas de utilizando esses parametros após imprimir a biblioteca.

**Tempo estimado**: 60m

### 4 — Trabalhando com refatoração de programas, intermediario

**IMPORTANTE**: para a realização desse exercicio, não deve ser utilizado dynamic.

**Objetivo do programa**: fazer a comparação de formas geometricas para identificar o de maior area e o de maior
perimetro e imprimir o nome e as medidas desses objetos.

Considerando o objetivo do programa, efetue uma refatoração utilizando os conceitos de orientação a objetos, completando
os requisitos especificados abaixo, utilizando comentarios para demarcar no código onde os objetivos foram atingidos.

1. Utilizar herança
2. Utilizar polimorfismo
3. Alterar a classe _ComparadorFormasGeometricas_ para ter apenas dois metodos, uma para area e um para perimetro
4. Inclua no sistema a definição da forma geometrica _Triangulo equilatero_
5. Inclua no sistema a definição da forma geometrica _Triangulo retangulo_
6. Inclua no sistema a definição da forma geometrica _Pentagono regular_
7. Inclua no sistema a definição da forma geometrica _Hexagono regular_

**Tempo estimado**: 120m

```dart
import 'dart:math' as math;

void main() {
   // Definindo o comparador de formas
   final comparador = ComparadorFormasGeometricas();

   // Definindo as formas geometricas
   final circuloA = Circulo('Circulo A', 3);
   final circuloB = Circulo('Circulo B', 8);
   final retanguloA = Retangulo('Retangulo A', 4, 3);
   final retanguloB = Retangulo('Retangulo B', 19, 11);

   final circuloMaiorArea = comparador.circuloDeMaiorArea(circuloA, circuloB);
   final retanguloMaiorArea = comparador.retanguloDeMaiorArea(
      retanguloA,
      retanguloB,
   );

   if (circuloMaiorArea.area > retanguloMaiorArea.area) {
      print(
         'A maior area é ${circuloMaiorArea.area.toStringAsFixed(2)} '
         'e pertence a ${circuloMaiorArea.nome}',
      );
   } else {
      print(
         'A maior area é ${retanguloMaiorArea.area.toStringAsFixed(2)} '
         'e pertence a ${retanguloMaiorArea.nome}',
      );
   }

   final circuloaiorPerimetro = comparador.circuloDeMaiorPerimetro(
      circuloA,
      circuloB,
   );
   final retanguloMaiorPerimetro = comparador.retanguloDeMaiorPerimetro(
      retanguloA,
      retanguloB,
   );
   if (circuloaiorPerimetro.area > retanguloMaiorPerimetro.area) {
      print(
         'O maior perimetro é ${circuloaiorPerimetro.perimetro.toStringAsFixed(2)} '
         'e pertence a ${circuloaiorPerimetro.nome}',
      );
   } else {
      print(
         'O maior perimetro é ${retanguloMaiorPerimetro.perimetro.toStringAsFixed(2)} '
         'e pertence a ${retanguloMaiorPerimetro.nome}',
      );
   }
}

/// Representa a forma geometrica "círculo"
class Circulo {
   /// Construtor padrão, recebe o [raio] do círculo.
   Circulo(this.nome, this.raio);

   final String nome;
   final double raio;

   /// Retorna a area desse circulo
   double get area => math.pi * math.pow(raio, 2);

   /// Retorna o perimetro desse circulo
   double get perimetro => 2 * math.pi * raio;
}

/// Representa a forma geometrica "retangulo", forma geometrica de quatro lados
/// e angulos retos (90 graus).
class Retangulo {
   /// Construtor padrão, recebe a [altura] e [largura] do retangulo
   Retangulo(this.nome, this.altura, this.largura);

   final String nome;
   final double largura;
   final double altura;

   /// Retorna a area desse circulo
   double get area => altura * largura;

   /// Retorna o perimetro desse circulo
   double get perimetro => (altura * 2) + (largura * 2);
}

/// Representa a forma geometrica "quadrado", que é um formato especial de
/// retangulo, onde todos os lados possuem o mesmo tamanho.
class Quadrado {
   /// Construtor padrão, recebe o [lado] do quadrado
   Quadrado(this.nome, this.lado);

   final String nome;
   final double lado;

   /// Retorna a area desse quadrado
   double get area => lado * lado;

   /// Retorna o perimetro desse quadrado
   double get perimetro => lado * 4;
}

/// Compara caracteristicas de formas geometricas
class ComparadorFormasGeometricas {
   /// Retorna o circulo com a maior area, ou [circuloA] caso as areas sejam
   /// iguais
   Circulo circuloDeMaiorArea(Circulo circuloA, Circulo circuloB) {
      if (circuloA.area > circuloB.area) {
         return circuloA;
      } else if (circuloB.area > circuloA.area) {
         return circuloB;
      }
      return circuloA;
   }

   /// Retorna o circulo com o maior perimetro, ou [circuloA] caso os perimetros
   /// sejam iguais
   Circulo circuloDeMaiorPerimetro(Circulo circuloA, Circulo circuloB) {
      if (circuloA.perimetro > circuloB.perimetro) {
         return circuloA;
      } else if (circuloB.perimetro > circuloA.perimetro) {
         return circuloB;
      }
      return circuloA;
   }

   /// Retorna o retangulo com o maior perimetro, ou [retanguloA] caso os
   /// perimetros sejam iguais
   Retangulo retanguloDeMaiorPerimetro(Retangulo retanguloA, Retangulo retanguloB) {
      if (retanguloA.perimetro > retanguloB.perimetro) {
         return retanguloA;
      } else if (retanguloB.perimetro > retanguloA.perimetro) {
         return retanguloB;
      }
      return retanguloA;
   }

   /// Retorna o retangulo com o maior perimetro, ou [retanguloA] caso os
   /// perimetros sejam iguais
   Retangulo retanguloDeMaiorArea(Retangulo retanguloA, Retangulo retanguloB) {
      if (retanguloA.area > retanguloB.area) {
         return retanguloA;
      } else if (retanguloB.area > retanguloA.area) {
         return retanguloB;
      }
      return retanguloA;
   }
}
```

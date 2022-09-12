# Praticando uso de coleções

Utilize a ferramenta da sua preferência para realizar os exercicios abaixo.  
Caso não tenha acesso a um ambiente com a Dart SDK instalada, todos os exercicios podem ser implementados utilizando o
ambiente online [DartPad](https://dartpad.dev/?).

[Lista de respostas](EXERCICIOS_3_RESPOSTAS.md)

### 1 — Baseado na situação descrita abaixo, escreva um programa utilizando a estrutura "lista".

**IMPORTANTE**: para a realização desse exercicio, não deve ser utilizado dynamic.

Crie uma classe para auxiliar no controle de itens que devem ser comprados numa visita ao mercado. O programa deve
possuir o nome dos itens a serem comprados, e a quantidade desejada. Essa classe deve possuir as seguintes ações:

1. Incluir novos itens desejados;
2. Separar os itens já comprados dos itens desejados;
3. Separar os itens que não havia estoque dos itens desejados;
4. Exibir no console os itens desejados, com as suas quantidades;
5. Escolher um item pendente aleatoriamente;
6. Mostrar um indicador de progresso, com o número de itens desejados versus o numero de itens comprados (ex.: "
   Progresso: 7/12");
7. No metodo main, instanciar a classe criada e simular a criação de uma lista de compras com pelo menos 3 itens, e
   demonstrar o funcionamento marcando 2 itens como comprados, e 1 como item sem estoque.

**Tempo estimado**: 45m

### 2 — Crie uma classe que controle um baralho de cartas, seguindo as especificações:

**IMPORTANTE**: para a realização desse exercicio, não deve ser utilizado dynamic.

1. Não utilizar a classe List, deve ser utilizada uma classe do pacote 'dart:collections' especializada nesse tipo de
   manipulação de coleções (manipular extremidades de coleções — primeiro e ultimo item)
2. O baralho permite empilhar uma carta por vez
3. O baralho permite remover uma carta por vez, a carta removida deve sempre ser a carta que está no topo do baralho;
4. As cartas só podem ser criadas com os naipes validos (paus/copas/espadas/ouros)
5. No metodo main, deve-se incluir no baralho as seguintes cartas, na ordem especificada:
    1. A ♧ (paus - U+2663)
    2. A ♡ (copas - U+2665)
    3. A ♤ (espadas - U+2660)
    4. A ♢ (ouros - U+2666)
6. Ainda no metodo main, deve ser utilizada uma estrutura de repetição (loop), para remover todas as cartas do baralho,
   seguindo a regra definida no item 2 (uma carta removida por vez, sendo a carta que está no topo do baralho).

**Tempo estimado**: 35m

### 3 — Crie uma classe para controlar uma fila de um mercado, seguindo as especificações:

**IMPORTANTE**: para a realização desse exercicio, não deve ser utilizado dynamic.

1. Não utilizar a classe List, deve ser utilizada uma classe do pacote 'dart:collections' especializada nesse tipo de
   manipulação de coleções (manipular extremidades de coleções — primeiro e ultimo item)
2. Quem entra na fila primeiro, será atendido primeiro;
3. Cada pessoa da fila deve ter um nome e sobrenome gerado aleatoriamente. O gerador de nomes deve ser uma classe
   separada, que tenha apenas o metodo "gerarNomeAleatorio";
4. Quando uma pessoa entra na fila, deve ser exibido no console "*(Fulano Silva) entrou na fila"
5. Quando uma pessoa for atendida, deve ser exibido no console uma mensagem dizendo "*(Fulano Silva) foi atendido(a)"
6. No metodo main, a fila deve ser populada com 10 pessoas;
7. No metodo main, as pessoas devem ser atendidas corretamente de acordo com a ordem que entraram na fila, até a fila
   ser esgotada

** _substituir (Fulano Silva) pelo nome da pessoa_

**Tempo estimado**: 35m

### 4 — Crie uma classe para controlar um album de figuras, seguindo as especificações:

**IMPORTANTE**: para a realização desse exercicio, não deve ser utilizado dynamic.

1. Não utilizar a classe List, exceto onde explicitamente permitido;
2. Deve ser definida uma lista com vinte figuras;
3. Cada figura deve ter um nome e um código unico;
4. Deve ser criado uma classe de "pacote de figuras" que será inicializado com 4 figuras aleatorias da lista (pode
   utilizar a classe List);
5. O album é considerado completo, quando todas as figuras definidas no item 2 forem incluidas no album;
6. O album não pode ter figuras repetidas;
7. O Album deve possuir um metodo para imprimir no console as figuras coladas. As figuras devem ser impressas em ordem
   conforme o código da figura.
8. Criar uma estrutura extra, para armazenar as figuras repetidas (pode utilizar a classe List);
9. No metodo main, faça uma lógica para gerar novos pacotes de figuras e adicionar no album até o album ser completado.
10. No metodo main, imprima o número de figuras repetidas, e chame o metodo de impressão do album.

**Tempo estimado**: 90m

### 5 — O programa abaixo faz a busca de pessoas conforme o mes de nascimento. Efetue a refatoração do programa utilizando as estruturas de coleção adequadas para reduzir o número de iterações realizados do programa.

**IMPORTANTE**: para a realização desse exercicio, não deve ser utilizado dynamic.

**Tempo estimado**: 20m  

Código base:

```dart
void main() {
   final controleDePessoas = ControleDePessoas();

   // Cadastrando pessoas no sistema
   controleDePessoas
      ..cadastrarPessoa(Pessoa('Jose', Mes.abril))
      ..cadastrarPessoa(Pessoa('Arthur', Mes.agosto))
      ..cadastrarPessoa(Pessoa('João', Mes.abril))
      ..cadastrarPessoa(Pessoa('Jesse', Mes.dezembro))
      ..cadastrarPessoa(Pessoa('Roberta', Mes.fevereiro))
      ..cadastrarPessoa(Pessoa('Carla', Mes.fevereiro))
      ..cadastrarPessoa(Pessoa('Thania', Mes.agosto))
      ..cadastrarPessoa(Pessoa('Rafaela', Mes.marco))
      ..cadastrarPessoa(Pessoa('Yuri', Mes.junho))
      ..cadastrarPessoa(Pessoa('Jonas', Mes.setembro))
      ..cadastrarPessoa(Pessoa('Elias', Mes.outubro))
      ..cadastrarPessoa(Pessoa('Abel', Mes.maio))
      ..cadastrarPessoa(Pessoa('Danilo', Mes.abril))
      ..cadastrarPessoa(Pessoa('Jonathan', Mes.abril))
      ..cadastrarPessoa(Pessoa('Joseph', Mes.setembro))
      ..cadastrarPessoa(Pessoa('Abdul', Mes.janeiro))
      ..cadastrarPessoa(Pessoa('Jean', Mes.abril));

   // Passar por todos os meses com pessoas, e imprimir os nomes das pessoas
   for (final mes in controleDePessoas.mesesComPessoas) {
      print('\n${mes.name}');

      for (final pessoa in controleDePessoas.pessoasPorMes(mes)) {
         print(' > ${pessoa.nome}');
      }
   }
}

enum Mes {
   janeiro,
   fevereiro,
   marco,
   abril,
   maio,
   junho,
   julho,
   agosto,
   setembro,
   outubro,
   novembro,
   dezembro,
}

class Pessoa {
   Pessoa(this.nome, this.mesDeNascimento);

   final String nome;
   final Mes mesDeNascimento;
}

class ControleDePessoas {
   final _pessoas = <Pessoa>[];

   /// Cadastra uma pessoa no sistema
   void cadastrarPessoa(Pessoa pessoa) => _pessoas.add(pessoa);

   /// Retorna a lista de meses com pessoas cadastradas
   List<Mes> get mesesComPessoas {
      final meses = <Mes>{};
      for (final pessoa in _pessoas) {
         if (!meses.contains(pessoa.mesDeNascimento)) {
            meses.add(pessoa.mesDeNascimento);
         }
      }
      return meses.toList()..sort((a, b) => a.index.compareTo(b.index));
   }

   /// Retorna a lista de pessoas que nasceram no [mes] especificado
   List<Pessoa> pessoasPorMes(Mes mes) {
      final pessoas = <Pessoa>[];
      for (final pessoa in _pessoas) {
         if (pessoa.mesDeNascimento == mes) {
            pessoas.add(pessoa);
         }
      }
      return pessoas;
   }
}
```
# Praticando lógica de programação: Respostas

### 1 — Escreva um programa que receba uma lista de raios de círculos e com base nos raios, calcule o area e o perimetro de cada círculo e exiba no console. Utilize a biblioteca dart:math.

```dart
import 'dart:math' as math;

void main() {
  final raios = [5.0, 8.0, 12.0, 6.3, 15.0];
  calcularRaios(raios);
}

double areaCirculo(double raio) => math.pi * math.pow(raio, 2);

double perimetroCirculo(double raio) => 2 * math.pi * raio;

void calcularRaios(List<double> raios) {
  for (final raio in raios) {
    final area = areaCirculo(raio);
    final perimetro = perimetroCirculo(raio);
  
    print('Raio: $raio, área: ${area.toStringAsFixed(2)}, perímetro: ${perimetro.toStringAsFixed(2)}.');
  }
}
```

### 2 — Escreva um programa que converta uma lista temperaturas de celcius para Fahrenheit e Kelvin.

```dart 
void main() {
  final temperaturas = [0.0, 4.2, 15.0, 18.1, 21.7, 32.0, 40.0, 41.0];
  converterTemperaturas(temperaturas);
}

double celciusFahrenheit(double celcius) => celcius * (9/5) + 32;

double celciusKelvin(double celcius) => celcius + 273.15;

void converterTemperaturas(List<double> temperaturas) {
  for (final celcius in temperaturas) {
    final fahrenheit = celciusFahrenheit(celcius);
    final kelvin = celciusKelvin(celcius);
    
    print('Celcius: ${celcius.toStringAsFixed(2)}, ' 
          'fahrenheit: ${fahrenheit.toStringAsFixed(2)}, '
          'kelvin: ${kelvin.toStringAsFixed(2)}');
  }
}
```

### 3 — Escreva um programa que receba um parágrafo, e imprima no console as seguintes informações:

```dart
const vogais = 'aeiou';
const consoantes = 'bcdfghjklmnpqrstvwxyz';

void main() {
  final paragrafo = 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam venenatis nunc et posuere vehicula. Mauris lobortis quam id lacinia porttitor.';
  final palavras = contarPalavras(paragrafo);
  final tamanhoDoTexto = contarTamanhoTexto(paragrafo);
  final numeroDeFrases = contarNumeroDeFrases(paragrafo);
  final numeroDeVogais = contarNumeroDeVogais(paragrafo);
  final consoantesEncontradas = pegarConsoantesUtilizadas(paragrafo);

  print('Paragrafo: $paragrafo');
  print('Número de palavras: $palavras');
  print('Tamanho do texto: $tamanhoDoTexto');
  print('Número de frases: $numeroDeFrases');
  print('Número de vogais: $numeroDeVogais');
  print('Consoantes encontradas: $consoantesEncontradas');
}

int contarPalavras(String paragrafo) {
  if (paragrafo.trim().isEmpty) {
    return 0;
  }
  return paragrafo.split(' ').length;
}

int contarTamanhoTexto(String paragrafo) => paragrafo.trim().length;

int contarNumeroDeFrases(String paragrafo) {
  var contadorFrases = 0;
  final frases = paragrafo.trim().split('.');
  for (final frase in frases) {
    if (frase.isNotEmpty) {
      contadorFrases++;
    }
  }
  return contadorFrases;
}

int contarNumeroDeVogais(String paragrafo) {
  var contadorVogais = 0;
  for (final rune in paragrafo.trim().runes) {
    final caractere = String.fromCharCode(rune).toLowerCase();
    if (vogais.contains(caractere)) {
      contadorVogais++;
    }
  }
  return contadorVogais;
}

String pegarConsoantesUtilizadas(String paragrafo) {
  final consoantesEncontradas = <String>{};

  for (final rune in paragrafo.trim().runes) {
    final caractere = String.fromCharCode(rune).toLowerCase();
    final ehConsoante = consoantes.contains(caractere);
    if (!ehConsoante) {
      continue;
    }
    
    final jaEncontrada = consoantesEncontradas.contains(caractere);
    if (!jaEncontrada) {
      consoantesEncontradas.add(caractere);
    }
  }
  final ordenado = (consoantesEncontradas.toList())..sort();
  
  return ordenado.join(', ');
}
```

### 4 — Escreva um programa que some 18 dias de semana (ignorar sabado e domingo) partindo da data atual, e imprima a data atual e data calculada formatada no padrão dia/mes/ano (ex.: 01/01/2022).

```dart
import 'package:intl/intl.dart';

void main() {
  final dateFormat = DateFormat('dd/MM/yyyy');
  final dataAtual = DateTime.now();
  
  var diasUteisRestantes = 18;
  var dataCalculada = dataAtual;
  
  while (diasUteisRestantes > 0) {
    dataCalculada = dataCalculada.add(Duration(days: 1));
    final ehSabado = dataCalculada.weekday == DateTime.friday;
    final ehDomingo = dataCalculada.weekday == DateTime.sunday;
    
    if (ehSabado || ehDomingo) {
      continue;
    }
    
    diasUteisRestantes--;
  }
  
  print('Data atual: ${dateFormat.format(dataAtual)}');
  print('Data calculada: ${dateFormat.format(dataCalculada)}');
}
```

### 5 — Escreva um programa que gere sugestões de nomes, com base em listas pré-definidas de nomes e sobrenomes.

```dart
import 'dart:math' as math;

const nomes = [
  'Ana',
  'Maria',
  'Francisco',
  'João',
  'Pedro',
  'Gabriel',
  'Rafaela',
  'Marcio',
  'Jose',
  'Carlos',
  'Patricia',
  'Helena',
  'Camila',
  'Mateus',
  'Gabriel',
  'Samuel',
  'Karina',
  'Antonio',
  'Daniel',
  'Joel',
  'Cristiana',
  'Sebastião',
  'Paula'
];

const sobrenomes = [
  'Silva',
  'Souza',
  'Almeida',
  'Azevedo',
  'Braga',
  'Barros',
  'Campos',
  'Cardoso',
  'Costa',
  'Teixeira',
  'Santos',
  'Rodrigues',
  'Ferreira',
  'Alves',
  'Pereira',
  'Lima',
  'Gomes',
  'Ribeiro',
  'Carvalho',
  'Lopes',
  'Barbosa'
];

void main() {
  final random = math.Random();
  final nomeGerado = nomes[random.nextInt(nomes.length)];
  final sobrenomeGerado = sobrenomes[random.nextInt(sobrenomes.length)];
  final nomeCompletoGerado = '$nomeGerado $sobrenomeGerado';

  print('Nome gerado: $nomeCompletoGerado');
}
```

### 6 — Escreva um programa que receba uma lista de números inteiros e imprima no console em ordem crescente os números representados na forma decimal, binaria, octal e hexadecimal.

```dart
void main() {
  final numeros = [3, 17, 23, 49, 328, 1358, 21, 429, 12, 103, 20021];
  imprimirNumeros(numeros);
}

void imprimirNumeros(List<int> numeros) {
  for (final decimal in numeros..sort()) {
    print('decimal: $decimal, '
          'binario: ${decimal.toRadixString(2)}, '
          'octal: ${decimal.toRadixString(8)}, '
          'hexadecimal: ${decimal.toRadixString(16)}');
  }
}
```

### 7 — Escreva um programa que receba uma lista de números inteiros, e retorne o somatorio dos números na lista. Implemente essa função em três modelos:

```dart
void main() {
  final numeros = [10, 35, 999, 126, 95, 7, 348, 462, 43, 109];
  final resultadoFor = somaFor(numeros);
  final resultadoWhile = somaWhile(numeros);
  final resultadoLista = somaLista(numeros);
  final resultadoRecursivo = somaRecursivo(numeros);
  
  print('for: $resultadoFor');
  print('while: $resultadoWhile');
  print('recursão: $resultadoLista');
  print('lista: $resultadoRecursivo');
}

int somaFor(List<int> numeros) {
  var soma = 0;
  for (final numero in numeros) {
    soma += numero;
  }
  return soma;
}

int somaWhile(List<int> numeros) {
  var soma = 0;
  final iterador = numeros.iterator;
  while(iterador.moveNext()) {
    soma += iterador.current;
  }
  return soma;
}

int somaLista(List<int> numeros) => numeros.reduce((a, b) => a + b);

int somaRecursivo(List<int> numeros) {
  if (numeros.isEmpty) {
    return 0;
  }
  return numeros.first + somaRecursivo(numeros.sublist(1));
}
```

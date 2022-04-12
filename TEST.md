# Teste para pessoa desenvolvedora PHP

[← Voltar](README.md).

⚠️ Todas as perguntas são baseadas no **PHP 7.4.28**.

## Exemplo

### 0. Quais os valores de `$a` e `$b` no código abaixo? Por quê?

```php
$a = array_merge(array(1,2), NULL);
$b = array_merge($a, array(3));

var_dump($a);
var_dump($b);
```

> ```
> NULL
> NULL
> ```
> 
> A função `array_merge` retorna `NULL` quando qualquer um dos argumentos não for do tipo `array`. Embora o PHP 7 emita warnings sobre erro no tipo do argumento nem toda instalação está configurada para exibir warnings, logo é importante o desenvolvedor verificar os valores maualmente antes da chamada do `array_merge`, especialmente quando estamos concatenando o retorno de um `array_merge`.
>
> No PHP 8 esse comportamento foi atualizado para emitir um erro, o que ajuda a prevenir problemas.
> 
> ```
> Fatal error: Uncaught TypeError: array_merge(): Argument #2 must be of type array
> ```

## Perguntas

### 1. Qual a diferença entre `echo` e `print`?

> (O echo por ser implementado diretamente na linguagem e por não ter retorno é ligeiramente mais rápido e por isso é recomendado seu uso, o print pode ser utilizado em expressões, ambos tem a mesma finalidade.)

### 2. Qual é a saída do código abaixo? Por quê?

```php
$x = true and false;
var_dump($x);
```

> (Nesse caso o valor atribuído mais próximo do = que é que vale pois ficaria basicamente assim a expressão:
> ($x = true) and false;
> se trocássemos a ordem daria false no var_dump.)

### 3. Qual é a saída do código abaixo? Por quê?

```php
$x = 5;
$a = array(
    $x++ + $x++,
    $x,
    $x-- - $x--,
    $x,
);

var_dump($a);
```

> (Saída: array(4) { [0]=> int(11) [1]=> int(7) [2]=> int(1) [3]=> int(5) }  
> Na posição [0] o $x que valia 5 foi somado ao $x que já valia 6 então o resultado é 11.  
> Na posição [1] o $x que agora valia 7, resultado do incremento da posição [0] onde foi incrementado duas vezes é apenas exibido sem somar e sem incrementar.  
> Na posição [2] o $x que valia 7 é subtraído do mesmo $x, porém que já passa a valer 6 pois foi decrementado, então o resultado é 1, e o mesmo $x é decrementado novamente.  
> Na posição [3] o $x volta a valer 5 pois foi decrementado duas vezes na posição [2].)

### 4. Quais serão os valores de `$a` e `$b` após a execução do código abaixo? Por quê?

```php
$a = '1';
$b = &$a;
$b = "2$b";
```

> (21 e 21 respectivamente, pois colocando o & significa fazer uma referência a outra variável, então alterado o valor de uma altera o da outra também.)

### 5. O que são Traits e para que servem? 

> (Traits são pedaços de código que precisam ser utilizados por diferentes classes, porém sem a necessidade de herança.)

### 6. Qual será a saída do código abaixo? Por quê?

```php
var_dump(0123 == 123);
var_dump('0123' == 123);
var_dump('0123' === 123);
```

> (Saída: bool(false) bool(true) bool(false)  
> O primeiro var_dump retorna false porque estamos comparando um número octal com um número decimal, 0123 = 83 em decimal, logo diferente de 123.  
> O segundo var_dump retorna true pois estamos comparando uma string com um inteiro, essa string é forçada a ser convertida em um número inteiro, nessa conversão que dará certo o 0 (zero) é ignorado, então 123 == 123 está correto.  
> O terceiro var_dump utiliza uma comparação mais restrita, e este não faz a conversão de string para inteiro retornando false.)

### 7. Qual será a saída do código abaixo? Por quê?

```php
$a = '';
$b = 0;
$c = '0a';

var_dump($a == $b);
var_dump($b == $c);
var_dump($c == $a);
```

> (bool(true) bool(true) bool(false)  
> True porque fará a conversão pra inteiro, e $b sendo 0 ele não espera nada.  
> True porque novamente tentará fazer a conversão pra inteiro de $c e dará 0, então 0 == 0.  
> False porque uma string é realmente diferente da outra.)

### 8. Qual será o valor de `$x` após a execução do código abaixo? Por quê?

```php
$x = 3 + "15%";
```

> (Ele nos dá um aviso sobre o número encontrado: NOTICE A non well formed numeric value encountered on line number 3  
> E nos exibe um número inteiro 18, pois ele tenta converter a string para um inteiro, e como há o 15, a conversão é feita realizando 3 + 15 = 18.)

### 9. Qual a diferença entre `require_once()` e `include_once()`?

> (Em ambos os casos a junção do _once verifica se o arquivo já foi incluso, isso faz garantir que não seja incluso novamente.  
> A diferença entre os dois é basicamente que em caso de falha o require_once fará o script parar com um erro de nível fatal E_COMPILE_ERROR, no caso do include ele apenas irá dar warnings que podem ser escondidos com o uso do @.)

### 10. Qual será o valor de `$name` após a execução do código abaixo? Por quê?

```php
$name = 'John ';
$name[10] = 'Doe';
```

> (Saída: John D  
> Uma string é um array de caractéres, então quando adicionamos Doe na posição 10 de $name ele consegue apenas pegar uma letra por vez, que no caso a primeira é D, ao printar ele não exibe todos os espaços, mas se dermos um strlen em $name irá nos retornar 11.)

### 11. Qual será a saída do código abaixo? Por quê?

```php
$x = PHP_INT_MAX;
echo gettype($x + 1);
echo (int)($x + 1);

$y = 1.0;
echo is_float($y);
echo gettype($y);
```

> (No primeiro echo temos que $x é double, porque com a soma do int maximo com 1, ele faz este calculo: 0111 (=7) + 0001 (=1) = 1000 (= -7) assim transformando o número em double.  
> No segundo echo ele nos exibe -9223372036854775808 pois houve um estouro de número inteiro, onde é feita a conversão do número pra inteiro que antes era assim 9.2233720368548E+18.  
> No terceiro echo é verificado se a variável é do tipo float, retornando 1 já que é float.  
> No último echo ele exibe que o tipo é double, como está descrito na própria documentação do php: "por razões históricas "double" é retornado no caso de float, e não simplesmente float".)

### 12. Qual será o valor de `$x` após a execução do código abaixo? Por quê?

```php
$x = "one" + 1;
```

> (O resultado será 1, pois é tentado a soma da string com o inteiro mas na string não possui nenhum número para ser convertido para inteiro.)

### 13. Qual a diferença entre `isset()` e `empty()`?

> (isset verifica se a variável está definida e se não é nula, se for nula ou não definida retorna false, caso contrário true.  
> empty verifica se a variável está vazia, se ela não existir, for nula, ou tiver um valor do tipo string '' ou int 0, também será vazia retornando true, caso contrário false.)

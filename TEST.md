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

> (Sua resposta aqui.)

### 2. Qual é a saída do código abaixo? Por quê?

```php
$x = true and false;
var_dump($x);
```

> (Sua resposta aqui.)

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

> (Sua resposta aqui.)

### 4. Quais serão os valores de `$a` e `$b` após a execução do código abaixo? Por quê?

```php
$a = '1';
$b = &$a;
$b = "2$b";
```

> (Sua resposta aqui.)

### 5. O que são Traits e para que servem? 

> (Sua resposta aqui.)

### 6. Qual será a saída do código abaixo? Por quê?

```php
var_dump(0123 == 123);
var_dump('0123' == 123);
var_dump('0123' === 123);
```

> (Sua resposta aqui.)

### 7. Qual será a saída do código abaixo? Por quê?

```php
$a = '';
$b = 0;
$c = '0a';

var_dump($a == $b);
var_dump($b == $c);
var_dump($c == $a);
```

> (Sua resposta aqui.)

### 8. Qual será o valor de `$x` após a execução do código abaixo? Por quê?

```php
$x = 3 + "15%";
```

> (Sua resposta aqui.)

### 9. Qual a diferença entre `require_once()` e `include_once()`?

> (Sua resposta aqui.)

### 10. Qual será o valor de `$name` após a execução do código abaixo? Por quê?

```php
$name = 'John ';
$name[10] = 'Doe';
```

> (Sua resposta aqui.)

### 11. Qual será a saída do código abaixo? Por quê?

```php
$x = PHP_INT_MAX;
echo gettype($x + 1);
echo (int)($x + 1);

$y = 1.0;
echo is_float($y);
echo gettype($y);
```

> (Sua resposta aqui.)

### 12. Qual será o valor de `$x` após a execução do código abaixo? Por quê?

```php
$x = "one" + 1;
```

> (Sua resposta aqui.)

### 13. Qual a diferença entre `isset()` e `empty()`?

> (Sua resposta aqui.)

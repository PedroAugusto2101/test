# Início

---

- Máquinas só entendem binários. Enquanto humanos esrcevem o código fonte - que é uma lista de instruções para o computador escrita de forma que um humano consegue ler - as máquinas entendem apenas o que chamamos de código de máquina (padrões de 1s e 0s).
- Compilador → software que nos permite converter o código fonte em código de máquina.
- Não só escrever código, devemos escrever bons códigos.
- Um código pode ser dividido em três pontos importantes:
    - Correção: o código funciona como deveria?
    - Design: quão bom estruturado está o código?
    - Estilo: o quão bonito e legível está o código?

# Hello World

---

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/80f2fb02-6347-4ab2-9ad9-8591ced5e730/Untitled.png)

1. Explorador de arquivos: onde estão os arquivos criados;
2. Editor de texto: onde você escreve o seu código;
3. Terminal: onde você manda comandos para o computador.
- Para criar e rodar um programa, segue-se os três comandos exemplo abaixo:

```bash
code hello.c # cria o arquivo para se digitar o código fonte
make hello # compila o código para a máquina entender e cria um executável
./hello # roda o código criado, tendo o resultado esperado
```

- São criados dois arquivos:
    - hello.c → onde o seu código está armazenado;
    - hello → arquivo executável do código;
- O compilador permite que clicamos onde queremos que faça algo, ou então que façamos tudo pelo terminal.
- Tentar sempre usar o terminal dentro do compilador -> aprende mais, mais hardcode (melhor pro aprendizado).
- DICA: ocultar as outras abas e deixar focado somente no código e no terminal
$ -> prompt - terminal.
- Por convenção, nunca usar letras maiúsculas ou espaço para nomes de arquivos e programas.

```c
#include <stdio.h>

int main(void)
{
	printf("hello, world\n");
}
```

- C é uma das linguagens mais antigas.

# Funções

---

- No Scratch, a função para escrever na tela é o `say`, enquando que no C, a função seria o `printf`.

```c
printf("hello, world\n");
```

O argumento passado para a função `printf` é o `‘hello, world\n’`. Toda linha de código deve ser fechada com um `;`.

- A `\` é um caracter de escape, que define para o compilador que o `\n` é uma instrução especial (no caso, o cursor salta para a próxima linha).
- A declaração `#include <stdio.h>` no início do código diz que vamos usar as dependências da biblioteca chamada `stdio.h` - um arquivo de cabeçalho. É o que permite usar a função `printf`.
- Bibliotecas são coleções pré-escritas de funções que outras pessoas criaram para facilitar o desenvolvimento de um código.

# Variáveis

---

```c
#include <stdio.h>

int main(void)
{
    string answer = get_string("What's your name? ");
    printf("hello, %s\n", answer);
}
```

A função `get_string` é usada para pegar a `string` digitada pelo usuário, e armazenada na variável `answer` (lembrando que na lingaugem C, devemos por o tipo da variável declarada). Após isso, a variável `answer` é passada para a função `printf`, em que o `%s` diz ao `printf` que receberá o valor da variável `answer` como saída.

- %s é chamado de formato de código, e fiz à função printf para preparar para receber a string (no caso, armazenada em answer);
- get_string não será reconhecida, pois não importamos sua biblioteca - devemos sempre importar a bibliotecas que contenham as funções que vamos utilizar.

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    string answer = get_string("What's your name? ");
    printf("hello, %s\n", answer);
}
```

- printf permite vários formatos de código:
    - %c → caractere
    - %f → float
    - %i → integer
    - %li → long integer
    - %s → string

# Condicionais

---

- Em C, para atribuir um valor para um `int`:

```c
int counter = 0;
```

- Também podemos representar a adição de um ao counter:

```c
counter = counter + 1;
```

- Ou então da seguinte maneira:

```c
counter = counter++;
```

- Para reduzir um:

```c
counter = counter--;
```

- O nome da expressão que dá condição ao condicionais se chama "Expressão booleana".
- Se tivermos apenas uma linha dentro da condição, não é necessário isar os { }.
- Tente sempre buscar escrever menos na tela, ter sempre o menor código possível.
- `./` significa que o arquivo está no diretório atual.
`../` siginfica que o arquivo está no diretório anterior.
- Estrutura condicional:

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int x = get_int("What's x? ");
    int y = get_int("What's y? ");

    if (x < y)
    {
        printf("x is less than y\n");
    }
}
```

- `string` refere-se a uma série de caracteres, `char` refere-se a um único caracter.
- Programa “agree”:

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    // Prompt user to agree
    char c = get_char("Do you agree? ");

    // Check whether agreed
    if (c == 'Y' || c == 'y')
    {
        printf("Agreed.\n");
    }
    else if (c == 'N' || c == 'n')
    {
        printf("Not agreed.\n");
    }
}
```

- Note que `‘ ‘` é usado para apenas um carecter, enquanto que `“ “` é usado para mais de um caracter.
- `==` diz que algo é igual a alguma outra coisa, enquanto que `=` atribui o valor de algo a alguma outra coisa.
- `||` siginifica “ou”.

# Loops

---

```c
int counter = 3;
while (counter > 0)
{
    printf("meow\n");
    counter = counter - 1;
}
```

- Exemplo de código que pode ser melhorado um um loop:

```c
#include <stdio.h>

int main(void)
{
    printf("meow\n");
    printf("meow\n");
    printf("meow\n");
}
```

- Podemos melhorá-lo com o código abaixo:

```c
#include <stdio.h>

int main(void)
{
    int i = 3;
    while (i > 0)
    {
        printf("meow\n");
        i--;
    }
}
```

- Como boa prática, utilizamos o ‘i’ como contadores, incremetamos variáveis com o ‘i++’ e iniciamos nossos contadores com zero ‘i = 0;’.

```c
#include <stdio.h>

int main(void)
{
    int i = 0;
    while (i < 3)
    {
        printf("meow\n");
        i++;
    }
}
```

- For loop

```c
#include <stdio.h>

int main(void)
{
    for (int i = 0; i < 3; i++)
    {
        printf("meow\n");
    }
}
```

int i = 0 → inicia o contador em zero, i < 3 → condição para sair do loop, limitador, i++ → modo de incremento do contador toda vez que roda o loop.

- Loop infinito → while (True)

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    while (true)
    {
        printf("meow\n");
    }
}
```

O único jeito de sair de um loop infinito em C é apertando `ctrl + C`

# Criando funções em C

---

```c
void meow(void)
{
	printf("meow\n");
}
```

O `void` inicial significa que a função não retorna nenhum valor. O `(void)` significa que nenhum valor é dado como input da função.

- Chamando a função:

```c
#include <stdio.h>

int main(void)
{
	for (int i = 0; i < 3; i++)
	{
		meow();
	}
}
```

- Devemos definir as funções antes de usá-las.
- Para evitar que criemos várias funções antes do main, sendo que é uma boa prática o main sempre ficar nas primeiras linhas de código, apenas criamos uma indicação (protótipo) de que terá a função meow, assim o código irá ser lido por completo para verificar se essa função existe, e existindo, irá reconhecê-la, mesmo que esteja após chamar a função. Exemplo:

```c
#include <stdio.h>

void meow(void);

int main(void)
{
	for (int i = 0; i < 3; i++)
	{
		meow();
	}
}

void name(void)
	{
		printf("meow\n");
	}
```

- Para se criar inputs nas funções, devemos indicar qual o tipo, e o nome do input. Exemplo:

```c
#include <stdio.h>

void meow(int n);

int main(void)
{
    meow(3);
}

// Meow some number of times
void meow(int n)
{
    for (int i = 0; i < n; i++)
    {
        printf("meow\n");
    }
}
```

Aqui, nós definimos `n` como o input da função, e esse `n` está sendo utilizado como limitador do for. Ou seja, podemos `controlar o limite do contador do for` nesse exemplo acima.

# Operadores e Abstração

---

- Calculadora em C.

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
	// Comando do usuário para x
	int x = get_int("x: ");
	
	// Comando do usuário para y
	int y = get_int("y: ");
	
	// Realizando a adição
	printg("%i\n", x + y);
}
```

- **Operadores** referem-se a operações matemáticas que são suportadas pelo compilador. Em C, essas operações incluem:
    - `+` para adição
    - `-` para subtração
    - `*` para multiplicação
    - `/` para divisão
    - `%` para resto da divisão
- **Abstração** é o processo de simplificar nosso código a fim de que lidemos com problemas cada vez menores.
- Podemos abstrair nossa adição em uma função:

```c
#include <cs50.h>
#include <stdio.h>

int add(int a, int b);

int main(void)
{
	// Comando do usuário para x
	int x = get_int("x: ");
	
	// Comando do usuário para y
	int y = get_int("y: ");
	
	// Realizando a adição
	printg("%i\n", x + y);
}

int add(int a, int b)
{
	int c = a + b;
	return c;
}
```

Note que a função `add` tem duas variáveis como input, `a` e `b`, e realizam o cálculo retornando `c`. Além disso, o `escopo (contexto em que uma variável existe)` de `x` é a função `main`. A variável `c` está dentro somente da função `add`.

- Podemos melhorar ainda mais o design do programa:

```c
#include <cs50.h>
#include <stdio.h>

int add(int a, int b);

int main(void)
{
	// Comando do usuário para x
	int x = get_int("x: ");
	
	// Comando do usuário para y
	int y = get_int("y: ");
	
	// Realizando a adição
	printg("%i\n", x + y);
}

int add(int a, int b)
{
	return a + b;
}
```

# Linux e Linha de Comando

---

- `Linux` é o sistema utilizado no VS Code e acessado via terminal.
- Argumentos de linha de comando mais comuns:
    - `cd`, para mudar o deretório atual (pasta)
    - `cp`, para copiar arquivos e diretórios
    - `ls`, para listar os arquivos em um diretório
    - `mkdir`, para criar um diretório
    - `mv`, para mover (renomeando) arquivos e diretórios
    - `rm`, para remover (deletando) arquivos
    - `rmdir`, para remover (deletando) diretórios
- O comando mais utilizado é o `ls`.
- Outro comando útil é o `mv`, pois podemos usá-lo para renomear um arquivo, digitando `mv Hello.c hello.c`, em que renomeamos Hello.c para `hello.c`.

# Mario

---

- Tudo discutido tem foco relação com vários blocos de contrução distribuidos verticalmente ou horizontalmente.
- Como por exemplo, caso queiramos emular o visual do jogo mário, como podemos fazer?

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/2eff74a4-a2ea-4fcf-be76-fc7a99978f9e/Untitled.png)

```c
#include <stdio.h>

int main(void)
{
	for (int i = 0; i < 4; i++)
	{
		printf("?");
	}
}
```

- Podemos aplicar a mesma lógica para blocos verticias:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/6bd04300-0939-4fd2-ba1d-d10127ca973e/Untitled.png)

```c
#include <stdio.h>

int main(void)
{
	for (int i = 0; i < 3; i++)
	{
		printf("#\n");
	}
}
```

- Agora, para combinar as duas ideias e criar um bloco três por três:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/85a3a532-c493-4960-a731-a4822a0ccf8d/8ca4e5bb-07fb-4c2d-9e5c-94aa6731b421/Untitled.png)

```c
#include <stdio.h>

int main(void)
{
	for (int = 0; i < 3; i++)
	{
		for (int j = 0; j < 3; j++)
		{
			printf("#");
		}
		printf("\n");
	}
}
```

- Podemos definir um valor constante para setarmos o tamanho do bloco:

```c
int main(void)
{
    const int n = 3; // setando o tamanho do bloco para 3x3
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            printf("#");
        }
        printf("\n");
    }
}
```

- Podemos também pedir para o usuário definir o tamanho que ele deseja:

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int n = get_int("Size: ");

    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            printf("#");
        }
        printf("\n");
    }
}
```

- Uma dica importante para programação, é que não devemos nunca confiar que o usuário irá usar o programa da maneira correta. Para isso, podemos proteger nosso programa contra comportamentos errados, checando se o input do usuário satisfaz o que o código necessita.

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int n;
    do
    {
        n = get_int("Size: ");
    }
    while (n < 1);

    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            printf("#");
        }
        printf("\n");
    }
}
```

# Comentários

---

- Comentários são uma parte fundamental de um programa, em que podemos deixar recados para nós mesmos ou para outros, colaborando para o entendimento do código;
- Ou seja, cada comentário é um grupo de palavras que permite o leitor a oportunidade de entender o que está acontecendo em um bloco específico de código. Podem servir também como um lembrete futuro para quando precisar revisar o código.
- Em C, comentário são inseridos após o uso de `//`

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    // Prompt user for positive integer
    int n;
    do
    {
        n = get_int("Size: ");
    }
    while (n < 1);

    // Print an n-by-n grid of bricks
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            printf("#");
        }
        printf("\n");
    }
}
```

# Tipos

---

- Enquanto a linguagem C fornece um imenso controle sobre como a memória é utilizada, programadores têm que estar sempre atento aos problemas de gerenciamento de memória.
- **Tipos** referem-se ao possível dado que pode ser amarzenado em determinada variável. Por exemplo, um `char` é feito para armazenar **um único caractere**, como `a` ou `2`.
- Os tipos são importantes porque cada tipo tem um limite específico. Devido ao limite na sua memória, o valor máximo que um `int` pode ter é `4294967295`. Se tentar armazenar um valor superior em um `int`, um ***integer overfow*** será resultado no valor armazenado nesta variável.
- O número de bits limita o quão alto ou baixo nós podemos contar.
- Tipos que podemos utilizar:
    - `bool`, uma expressão booleana é true ou false
    - `char`, um caractere único como a ou 2
    - `double`, um valor de ponto flutuante com mais dígitos que um float
    - `float`, um valor de ponto flutuante, ou número real com valor decimal
    - `int`, inteiros até um determinado valor ou número de bits
    - `long`, inteiros com mais bits, então podem contar mais que um int
    - `string`, uma sequência de caracteres

# Aula 02 — Clique e Sorteio

Lista de exercícios da disciplina de Mobile — Aula 02.

Os exercícios trabalham eventos de clique usando `android:onClick`, atualização de componentes da interface com `findViewById` e `setText`, geração de números aleatórios e mensagens no Logcat.

## Tecnologias utilizadas

* Java
* Android Studio
* Android SDK
* XML
* ConstraintLayout

---

# Exercício 1 — Saudar

Criação de um botão **"Saudar"** ligado à função `saudarUsuario()`.

Ao clicar no botão, o aplicativo:

* Imprime uma mensagem no Logcat.
* Atualiza o `TextView` com a mensagem **"Olá, seja bem-vindo(a)!"**.

### Código Java

```java
public void saudarUsuario(View view) {
    System.out.println("Usuário clicou em Saudar!");

    TextView texto = findViewById(R.id.txtSaudacao);
    texto.setText("Olá, seja bem-vindo(a)!");
}
```

---

# Exercício 2 — Contador de Cliques

Criação de um botão **"Contar"** que registra quantas vezes foi clicado.

A variável `contador` fica fora da função para manter o valor entre os cliques.

### Variável

```java
int contador = 0;
```

### Código Java

```java
public void contarClique(View view) {
    contador++;

    TextView texto = findViewById(R.id.txtContador);
    texto.setText("Cliques: " + contador);

    System.out.println("botão clicado " + contador + " vezes");
}
```

Exemplo:

```text
Cliques: 1
Cliques: 2
Cliques: 3
```

---

# Exercício 3 — Sorteio com Aviso no Logcat

O aplicativo sorteia um número de **0 a 10**.

O número aparece no `TextView` e também é informado no Logcat como par ou ímpar.

### Código Java

```java
public void sortear(View view) {
    TextView textoResultado = findViewById(R.id.txtResultado);

    Random random = new Random();
    int numero = random.nextInt(11);

    textoResultado.setText("Resultado gerado: " + numero);

    if (numero % 2 == 0) {
        System.out.println("número par sorteado: " + numero);
    } else {
        System.out.println("número ímpar sorteado: " + numero);
    }
}
```

### Exemplo no Logcat

```text
número par sorteado: 8
```

ou

```text
número ímpar sorteado: 5
```

---

# Exercício 4 — Dado com Histórico

A função `sortear()` é transformada em `rolarDado()`.

O aplicativo:

* Sorteia um número de 1 a 6.
* Conta quantas vezes o dado foi rolado.
* Mostra a rolagem e o resultado no `TextView`.
* Registra cada rolagem no Logcat.

### Variável

```java
int contador = 0;
```

### Código Java

```java
public void rolarDado(View view) {
    contador++;

    Random random = new Random();
    int numero = random.nextInt(6) + 1;

    TextView textoResultado = findViewById(R.id.txtResultado);

    textoResultado.setText(
            "Rolagem " + contador + ": resultado " + numero
    );

    System.out.println(
            "Rolagem " + contador + ": resultado " + numero
    );
}
```

### Exemplo na tela

```text
Rolagem 3: resultado 5
```

O número sorteado sempre estará entre **1 e 6**.

---

# Exercício 5 — Dois Botões e uma Função em Comum

Neste exercício existem três botões:

* **Aviso** — apenas imprime uma mensagem no Logcat.
* **Sortear** — apenas sorteia e mostra o resultado na tela.
* **Ambos** — faz as duas ações.

## Função Aviso

```java
public void aviso(View view) {
    System.out.println("Botão Aviso clicado!");
}
```

## Função Sortear

```java
public void sortear(View view) {
    TextView textoResultado = findViewById(R.id.txtResultado);

    Random random = new Random();
    int numero = random.nextInt(11);

    textoResultado.setText("Resultado gerado: " + numero);
}
```

## Função Ambos

```java
public void avisarESortear(View view) {
    System.out.println("Botão Ambos clicado!");

    TextView textoResultado = findViewById(R.id.txtResultado);

    Random random = new Random();
    int numero = random.nextInt(11);

    textoResultado.setText("Resultado gerado: " + numero);
}
```

### XML dos botões

```xml
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Aviso"
    android:onClick="aviso" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Sortear"
    android:onClick="sortear" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Ambos"
    android:onClick="avisarESortear" />
```

---

# Exercício 6 — Cor conforme o resultado

O aplicativo sorteia um número e muda a cor do texto dependendo se o número é par ou ímpar.

Também registra no Logcat qual cor foi aplicada.

### Imports

```java
import android.graphics.Color;
import java.util.Random;
```

### Código Java

```java
public void sortear(View view) {
    TextView textoResultado = findViewById(R.id.txtResultado);

    Random random = new Random();
    int numero = random.nextInt(11);

    textoResultado.setText("Resultado gerado: " + numero);

    if (numero % 2 == 0) {
        textoResultado.setTextColor(
                Color.parseColor("#1F7A6C")
        );

        System.out.println(
                "Número par: " + numero + " — cor verde aplicada"
        );

    } else {
        textoResultado.setTextColor(
                Color.parseColor("#C62828")
        );

        System.out.println(
                "Número ímpar: " + numero + " — cor vermelha aplicada"
        );
    }
}

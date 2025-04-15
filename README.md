# Quais são os 4 pilares da Programação Orientada a Objetos? (POO)

A Programação Orientada a Objetos é como um jogo de Lego: você constrói sistemas complexos a partir de peças menores e organizadas. 

Para que tudo funcione harmoniosamente, a POO se apoia em quatro princípios fundamentais, veja quais são.

## 1. Abstração: foco no essencial
Imagine descrever um avião para alguém. Você fala sobre asas, motores e assentos, mas não menciona cada parafuso ou fio interno. 

A abstração faz o mesmo no código: ela extrai apenas os elementos relevantes de um objeto, ignorando detalhes desnecessários. 

É como criar um modelo simplificado do mundo real.

## 2. Encapsulamento: proteção e controle
Pense em um cofre: você não pode simplesmente pegar o dinheiro dentro dele – precisa digitar a senha correta. 

O encapsulamento segue essa lógica: ele esconde os detalhes internos de um objeto e só permite acesso através de métodos controlados. 

Isso evita que dados importantes sejam alterados de forma imprevisível.

## 3. Herança: reaproveitamento inteligente
Na natureza, um gato herda características dos felinos (como garras retráteis).

Na POO, a herança funciona assim: você cria uma classe “pai” com características gerais e classes “filhas” que herdam essas propriedades, mas podem ter features exclusivas. 

É um jeito de evitar repetição de código e manter tudo organizado.

## 4. Polimorfismo: flexibilidade em ação
A palavra “polimorfismo” vem do grego e significa “muitas formas”. Na prática, é a capacidade de um mesmo método se comportar de maneiras diferentes, dependendo do objeto que o executa. 

Por exemplo, o comando “mover()” pode fazer um carro acelerar, um avião decolar ou um barco navegar: mesmo nome, ações distintas.

# Quais são os principais conceitos de POO em Python?
Vamos traduzir os conceitos para código de verdade. Com a orientação a objetos em Python, teríamos:

Classe: a “receita” do objeto (ex.: class Bolo:);
Objeto: o bolo pronto (ex.: meu_bolo = Bolo(“chocolate”));
Atributo: características (ex.: meu_bolo.sabor = “morango”);
Método: ações (ex.: meu_bolo.assar()).

Entenda no exemplo prático abaixo:

```python
class Celular:  
    def __init__(self, modelo):  
        self.modelo = modelo
        self.carga = 100  

    def tirar_foto(self):  
        if self.carga > 0:
            print("Foto tirada!")  
            self.carga -= 10  
        else:  
            print("Sem bateria!")  

# Usando a classe  
meu_celular = Celular("Galaxy")  
meu_celular.tirar_foto()  # Saída: "Foto tirada!"

```

# Uso do "_" no Pytho

### ✅ **1. `_variavel` (underscore no início)**
- **Indica que o atributo ou método é "protegido"**.
- É uma convenção para dizer: "isso é interno, não use diretamente fora da classe ou herança".
- **Não impede o acesso**, mas avisa o programador que ele deve ser cuidadoso.

```python
class Pessoa:
    def __init__(self, nome):
        self._nome = nome  # protegido por convenção
```

---

### ✅ **2. `__variavel` (dois underscores no início)**
- Ativa o **name mangling**: o Python renomeia internamente para evitar colisões em subclasses.
- Usado para indicar que é **privado de verdade** (ou o mais próximo disso no Python).
- Útil em herança quando você quer evitar sobrescrita acidental.

```python
class Pessoa:
    def __init__(self, nome):
        self.__segredo = nome  # vira _Pessoa__segredo internamente
```

---

### ✅ **3. `variavel__` (dois underscores no final)**
- Evita conflito com palavras-chave do Python.
- Raramente usado, mas pode ser útil.

```python
class Classe:
    def __init__(self, class__):
        self.class__ = class__
```

---

### ✅ **4. `_` (underscore sozinho)**
- Usado como **variável descartável**, quando você não vai usar o valor.

```python
for _ in range(5):  # não preciso do valor do loop
    print("Olá")
```

- Também pode ser usado no terminal interativo para pegar o último valor retornado:
```python
>>> 3 + 4
7
>>> _
7
```

---

### ✅ **5. Métodos especiais (`__init__`, `__str__`, etc.)**
- Chamados de **"dunder methods"** (double underscore).
- Fazem parte da **interface do Python** para objetos.
- Servem para comportamentos mágicos (construtor, representação em string, operadores, etc).

```python
class Pessoa:
    def __init__(self, nome):
        self.nome = nome

    def __str__(self):
        return self.nome
```

---

# Conceitos:  **constructor** e **decorator** 

---

## 🔧 **Constructor (Construtor)**

### O que é?
- É o método chamado automaticamente **quando um objeto é criado**.
- Em Python, o construtor é o método especial `__init__`.

### Sintaxe:
```python
class Pessoa:
    def __init__(self, nome, idade):
        self.nome = nome
        self.idade = idade
```

### Uso:
```python
p = Pessoa("Ana", 30)  # __init__ é chamado aqui
print(p.nome)  # Ana
```

### Explicação:
- O `__init__` **inicializa o objeto**, dando valores iniciais aos atributos.
- O `self` representa a **instância da classe** (tipo `this` em outras linguagens).

---

## 🎀 **Decorator (Decorador)**

### O que é?
- É uma **função que modifica o comportamento de outra função ou método**, sem alterá-la diretamente.
- Muito usado para **reutilizar código**, **verificar permissões**, **criar logs**, **medir tempo de execução**, etc.

### Sintaxe básica:
```python
def meu_decorator(func):
    def wrapper():
        print("Antes da função")
        func()
        print("Depois da função")
    return wrapper

@meu_decorator
def diz_oi():
    print("Oi!")

diz_oi()
```

### Saída:
```
Antes da função
Oi!
Depois da função
```

### Explicação:
- O `@meu_decorator` é **açúcar sintático** para `diz_oi = meu_decorator(diz_oi)`
- O `wrapper()` é a função que **envolve** a original.

---

### Decorators comuns em POO:

#### ✅ `@property`
Torna um método acessível como um atributo:
```python
class Retangulo:
    def __init__(self, largura, altura):
        self.largura = largura
        self.altura = altura

    @property
    def area(self):
        return self.largura * self.altura

r = Retangulo(3, 4)
print(r.area)  # 12, sem parênteses
```

#### ✅ `@classmethod` e `@staticmethod`

```python
class Exemplo:
    @staticmethod
    def saudacao():
        print("Oi!")

    @classmethod
    def criar(cls):
        return cls()
```
Boa! O uso do `__main__` é uma daquelas coisas simples **mas super poderosas** em Python, especialmente pra **organizar melhor o código**, criar **scripts reutilizáveis** e evitar bugs. Bora entender 👇

---

## 🧠 O que é `__main__`?

Quando você roda um arquivo `.py`, o Python define uma variável especial chamada `__name__`.  
- Se o arquivo estiver sendo **executado diretamente**, `__name__ == "__main__"`.
- Se o arquivo for **importado como módulo**, `__name__` vai valer o **nome do arquivo**, e **não será `"__main__"`**.

---

## ✅ Exemplo prático:

```python
# arquivo: meu_script.py

def saudacao():
    print("Olá!")

if __name__ == "__main__":
    saudacao()
```

### Resultado:
- Se você rodar no terminal: `python meu_script.py`  
  → Saída: `Olá!`

- Se importar esse arquivo num outro script:
```python
import meu_script
```
→ **Nada acontece!** (a função só é chamada se você quiser)

---

## 🤔 Por que usar isso?

1. **Evita que código seja executado quando o módulo for importado.**
2. **Permite reaproveitar funções e classes sem efeitos colaterais.**
3. É o que dá ao Python aquela flexibilidade de "isso pode ser script ou biblioteca".

---

## 🔁 Analogia simples

Pensa assim:

```python
if __name__ == "__main__":  # "Sou o principal que está sendo rodado?"
```

Se sim → "Pode executar tudo que está aqui dentro".  
Se não → "Fica quietinho aí, só me usa se quiser importar!"

---

- `@staticmethod`: não usa `self` nem `cls` — é só uma função dentro da classe.
- `@classmethod`: recebe `cls` em vez de `self` — útil para **fábricas de objetos**.

---


# **Desafio dio - Abstraindo Formações da DIO Usando Orientação a Objetos com Kotlin**

###### 

Neste projeto aprimorado, expandimos nosso sistema para abstrair formações da DIO usando orientação a objetos com Kotlin. Além das classes básicas, adicionamos novas funcionalidades e cenários de teste.

## **Novas Funcionalidades**

- **Níveis de Formação:** Adicionamos o enum `Nivel` para representar os níveis de dificuldade das formações (Básico, Intermediário, Difícil).
- **Matrícula de Usuários:** Adicionamos o método `matricular` à classe `Formacao` para permitir que usuários se matriculem em formações.
- **Gerenciamento de Inscritos:** Mantemos uma lista de usuários inscritos em cada formação na propriedade `inscritos`.

### **Cenários de Teste**

- **Criação de Formações:** Criamos várias formações com diferentes nomes, níveis e conteúdos.
- **Matrícula de Usuários:** Matriculamos vários usuários em diferentes formações.
- **Verificação de Inscritos:** Verificamos se os usuários estão corretamente inscritos nas formações.

### **Evolução das Classes**

- **Classe `Usuario`:** Adicionamos uma propriedade `nome` para identificar os usuários.
- **Classe `ConteudoEducacional`:** Adicionamos um construtor secundário para permitir a criação de conteúdos sem duração especificada.
- **Classe `Formacao`:** Adicionamos uma propriedade `nivel` para representar o nível de dificuldade da formação.

Kotlin

```kotlin
enum class Nivel { BASICO, INTERMEDIARIO, DIFICIL }

data class Usuario(val nome: String)

data class ConteudoEducacional(var nome: String, val duracao: Int = 60)

data class Formacao(val nome: String, var conteudos: List<ConteudoEducacional>, val nivel: Nivel) {

    val inscritos = mutableListOf<Usuario>()
    
    fun matricular(usuario: Usuario) {
        inscritos.add(usuario)
        println("${usuario.nome} matriculado na formação ${this.nome}")
    }
}

fun main() {
    // Criação de Formações
    val formacao1 = Formacao("Formação Kotlin", listOf(ConteudoEducacional("Introdução ao Kotlin"), ConteudoEducacional("Kotlin Avançado")), Nivel.BASICO)
    val formacao2 = Formacao("Formação Java", listOf(ConteudoEducacional("Introdução ao Java"), ConteudoEducacional("Java Avançado")), Nivel.INTERMEDIARIO)

    // Criação de Usuários
    val usuario1 = Usuario("william")
    val usuario2 = Usuario("Eliana")

    // Matrícula de Usuários
    formacao1.matricular(usuario1)
    formacao2.matricular(usuario2)

    // Verificação de Inscritos
    println("Inscritos na formação ${formacao1.nome}: ${formacao1.inscritos.map { it.nome }}")
    println("Inscritos na formação ${formacao2.nome}: ${formacao2.inscritos.map { it.nome }}")
}
```



## **Conclusão**

Neste projeto aprimorado, evoluímos nosso sistema para abstrair formações da DIO usando orientação a objetos com Kotlin. Adicionamos novas funcionalidades e cenários de teste para garantir a robustez e usabilidade do sistema.

## **Aplicabilidade Prática**

Este sistema pode ser aplicado em vários cenários do mundo real, como:

- Gerenciamento de inscrições de alunos em formações.
- Geração de certificados de conclusão de formações.
- Análise de dados de desempenho de formações.
- Recomendação de formações personalizadas para usuários.

## Outra Opção:  Sistema de Compras no Super Mercado



Neste projeto, desenvolveremos um sistema de compras para comércio usando Kotlin. O sistema permitirá que usuários naveguem por produtos, adicionem itens ao carrinho e concluam a compra.

### **Classes**

- **Produto:** Representa um produto à venda, com propriedades como nome, preço e quantidade em estoque.
- **Carrinho:** Representa o carrinho de compras do usuário, contendo uma lista de produtos e a quantidade de cada produto.
- **Compra:** Representa uma compra concluída, contendo os produtos comprados, o valor total e o endereço de entrega.

### **Funções**

- **Adicionar ao Carrinho:** Adiciona um produto ao carrinho do usuário.
- **Remover do Carrinho:** Remove um produto do carrinho do usuário.
- **Atualizar Quantidade:** Atualiza a quantidade de um produto no carrinho do usuário.
- **Concluir Compra:** Conclui a compra, gerando uma nova instância de `Compra` e esvaziando o carrinho.

### **Cenários de Uso**

- **Navegação de Produtos:** Os usuários podem navegar pelos produtos disponíveis e visualizar seus detalhes.
- **Adição ao Carrinho:** Os usuários podem adicionar produtos ao carrinho para compra posterior.
- **Gerenciamento do Carrinho:** Os usuários podem gerenciar o conteúdo do carrinho, adicionando, removendo ou atualizando itens.
- **Conclusão da Compra:** Os usuários podem concluir a compra, fornecendo seus dados de entrega e finalizando o pagamento.

##### **Exemplo de Código**

kotlin

```kotlin
class Produto(val nome: String, val preco: Double, var quantidade: Int)

class Carrinho {
    val produtos = mutableListOf<Produto>()

    fun adicionar(produto: Produto, quantidade: Int) {
        val produtoExistente = produtos.find { it.nome == produto.nome }
        if (produtoExistente != null) {
            produtoExistente.quantidade += quantidade
        } else {
            produtos.add(produto.copy(quantidade = quantidade))
        }
    }

    fun remover(produto: Produto) {
        produtos.remove(produto)
    }

    fun atualizarQuantidade(produto: Produto, novaQuantidade: Int) {
        val produtoExistente = produtos.find { it.nome == produto.nome }
        if (produtoExistente != null) {
            produtoExistente.quantidade = novaQuantidade
        }
    }

    fun concluirCompra(): Compra {
        val valorTotal = produtos.sumOf { it.preco * it.quantidade }
        val compra = Compra(produtos, valorTotal)
        produtos.clear()
        return compra
    }
}

class Compra(val produtos: List<Produto>, val valorTotal: Double)
```

### **Conclusão**

Este sistema de compras para comércio fornece uma base para desenvolver um aplicativo de e-commerce completo. Ele permite que os usuários gerenciem seus carrinhos de compras e concluam compras com facilidade.

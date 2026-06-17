📄 Documentação do Sistema FinTrack

1. 📋 Visão Geral
FinTrack é um sistema de controle financeiro pessoal desenvolvido em Java, executado via terminal. Permite ao usuário registrar, listar, calcular saldo e remover transações financeiras de forma simples e interativa.

2. 🏗️ Arquitetura do Projeto
O projeto segue o padrão MVC (Model-View-Controller):

FinTrack/
│
├── src/
│   ├── app/
│   │   └── Main.java              → Ponto de entrada do sistema
│   │
│   ├── controller/
│   │   └── FinTrack.java          → Regras de negócio
│   │
│   └── model/
│       └── Transacao.java         → Estrutura de dados
│
└── dist/
    └── FinTrack.jar               → Executável gerado
[[MVC architecture diagram Java]]

3. 📦 Classes e Responsabilidades
3.1 model/Transacao.java
Representa uma transação financeira no sistema.

Atributos:

Atributo	Tipo	Descrição
descricao	String	Descrição da transação
valor	double	Valor monetário da transação
tipo	String	Tipo: "receita" ou "despesa"

Exportar

Copiar
Métodos:

Método	Retorno	Descrição
Transacao(String, double, String)	—	Construtor da classe
getDescricao()	String	Retorna a descrição
setDescricao(String)	void	Define a descrição
getValor()	double	Retorna o valor
setValor(double)	void	Define o valor
getTipo()	String	Retorna o tipo
setTipo(String)	void	Define o tipo
toString()	String	Representação textual da transação

Exportar

Copiar
Exemplo de uso:

java
Copiar

Transacao t = new Transacao("Salário", 3000.0, "receita");
System.out.println(t);
// Saída: Tipo: receita Descricao: Salário Valor: R$ 3000.0
3.2 controller/FinTrack.java
Contém todas as regras de negócio e operações sobre as transações.

Atributos:

Atributo	Tipo	Descrição
transacoes	ArrayList<Transacao>	Lista de transações cadastradas

Exportar

Copiar
Métodos:

Método	Retorno	Descrição
FinTrack()	—	Construtor, inicializa a lista
adicionarTransacao(Transacao)	void	Adiciona uma transação à lista
listarTransacoes()	void	Exibe todas as transações
calcularSaldoTotal()	double	Calcula e retorna o saldo total
removerTransacao(int)	void	Remove uma transação pelo índice

Exportar

Copiar
Exemplo de uso:

java
Copiar

FinTrack finTracker = new FinTrack();

// Adicionando transações
finTracker.adicionarTransacao(new Transacao("Salário", 3000.0, "receita"));
finTracker.adicionarTransacao(new Transacao("Aluguel", 800.0, "despesa"));

// Calculando saldo
double saldo = finTracker.calcularSaldoTotal();
// saldo = 2200.0

// Listando
finTracker.listarTransacoes();

// Removendo pelo índice
finTracker.removerTransacao(0);
3.3 app/Main.java
Ponto de entrada do sistema. Gerencia a interface com o usuário via terminal.

Responsabilidades:

Exibir o menu principal
Capturar entradas do usuário via Scanner
Direcionar as ações para o FinTrack
Tratar exceções de entrada inválida
Fluxo do menu:

┌─────────────────────────┐
│       FINTRACKER        │
├─────────────────────────┤
│ 1. Adicionar transação  │
│ 2. Listar transações    │
│ 3. Mostrar saldo        │
│ 4. Remover transação    │
│ 5. Sair                 │
└─────────────────────────┘
4. 🔄 Fluxo de Funcionamento
Início
  │
  ▼
Exibe Menu
  │
  ▼
Usuário escolhe opção
  │
  ├──► 1. Adicionar ──► Solicita dados ──► Cria Transacao ──► adicionarTransacao()
  │
  ├──► 2. Listar ──────► listarTransacoes()
  │
  ├──► 3. Saldo ───────► calcularSaldoTotal() ──► Exibe resultado
  │
  ├──► 4. Remover ─────► Solicita índice ──► removerTransacao(indice)
  │
  ├──► 5. Sair ────────► Encerra o programa
  │
  └──► Opção inválida ──► Exibe mensagem de erro ──► Volta ao menu

5. ⚙️ Requisitos do Sistema
Item	Versão
Java	21 ou superior
IDE recomendada	Apache NetBeans
Build Tool	Ant (integrado ao NetBeans)



6. ▶️ Como Executar
Pela IDE (NetBeans):
1. Abra o projeto no NetBeans
2. Pressione F6 ou clique em Run Project
Pelo terminal:
bash
   

java -jar "caminho/para/FinTrack.jar"
Clean and Build:
Shift + F11
7. 🛡️ Tratamento de Erros
Situação	Tratamento
Entrada não numérica no menu	try/catch captura e solicita nova entrada
Índice inválido na remoção	Verificação com if antes de remover
Lista vazia ao listar	Mensagem informativa ao usuário




8. 🚀 Melhorias Futuras Sugeridas
📅 Adicionar data às transações
💾 Persistência de dados em arquivo .txt ou banco de dados
📊 Filtrar transações por tipo (receita/despesa)
🔍 Buscar transação por descrição
📈 Relatório mensal de gastos
🔐 Autenticação de usuário
9. 👨‍💻 Informações do Projeto
Campo	Info
Nome	FinTrack
Linguagem	Java 21
Padrão	MVC
Interface	Terminal (CLI)
IDE	Apache NetBeans

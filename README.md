# Atividade Proxy --- Padrão de Projeto

Implementação do padrão de projeto **Proxy** em Java, aplicado ao contexto de operações bancárias (saque em conta corrente).

## Sobre o Padrão Proxy

O Proxy atua como um intermediário entre o cliente e o objeto real, controlando o acesso a ele. Neste projeto, o ContaProxy intercepta as chamadas de saque antes de delegá-las à ContaCorrente, adicionando:

- **Controle de acesso** bloqueia operações de usuários não autenticados
- **Limite diário** impede saques que ultrapassem o limite configurado
- **Lazy Initialization** a ContaCorrente real só é criada quando necessário
- **Log** registra o horário e os detalhes de cada saque

## Estrutura

Conta.java          # Interface com o método sacar()
ContaCorrente.java  # Objeto real que executa o saque
ContaProxy.java     # Proxy que controla o acesso à ContaCorrente
Main.java           # Demonstração com usuário autenticado e não autenticado

## Como executar

bash
javac *.java
java Main

## Exemplo de saída

=== USUÁRIO NÃO AUTENTICADO ===
Acesso NEGADO. Usuário não autenticado.

=== USUÁRIO AUTENTICADO ===
ContaCorrente criada.
[10:30:00] Saque solicitado: R$ 300.0
Sacando R$ 300.0
Quantidade de saques hoje: 1
Total sacado hoje: R$ 300.0

[10:30:00] Saque solicitado: R$ 500.0
Sacando R$ 500.0
Quantidade de saques hoje: 2
Total sacado hoje: R$ 800.0

Limite diário excedido.

## Tecnologias

- Java (sem dependências externas)

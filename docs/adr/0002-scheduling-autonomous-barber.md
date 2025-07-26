# ADR 2: Agendamento com Barbeiro Autônomo

## Contexto
O aplicativo também deve permitir que clientes agendem diretamente com barbeiros autônomos, sem vínculo com uma barbearia específica. O fluxo de dados seguirá do frontend para o backend com persistência no Supabase.

## Decisão
Criaremos um fluxo de agendamento exclusivo para barbeiros autônomos, onde cada barbeiro gerencia seus próprios horários no sistema.

## Fluxo do Frontend ao Backend
1. **Seleção de Barbeiro Autônomo**: o usuário escolhe o barbeiro disponível na plataforma.
2. **Escolha de Horário**: o frontend consulta no backend os horários desse barbeiro.
3. **Solicitação de Agendamento**: o frontend envia a requisição com dados do cliente e horário escolhido.
4. **Persistência no Supabase**: o backend registra o agendamento na tabela `agendamentos_autonomos` ou usa um campo para diferenciar o tipo de barbeiro.
5. **Confirmação ao Cliente**: o backend retorna a confirmação para o frontend.

## Fallback para Instabilidade de Internet
Se a conexão falhar após o usuário escolher o horário, a aplicação salvará temporariamente as informações no cache local. Assim que a internet voltar, será enviado automaticamente o pedido de agendamento ao backend, evitando perda de dados.

## Consequências
- Possibilita agendar diretamente com barbeiros autônomos.
- A estratégia de cache local reduz falhas de agendamento causadas por instabilidades de rede.

## Diagrama de Sequência
O diagrama de sequência está disponível em [../diagramas/0002-scheduling-autonomous-barber.puml](../diagramas/0002-scheduling-autonomous-barber.puml).

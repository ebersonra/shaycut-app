# ADR 1: Agendamento para Barbearia

## Contexto
O aplicativo precisa permitir que clientes agendem horários em uma barbearia com múltiplos barbeiros. O fluxo de dados deve passar do aplicativo (frontend) para o backend e ser persistido no Supabase.

## Decisão
Implementaremos um fluxo de agendamento específico para estabelecimentos (barbearias) que contém múltiplos barbeiros.

## Fluxo do Frontend ao Backend
1. **Seleção de Barbearia**: o usuário escolhe a barbearia desejada.
2. **Escolha de Barbeiro e Horário**: o frontend consulta a lista de barbeiros e horários disponíveis via API do backend.
3. **Solicitação de Agendamento**: o frontend envia uma requisição ao backend com os dados do agendamento (barbearia, barbeiro, horário e dados do cliente).
4. **Persistência no Supabase**: o backend grava o agendamento na tabela `agendamentos` do banco Supabase.
5. **Confirmação ao Cliente**: o backend retorna uma confirmação de agendamento para o frontend.

## Fallback para Instabilidade de Internet
Caso o dispositivo do usuário perca a conexão após a seleção de horário, o frontend armazena a requisição em cache local (por exemplo, `localStorage`). Assim que a internet estiver estável, o app reenviará a requisição ao backend automaticamente, garantindo que o agendamento seja processado.

## Consequências
- Simplifica o agendamento em uma barbearia com vários barbeiros.
- O uso de cache local minimiza perda de dados em conexões instáveis.

## Diagrama de Sequência

O diagrama de sequência está disponível em [../diagramas/0001-scheduling-barbershop.puml](../diagramas/0001-scheduling-barbershop.puml).
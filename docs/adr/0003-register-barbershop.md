# ADR 3: Cadastro de Barbearia pelo Proprietário

## Contexto
Para que clientes possam encontrar e agendar serviços em uma barbearia, é necessário que o próprio dono cadastre seu estabelecimento no aplicativo. O cadastro deve permitir informar detalhes básicos e disponibilizar a barbearia para consultas.

## Decisão
Será implementada uma funcionalidade de cadastro de barbearia onde o proprietário envia dados e midia para o backend, que os armazena no Supabase. A barbearia ficará visível para clientes após a conclusão desse registro.

## Fluxo do Frontend ao Backend
1. **Preenchimento de Formulário**: o dono da barbearia insere nome, endereço, horários de atendimento, lista de barbeiros, serviços oferecidos e faz upload de imagem ou logo.
2. **Envio para o Backend**: o frontend envia esses dados via API REST ou GraphQL para o backend.
3. **Upload de Imagem/Logo**: o backend envia a imagem para o storage do Supabase e recebe a URL resultante.
4. **Gravação no Supabase**: todos os dados, inclusive a URL da imagem, são armazenados em uma tabela `barbearias` no Supabase.
5. **Confirmação ao Proprietário**: o backend retorna uma confirmação de cadastro e a barbearia passa a estar disponível para busca pelos clientes.

## Fallback para Instabilidade de Internet
Se a conexão falhar durante o envio do cadastro, o frontend armazena temporariamente as informações em cache local até que a internet esteja estável. Assim que possível, os dados são reenviados ao backend para completar o registro sem perda de informações.

## Consequências
- Permite que barbearias cadastrem seus serviços e barbeiros de forma estruturada.
- O fallback com cache local evita perder dados de cadastro quando a conexão oscila.

## Diagrama de Sequência

O diagrama de sequência está disponível em [../diagramas/0003-register-barbershop.puml](../diagramas/0003-register-barbershop.puml).
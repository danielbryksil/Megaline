# Megaline

## Descrição do Projeto:

A empresa de telecomunicações Megaline oferece aos seus cliente planos pré-pagos, Surf e Ultimate. O departamento comercial quer saber quais dos planos dão mais receita para ajustar o orçamento de publicidade.
Realizei uma primeira análise dos planos baseados em uma pequena seleção de clientes. Com dados de 500 clientes da Megaline: que clientes são, de onde eles são, qual plano usam, o número de chamadas que eles fizeram e mensagens que eles enviaram em 2018. Em posse desses dados, analisei o comportamento dos clientes para determinar quais planos pré-pagos geram mais receita.

## Descrição dos planos:
A Megaline arredonda segundos para minutos, e megabytes para gigabytes. Para chamadas, cada chamada individual é arredondada para cima: mesmo se uma chamada tenha durado apenas um segundo, será contado como um minuto. Para trafego de web, sessões individuais de web não são arredondadas para cima. Ao invés disso, o total do mês é arredondado para cima. Se alguém usar 1025 megabytes esse mês, eles serão cobrados por 2 gigabytes.

### Surf
1. Preço mensal: $20
2. 500 minutos mensais, 50 mensagens de texto, e 15 GB de dados
3. Depois de exceder os limites do pacote:
  * 1 minuto: 3 centavos
  * 1 mensagem de texto: 3 centavos
  * 1 GB de dados: $10

### Ultimate
1. Preço mensal: $70
2. 3000 minutos mensais, 1000 mensagens de texto, e 30 GB de dados
3. Depois de exceder os limites do pacote:
   * 1 minuto: 1 centavo
   * 1 mensagem de texto: 1 centavo
   * 1 GB de dados: $7

## Pontos analisados no projeto:
- Preparar os dados: converta os dados para os tipos necessários, encontre e elimine erros nos dados
- Para cada usuário, encontrar:
  1. O número de chamadas feitas e minutos usados por mês.
  2. O número de mensagens de texto enviadas por mês.
  3. O volume de dados por mês.
  4. A receita mensal para cada usuário (subtraia o limite do pacote grátis do número total de chamadas, mensagens de texto, e dados; multiplique o resultado pelos valores do plano; adicione o preço mensal dependendo do plano de chamada).

- Descrever o comportamento dos clientes. Encontre os minutos, mensagens de texto e volume de dados que usuários de cada plano necessitam por mês. Calcular a média, variância e o desvio padrão. Construir histogramas. Descrever as distribuições.

### Testar as hipóteses:
1. A receita média dos usuários dos planos Ultimate e Surf são diferentes.
2. A receita média dos usuários da área de NY-NJ é diferente dos usuários de outras regiões.

## Descrição dos dados
A tabela users (dados sobre usuários):
- user_id — identificação do usuário
- first_name — nome do usuário
- last_name — último sobrenome do usuário
- age — idade do usuário (em anos)
- reg_date — data da inscrição (dd, mm, aa)
- churn_date — a data que o usuário parou de usar o serviço (se o valor for ausente, o plano estava sendo usado quando esse dado foi gerado)
- city — cidade de residência do usuário
- plan — nome do plano

A tabela calls (dados sobre as chamadas):
- id — identificador de chamada unívoco
- call_date — data da chamada
- duration — duração da chamada (em minutos)
- user_id — o identificador do usuário que faz a chamada

A tabela messages (dados nas mensagens de texto):
- id — identificador unívoco de mensagem de textos
- message_date — data da mensagem de texto
- user_id — o identificador do usuário que envia a mensagem de texto

A tabela internet (dados sobre sessões web):
- id — identificador de sessão unívoco
- mb_used — o volume de dados gasto durante a sessão ( em megabytes)
- session_date — data da sessão web
- user_id — identificador do usuário

A tabela plans(dados sobre os planos):
- plan_name — o nome do plano de chamadas
- usd_monthly_fee — preço mensal em dólares dos EUA
- minutes_included — pacote de minutos mensal
- messages_included — pacote de mensagens de texto mensal
- mb_per_month_included — pacote de volume de dados (em megabytes)
- usd_per_minute — preço por minuto depois de exceder o limite do pacote (por exemplo, se o pacote inclui 100 minutos, o primeiro minuto excedente será cobrado)
- usd_per_message — preço por mensagem de texto depois de exceder o limite do pacote
- usd_per_gb — preço por gigabyte extra de dados após exceder o limite do pacote (1 GB = 1024 megabytes)

# PLATAFORMA DE HOSPEDAGEM
<img width="1400" height="425" alt="image" src="https://github.com/user-attachments/assets/e521aa22-76f4-45d6-ad5e-4752e112d655" />
🏨 Práticas de SQL — Banco de Dados de hospedagem de hotel

Repositório criado para guardar os scripts de SQL que desenvolvi durante as aulas de Banco de Dados no curso técnico de Desenvolvimento de Sistemas. 

A ideia aqui foi usar a base de dados de uma plataforma de hospedagens (com tabelas de endereços, proprietários, hospedagens e aluguéis) para ir praticando na massa, começando pelas consultas mais simples até chegar em relatórios mais completos e alterações na estrutura do banco.

## 📝 O que foi feito nas aulas

### 1. Começando pelo básico: Filtros e Ordenação
Nas primeiras práticas, o foco foi aprender a buscar exatamente o que a gente precisava na tabela de `enderecos`:
* Puxar colunas específicas (como só `cidade` e `estado`) em vez de trazer a tabela inteira.
* Usar o `WHERE` para filtrar por estado (`AL`, `PB`), bairro (`centro`) ou numeração específica (`numero = 100`, `>= 150`, `< 100`), juntando condições com `AND`.
* Organizar os resultados do maior para o menor (`DESC`) ou vice-versa (`ASC`) e usar o `LIMIT` para não poluir a tela com um monte de linhas.

### 2. Fazendo contas com os dados (Agregação e Datas)
Depois que peguei o jeito dos filtros, começamos a extrair informações mais úteis da tabela de `alugueis`:
* **Ticket médio:** Usei `AVG` junto com `GROUP BY` para descobrir quanto cada cliente gasta em média.
* **Tempo de estadia:** Calculei a média de dias que o pessoal costuma ficar hospedado usando `DATEDIFF(data_fim, data_inicio)`.
* **Meses mais movimentados:** Quebrei as datas usando `YEAR` e `MONTH` junto com `COUNT(*)` para ver em quais meses a plataforma teve mais e menos aluguéis.

### 3. Cruzando tabelas com JOIN
Como os dados ficam espalhados, pratiquei bastante o uso de `INNER JOIN` para juntar as informações:
* Cruzei `hospedagens` com `enderecos` para checar quais imóveis estavam ativos ou inativos.
* Juntei `proprietarios` e `hospedagens` para montar um Top 10 de quem tinha mais hospedagens ativas (`ativo = 1`) e também quem tinha mais inativas (`ativo = 0`).

### 4. Alterando a estrutura do banco (DDL)
Na última parte, simulamos uma demanda real onde a plataforma pediu mudanças na estrutura que já estava pronta. Para isso, usei o `ALTER TABLE` para:
* Adicionar a coluna `QNT_HOSPEDAGEM` na tabela de `proprietarios`, já que ainda não tínhamos esse controle.
* Renomear a tabela `alugueis` para `RESERVAS` e a coluna `ALUGUEL_ID` para `RESERVA_ID`, porque fazia muito mais sentido para a regra de negócio do sistema.

## 🛠️ Ferramentas usadas
* **SQL** (MySQL)
* **MySQL Workbench** (Aplicativo)

# Desafio de Projeto - Processando e Transformando Dados com Power BI

Neste projeto, realizamos uma série de operações de manipulação e visualização de dados no Power BI. A seguir, detalharei cada etapa do processo, fornecendo explicações e capturas de tela quando relevante.

## Passo 1: Verifique os cabeçalhos e tipos de dados

### 1.1. Após conectar a fonte de dados, examinamos as tabelas para verificar os nomes das colunas e os tipos de dados atribuídos.

![Passo 1.1]
![image](https://github.com/hudsonfarias/projetoPowerBI/assets/138171591/a957741a-39ad-4ee6-8bd0-b2eee05102d1)

## Passo 2: Modifique os valores monetários para o tipo double preciso

### 2.1. Identificamos as colunas que continham valores monetários, como "Salary", e modificamos o tipo de dados para "Número Decimal" para maior precisão.

![Passo 2.1]
![image](https://github.com/hudsonfarias/projetoPowerBI/assets/138171591/8ca5f395-9d82-4821-b089-eec2db483df5)

## Passo 3: Verifique a existência dos nulos e analise a remoção

### 3.1. Verificamos as colunas em busca de valores nulos e determinamos a abordagem apropriada para tratá-los, como a remoção ou substituição por valores padrão.

## Passo 4: Os employees com nulos em Super_ssn podem ser os gerentes. Verifique se há algum colaborador sem gerente

### 4.1. Analisamos a coluna "Ssn" para identificar funcionários que não têm um gerente (valores nulos).
![image](https://github.com/hudsonfarias/projetoPowerBI/assets/138171591/5982b3e2-b362-4b9b-9c24-d7c416bdbd38)
## Passo 5: Verifique se há algum departamento sem gerente.
![image](https://github.com/hudsonfarias/projetoPowerBI/assets/138171591/6cf492e3-37d3-4616-8acf-dc9ad1e7b420)
### 5.1. Analisamos a tabela de departamentos e verificamos se havia departamentos sem gerentes designados.

## Passo 6: Se houver departamento sem gerente, suponha que você possui os dados e preencha as lacunas

### 6.1. Caso tenha identificado departamentos sem gerentes, supomos que possuímos os dados necessários e atribuímos um gerente a esses departamentos.

## Passo 7: Verifique o número de horas dos projetos
![image](https://github.com/hudsonfarias/projetoPowerBI/assets/138171591/78ce0415-4694-4d39-acbf-b04177e80c10)
### 7.1. Analisamos a tabela "works_on" para verificar o número de horas atribuídas a cada projeto e funcionário.

## Passo 8: Separar colunas complexas

### 8.1. Identificamos colunas complexas que poderiam ser separadas em colunas distintas para facilitar a análise.

## Passo 9: Mesclar consultas employee e departament para criar uma tabela employee com o nome dos departamentos associados aos colaboradores
![image](https://github.com/hudsonfarias/projetoPowerBI/assets/138171591/03d91708-c284-43d6-8a74-941e3b98f8f5)
### 9.1. No Power Query Editor, realizamos a junção das tabelas "employee" e "department" com base na tabela "employee" para criar uma nova tabela "employee" com o nome dos departamentos associados aos funcionários.

## Passo 10: Neste processo elimine as colunas desnecessárias

### 10.1. No Power Query Editor, removemos colunas desnecessárias das tabelas para simplificar a estrutura de dados.

## Passo 11: Realize a junção dos colaboradores e respectivos nomes dos gerentes

### 11.1. Executamos uma consulta SQL para unir as tabelas "employee" e "department" e adicionamos os nomes dos gerentes aos funcionários.

```sql
-- Exemplo de consulta SQL
SELECT E.*, D.Mgr_ssn AS Mgr_ssn, E2.Fname AS Mgr_Fname, E2.Lname AS Mgr_Lname
FROM employee E
LEFT JOIN department D ON E.Ssn = D.Mgr_ssn
LEFT JOIN employee E2 ON D.Mgr_ssn = E2.Ssn
```
## Passo 12: Mescle as colunas de Nome e Sobrenome

### 12.1. No Power Query Editor, combinamos as colunas "Nome" e "Sobrenome" em uma única coluna chamada "Nome Completo".

## Passo 13: Mescle os nomes de departamentos e localização

### 13.1. Combinamos as colunas "Dname" (nome do departamento) e "Dlocation" (localização) para criar uma única coluna única, que ajudaria na criação de um modelo estrela em um módulo futuro.

## Passo 14: Explicação por que, neste caso supracitado, podemos apenas utilizar o mesclar e não o atribuir

### 14.1. Optamos por mesclar as colunas, pois isso cria um relacionamento mais dinâmico entre as tabelas e permite que as alterações sejam refletidas automaticamente.

## Passo 15: Agrupe os dados a fim de saber quantos colaboradores existem por gerente

### 15.1. Criamos um resumo que agrupava os dados por gerente e contava o número de colaboradores para cada gerente.

## Passo 16: Elimine as colunas desnecessárias

### 16.1. No Power Query Editor, eliminamos as colunas que não serão usadas nos relatórios finais.


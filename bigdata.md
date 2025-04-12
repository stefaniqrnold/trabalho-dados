---
# configurações do marp
marp: true
theme: gradient
class:  
- blue # classe azul do tema
- lead # centralizar

style: |
    img[alt~="center"] {
      display: block;
      margin: 0 auto;
    }

paginate: true 

# canto dos slides
header: 'Aplicação de Técnicas de Big Data'
---

# **Solução de apoio à gestão de saúde pública - Comparação do número de farmacêuticos em Ijuí e Santa Rosa**
## - Engenharia de Software e Ciência da Computação
## - Big Data, Analytics e Métricas
### **Stéfani Arnold e Henrique Fritz**
### `Módulo 01/2025`

---

<!-- Slide 2 -->
## Introdução
- Estudo de caso baseado no DATASUS  
- Proposta: Criar uma solução de apoio à decisão para a gestão da saúde pública  
- Enfoque: Comparar dados de farmacêuticos em Ijuí e Santa Rosa  

---

<!-- Slide 3 -->
## Problema
- Como otimizar a distribuição e gestão de farmacêuticos em cidades diferentes?  
- Quais dados podem embasar decisões públicas mais eficazes?  

---

<!-- Slide 4 -->
## Justificativa
- Necessidade de análise eficiente de dados públicos de saúde  
- Potencial de "Business Intelligence" no suporte à gestão pública  
- Impacto direto na alocação de recursos e melhoria do atendimento  

---

<!-- Slide 5 -->
## Objetivos

### Geral:
Desenvolver uma solução analítica baseada em OLAP para apoiar decisões na área da saúde pública.

### Específicos:
- Construir modelo dimensional (esquema estrela)  
- Desenvolver um cubo de dados com drill down/roll up  
- Realizar comparações entre Ijuí e Santa Rosa  

---

<!-- Slide 6 -->
## Metodologia
- Estudo do modelo OLTP do DATASUS (SIASUS)  
- Definição da tabela fato e dimensões  
- Implementação em banco analítico (DWSIA)  
- Criação de cubo de dados e análise com ferramentas OLAP (Excel, SSAS)  

---

<!-- Slide 7 -->
## Modelo Dimensional
- **Fato**: Produção ambulatorial por profissional  
- **Dimensões**:
  - Tempo  
  - Município  
  - Profissional  
  - Unidade de Saúde  
  - Procedimento  
- **Medidas**: Nº de atendimentos, quantidade de profissionais  

---

<!-- Slide 8 -->
## Granularidade
- Nível de detalhamento:  
  - Município → Unidade → Profissional  
  - Data (Ano/Mês/Dia)  
  - Tipo de procedimento  

---

<!-- Slide 9 -->
## Operações OLAP
- **Drill Down**: Ijuí → Unidade de Saúde → Profissional  
- **Roll Up**: Profissional → Unidade → Município  
- **Slice/Dice**: Comparação entre municípios em determinado mês  

---

<!-- Slide 10 -->
## Cubo de Dados
- Cubo multidimensional com:  
  - Eixos: Tempo, Município, Profissional  
  - Métricas: Quantidade de atendimentos, número de farmacêuticos  

---

<!-- Slide 11 -->
## Exemplos de Análise
- Uso do Excel como ferramenta OLAP  
- Relatórios:
  - Evolução mensal de atendimentos  
  - Comparativo de farmacêuticos por município  

---

<!-- Slide 12 -->
## Implementação Técnica - ETL
- Criação dos bancos: `DBSIA` (operacional) e `DWSIA` (analítico)  
- Extração de dados do SIASUS para arquivos `.txt`  
- Transformação: Filtragem, normalização e agregação dos dados  
- Carga no Data Warehouse com comandos `BULK INSERT`  
- Execução de scripts no prompt da ISO personalizada (Windows 7 modificado)

---

![center](/fotos/p1-abrindo-cmd-personalizada.png)

---

![center](/fotos/p2-criando%20os%20dbs.png)

---

![center](/fotos/p3-criando-tabelas%20e%20caregando-arquivos-para-db-operacional.png)

---

![center](/fotos/p4-selecionando%20e%20exportando%20dados%20do%20dbsia.png)

---

![center](/fotos/p15-5-todas%20as%20dimenções%20do%20cubo%20de%20dados.png)

---

![center](/fotos/p6-importando%20dados%20do%20dbdia%20para%20o%20dwsia.png)

---

![center](/fotos/p7-criando%20projeto%20para%20cubo-dados.png)

---

![center](/fotos/p8-criando%20conexão%20dwsia.png)

---

![center](/fotos/p9-criando%20views%20das%20tabélas.png)

---

![center](/fotos/p10-view%20e%20chaves%20primarias-estrangeiras.png)

---

![center](/fotos/p11-criando%20cubo%20de%20dados1-comfig-padrão.png)

---

![center](/fotos/p12-2-dados%20para%20cubo%20de%20dados%20vem%20do%20dwsia.png)

---

![center](/fotos/p13-3-definindo%20o%20que%20é%20fato%20e%20dimenção%20do%20cubo-dados.png)

---

![center](/fotos/p15-5-todas%20as%20dimenções%20do%20cubo%20de%20dados.png)

---

![center](/fotos/p16-6-finalização-cubo%20de%20dados.png)

---

![center](/fotos/p17-imagem%20cubo-dados-dwsia.png)

---

![center](/fotos/p18-dando%20permisão%20para%20ignorar%20erros%20de%20dados.png)

---

![center](/fotos/p19-ignorando%20erros%20de%20inconcistencia%20de%20dados.png)

---

![center](/fotos/p20-1-proceso%20de%20deploy-implantação.png)

---

![center](/fotos/p20-2-proceso%20de%20deploy-implantação.png)

---

![center](/fotos/1.jpg)

---

![center](/fotos/2.jpg)

---

<!-- Slide 13 -->
## Estrutura do Banco Analítico
- Modelo Estrela aplicado no `DWSIA`  
  - **Fato**: `fato_producao`  
  - **Dimensões**:
    - `dim_tempo`, `dim_municipio`, `dim_profissional`, `dim_estabelecimento`, `dim_procedimento`, `dim_cbo`, `dim_cid`  
- Dados prontos para análise OLAP (Excel, Power BI, SSAS)  
- Criação de cubo com medidas agregadas e hierarquias de drill down

---

<!-- Slide 14 -->
## Resultados Esperados
- Sistema de apoio à decisão para gestão de farmacêuticos  
- Insights úteis para políticas públicas locais  
- Ferramentas visuais e interativas para análise  

---

<!-- Slide 15 -->
## Conclusão
- A análise comparativa possibilita decisões baseadas em dados  
- OLAP e BI agregam valor à gestão pública  
- O projeto contribui para a eficiência dos serviços de saúde  

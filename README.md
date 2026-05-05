---
# <center><font size='6'>**ANÁLISE GEOESPACIAL, SUBNOTIFICAÇÃO E BUSCADOR INTERATIVO DE SERVIÇOS DE ATENDIMENTO ÀS VÍTIMAS DE VIOLÊNCIA SEXUAL NO BRASIL**
---
## 👨‍💻 Autor

**Otávio Fabbro**
• *Bacharel em Ciências Sociais (FFLCH-USP) e Especialista em Ciência de Dados (ICMC-USP)*

Interessado na aplicação de dados para impacto social e políticas públicas. Sinta-se à vontade para entrar em contato para trocas de conhecimento ou oportunidades profissionais!

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/otaviofabbrodata)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](https://mail.google.com/mail/?view=cm&fs=1&to=otaviofabbro2@gmail.com)

---
*Este projeto é parte de um esforço contínuo para masterizar ferramentas de análise e engenharia de dados (Python, SQL, Power BI) aplicadas a contextos sociais complexos.*
---

## 📌 Contexto e Objetivo

No Brasil, o acesso a serviços especializados de atendimento a vítimas de violência sexual ainda é marcado por uma severa **desigualdade territorial** e por uma profunda fragmentação de informações institucionais. Este projeto nasce com dois objetivos concretos: **democratizar o acesso à rede de apoio** e **diagnosticar falhas estruturais nas políticas públicas de proteção**.

> ℹ️ **Sobre este projeto:**
>
> A primeira frente deste *notebook* consolida bases governamentais brutas em ferramentas de utilidade pública. Utilizando algoritmos geolocalizados, o sistema atua como um **"GPS de Acolhimento"**, calculando distâncias para conectar vítimas aos serviços mais próximos, transpondo as barreiras do "apagão" de infraestrutura em municípios do interior.
>
> Na segunda frente, realiza-se uma análise aprofundada da infraestrutura de acolhimento (Oferta) em contraste com os índices de violência (Demanda), evidenciando os gargalos geográficos através da análise de quadrantes.

Para além do mapeamento, o estudo mergulha em um dos fenômenos mais complexos da saúde pública: a **Cifra Oculta**. Ao cruzar registros de entrada em hospitais (SINAN), boletins de ocorrência em delegacias (Anuário de Segurança Pública) e estimativas científicas (IPEA/PNS), a análise cria **métricas derivadas de invisibilidade**, quantificando o exato tamanho do abismo institucional onde milhares de vítimas permanecem desamparadas.

---

## 🗂️ Estrutura da Análise

A jornada dos dados está desenhada em uma progressão lógica, dividida nas seguintes etapas:

| Etapa | Abordagem Analítica | Descrição |
| :---: | :--- | :--- |
| **1** | **Buscador Local** | Filtro dinâmico (*dropdowns*) por UF e município para localizar serviços dentro da própria cidade. |
| **2** | **GPS de Acolhimento** | Busca por proximidade usando a fórmula de *Haversine* para indicar a rota exata aos 2 estabelecimentos mais próximos de cada categoria de serviço. |
| **3** | **Mapeamento Geoespacial** | Mapa interativo (`folium`) de alta precisão com painel de controle lateral para filtragem visual de categorias em tempo real. |
| **4** | **Arquitetura da Rede** | Decomposição estadual da infraestrutura de atendimento (*Treemap* e *Stacked Bars*). |
| **5** | **Termômetro da Violência** | Ranking de incidência criminal através da taxa de estupro por 100 mil mulheres. |
| **6** | **Oferta vs. Demanda** | Análise de dispersão e quadrantes cruzando infraestrutura (*CNES*) com criminalidade (*Anuário*). |
| **7** | **Descompasso Institucional** | Análise de divergência absoluta entre órgãos de Saúde e Polícia (Lollipops da *Cifra Oculta*). |
| **8** | **A Ponta do Iceberg** | Contraste em escala logarítmica dos dados formais contra a estimativa real estruturada pelo IPEA. |
| **9** | **KPI de Invisibilidade** | Cálculo de subnotificação estadual evidenciando a distância entre a realidade e o Estado (*Dumbbell Plot*). |

---

## 📊 Fontes de Dados

Este projeto baseia-se no cruzamento de dados públicos e oficiais, garantindo a confiabilidade do diagnóstico metodológico:

**1. Infraestrutura de Atendimento (Saúde)**
* **Conjunto de Dados:** CNES - Serviços Especializados
* **Órgão Responsável:** Ministério da Saúde / DATASUS
* **Acesso:** ElastiCNES ([elasticnes.saude.gov.br](https://elasticnes.saude.gov.br/servicos-especializados))
* **Data de Extração:** 26 de abril de 2026

**2. Indicadores de Violência (Polícia)**
* **Documento:** 19º Anuário Brasileiro de Segurança Pública (2025)
* **Organização Responsável:** Fórum Brasileiro de Segurança Pública (FBSP)
* **Acesso:** Repositório Oficial ([publicacoes.forumseguranca.org.br](https://publicacoes.forumseguranca.org.br/items/c3605778-37b3-4ad6-8239-94e4cb236444))
* **Data de Extração:** 26 de abril de 2026

**3. Notificações de Violência (Saúde)**
* **Conjunto de Dados:** Sistema de Informação de Agravos de Notificação (SINAN) - Violência Interpessoal e Autoprovocada
* **Órgão Responsável:** Ministério da Saúde / DATASUS
* **Acesso:** TABNET DATASUS ([tabnet.datasus.gov.br](https://tabnet.datasus.gov.br/cgi/deftohtm.exe?sinannet/cnv/violebr.def))
* **Data de Extração:** 28 de abril de 2026

**4. Estimativa Real: Estupros (PNS) *vs* Notificações Oficiais**
* **Acesso**: [IBGE - Pesquisa Nacional de Saúde (PNS)](https://www.ibge.gov.br/estatisticas/sociais/saude/9160-pesquisa-nacional-de-saude.html?edicao=30563&t=downloads)
* **Acesso**: [IPEA - Elucidando a prevalência de estupro no Brasil a partir de diferentes bases de dados](https://repositorio.ipea.gov.br/server/api/core/bitstreams/483862e7-820f-44a5-8708-d499ba857ab5/content)
* **Data de Extração**: 01 de maio de 2026

---

## 🛠️ Stack Utilizada

![Python](https://img.shields.io/badge/Python-3670A0?style=flat-square&logo=python&logoColor=ffdd54)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-3F4F75?style=flat-square&logo=plotly&logoColor=white)
![Folium](https://img.shields.io/badge/Folium-77B829?style=flat-square&logo=python&logoColor=white)
![ipywidgets](https://img.shields.io/badge/ipywidgets-F37626?style=flat-square&logo=jupyter&logoColor=white)
![HTML/CSS](https://img.shields.io/badge/HTML5_&_CSS3-E34F26?style=flat-square&logo=html5&logoColor=white)

---
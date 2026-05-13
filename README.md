<div align="center">

# 🔍 Violência Sexual no Brasil: Geoanálise, Subnotificação e Buscador Interativo de Serviços de Acolhimento

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
  <img src="https://img.shields.io/badge/Folium-Geoespacial-77B829?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Plotly-Visualização-3F4F75?style=for-the-badge&logo=plotly&logoColor=white"/>
  <img src="https://img.shields.io/badge/ipywidgets-Interatividade-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Área-Políticas_Públicas-6A0DAD?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Tema-Saúde_Pública-2ECC71?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Dados-CNES_·_SINAN_·_FBSP_·_IPEA-E67E22?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Demandado_por-MPF_·_PFDC-003082?style=for-the-badge"/>
</p>

<br/>

<br/>

<div align="center">
  
  <a href="https://otaviofabbro.github.io/geoanalise-violencia-sexual-br/">
    <img width="500" src="https://img.shields.io/badge/▶_CLIQUE_AQUI_PARA_ACESSAR_A_APRESENTAÇÃO-003082?style=for-the-badge"/>
  </a>
  
  <p><i>👆 Clique no botão acima para abrir a versão final com os mapas, buscadores e gráficos dinâmicos no seu navegador.</i></p>
</div>

<br/>

<br/>

> *A esmagadora maioria das vítimas de violência sexual no Brasil sofre em silêncio absoluto, sem nunca pisar em um hospital ou delegacia. Planejar a rede de acolhimento baseando-se apenas em Boletins de Ocorrência é preparar o Estado para acolher apenas a ponta do iceberg.*

<br/>

</div>

---

## 📌 Sumário

- [Visão Geral](#-visão-geral)
- [Frentes de Análise](#-frentes-de-análise)
- [Ferramentas Interativas](#-ferramentas-interativas)
- [Análise da Infraestrutura de Atendimento](#-análise-da-infraestrutura-de-atendimento)
- [Análise da Violência: Oferta vs. Demanda](#-análise-da-violência-oferta-vs-demanda)
- [A Cifra Oculta e a Subnotificação](#-a-cifra-oculta-e-a-subnotificação)
- [Fontes de Dados](#-fontes-de-dados)
- [Stack Tecnológica](#-stack-tecnológica)
- [Como Executar](#-como-executar)
- [Limitações e Notas Metodológicas](#-limitações-e-notas-metodológicas)
- [Referências](#-referências)
- [Autor](#-autor)

---

## 🔭 Visão Geral

Este projeto foi desenvolvido a pedido da [**Comissão de Igualdade de Gênero da Procuradoria
Federal dos Direitos do Cidadão (MPF)**](https://www.mpf.mp.br/atuacao/pfdc/comissoes-e-rts/igualdade-de-genero)
e nasce de dois objetivos concretos e complementares: **democratizar o acesso à rede de apoio**
às vítimas de violência sexual no Brasil e **diagnosticar falhas estruturais nas políticas
públicas de proteção**.

O trabalho não é uma análise estática — é um conjunto de **ferramentas de utilidade pública
e diagnóstico territorial** construídas sobre dados governamentais abertos. Ao cruzar registros
de hospitais (SINAN), boletins de ocorrência (Anuário de Segurança Pública) e estimativas
científicas (IPEA/PNS), o projeto cria **métricas derivadas de invisibilidade** que quantificam
o tamanho do abismo institucional onde milhares de vítimas permanecem desamparadas.

---

## 📁 Estrutura do Repositório

```
geoanalise-violencia-sexual-br/
│
├── 🗃️ data/
│   ├── busca_estabelecimentos_servicos_especializados.csv   # CNES tratado: estabelecimentos com geolocalização e contatos padronizados
│   ├── estupro_e_estupro_de_vulneravel_vitimas_mulheres_2024.xlsx   # Anuário FBSP 2025: taxa de estupro por 100 mil mulheres por UF
│   └── sinan_vs_anuario_seguranca_publica-2024_vs_IPEA-2019.xlsx   # SINAN + Anuário + Estimativa IPEA consolidados por UF
│
├── 📓 notebooks/
│   └── violencia_sexual_e_estabelecimentos_servicos_especializados.ipynb   # Notebook principal
│
├── 📄 README.md
└── requirements.txt
```

> Os arquivos em `data/` foram obtidos nas fontes originais listadas na seção [Fontes de Dados](#-fontes-de-dados), passaram por um processo de limpeza e tratamento (padronização de endereços, consolidação de tabelas, normalização de colunas) e foram salvos no repositório em seu formato final para garantir reprodutibilidade sem dependência de acesso externo.

---

## 🗂️ Frentes de Análise

O notebook está organizado em uma progressão lógica de nove etapas:

| Etapa | Abordagem | Descrição |
|:---:|:---|:---|
| **1** | Buscador Local | Filtro dinâmico por UF e município para localizar serviços na própria cidade |
| **2** | GPS de Acolhimento | Busca por proximidade via Fórmula de Haversine — os 2 estabelecimentos mais próximos por categoria |
| **3** | Mapeamento Geoespacial | Mapa interativo Folium com painel lateral de filtragem por tipo de serviço |
| **4** | Arquitetura da Rede | Decomposição estadual da infraestrutura (Treemap e Stacked Bars) |
| **5** | Termômetro da Violência | Ranking de incidência criminal pela taxa de estupro por 100 mil mulheres |
| **6** | Oferta vs. Demanda | Análise de dispersão e quadrantes cruzando infraestrutura (CNES) com criminalidade (Anuário) |
| **7** | Descompasso Institucional | Divergência absoluta entre Saúde e Polícia — Lollipop da Cifra Oculta |
| **8** | A Ponta do Iceberg | Contraste em escala logarítmica entre dados formais e estimativa real (IPEA/PNS) |
| **9** | KPI de Invisibilidade | Taxa de subnotificação estadual — a distância entre a realidade e o Estado (Dumbbell Plot) |

---

## 🛠️ Ferramentas Interativas

### Buscador Local — Filtro por Estado e Município

Um widget funcional construído com `ipywidgets` que transforma uma base CSV complexa em uma interface amigável. O usuário seleciona a UF e o município e recebe imediatamente o nome, tipo de serviço, endereço e telefone das unidades disponíveis.

> O objetivo não é apenas gerar relatórios para gestores, mas criar soluções de utilidade pública — diminuindo a fricção entre a vítima e o atendimento especializado.

### GPS de Acolhimento — Busca por Proximidade (Haversine)

Vai além do filtro municipal: rastreia todo o território nacional e indica as unidades mais próximas da cidade informada, mesmo que estejam em municípios ou estados vizinhos. Para cada uma das quatro categorias de serviço (*Atenção Ambulatorial, Atenção Integral, Coleta de Vestígios* e *Interrupção de Gravidez nos Casos Previstos em Lei*), são exibidas as duas unidades mais próximas — com endereço, contatos e quilometragem exata.

```
distância = Haversine(lat_origem, lon_origem, lat_destino, lon_destino)
```

### Mapa Interativo — Raio-X Geoespacial da Rede

Mapa de alta precisão com `folium` onde cada ponto representa um estabelecimento cadastrado. O painel lateral exibe estatísticas gerais e permite filtrar as camadas por categoria de serviço em tempo real, revelando visualmente os vazios assistenciais no interior do Brasil.

---

## 🏗️ Análise da Infraestrutura de Atendimento

### Distribuição por tipo de serviço

Ranking dos tipos de atendimento disponíveis, com quantidade absoluta e participação percentual — permitindo diagnosticar se a rede pública oferece um ciclo de cuidado completo ou apenas respostas isoladas.

### Composição estadual (Stacked Bars e Treemap)

Os estados são ranqueados pelo tamanho da infraestrutura, mas o detalhe está na **composição interna**: uma barra longa e monocromática indica uma rede desequilibrada; barras diversificadas indicam um ecossistema completo de saúde, segurança e assistência social.

O Treemap hierárquico (Brasil → UF → Serviço) permite explorar a dominância de cada estado com um clique.

### Cobertura proporcional (Choropleth + Lollipop)

Para evitar a "miopia populacional", todos os indicadores são normalizados por 100 mil habitantes (dados do Censo IBGE 2022). Dois mapas coropléticos mostram a cobertura absoluta e o desvio em relação à média nacional — identificando rapidamente os "desertos de assistência".

### Heatmap de lacunas qualitativas

Matriz estado × tipo de serviço em taxa por 100 mil habitantes. Células vazias ou em tom claro sinalizam ausência de determinado serviço em uma UF — revelando lacunas qualitativas que o volume total esconde.

---

## ⚖️ Análise da Violência: Oferta vs. Demanda

### Termômetro da violência

Ranking estadual pela taxa de estupro por 100 mil mulheres (Anuário Brasileiro de Segurança Pública 2025), com gradação de cores por intensidade e linha de referência da média nacional.

### Análise de quadrantes — O ponto de encontro

Gráfico de dispersão cruzando infraestrutura de atendimento (eixo X) com taxa de violência (eixo Y), dividido pelas medianas em quatro zonas diagnósticas:

| Quadrante | Taxa de estupro | Taxa de estabelecimentos | Diagnóstico | Ação indicada |
|:---|:---:|:---:|:---|:---|
| **Superior esquerdo** | Alta | Baixa | Subatendimento crítico | Expansão urgente de serviços |
| **Superior direito** | Alta | Alta | Problema de efetividade | Auditoria e qualificação |
| **Inferior esquerdo** | Baixa | Baixa | Possível subnotificação | Campanhas de denúncia + expansão gradual |
| **Inferior direito** | Baixa | Alta | Melhor situação relativa | Manter como referência de modelo |

---

## 📉 A Cifra Oculta e a Subnotificação

### Hospitais vs. Delegacias

Comparação direta entre os registros do SINAN (Saúde) e do Anuário de Segurança Pública (Polícia) para 2024 — por perfil de vítima (mulheres e vulneráveis). A divergência entre essas duas fontes revela falhas de integração na rede de proteção: vítimas que acessam uma porta do Estado, mas não são conduzidas à próxima etapa.

### Discrepância proporcional (Lollipop + Scatter Log)

Além da divergência absoluta, o projeto calcula a **razão Anuário/SINAN** por estado em escala logarítmica — identificando *outliers* onde a fratura institucional é tão profunda que uma fonte registra cinco vezes mais casos que a outra.

### A ponta do iceberg — Estimativa IPEA/PNS

O gráfico mais impactante do projeto: confronta os totais nacionais de ambas as fontes oficiais com a **estimativa científica do IPEA** (baseada na Pesquisa Nacional de Saúde do IBGE). A escala logarítmica é necessária porque a estimativa real é ordens de grandeza maior que os registros formais.

```
Registros oficiais  ──────────────────────────────┐  ← topo do iceberg
Estimativa IPEA/PNS ──────────────────────────────┘  ← base submersa
```

### KPI de Invisibilidade — Taxa de Subnotificação por UF

**Métrica derivada** criada para este projeto:

```
Taxa de Subnotificação = 1 − (média SINAN + Anuário) / Estimativa IPEA
```

A média entre as duas fontes oficiais serve como linha de base conservadora para evitar dupla contagem. O resultado é o exato percentual de casos que o Estado não captura — o "ponto cego" institucional de cada UF.

### Dumbbell Plot — Descompasso institucional

Compara simultaneamente a subnotificação do SINAN (🟠) e do Anuário (🔵) para cada estado. A **linha conectora** representa o vão de integração entre as duas instituições: uma linha longa indica que saúde e segurança pública estão operando de costas uma para a outra, deixando vítimas invisíveis para ao menos um dos sistemas.

---

## 📦 Fontes de Dados

Os dados utilizados neste projeto foram coletados manualmente nas fontes oficiais abaixo, tratados localmente e salvos na pasta `data/` do repositório. O notebook consome exclusivamente esses arquivos — não há chamadas externas para obtenção dos dados analíticos.

| Arquivo | Fonte original | Órgão | Coleta |
|:---|:---|:---|:---:|
| `busca_estabelecimentos_servicos_especializados.csv` | [ElastiCNES — Serviços Especializados](https://elasticnes.saude.gov.br/servicos-especializados) | Ministério da Saúde / DATASUS | Abr/2026 |
| `estupro_e_estupro_de_vulneravel_vitimas_mulheres_2024.xlsx` | [19º Anuário Brasileiro de Segurança Pública](https://publicacoes.forumseguranca.org.br/items/c3605778-37b3-4ad6-8239-94e4cb236444) | Fórum Brasileiro de Segurança Pública (FBSP) | Abr/2026 |
| `sinan_vs_anuario_seguranca_publica-2024_vs_IPEA-2019.xlsx` | [SINAN/DATASUS](https://tabnet.datasus.gov.br/cgi/deftohtm.exe?sinannet/cnv/violebr.def) · [PNS/IBGE](https://www.ibge.gov.br/estatisticas/sociais/saude/9160-pesquisa-nacional-de-saude.html) · [Nota Técnica IPEA](https://repositorio.ipea.gov.br/server/api/core/bitstreams/483862e7-820f-44a5-8708-d499ba857ab5/content) | MS/DATASUS · IBGE · IPEA | Mai/2026 |

> **Nota sobre o arquivo consolidado:** `sinan_vs_anuario_seguranca_publica-2024_vs_IPEA-2019.xlsx` reúne três fontes distintas em uma única tabela tratada — os registros de violência da Saúde (SINAN), os boletins de ocorrência da Polícia (Anuário FBSP) e a estimativa científica de prevalência real calculada pelo IPEA a partir da Pesquisa Nacional de Saúde (PNS) do IBGE.

---

## 🛠️ Stack Tecnológica

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white"/>
  <img src="https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white"/>
  <img src="https://img.shields.io/badge/Plotly-3F4F75?style=flat-square&logo=plotly&logoColor=white"/>
  <img src="https://img.shields.io/badge/Folium-77B829?style=flat-square&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/ipywidgets-F37626?style=flat-square&logo=jupyter&logoColor=white"/>
  <img src="https://img.shields.io/badge/Requests-2E8B57?style=flat-square"/>
  <img src="https://img.shields.io/badge/HTML5_&_CSS3-E34F26?style=flat-square&logo=html5&logoColor=white"/>
</p>

| Biblioteca | Finalidade |
|:---|:---|
| `pandas` | Manipulação, limpeza e agregação dos dados governamentais |
| `numpy` | Operações numéricas e cálculo da distância de Haversine |
| `plotly` | Visualizações interativas (choropleth, treemap, scatter, lollipop, dumbbell) |
| `folium` | Mapa geoespacial interativo com camadas e painel lateral customizado |
| `ipywidgets` | Buscador interativo por estado/município e GPS de acolhimento |
| `requests` | Carregamento do GeoJSON dos estados brasileiros |
| HTML/CSS | Interface customizada dos cards de resultado nos buscadores |

---

## ▶️ Como Executar

### 1. Clone o repositório

```bash
git clone https://github.com/otaviofabbro/geoanalise-violencia-sexual-br.git
cd geoanalise-violencia-sexual-br
```

### 2. Crie e ative um ambiente virtual

```bash
python -m venv venv
source venv/bin/activate        # Linux / macOS
venv\Scripts\activate           # Windows
```

### 3. Instale as dependências

```bash
pip install pandas numpy plotly folium ipywidgets requests openpyxl jupyter
```

### 4. Execute o notebook

```bash
jupyter notebook notebooks/violencia_sexual_e_estabelecimentos_servicos_especializados.ipynb
```

> **Importante:** Use "Executar Tudo" (`Kernel → Restart & Run All`) antes de interagir com os buscadores — os widgets dependem de variáveis carregadas nas células anteriores.

> **Nota:** Os dados são carregados diretamente deste repositório público via URL — nenhum download manual é necessário.

---

## ⚠️ Limitações e Notas Metodológicas

**1. Proxy de dupla contagem:** A mesma vítima pode ter sido atendida tanto pelo SINAN quanto registrada no Anuário. Por isso, a métrica de subnotificação usa a *média* entre as duas fontes como linha de base conservadora, não a soma.

**2. Defasagem temporal entre fontes:** Os dados do CNES e do SINAN/Anuário são de 2024–2026; a estimativa do IPEA é baseada na PNS de 2019. A comparação é estrutural, não pontual — os achados indicam tendências, não valores absolutos precisos.

**3. Subnotificação como piso, não como teto:** A estimativa do IPEA foi construída para mulheres adultas. Casos envolvendo vulneráveis (crianças, pessoas com deficiência) provavelmente elevam ainda mais o número real.

**4. Policiamento diferencial:** Taxas mais altas de registro policial em alguns estados podem refletir maior cobertura de delegacias especializadas (DEAMs) e não necessariamente maior incidência real de violência.

**5. Geolocalização do CNES:** Estabelecimentos sem coordenadas cadastradas foram excluídos do mapa e do GPS de acolhimento, o que pode subestimar a cobertura real em algumas regiões.

---

## 📚 Referências

- Fórum Brasileiro de Segurança Pública. (2025). [19º Anuário Brasileiro de Segurança Pública](https://publicacoes.forumseguranca.org.br/items/c3605778-37b3-4ad6-8239-94e4cb236444).
- Ministério da Saúde / DATASUS. [SINAN — Violência Interpessoal e Autoprovocada](https://tabnet.datasus.gov.br/cgi/deftohtm.exe?sinannet/cnv/violebr.def).
- Ministério da Saúde / DATASUS. [ElastiCNES — Serviços Especializados](https://elasticnes.saude.gov.br/servicos-especializados).
- IBGE. [Pesquisa Nacional de Saúde (PNS) 2019](https://www.ibge.gov.br/estatisticas/sociais/saude/9160-pesquisa-nacional-de-saude.html).
- IPEA. [Elucidando a prevalência de estupro no Brasil a partir de diferentes bases de dados](https://repositorio.ipea.gov.br/server/api/core/bitstreams/483862e7-820f-44a5-8708-d499ba857ab5/content).

---

## 👤 Autor
<div align="center">
<table>
  <tr>
    <td align="center">
      <b>Otávio Fabbro Machado</b><br/>
      Bacharel em Ciências Sociais (FFLCH-USP)<br/>
      Especialista em Ciência de Dados (ICMC-USP)<br/><br/>
      <a href="https://www.linkedin.com/in/otaviofabbrodata">
        <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white"/>
      </a>
      <a href="https://github.com/otaviofabbro">
        <img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white"/>
      </a>
      <a href="mailto:otaviofabbro2@gmail.com">
        <img src="https://img.shields.io/badge/Gmail-D14836?style=flat-square&logo=gmail&logoColor=white"/>
      </a>
    </td>
  </tr>
</table>

</div>

---

<div align="center">

<sub>Projeto desenvolvido com fins de utilidade pública.<br/>
Todos os dados utilizados são públicos e de acesso aberto.<br/><br/>
📞 <b>Ligue 180</b> — Central de Atendimento à Mulher · 24h · gratuito e sigiloso</sub>

</div>

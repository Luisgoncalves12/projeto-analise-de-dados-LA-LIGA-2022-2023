#  Análise de Dados — La Liga 2022/2023
> Projeto de análise exploratória da temporada 2022/2023 da La Liga, desenvolvido como parte do portfólio de entrada na área de dados.

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

---

## 📋 Sobre o Projeto

Análise exploratória do dataset da La Liga 2022/2023 (Kaggle), simulando uma entrega para a empresa fictícia **DataSports Analytics**. O objetivo foi extrair insights sobre eficiência ofensiva, perfil dos elencos, disciplina e desempenho individual dos jogadores.

**Dataset:** [La Liga 2022/2023 — Kaggle](https://www.kaggle.com/)  
**Linhas:** 542 jogadores | **Colunas:** 15 variáveis

---

## 🔍 Análises Realizadas

### 1. Eficiência Ofensiva por 90 min
Criação das métricas **GP** (gols por 90 min) e **AP** (assistências por 90 min), filtradas para jogadores com mais de 900 minutos jogados.

```python
df_900 = df[df["MinP"] > 900]
df_900["GP"] = (df_900["Goals"] / df_900["MinP"]) * 90
df_900["AP"] = (df_900["Assist"] / df_900["MinP"]) * 90
```

<img width="1311" height="741" alt="Captura de tela 2026-06-05 145606" src="https://github.com/user-attachments/assets/f8ab7672-b2b2-42c0-bae0-ae642e1abbef" />



---

### 2. Média de Idade x Produção Ofensiva por Time
Cruzamento da média de idade do elenco com o total de gols e assistências por clube, para identificar se times mais jovens produzem menos ofensivamente.

```python
idade_media = df.groupby('Team-name').agg(
    idade_media=('Age', 'mean'),
    total_gols=('Goals', 'sum'),
    total_assists=('Assist', 'sum')
).sort_values('idade_media', ascending=True)
```

<img width="1310" height="738" alt="image" src="https://github.com/user-attachments/assets/39037c8b-10e1-4675-8818-1da0e94f2667" />



---

### 3. Disciplina por Time — Cartões Amarelos e Vermelhos
Ranking dos clubes mais indisciplinados da temporada, com separação entre amarelos, vermelhos e total.

<img width="1311" height="735" alt="Captura de tela 2026-06-05 145644" src="https://github.com/user-attachments/assets/8170a8d2-a899-4bb1-a541-b6246694c3df" />


---

### 4. MOTM x Rating — Os Melhores da Temporada
Scatter chart cruzando prêmios de Melhor em Campo com a nota média dos jogadores. Lewandowski se destaca isolado no quadrante superior direito.

<img width="1307" height="737" alt="Captura de tela 2026-06-05 145634" src="https://github.com/user-attachments/assets/4b1c0ad4-8cf9-4b45-825a-5176b73a9b06" />


---

## 🛠️ Tecnologias

| Ferramenta | Uso |
|---|---|
| Python + Pandas | Limpeza, transformação e criação de métricas |
| Jupyter Notebook | Desenvolvimento e documentação das análises |
| Power BI | Visualização interativa dos dados |
| Excel (.xlsx) | Exportação dos dados tratados para o Power BI |

---

## 📁 Estrutura do Repositório

```
📦 laliga-analise
 ┣ 📂 notebooks
 ┃ ┣ 📓 not1_idade_elenco.ipynb
 ┃ ┣ 📓 not2_eficiencia_ofensiva.ipynb
 ┃ ┣ 📓 not3_motm_rating.ipynb
 ┃ ┗ 📓 not4_cartoes.ipynb
 ┣ 📂 data
 ┃ ┗ 📄 laliga_2223.csv
 ┣ 📂 exports
 ┃ ┣ 📊 eficiencia_jogadores.xlsx
 ┃ ┣ 📊 Idade_elenco.xlsx
 ┃ ┣ 📊 melhores_da_temp.xlsx
 ┃ ┗ 📊 Cartao.xlsx
 ┣ 📂 dashboard
 ┃ ┗ 📊 LaLiga_Dashboard.pbix
 ┗ 📄 README.md
```

---

## 💡 Principais Insights

- **Lewandowski** liderou tanto em GP (0,80 gols/90min) quanto em MOTM (7 prêmios), com o maior rating da temporada (7,53)
- **Mallorca** foi o time mais indisciplinado com 67 cartões no total; **Athletic Bilbao** o mais disciplinado com apenas 33
- Times mais jovens como **Valencia** (24 anos de média) e **Real Sociedad** (24,7) apresentaram produções ofensivas competitivas frente a elencos mais experientes
- **Antoine Griezmann** teve o melhor AP entre jogadores com +900 min (0,43 assistências/90min)

---

## 👤 Autor

**Luis Gustavo**  
Engenharia de Software — UDF  
[LinkedIn](https://www.linkedin.com/in/luis-gustavo-2422b2338/) · [GitHub](https://github.com/Luisgoncalves12)

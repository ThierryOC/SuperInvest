<div align="center">

# SuperInvest — Detalhes Técnicos / Technical Details

🇧🇷 [Português](#-português) · 🇺🇸 [English](#-english)

</div>

---

## 🇧🇷 Português

> ⚠️ **Isto não é recomendação de investimento.** Ver aviso completo no [README](README.md).

### O que é

Aplicativo desktop (Windows) que reúne quatro classes de ativo do mercado brasileiro — **ações, FIIs, criptomoedas e renda fixa (Tesouro Direto)** — num único painel, com dois motores de análise distintos e claramente separados:

- **Motor de score por regras**: cinco eixos (risco, qualidade, valuation, potencial de retorno, categoria), 100% transparente e explicável — cada nota vem com a razão que a gerou.
- **Ranking ML experimental**: um conselho de três arquiteturas de machine learning (XGBoost, CatBoost, regressão Ridge) treinado para ranquear ativos por retorno futuro esperado, combinado por peso estatístico de cada modelo.

Inclui também controle de posições (custo médio, estimativa de Imposto de Renda) e login com trava de dispositivo.

### Por que é diferente de "mais um app de ranking"

A parte que mais interessa a quem avalia o projeto tecnicamente não é a interface — é a disciplina de validação por trás do Ranking ML, construída para evitar os erros mais comuns (e mais silenciosos) de machine learning aplicado a séries temporais financeiras:

- **Validação combinatorial purgada (CPCV)**, método de Marcos López de Prado (*Advances in Financial Machine Learning*) — com purga e embargo nos dois lados de cada bloco de teste, para nenhuma informação do futuro vazar para o treino.
- **Anti-vazamento comprovado por teste automatizado**, não apenas alegado no código.
- **Ensemble ponderado por IC** (Information Coefficient) de cada arquitetura, nunca um "vencedor" único escolhido a dedo por backtest.
- **Significância estatística de verdade**: teste-t e teste de permutação (10.000 permutações) sobre períodos não sobrepostos, antes de qualquer resultado ser considerado válido.
- **Disciplina de resultado negativo**: mais de dez sinais de timing de mercado foram pesquisados e testados ao longo do projeto (volatilidade implícita, prêmio de risco de variância, dados macroeconômicos do Banco Central, amplitude de mercado, cointegração entre pares, momentum cross-sectional) — a maioria não mostrou sinal estatisticamente significativo, e isso é reportado com a mesma honestidade dos resultados positivos.

### Stack técnica

`Python` · `PySide6 (Qt)` · `XGBoost` · `CatBoost` · `scikit-learn` · `Optuna` (busca de hiperparâmetro) · `pandas` / `NumPy` · `statsmodels` · `Supabase` (autenticação) · `PyInstaller` + `Cython` (build do instalador) · `Inno Setup`

Fontes de dado — todas gratuitas: yfinance, Banco Central do Brasil (SGS), CoinGecko, Deribit, Binance (dado público), Tesouro Transparente.

*(O código-fonte deste projeto é mantido privado — este repositório serve como portfólio e canal de distribuição do instalador já compilado.)*

---

## 🇺🇸 English

> ⚠️ **This is not investment advice.** See the full disclaimer in the [README](README.md).

### What it is

A Windows desktop application covering four asset classes in the Brazilian market — **stocks, real estate funds (FIIs), cryptocurrency, and government bonds (Tesouro Direto)** — in a single dashboard, built around two clearly separated analysis engines:

- **Rule-based scoring engine**: five axes (risk, quality, valuation, return potential, category), fully transparent and explainable — every score ships with the reasoning behind it.
- **Experimental ML ranking**: an ensemble of three machine learning architectures (XGBoost, CatBoost, Ridge regression) trained to rank assets by expected forward return, combined by each model's statistical weight.

It also includes position tracking (weighted-average cost basis, income-tax estimation) and login with device-lock authentication.

### Why it's more than "another ranking app"

What's most relevant to a technical reviewer isn't the UI — it's the validation discipline behind the ML ranking, built specifically to avoid the most common (and most silent) failure modes of machine learning applied to financial time series:

- **Combinatorial Purged Cross-Validation (CPCV)**, following Marcos López de Prado's method (*Advances in Financial Machine Learning*) — with purging and embargo on both sides of every test block, so no future information leaks into training.
- **Leakage-freedom verified by automated tests**, not just asserted in comments.
- **IC-weighted ensemble** (Information Coefficient) across architectures — never a single "winner" hand-picked from a backtest.
- **Real statistical significance testing**: t-test and permutation test (10,000 permutations) over non-overlapping periods, before any result is treated as valid.
- **A discipline of reporting negative results**: more than ten market-timing signals were researched and tested over the course of the project (implied volatility, variance risk premium, Brazilian central-bank macro data, market breadth, pairs cointegration, cross-sectional momentum) — most showed no statistically significant signal, and that's reported with the same honesty as the positive findings.

### Tech stack

`Python` · `PySide6 (Qt)` · `XGBoost` · `CatBoost` · `scikit-learn` · `Optuna` (hyperparameter search) · `pandas` / `NumPy` · `statsmodels` · `Supabase` (auth) · `PyInstaller` + `Cython` (installer build) · `Inno Setup`

Data sources — all free tier: yfinance, Central Bank of Brazil (SGS), CoinGecko, Deribit, Binance (public data), Tesouro Transparente.

*(The source code for this project is kept private — this repository serves as a portfolio piece and as the distribution channel for the compiled installer.)*

---

<div align="center">

Feito por **Thierry de Oliveira Ciaramicolo**, formado em Ciência da Computação — desenvolvido com apoio de ferramentas de Inteligência Artificial generativa.
*Built by **Thierry de Oliveira Ciaramicolo**, Computer Science graduate — developed with the support of generative AI tools.*

</div>

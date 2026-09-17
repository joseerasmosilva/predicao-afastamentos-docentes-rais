# Predição de afastamentos por doença em vínculos docentes da educação básica com aprendizado de máquina

Repositório de reprodutibilidade do Trabalho de Conclusão de Curso em Engenharia de Software.

## Escopo

O estudo utiliza registros da RAIS de 2020 a 2025 e trata o afastamento por doença no nível **vínculo-ano**. O desenho temporal da versão final é:

- treino: 2020–2023;
- validação temporal e definição do limiar: 2024;
- teste temporal posterior: 2025;
- modelo final: Random Forest;
- limiar congelado após 2024: 0,7253175378.

Os escores do Random Forest são utilizados para discriminação e priorização relativa e **não devem ser interpretados como probabilidades individuais calibradas**.

## Ordem de execução

1. `notebooks/00_download_filtro_RAIS_5CBO.ipynb` — download/reutilização dos arquivos da RAIS e filtro das famílias CBO docentes.
2. `notebooks/01_recuperar_validar_RAIS_2022.ipynb` — recuperação e validação específica da RAIS de 2022.
3. `notebooks/02_auditoria_ETL_base_final_V2.ipynb` — auditoria e harmonização da base intermediária.
4. `notebooks/03_construir_RAIS_BASE_MODELO_FINAL_V3.ipynb` — construção da base final utilizada na modelagem.
5. `notebooks/04_comparacao_inicial_modelos.ipynb` — comparação inicial entre referência por prevalência, regressão logística, Random Forest, XGBoost, LightGBM e CatBoost.
6. `notebooks/05_modelo_final_RF_risco_historico_municipal.ipynb` — treinamento do Random Forest final, validação de 2024 e teste temporal de 2025.
7. `notebooks/06_complemento_SHAP_rankings_resumo_final.ipynb` — interpretação por SHAP e consolidação de resultados complementares.
8. `notebooks/07_resultados_municipais_teste_temporal_2025.ipynb` — agregação municipal dos resultados do conjunto de teste de 2025.

## Metadados

O arquivo `metadata/22_manifesto_final.json` registra os principais parâmetros do experimento final, incluindo períodos temporais, preditores, limiar, alpha municipal, tamanho da amostra SHAP e semente pseudoaleatória.

## Dados e artefatos

As bases brutas e intermediárias da RAIS, arquivos Parquet, vetores de predição, modelos serializados e planilhas de resultados não são versionados neste repositório. Os notebooks utilizam caminhos do Google Drive empregados durante a execução original e podem exigir adaptação para outro ambiente.

A planilha complementar com os resultados municipais de 2025 está disponível em:

https://cutt.ly/5yx6ScHx

## Ambiente computacional

A execução original foi realizada no Google Colab. Foram utilizados, entre outros, pandas, NumPy, PyArrow, joblib, scikit-learn, XGBoost, LightGBM, CatBoost e SHAP. O artefato final registrou scikit-learn 1.6.1. As versões exatas do Python e de todos os demais pacotes não foram persistidas de forma completa, portanto não foi feito pinning retrospectivo de versões não comprovadas.

## Observação sobre os notebooks publicados

Os notebooks deste repositório correspondem aos códigos utilizados nas etapas finais do estudo. Para publicação, foram removidos outputs de células e metadados pessoais/operacionais do Google Colab; o código-fonte das células foi preservado.

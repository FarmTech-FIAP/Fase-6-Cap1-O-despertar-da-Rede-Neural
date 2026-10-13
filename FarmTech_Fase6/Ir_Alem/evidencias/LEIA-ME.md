# Evidências — Ir Além, Fase 6

Arquivos exportados pela última célula do notebook `CarolineCoelhoMendes_rm570370_ir_alem_fase6.ipynb`.

- `original_mascara_sem_fundo.png`: imagem original, máscara do SAM 2 e objeto com fundo branco.
- `curvas_transfer_learning.png`: acurácia de treino e validação das duas MobileNetV2, com o início do Fine Tuning marcado.
- `matrizes_confusao.png`: matrizes de confusão das duas MobileNetV2 no teste.
- `comparacao_acuracia.png`: acurácia das duas MobileNetV2 nas mesmas 8 imagens de teste.
- `cnn_zero_com_sem_fundo.png` e `cnn_zero_sementes.csv`: CNN do zero com e sem fundo, 5 sementes por versão.
- `camadas_fine_tuning.csv`: camadas da MobileNetV2 liberadas no Fine Tuning.
- `comparacao_pareada_teste.csv`: predição de cada modelo, e da própria YOLO, em cada imagem de teste.
- `metricas_resumidas.csv`: acertos, F1, tempos de treino e de inferência.
- `conclusoes_ir_alem.md`: conclusões geradas automaticamente a partir das métricas.

**Cautela:** 8 imagens de teste são uma amostra muito pequena; 8/8 não comprova acurácia de 100% fora desta base. Máscaras válidas não equivalem a uma validação manual pixel a pixel.

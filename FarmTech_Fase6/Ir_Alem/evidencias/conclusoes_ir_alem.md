# Conclusões — Ir Além (resultados desta execução)

**Hipótese 1 — Transfer Learning:** a MobileNetV2 pré-treinada na ImageNet, com Fine Tuning das últimas 30 camadas (BatchNormalization congelada), alcançou **100.0%** nas 8 imagens de teste com imagens inteiras. A CNN do zero da Entrega 2 obteve 37.5% no mesmo teste, e a média das 5 sementes da CNN do zero com imagem inteira (seção 7.1) foi 42.5%. O resultado é compatível com o benefício do pré-treinamento, mas as redes diferem também em arquitetura e resolução, e a amostra é pequena; não é uma prova causal isolada.

**Hipótese 2 — Segmentação, com a MobileNetV2:** a versão com fundo removido alcançou **100.0%** (diferença de +0.0%). As duas versões acertaram 8/8: há **efeito teto**, e esta comparação é **inconclusiva** — não mostra que a segmentação ajuda, nem que atrapalha. Imagens corrigidas pela máscara: 0; prejudicadas: 0.

**Hipótese 2 — Segmentação, com a CNN do zero (5 sementes):** média de **42.5% ± 6.8%** com imagem inteira e **42.5% ± 11.2%** com fundo removido (diferença de +0.0%). Nos 40 pares imagem × semente, a máscara corrigiu 7 e prejudicou 7 (teste pareado exato p=1.000, exploratório). Conclusão: a remoção do fundo **não alterou** a média da CNN do zero; os dados não sustentam a hipótese 2.

**A própria YOLO como classificador:** a classe atribuída pela YOLO ao objeto principal acertou **8/8** imagens de teste (100%). Ou seja, no pipeline segmentado o primeiro estágio já carrega a informação de classe; para esta base, o classificador após a máscara acrescenta pouco além de uma segunda opinião.

**Qualidade da segmentação:** 0 casos sem máscara válida entre 80 imagens (0 no teste). Máscara válida não significa contorno perfeito (seção 5.1).

**Custo computacional:** mediana de **144.4 ms por imagem** para localizar (YOLO) e segmentar (SAM 2), além da classificação. Pipeline total: **6.1 ms** (imagem inteira) contra **150.2 ms** (fundo removido) por imagem na GPU desta execução. Treino das MobileNetV2: 0.44 e 0.34 min (sem incluir a geração das máscaras).

**Limitações:** conjunto muito pequeno, rótulos de detecção parcialmente completos, segmentação dependente de uma YOLO treinada no domínio, escolha automática de um único objeto e tempos dependentes da GPU. São conclusões de uma prova de conceito acadêmica.

**Decisão para o cliente fictício:** para classificação, usar a **MobileNetV2 com a imagem inteira** — mesma acurácia observada, menos componentes e menor custo. Reavaliar a segmentação quando houver mais dados e cenas mais difíceis.

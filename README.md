# Recuperação de Dados do Nanodrop

Problema:
O equipamento NanoDrop 2000/2000c travou pasta com dados, sendo necessária recuperação por meio da pasta AutoSave. Esta, não realiza separação por usuário ou por comprimento de onda, por isso, foi necessária a criação do código de recuperação.

Contexto geral:
No meu mestrado em Biotecnologia, pela Universidade de São Paulo, eu estudei o crescimento de três espécies de cianobactérias (com códigos 230, 159 e 163) em simulações de ambiente marciano, pensando no contexto de Astrobiologia. Uma das simulações tinha como objetivo avaliar o crescimento desses organismos a diferentes doses de radiação UV-C, a qual é considerada letal e é uma das condições em Marte desfavoráveis à manutenção da vida.

Nesse experimento, cada espécie era exposta a 6 doses diferentes de radiação (0, 100, 300, 500, 700 e 1000J), dando um total de 18 amostras. Como esses organismos crescem em meio líquido, a forma de medir o crescimento em cada condição foi por meio de uma curva de crescimento de absorbância por dia. A medida de absorbância era feita por meio do espectrofotômetro e as medidas foram feitas diariamente por cerca de 30 dias. Quanto mais células na amostra, maior a absorbância.

O objetivo no final era obter uma curva de crescimento para cada dose e para cada espécie.

Processo de medida:
Diariamente, uma pequena alíquota de cada amostra era retirada e colocada em uma cubeta que era colcoada no equipamento. Cada amostra era medida três vezes para a obtenção de erro estatístico, sendo cerca de 54 medidas por dia. Cada medida recebia um nome padrão, indicando a espécie e a dose (exemplo: '230 500J'). Além disso, mesmo que o NanoDrop meça a absorbância em todo o espectro, apenas um valor de comprimento de onda foi selecionado para a obtenção dos resultados, que no caso foi 750nm. 

Então, no final, o equipamento deveria me retornar uma planilha contendo cada medida, a data realizada e a absorbância a 750nm.

O problema é que, após mais de 340 medidas, a minha pasta travou com todos os resultados. Como não houve aviso prévio pelo equipamento, suponho que a causa disso seja a grande quantidade de informações na pasta.

Como a pasta possui uma extensão específica, ela só poderia ser acessada por meio do equipamento.
Entrei em contato com o suporte, mas também não conseguiram o acesso aos dados. A solulão proposta foi usar a pasta AutoSave no computador onde são salvas planilhas .csv diárias de uso do equipamento. Todas as medidas feitas por dia são armazenadas na planilha, sendo uma página por medida. Nessas planilhas, não há identificação do usuário que fez a medida e o dado no comprimento de onda selecionado não é separado, sem fornecido os dados em todo o espectro.

Solução:
Para conseguir selecionar as minhas medidas, eu criei o código presente em Recuperacao_e_selecao_Nanodrop, que tem acesso a uma pasta no computador contendo as planilhas de cada dia. Para cada planilha na pasta, o código olha o título da medida para identificar se contém o código da cianobactéria. Se sim, ele recupera a data da medida, a dose (também do título) e ele busca a linha que contém o comprimento de onda desejado (750nm). Essas informações são salvas em uma nova planilha.

Após isso, eu configurei as planilhas com o arquivo em Configuracao_das_planilhas para realizar o ajuste das curvas em Ajuste_das_curvas.

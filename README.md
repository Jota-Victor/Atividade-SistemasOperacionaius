# Atividade-SistemasOperacionaius
Atividade avaliativa feita em equipe com os seguintes membros: Joao Victor, Ronald, Lara, Giovani, Cainan e Pedro Saulo

Simulação de Gerenciamento de Memória com Partições Fixas
Este projeto consiste em uma simulação de gerenciamento de memória utilizando a estratégia de partições fixas, desenvolvida para a disciplina de Sistemas Operacionais
. O objetivo principal é analisar o comportamento da memória e métricas como utilização, fragmentação interna e tempo de espera de processos
.
Descrição do Projeto
A simulação emula um ambiente onde a memória principal é dividida em blocos de tamanho estático
. O sistema utiliza a política de alocação First Fit, onde cada processo é colocado na primeira partição livre que possua tamanho suficiente para comportá-lo
. Caso não haja espaço imediato, o processo é enviado para uma fila de espera e aguarda a liberação de recursos (swapping)
.
Estruturas de Dados
Listas (Vetores): Utilizadas para representar as partições de memória e a fila de espera
.
Classes Python:
Processo: Armazena ID, tamanho e tempo de espera
.
Particao: Controla o estado de ocupação e calcula a fragmentação interna
.
GerenciadorMemoria: Coordena a alocação, liberação e registro de métricas
.
Instruções Passo a Passo
1. Preparação do Ambiente
Para executar a simulação, é necessário ter o Python instalado. O código utiliza a biblioteca pandas para manipulação de dados em versões estendidas, embora a lógica central dependa de estruturas nativas
.
2. Definição da Memória
O primeiro passo no código é instanciar o gerenciador com os tamanhos das partições fixas. No modelo simulado, foram utilizadas partições de 100, 200, 300 e 400 unidades
: gm = GerenciadorMemoria()
3. Criação de Processos
Defina os processos que tentarão ocupar a memória, especificando seu ID e tamanho
. No cenário de teste, foram criados processos variando de 50 a 450 unidades
.
4. Execução da Alocação
Utilize o método alocar(processo) para iniciar o carregamento na memória
.
Se o processo couber em uma partição, ele é alocado e a fragmentação interna daquela partição é calculada (tamanho da partição menos tamanho do processo)
.
Se nenhum bloco for grande o suficiente, o processo vai para a fila
.
5. Liberação e Swapping
Para simular a dinâmica do sistema, utilize liberar(id_processo)
. Quando uma partição é liberada, o gerenciador verifica automaticamente a fila de espera para tentar alocar processos que aguardavam espaço
.
6. Geração de Relatórios
Ao final da execução, invoque o método relatorio_final() para visualizar o desempenho do sistema, incluindo o tempo médio de espera e a utilização média da memória
.
Resultados da Simulação
Com base nos testes realizados:
Utilização Média: Aproximadamente 75%
.
Fragmentação Interna: Aproximadamente 16%
.
Observação de Fragmentação: O processo P5 (450 unidades) não pôde ser alocado mesmo com memória livre total disponível, pois não havia uma partição contígua de tamanho suficiente
.
Limitações e Melhorias
Fragmentação: O uso de partições fixas gera desperdício inevitável de memória quando o processo é menor que o bloco alocado
.
Políticas: O sistema utiliza First Fit, mas poderia ser expandido para incluir Best Fit ou Worst Fit para fins comparativos
.
Ausência de Compactação: Não há realocação de processos para agrupar espaços vazios
.

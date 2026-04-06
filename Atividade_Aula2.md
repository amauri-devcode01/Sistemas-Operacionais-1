# Resumo: História e Evolução dos Sistemas Operacionais
## Referência: TANENBAUM, A. S.; BOS, H. Sistemas Operacionais Modernos. 4. ed. 2015.

---

## 1. Introdução ao Conceito de Sistema Operacional
Antes de mergulhar na história, é fundamental entender o que os autores definem como a função de um Sistema Operacional (SO). Segundo Tanenbaum e Bos, o SO atua essencialmente em duas frentes principais:
1. **Gerenciador de Recursos:** Ele atua como um gerente que aloca tempo de CPU, memória, espaço em disco e dispositivos de I/O (Entrada/Saída) para os diversos programas que competem por eles.
2. **Máquina Estendida (ou Virtual):** Ele oferece aos programadores uma abstração mais limpa, simples e de alto nível do hardware, escondendo a complexidade feia e caótica dos circuitos eletrônicos.

A evolução dos sistemas operacionais está diretamente ligada à evolução do próprio hardware. À medida que os computadores se tornaram mais rápidos, menores e mais baratos, os sistemas operacionais precisaram evoluir para aproveitar esse novo poder computacional.

---

## 2. A Geração Zero: Computadores Mecânicos (1642 - 1945)
Embora o livro foque a partir de 1945, os autores costumam referenciar os primórdios para contextualizar a evolução:
* **Blaise Pascal (1642):** Construiu a primeira máquina de calcular mecânica.
* **Charles Babbage (Século XIX):** Projetou a "Máquina Analítica", que continha pela primeira vez conceitos modernos como memória (massa) e CPU (moinho). No entanto, por ser puramente mecânica (engrenagens e rodas dentadas), a tecnologia da época não permitia sua construção em larga escala.
* **Ada Lovelace:** Considerada a primeira programadora do mundo, por criar algoritmos para a máquina de Babbage.

Nessa época, **não existia o conceito de Sistema Operacional**. Os cálculos eram feitos ajustando engrenagens manualmente.

---

## 3. A Primeira Geração: Válvulas e Painéis (1945 – 1955)
Após os esforços da Segunda Guerra Mundial, surgiram os primeiros computadores digitais verdadeiros.

### Características do Hardware
* Uso massivo de **válvulas a vácuo**.
* Máquinas gigantescas que ocupavam salas inteiras (ex: ENIAC).
* Milhares de vezes mais lentas que o mais simples microprocessador atual.
* Altíssima taxa de falha (as válvulas queimavam constantemente devido ao calor excessivo).

### Operação e Software
* **Ausência de Sistema Operacional:** O programador era também o operador da máquina.
* **Linguagem de Máquina Absoluta:** Toda a programação era feita diretamente em código binário ou através de conexões físicas.
* **Painéis de Plugues (Plugboards):** Para programar, era necessário conectar e desconectar centenas de fios em painéis físicos para direcionar o fluxo de dados.
* **Processo de Trabalho:** O usuário reservava um bloco de tempo na parede (ex: das 2h às 4h da manhã), entrava na sala, plugava os cabos, carregava os dados e torcia para que nenhuma das milhares de válvulas queimasse durante a execução.

No início da década de 1950, houve uma pequena evolução com a introdução dos **cartões perfurados**. Agora era possível escrever programas em cartões e lê-los, em vez de usar os painéis de plugues, mas o modelo de "um usuário por vez" permanecia.

---

## 4. A Segunda Geração: Transistores e Sistemas em Lote (1955 – 1965)
A introdução do **transistor** no meio da década de 1950 mudou tudo radicalmente. As máquinas tornaram-se confiáveis o suficiente para serem fabricadas e vendidas a clientes pagantes (grandes empresas e governos).

### Características do Hardware
* Substituição das válvulas por **transistores**.
* Computadores menores, mais rápidos, mais baratos e que consumiam menos energia.
* Surgimento dos *Mainframes* (como o IBM 7094).
* Distinção clara entre projetistas, construtores, operadores, programadores e pessoal de manutenção.

### O Surgimento dos Sistemas Operacionais e o Processamento em Lote (*Batch*)
Como o tempo de computador era extremamente caro, deixar a máquina ociosa enquanto o programador andava pela sala montando fitas era um desperdício intolerável. Surgiu então o **Sistema de Processamento em Lote** (*Batch Processing*).

* **O Fluxo de Trabalho:**
  1. O programador escrevia o código em papel (geralmente em FORTRAN ou Assembler).
  2. Perfurava o código em cartões.
  3. Entregava a pilha de cartões ao operador.
  4. O operador agrupava vários trabalhos (um "lote") em uma fita magnética usando um computador menor e mais barato (como o IBM 1401).
  5. A fita era levada para o computador principal (IBM 7094), que lia os trabalhos sequencialmente e gravava os resultados em outra fita.
  6. A fita de saída era levada de volta ao computador menor para imprimir os resultados.

* **O Papel do SO primitivo:**
  * O ancestral do sistema operacional moderno era apenas um pequeno programa residente na memória chamado **Monitor**.
  * Sua única função era ler o próximo trabalho da fita, carregá-lo na memória, executá-lo e, quando terminasse, ler o próximo.
  * Sistemas notáveis dessa era: **FMS** (Fortran Monitor System) e **IBSYS** (da IBM).

---

## 5. A Terceira Geração: Circuitos Integrados e Multiprogramação (1965 – 1980)
Até o início dos anos 1960, a maioria dos fabricantes tinha duas linhas de produtos distintas e incompatíveis: computadores científicos (focados em cálculos numéricos rápidos) e computadores comerciais (focados em leitura e impressão de grandes volumes de dados).

### O IBM System/360
A IBM resolveu esse problema introduzindo a família **System/360**. Era uma série de máquinas compatíveis entre si, projetadas para atender tanto ao mercado científico quanto ao comercial.
* Uma empresa podia começar com um modelo pequeno e, conforme crescia, migrar para modelos maiores apenas movendo os programas, sem precisar reescrevê-los.
* O sistema operacional criado para gerenciar essa família foi o **OS/360**. Ele era gigantesco e continha milhares de bugs, mas introduziu conceitos que usamos até hoje.

### O Conceito de Multiprogramação
Na segunda geração, quando um trabalho precisava ler dados de uma fita ou disco, a CPU (que era caríssima) ficava completamente ociosa esperando o dispositivo mecânico terminar. Para resolver essa ineficiência, a terceira geração popularizou a **Multiprogramação**.

* **Como funciona:** A memória do computador é dividida em várias partições. Em cada partição, um trabalho diferente é colocado.
* Quando o trabalho atual precisa esperar por uma operação de I/O (como ler um arquivo), a CPU não fica parada. O sistema operacional simplesmente passa o controle da CPU para outro trabalho que está na memória e pronto para rodar.
* Isso maximizou o uso da CPU, garantindo que ela estivesse quase sempre processando algo útil.

### Spooling (*Simultaneous Peripheral Operation On-Line*)
Outro avanço foi o *Spooling*. Em vez de carregar cartões diretamente para a fita e da fita para a memória, os cartões eram lidos e armazenados diretamente no disco magnético assim que chegavam.
* Quando um trabalho terminava, o sistema operacional podia carregar um novo trabalho diretamente do disco para a partição de memória agora livre.
* Da mesma forma, as impressões eram gravadas no disco e impressas depois, sem travar o processamento principal.

### Sistemas de Compartilhamento de Tempo (*Time-Sharing*)
A multiprogramação resolveu o problema da CPU ociosa, mas criou outro: o tempo de resposta para o programador era horrível. Ele entregava seus cartões de manhã e só recebia o resultado impresso no dia seguinte. Se houvesse um erro de digitação (uma vírgula no lugar de um ponto), ele perdia o dia inteiro.

Para resolver isso, surgiu o compartilhamento de tempo (*Time-Sharing*):
* Uma variante da multiprogramação onde cada usuário possui um terminal interativo (teclado e monitor/impressora de fita).
* A CPU atende a cada usuário por uma fração de segundo (fatias de tempo ou *quantum*).
* Como o cérebro humano é lento comparado à velocidade da luz nos circuitos, cada um dos 50 usuários conectados simultaneamente tinha a ilusão de estar usando o computador sozinho.
* O primeiro sistema prático de tempo compartilhado foi o **CTSS** (desenvolvido no MIT).

### O Nascimento do MULTICS e do UNIX
Após o sucesso do CTSS, o MIT, a Bell Labs e a General Electric decidiram criar uma "utilidade de computação" gigante chamada **MULTICS**. O objetivo era criar uma máquina que suportasse centenas de usuários conectados simultaneamente, funcionando de forma contínua como a rede de energia elétrica.
* O projeto do MULTICS foi excessivamente complexo e ambicioso. A Bell Labs acabou desistindo do projeto.
* No entanto, um dos cientistas da Bell Labs que trabalhou no MULTICS, **Ken Thompson**, encontrou um computador PDP-7 ocioso e decidiu escrever uma versão simplificada e monousuário do MULTICS por conta própria. Esse sistema acabou sendo chamado de **UNIX**.
* Mais tarde, junto com **Dennis Ritchie**, eles reescreveram o UNIX na linguagem **C** (criada por Ritchie), o que tornou o UNIX extremamente portátil e amplamente adotado em universidades e no meio corporativo.

---

## 6. A Quarta Geração: Os Computadores Pessoais (1980 – Presente)
Com o surgimento dos circuitos integrados em larga escala (**LSI** e **VLSI**), tornou-se possível colocar milhares (e depois milhões) de transistores em um pequeno chip de silício. Isso deu origem à era dos computadores pessoais.

### O Surgimento do PC e do MS-DOS
Em 1980, a IBM decidiu entrar no mercado de computadores pessoais e precisava de um sistema operacional para o seu novo produto, o IBM PC.
* Eles procuraram a recém-fundada **Microsoft**, de Bill Gates.
* Gates não tinha um sistema pronto, então comprou um sistema operacional existente chamado QDOS (Quick and Dirty Operating System) de uma empresa local (Seattle Computer Products) por cerca de 50 mil dólares.
* Ele modificou o sistema, rebatizou-o de **MS-DOS** (Microsoft Disk Operating System) e o licenciou para a IBM.
* O MS-DOS era baseado puramente em linhas de comando (C:\>).

### A Revolução da Interface Gráfica (GUI)
A verdadeira revolução na facilidade de uso veio com a Interface Gráfica do Usuário (GUI).
* O conceito original de janelas, ícones, menus e ponteiro de mouse foi desenvolvido nos laboratórios da **Xerox PARC** na década de 1970.
* Steve Jobs viu essa tecnologia em uma visita à Xerox e a implementou no computador **Apple Lisa** e, posteriormente, no lendário **Apple Macintosh** em 1984. O Mac foi o primeiro computador comercial de sucesso com interface gráfica.
* Vendo o sucesso da Apple, a Microsoft lançou o **Windows** (originalmente apenas uma casca gráfica rodando em cima do MS-DOS). Foi somente a partir do Windows 95 que o Windows se tornou um sistema operacional completo e independente do DOS.

### O Fenômeno Linux
No início dos anos 1990, o UNIX era um sistema poderoso, mas caro e fechado. Um estudante finlandês chamado **Linus Torvalds** decidiu criar um clone do UNIX para rodar em seu computador pessoal baseado no processador Intel 386.
* Ele disponibilizou o código-fonte na internet gratuitamente.
* Programadores de todo o mundo começaram a contribuir, adicionando drivers, corrigindo bugs e expandindo o sistema.
* Hoje, o Linux domina os servidores de internet, supercomputadores e serve de base para o sistema operacional Android.

---

## 7. A Quinta Geração: Dispositivos Móveis e Computação Onipresente (1990 – Presente)
Embora os computadores pessoais continuem evoluindo, uma nova categoria surgiu e hoje é a mais numerosa do planeta: os dispositivos móveis.

### Sistemas Operacionais Móveis
* Com a chegada do iPhone em 2007, a Apple popularizou o **iOS**, um sistema operacional derivado do UNIX/macOS adaptado para telas sensíveis ao toque.
* O Google respondeu adquirindo e desenvolvendo o **Android**, um sistema baseado no núcleo (kernel) do Linux, projetado para ser aberto e rodar em hardware de diversos fabricantes.
* Os SOs móveis trouxeram novos desafios de gerenciamento: economia severa de bateria, gerenciamento dinâmico de memória para aplicativos em segundo plano e conectividade constante (4G/5G, Wi-Fi, Bluetooth).

---

## 8. Conclusão: O Que Mudou e O Que Permanece?
Olhando para trás, os conceitos fundamentais criados nas décadas de 1960 e 1970 ainda sustentam os sistemas de hoje. A multiprogramação, o compartilhamento de tempo, a abstração de arquivos e as chamadas de sistema continuam presentes tanto em um mainframe moderno quanto no smartphone no seu bolso. A história dos sistemas operacionais é uma constante busca por eficiência, abstração e facilidade de uso diante de um hardware que não para de evoluir.

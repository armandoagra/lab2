### Aula 1 - Plano de curso, instalação, Epic Games Store, primeiros minutos, interface, atalhos, place actors
*Aula inicial*

--> Apresentar plano de curso: avaliação, conteúdos, Unreal vs Unity/Construct, jogos feitos na Unreal, meus jogos na Unreal;

--> Mostrar instalação da Epic Games Store e da Unreal Engine;

--> Criação de projeto, diferentes templates (mostrar 2 ou 3);

--> Interface e janelas;

--> Atalhos (QWERT, movimentação de câmera, F)

--> Place actors e diferentes opções de objetos prontos

---
### Aula 2 - Criação de cenário, geometria, edição de geometria, materiais com e sem textura, vantagens de whiteboxing
*Aula prática, em laboratório*

-->  Diferentes actors prontos (cube, cyllinder, …)

-->  Breve explicação sobre objetos estáticos e light bakes, explicação das sombras, mostrar menu “Build” para corrigir problemas de iluminação;

--> Criação de pequeno cenário usando apenas as formas base;

--> Levantar problema: “e se eu quiser algo mais complexo?”

--> Apresentar geometria, formas de edição

--> Dinâmica: cada um deve parar um pouco e fazer um cenário. Eu faço um cenário também.

--> Problema: “Tá tudo muito branco”;


##### Criação de materiais com e sem texturas.

--> Com textura: só jogar a imagem num objeto.

--> Sem textura: botão direito → Material → Puxa input de Base Color → Create new parameter (ou similar) ou pesquisa por Vector Parameter → Define a cor

Pedir pros alunos fazerem a mesma coisa

Vantagens de whiteboxing
    
---

### Aula 3 - criação de terreno, textura para terreno

*Nessa aula, é mostrada uma forma de se criar terrenos e pintar com texturas*

##### Criação de texturas para terreno

--> Criar novo material;

--> Adicionar node: Landscape Layer Blend;

--> Selecionar Landscape Layer Blend, criar novas camadas;

--> Adicionar Texture Sample (nodes); (mostrar atalho T + clique)

--> As texturas levam para o Layer Blend, que leva para o Base Color;

--> Repetir para todas as propriedades (Roughness, Normal, …)

--> Adicionar um Landscape Coords e levar aos UVs das texturas;
    
##### Criação de terrenos

--> Criar terreno (Landscape);

--> Mostrar opções de customização na criação de terreno;

--> Selecionar o material criado;

--> Demonstrar as ferramentas disponíveis;

--> Modelar algo agradável.


##### Utilizando as texturas

--> Landscape Tools → Paint

--> Criar Target Layers, escolhendo a opção Weight-Blended Layer;

--> Criar uma Target Layer para cada textura;

    
##### Outras opções

--> É possível clicar com o botão direito em uma Layer e escolher a opção “Fill Layer”;

--> No material, em Landscape Coords, é possível mudar a escala.


---

### Aula 4 - criação de Blueprints

*Apresentação do conceito de Blueprints, criação de uma porta animada com Timeline*

---

### Aula 5 - variáveis e referências

*Melhorando o sistema de porta*

--> Variáveis: todos sabem o que são?

--> Referência: forma de um objeto se comunicar com outro

--> Criar um switch/botão no chão

--> Na porta: Criar uma variável booleana pública: "TaFechada". Mostrar como mudar o tipo de variável.

--> Após Cast para Player: Branch. Usar "TaFechada". Fazer a mesma coisa no "On End Overlap".

--> Criar uma Blueprint para o Trigger (Switch), estilizar, colocar Box Collision

--> Nova variável do tipo "DoorBP", e essa referência permite que a gente use as funções e variáveis da blueprint da porta. É importante "completar" a referência, ou seja, dizer QUAL é a porta que a gente está referenciando.

--> Para fazer isso: vai no Switch que tá no mundo e coloca a porta correta lá.

--> Para um pouco de feedback, você pode adicionar sons, efeitos visuais, algo na interface de usuário

---

### Otimizando a Unreal Engine

*Importante para PCs com baixo desempenho*

--> Epic Games Store/Launcher -> Biblioteca -> Opções -> Plataformas-alvo -> Desmarca plataformas que não vai usar

--> Na engine: Settings -> Engine Scalability Settings -> Low

--> Não usar luzes dinâmicas, desligar luzes que não sejam absolutamente necessárias

--> Não fazer o BUILD LIGHT completo, fazer por partes

--> Desativar sombras dos objetos

--> Se você trabalha com laptop/notebook, deixar ele sempre na tomada

--> Para quem quer fazer um upgrade, a ordem, DE FORMA GERAL, é: 

* SSD

* GPU ou memória RAM
  
* CPU + placa-mãe

AMD Ryzen 5 3600, GTX 1060 6GB, 16GB RAM, SSD NVMe

---

### Revisão 1

*Criação de cenário, geometria, materiais (com e sem textura), explicação blueprints, criando uma blueprint, variáveis e referências*

---

### Aula 6 - reforço Blueprints: moedas, pontuação, desbloqueio de portas

*Nessa aula, é criado um pequeno sistema de coleta de moedas, onde as moedas são coletadas quando o jogador encosta nelas. O jogador guarda uma variável que conta as moedas. O sistema também conta com portas que se abrem (animação ou destruição) quando o jogador possui a quantidade correta de moedas*

--> Criar uma Moeda_BP com cilindro e material de ouro, passo-a-passo;

--> Atribuir o material e adicionar o componente Box Collision, editando o tamanho para ficar compatível com a moeda

--> Adicionar um evento de OnOverlap;

--> Ao colidir com a moeda, é impressa uma mensagem e a moeda é destruída;

--> Criar um contador de moedas no jogador, que deve ser acessado publicamente;

--> Mostrar a importância do 'Cast to': não só a gente identifica quem é que está colidindo com a moeda, mas a gente também ganha acesso às funções desse objeto, sem ter que ter preparado uma referência antes;

--> A partir do Cast To, incrementamos a variável;

--> Imprimir a quantidade total de moedas;

--> Possivelmente mencionar que *talvez* não seja o ideal fazer esse incremento a partir da moeda, já que isso é algo que o Player deveria fazer, mas por enquanto a gente deixa assim;

--> Agora, podemos pensar em melhorar nosso sistema, criar um uso para essas moedas;

--> Criar uma Porta_BP que tem a porta e moldura, e quando o jogador colidir com o Box Collision presente, caso tenha mais moedas do que é necessário (3), a porta é destruída;

--> Por fim, transformar esse requerimento de moedas em uma variável pública, e criar diferentes portas com valores de destruição diferentes.

---

### Aula 7 - Open Level

--> Criar um Level Novo, adicionar: BP_Sky_Sphere, Cube (chão), Directional Light, SkyLight

--> No Blueprint: Open Level by Reference - coloca o level novo

---

### Aula 8 - Interface de Usuário

--> Menu de criação: User Interface -> Widget Blueprint

--> Opções de interface/resolução no canto superior

--> Janelas Designer/Graphs 

--> Palette - diversas opções de criação

--> Adicionar Text, opções/details, âncora

--> Criar Binding (Função): Update Score

--> Update Score: Get Player Character -> Cast to 3rd -> As 3rd Get Moedas -> Append String -> Return

--> Fazer o mesmo com um HP, criar variável antes no 3rd Person e tudo mais

--> Sistema de sofrer dano (mesma coisa que moedas, mas aplica dano no personagem)

--> Se chegar em 0 ou menos, delay e recarrega cena

--> Poção de HP para recuperar até HP máximo

--> Criar portal que checa quantidade de moedas e leva para um novo Level

---

### Aula 9 - Packaging, empacotamento, build (última aula antes da P1)

--> É um processo que serve para transformar nosso projeto em um pacote, jogável sem o editor

--> Mapa inicial: Settings -> Maps & Modes -> Game Default Mode

--> Target Platform: Settings -> Supported Platforms, Target Hardware

--> Editor Viewport: Settings -> Preview Rendering Level -> Escolhe

--> File -> Package Project -> Zip Up Project

---

### Aula 10 - UE5 

---
### Aula 10 - Criando personagem do zero

--> Baixa personagem (com esqueleto) e animações no Mixamo

--> Importa sem mexer nada, apresenta arquivos

--> Importa animações, especifica o esqueleto

--> Character BP (tipo: Character)

--> Skeletal Mesh: personagem baixado

--> Seleciona a CapsuleComponent, faz ajustes para o personagem caber legal

--> No mesh: Anim Class

--> Botão direito no Content Browser -> Animation -> Animation BP, escolhe o esqueleto

--> Cria mais um arquivo: Animation -> BlendSpace1D

--> Joga as animações no BlendSpace (0, 50, 100)

--> Asset Details -> Axis Settings -> Name: Velocidade, Maximum Axis Value: 400? 600? 500.

--> Anim Graph: criar State Machine, linkar ao resultado.

--> Duplo clique na máquina de estados -> Asset Browser -> Blend

--> Velocidade: promover variável, torna pública

--> Volta pra máquina de estados, puxa o pulo, liga as duas animações, entra na transição, promove a variável bool, TáPulando, mesma coisa na debaixo, mas usa um NOT

--> Na máquina de estados: Event Graph -> Event Blueprint Update Animation  -> IsValid -> Try Get Pawn Owner -> Is Valid: Speed -> Movement Component -> Get Velocity -> Get VectorLength -> Set Speed ^ 

--> Com o Get Movement Component -> Is Falling -> Set Is In Air

--> Volta no BP do personagem, Anim Class: PersonagemAnimBP

--> INPUT: TRABALHAR COM INPUT MAPPINGS, COPIAR DO 3RD PERSON POR ENQUANTO

--> GameMode: troca o ThirdPersonCharacter pelo personagem novo, pode deletar o personagem antigo. World Settings: GameMode Override: ThirdPersonGameMode

--> No personagem: Spring Arm, bota uma câmera filha, sobe o spring arm, aumenta o braço

--> Opções: Use Pawn Control Rotation SIM (SpringArm) --- no CharMovement: Orient Rotation to Movement --- ClassDefaults: Use Controller Rotation Yaw NÃO



---

### Aula 12 - IA

---

### Aula 13 - P2

Criação da atividade

Explicação, dúvidas sobre a P2

Sobre o conteúdo visto: fundamentos básicos, interface da Unreal, criação de objetos, texturas, materiais, terreno, Blueprints, programação na Unreal, variáveis e referências, carregamento de nível, interface de usuário, empacotamento, personagem com movimentação e animações do zero, inteligência artificial, timeline, restart level, linetrace, sistema de hp, colisores, e por aí vai

Interface de usuário: jogo de tiro que você fica sem bala e tem que recarregar: é necessário botar na HUD. jogo que vc tem que coletar moedas: indicador de quantas moedas vc tem, quantas tem no cenário, por aí vai

Condições de vitória

Dúvidas sobre mecânicas vistas em aula


Conteúdos alternativos: ranking (tempo, placar, etc.), outro personagem seguindo player, pause, arma em terceira pessoa, save/load, animation slot, 

### Referências

[Make Games With Katie UE4 Beginner’s Tutorial](https://www.youtube.com/watch?v=iTwxuahe5B4](https://www.youtube.com/watch?v=iTwxuahe5B4)
[Mateus Quadros](https://www.youtube.com/c/MateusQuadros/videos)
[Evil Cube Example](https://www.youtube.com/watch?v=QJpfLkEsoek)

[https://www.youtube.com/playlist?list=PLpZBns8dFbgwXYMrgvZ0H0vDsq4o9YbkQ](https://www.youtube.com/playlist?list=PLpZBns8dFbgwXYMrgvZ0H0vDsq4o9YbkQ)
[Introduction to Common UI](https://www.youtube.com/watch?v=TTB5y-03SnE)

  

Menu/HUD (https://www.youtube.com/watch?v=ygOO1vHsq5M, https://www.youtube.com/watch?v=UOHS3xx9EHw)

Full Games (https://www.youtube.com/playlist?list=PLM5xJtuLgIuyfyO_oYu5R3ACjUx9l2A8-)

Environment (https://www.youtube.com/playlist?list=PLsPHRLf6UN4m1LQhNlRM22np4-4bIcDa4)

Basics (https://docs.unrealengine.com/en-US/Basics/index.html)

Cursos (https://learn.unrealengine.com/home/library)

Nav Mesh/AI (https://www.youtube.com/watch?v=qu_5UJMjfd0)

Moedas/Pontuação ([https://www.youtube.com/watch?v=HScw_yhKl5c](https://www.youtube.com/watch?v=HScw_yhKl5c))

Unreal Hour of Code ([https://www.youtube.com/watch?v=rAVPEGnyatk](https://www.youtube.com/watch?v=rAVPEGnyatk))

  

Unreal Official Tutorials

> Blueprint Kickstart (https://www.unrealengine.com/en-US/onlinelearning-courses/blueprint-kickstart?sessionInvalidated=true)

> Blueprint Essential Concepts (https://www.unrealengine.com/en-US/onlinelearning-courses/blueprints---essential-concepts?sessionInvalidated=true)

> Blueprint and Gameplay for Game Designers (https://www.unrealengine.com/en-US/onlinelearning-courses/blueprints-and-gameplay-for-game-designers)

> Introducing Unreal Engine (https://www.unrealengine.com/en-US/onlinelearning-courses/introducing-unreal-engine)

> Your First Hour with Unreal Engine (https://www.unrealengine.com/en-US/onlinelearning-courses/your-first-hour-with-unreal-engine)

> Building Worlds ([https://docs.unrealengine.com/en-US/BuildingWorlds/index.html](https://docs.unrealengine.com/en-US/BuildingWorlds/index.html))

  

[https://docs.unrealengine.com/4.27/en-US/Basics/GettingStarted/](https://docs.unrealengine.com/4.27/en-US/Basics/GettingStarted/)

  

: Mais recursos :

1. Curso UE4 Udemy (https://www.udemy.com/course/curso-de-game-com-unreal-engine-4/learn/lecture/17333428#overview)

2. UE4 Blueprint Tutorial (https://www.youtube.com/watch?v=icR_EgXrS6o&list=PLsPHRLf6UN4k0YIcWFAgjG3SXuMWl-A3h&index=11)

3. UE4 Hour of Code Platformer (https://www.youtube.com/watch?v=rAVPEGnyatk)

4. Teaching & Learning Blueprints (https://www.youtube.com/watch?v=_oeBkRk3XIg)

5. Being an Unreal Engine Programmer (https://www.youtube.com/watch?v=PWc54yD9HwU)

6. [Playlist] UE4 Educator (https://www.youtube.com/playlist?list=PLZlv_N0_O1gbDlbg31JdDl-PTE2DDl_v4)

7. Variable & References (https://www.youtube.com/watch?v=01dEzec8bmo) + Todos os vídeos dela

8. Niagara Fire (https://www.youtube.com/watch?v=rKIqa_IUkBo)

9. Niagara Effects ([https://www.youtube.com/c/cghow/videos](https://www.youtube.com/c/cghow/videos))

  

- interface (curso gameplay designer)

[https://www.unrealengine.com/en-US/blog/the-15-best-online-courses-to-learn-unreal-engine](https://www.unrealengine.com/en-US/blog/the-15-best-online-courses-to-learn-unreal-engine)

UE5: [https://www.youtube.com/watch?v=DtCmVFqNf58](https://www.youtube.com/watch?v=DtCmVFqNf58)

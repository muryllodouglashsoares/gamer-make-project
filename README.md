# 🎮 Woman Importance

> Um jogo de ação *top-down* feito em **GameMaker** sobre respeito e igualdade de gênero. Uma professora enfrenta, com lápis como munição, um aluno que acredita que "computador é coisa de menino".

![GameMaker](https://img.shields.io/badge/GameMaker-2024.14-black?logo=gamemaker)
![Linguagem](https://img.shields.io/badge/linguagem-GML-green)
![Gênero](https://img.shields.io/badge/gênero-boss%20fight-red)
![Plataforma](https://img.shields.io/badge/plataforma-Windows-blue)

![Fase inicial](screenshots/fase_inicial.png)

---

## 📖 Sobre o jogo

Na sala de aula, **Pedro** debocha de **Ana** por ela querer participar da aula de computação. A **Prof. Clara** intervém, lembrando que mulheres foram cientistas, líderes e heroínas, e decide dar uma lição ao aluno.

O jogo mistura narrativa em *cutscenes* com uma **batalha de chefe em três fases**. Ao vencer, Pedro reconhece o erro, pede desculpas e a mensagem final fecha a história:

> *Respeitar as mulheres é construir um mundo melhor para todos.*

---

## 📸 Capturas de tela

| | |
|---|---|
| ![Cutscene inicial](screenshots/cutscene_inicial.png)<br>**Cutscene inicial:** Pedro debocha de Ana na sala de aula | ![Fase inicial](screenshots/fase_inicial.png)<br>**Fase inicial:** rajadas circulares de projéteis do chefe |
| ![Mobs](screenshots/mobs.png)<br>**Mobs:** caveiras e borboletas surgem com HP ≤ 75% | ![Fase final](screenshots/fase_final.png)<br>**Fase final:** cavaleiros perseguem a jogadora e o chefe fica mais agressivo |
| ![Fim de jogo](screenshots/end_game.png)<br>**Fim de jogo:** a mensagem final de respeito e igualdade | |

---

## 🕹️ Controles

| Ação | Teclado / mouse | Controle (gamepad) |
|---|---|---|
| Mover | `W` `A` `S` `D` ou setas | Analógico esquerdo / direcional |
| Mirar | Mouse | Analógico direito (zona morta configurável) |
| Atirar lápis | `Espaço` ou botão esquerdo | `RT` |
| Esquivar | `Shift` ou botão direito | `A` |
| Rajada de lápis | `R` | `X` |
| Escudo do Saber | `C` | `Y` |
| Pulso de concentração | `V` | `B` |
| Trocar lápis | `1`-`4`, `Q`/`E`, roda do mouse | `LB` / `RB` |
| Pausar | `Esc`, `P`, `Backspace` | `Start` |
| Menus / diálogos | `W`/`S`/`A`/`D`, `Enter`, clique | Direcional/analógico, `A` confirma, `B` volta |
| Tela cheia / som | `F` `G` `F11` / `M` | — |

O teclado e o mouse continuam funcionando com o controle conectado; conexão e desconexão são detectadas sem interromper a partida. **Não há remapeamento de teclas** (ver limitações).

---

## ⚔️ Mecânicas

### Jogadora (Prof. Clara)
- **100 HP**, com regeneração de 5 HP a cada 5 segundos.
- Atira lápis na direção do mouse (**20 de dano** por acerto).
- Após receber dano de inimigos, fica invulnerável por 1 segundo.
- **Esquiva** (`Shift`): ~180 px em 9 frames, recarga de 1,25 s e proteção durante o movimento.
- Os lápis também **anulam as bolas de fogo** do chefe e param nas tochas.
- Limitada à área da arena, com tochas nas bordas funcionando como obstáculos.

### Chefe (Pedro)
O chefe tem **1000 HP** e dispara rajadas circulares de projéteis. A luta muda conforme a vida dele diminui:

| Fase | Gatilho | O que acontece |
|---|---|---|
| **1** | Início | O chefe patrulha, **avisa** o ataque (círculo se fechando), dispara 3 anéis de projéteis e fica vulnerável por um instante |
| **2** | HP ≤ 75% | Chefe pausa os ataques e reaparece no centro; surgem **mobs** que perseguem a jogadora e **borboletas** |
| **2b** | HP ≤ 50% | As borboletas somem e entram **serras** quicando pela arena |
| **3** | HP ≤ 25% | As serras somem e entram **cavaleiros** perseguidores; o chefe ganha novo visual, dispara anéis mais densos e um leque mirado |

### Perigos da arena
| Perigo | Dano à jogadora |
|---|---|
| Projétil do chefe | 10 |
| Mob | 5 |
| Borboleta | 5 |
| Serra | 10 |
| Cavaleiro | 10 |
| Bloco caindo (avisado antes) | 10 |

Derrotar o chefe leva à cutscene final; zerar o HP leva à tela **"VOCÊ MORREU"**, onde `Enter` reinicia a luta.

---

## 🆕 Novidades da rodada "expansão e polimento"

- **Habilidades da Prof. Clara** (HUD no canto inferior esquerdo, com recarga): **Rajada de lápis** (5 lápis em leque, 6 s), **Escudo do Saber** (2,5 s anulando projéteis do chefe, 12 s) e **Pulso de concentração** (afasta mobs e cavaleiros, sem atravessar tochas nem sair da arena; não afeta o chefe, 10 s). Parâmetros em `global.cfg.hab_*`.
- **Chefe**: ataques variados em ciclo (anel, leque mirado, espiral; fase final com ataque misto), **janela de vulnerabilidade** após cada ataque (dano x1,5, configurável em `vuln_mult`, indicador "VULNERÁVEL!" e brilho azul).
- **Dificuldade** (História / Normal / Desafio): altera avisos, intervalos, velocidade dos projéteis, janelas de recuperação, dano recebido, quantidade e velocidade dos inimigos. Não multiplica a vida do chefe e mantém avisos mínimos.
- **Pontuação e nota**: sequência de acertos, bônus por esquiva precisa, resumo ao fim (tempo, dano causado/recebido, precisão, esquivas, nota S/A/B/C).
- **Conquistas** (14) e **recordes por dificuldade**, **estatísticas históricas** e **Códice** com 7 páginas (Ada Lovelace, Katherine Johnson, Carol Shaw, Grace Hopper, Mary Jackson, Hedy Lamarr, Marie Curie): três vêm da coleta na luta; as demais por desafios (vencer, sequência de 10 acertos, 5 esquivas precisas, vencer sem morrer).
- **Narrativa**: diálogo extra com a Ana em 50% de vida, falas curtas durante a luta (legendas que não congelam o jogo), epílogo com Ana participando da aula e Pedro mudando de atitude.
- **Revanche** (após concluir a campanha): só a luta ou com a história, escolhendo a dificuldade; não repete recompensas.
- **Tutorial interativo** (menu): movimento, mira/tiro, esquiva, avisos de ataque, habilidades e barra de vida; sem dano, repetível.
- **Opções/acessibilidade**: volume geral, música e efeitos separados, reduzir flashes e partículas, alto contraste, velocidade do texto (inclui instantâneo), zona morta da mira, apagar progresso (com confirmação).
- **Salvamento** em JSON (`woman_importance.sav`, pasta de dados do GameMaker): áudio, acessibilidade, dificuldade, conquistas, códice, recordes e estatísticas. Versionado (`SAVE_VERSAO`), tolera arquivo ausente/corrompido/campos antigos, grava ao desbloquear, ao fechar opções/pausa e ao fim da luta.

### Limitações conhecidas
- **Nada disto foi compilado nem executado**: o ambiente em que foi escrito não tem o GameMaker. A verificação foi estática (parênteses/chaves balanceados e todas as funções chamadas existem). Abra no GameMaker 2024.14+, rode (F5) e reporte erros.
- Sem remapeamento de teclas (a tela "Como jogar" mostra os controles atuais).
- O jogo não tem tremor de tela, então não há opção para isso; "reduzir flashes" corta partículas, vinheta de dano e piscadas do chefe.
- Sem ponto fraco localizado: a vulnerabilidade vale para o chefe inteiro durante a recuperação.
- Biografias do códice escritas de fatos conhecidos e conservadores, **sem nova checagem online**; confira as fontes citadas antes de publicar.
- Sons novos reutilizam os efeitos existentes (sem áudios novos para códice/habilidades).

### Estrutura nova
`scripts/src_entrada` (teclado/mouse/gamepad), `src_save` (persistência), `src_progresso` (dificuldade, pontuação, códice, falas, habilidades, tutorial), `src_telas` (opções, códice, progresso, resumo, controles). `obj_menu` foi reescrito (telas internas); `obj_controle`, `obj_boss`, `obj_player`, `obj_arma` e outros receberam integrações.

---

## 🆕 Melhorias desta versão
- **Combate**: lápis em passos curtos (sem atravessar inimigos), param nas tochas, mira com retículo, efeitos de impacto/partículas, inimigos piscam ao serem atingidos (mobs e cavaleiros agora aguentam 3 acertos).
- **Chefe**: máquina de estados (patrulha → aviso → ataque → recuperação), transições de fase que ocorrem uma única vez, com banner, som e pausa de impacto.
- **Justiça**: inimigos nascem piscando e inofensivos, longe da jogadora; blocos caindo têm aviso; bugs de borboletas/serras presas fora da sala corrigidos.
- **Experiência**: contagem "PREPARE-SE", painel de controles que se marca sozinho, pausa completa, volume/mudo, esquiva com HUD de recarga.
- **Áudio**: efeitos e músicas **sintetizados por script** (placeholders em `sounds/`); substitua pelos seus arquivos mantendo os nomes dos recursos.
- Todos os valores de balanceamento ficam em `global.cfg` (`scripts/src_jogo`).

---

## 🧭 Fluxo do jogo

```
Menu ──Enter──▶ Cutscene de introdução ──▶ Arena do chefe ──┬─▶ Cutscene final ──▶ Menu
                                                              └─▶ Tela de morte ──Enter──▶ Arena do chefe
```

---

## 🛠️ Tecnologias

- **[GameMaker](https://gamemaker.io/)** (projeto criado na IDE `2024.14.4`)
- **GML** (GameMaker Language)
- Sprites e tilesets em pixel art
- Resolução de janela de 1280×720, rodando a 60 FPS

---

## 🚀 Como executar

### Pré-requisitos
- [GameMaker](https://gamemaker.io/en/download) instalado (versão 2024.14 ou superior recomendada)

### Passo a passo
1. Clone o repositório:
   ```bash
   git clone https://github.com/muryllodouglashsoares/gamer-make-project.git
   ```
2. No GameMaker, use **File ▸ Open** e abra o pacote **`.yyz`** mais recente (pacote do projeto; o GameMaker oferece extraí-lo). A pasta `projeto-extraido/` contém os mesmos arquivos soltos, com o `SNCT_att.yyp`.
3. Pressione **F5** (ou clique em ▶ *Run*) para compilar e jogar.

---

## 📁 Estrutura do projeto

```
├── objects/        # Lógica do jogo (jogador, chefe, inimigos, cutscenes, menu...)
├── rooms/          # Salas: menu, cutscene, arena do chefe, tela de morte
├── scripts/        # Funções auxiliares (cenas/diálogos, balas, approach)
├── sprites/        # Animações dos personagens, projéteis, cenários e cenas
├── tilesets/       # Conjuntos de tiles da arena
├── fonts/          # Fonte dos diálogos
├── options/        # Configurações por plataforma (Windows, Opera GX, Reddit)
├── screenshots/    # Capturas de tela usadas neste README
└── woman-importance.yyp
```

### Principais objetos
| Objeto | Responsabilidade |
|---|---|
| `obj_player` | Movimento, esquiva, vida, animações e colisões do jogador |
| `obj_controle` | Pausa, tutorial, avisos de fase, mira, efeitos e fim de partida (criado pela jogadora) |
| `obj_arma` / `obj_balaplayer` | Disparo dos lápis e dano causado |
| `obj_boss` | IA do chefe, fases, HUD da barra de vida |
| `obj_mob`, `obj_cavaleiro` | Inimigos que perseguem o jogador |
| `obj_borboleta`, `obj_serras` | Inimigos que se movem pela arena |
| `obj_spawner` / `obj_bloco_caindo` | Blocos que caem aleatoriamente do topo |
| `obj_cutscene` | Diálogos com efeito de máquina de escrever |
| `obj_menu` / `obj_morte` | Tela inicial e tela de derrota |

### Scripts
- **`src_cenas`**: define os diálogos (`cenas_intro`, `cenas_final`) e inicia cutscenes com `cena_iniciar`.
- **`src_jogo`**: configuração de balanceamento (`global.cfg`), áudio, partículas, pausa/hit-stop, dano da jogadora, `bala_acertou` e as funções da IA do chefe.
- **`Script1`**: função `approach`, usada na barra de vida do chefe.

---

## ✏️ Personalizando

Quer adicionar ou editar diálogos? Altere as funções em `scripts/src_cenas/src_cenas.gml`:

```gml
{ img: spr_cena_1, quem: "Ana", txt: "Seu texto aqui..." }
```

---

## 🗺️ Ideias futuras

- [ ] Trilha sonora e efeitos sonoros
- [ ] Mais fases e outros chefes
- [ ] Suporte a gamepad
- [ ] Build para outras plataformas

---

## 👤 Autor

Desenvolvido por **Muryllo Douglas**
GitHub: [@muryllodouglashsoares](https://github.com/muryllodouglashsoares)

---

## 📄 Licença

Este projeto está sob a licença descrita no arquivo [LICENSE](LICENSE).

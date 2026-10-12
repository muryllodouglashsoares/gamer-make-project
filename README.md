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

| Tecla / ação | Função |
|---|---|
| `W` `A` `S` `D` (ou setas) | Mover a Prof. Clara (mesma velocidade nas diagonais) |
| `Espaço` | Atirar lápis (na direção do mouse) |
| `Mouse` | Mirar |
| `Enter` | Iniciar o jogo (menu) / reiniciar após morrer |
| `Espaço`, `Enter` ou clique | Avançar os diálogos das cutscenes |
| `F` / `G` / `F11` | Tela cheia / janela (funciona em qualquer tela) |
| `Shift` ou botão direito | Esquivar (curta, com recarga e proteção temporária) |
| `Esc`, `P` ou `Backspace` | Pausar (continuar, volume, som, reiniciar luta, menu principal) |
| `M` | Silenciar / reativar o som |
| Botão esquerdo | Também atira (alternativa ao `Espaço`) |

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
2. No GameMaker, use **File ▸ Open** e abra **`SNCT_att_ataques_OFC.yyz`** (pacote do projeto; o GameMaker oferece extraí-lo). A pasta `projeto-extraido/` contém os mesmos arquivos soltos, com o `SNCT_att.yyp`.
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

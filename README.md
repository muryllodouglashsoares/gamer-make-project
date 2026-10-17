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
Menu ─▶ Dificuldade ─▶ Introdução ─▶ Confronto 1 (Pedro) ─▶ Resultado + melhoria ─▶ Confronto 2 ─▶ Resultado + melhoria ─▶ Confronto 3 ─▶ Final ─▶ Resumo ─▶ Menu
                                           └─ derrota ─▶ Tela de morte ─▶ repete o mesmo confronto
```

---

## 🆕 Campanha de 3 confrontos, novos chefes e melhorias

O jogo agora é uma pequena campanha. **Nenhuma parte foi executada no GameMaker pelo autor desta atualização:** o código foi revisado de forma estática (veja "Verificação" abaixo) e precisa ser aberto e testado na IDE.

### Fluxo

`Menu → dificuldade → introdução → Confronto 1 (Pedro) → resultado + melhoria → Confronto 2 (Guardião do Preconceito) → resultado + melhoria → Confronto 3 (Autômato da Exclusão) → final → resumo da campanha`

- A dificuldade escolhida no menu vale para toda a campanha (nada muda silenciosamente).
- Em cada confronto aparecem "CONFRONTO n DE 3", o nome do chefe e o objetivo na contagem inicial; um rótulo fica no canto superior esquerdo durante a luta.
- **Derrota:** a tela de derrota mostra o chefe e o confronto; "Tentar novamente" repete o mesmo confronto, sem avançar a campanha e sem repetir melhorias. A nota de cada confronto só penaliza as derrotas *daquele* confronto.
- Cada vitória é somada uma única vez (há travas em `campanha_registrar_vitoria` e na escolha de melhoria).
- Voltar ao menu encerra a campanha em andamento. **A campanha em andamento não é salva:** se fechar o jogo no meio, começa de novo.
- Tutorial e revanche nunca iniciam a campanha.

### Chefes

| Confronto | Chefe | Resumo |
|---|---|---|
| 1 | **Pedro** | Batalha original, inalterada (3 fases, ataques, inimigos auxiliares, blocos). |
| 2 | **Guardião do Preconceito** (1100 HP) | Desliza entre pontos da arena longe da jogadora. Ataques: *rótulos* (leques mirados lentos e anel), *faixas* (duas ondas de faixas verticais; a 2ª cobre as brechas da 1ª), *muros* (muros temporários que bloqueiam a arena e protegem dos projéteis), *cerco* (muros + leques mais rápidos), *pinça* (bordas e depois o centro). Quando o ataque acaba, os muros caem e abre-se a janela de vulnerabilidade. Fases em 66% e 33% de vida. |
| 3 | **Autômato da Exclusão** (1200 HP) | Orbita o centro. Ataques: *salva* (rajadas mirando onde a jogadora vai estar, com linha de mira), *grade* (faixas cruzadas com espaço livre), *engrenagem* (projéteis que curvam), *sobrecarga* (anéis densos com brecha; aviso longo; o Escudo ou a esquiva resolvem), *combo* (grade + salvas, fase final). **Mecânica especial:** nas fases 2 e 3 ele fica **blindado** até a jogadora quebrar 3 módulos de energia (a Rajada ajuda); ao quebrar o escudo ele fica atordoado e vulnerável por mais tempo. Fases em 66% e 33%. |

Os dois são personagens fictícios. Reutilizam a máquina de estados de `obj_boss` (são objetos-filho): entrada, patrulha, preparando, atacando, recuperando, transição e derrotado. "Recuperando" é a janela de vulnerabilidade (dano x1.5). Os avisos têm tempo mínimo (`zona_aviso_min`, `tele_min`) em todas as dificuldades e não dependem só de cor: hachura diagonal, ícone "!" ou "MURO", texto de alerta e linha de mira. Nos confrontos 2 e 3 não caem blocos, para os avisos ficarem legíveis; cada confronto tem tochas extras e um visual próprio (tinta das camadas e decoração do piso).

### Melhorias (bônus temporários da campanha)

Após vencer os confrontos 1 e 2, a tela de preparo oferece 3 melhorias (uma de cada categoria) e é obrigatório escolher uma, com confirmação. Não há duplicatas na mesma campanha. Valores em `global.cfg.mel` (`src_jogo`); os efeitos são aplicados por `campanha_aplicar_melhorias()` sobre os valores originais, então nunca se acumulam por engano.

| Categoria | Melhoria | Efeito real |
|---|---|---|
| Sobrevivência | Reserva de vida | Vida máxima 100 → 120 |
| Sobrevivência | Recuperação aprimorada | Cura 7 a cada 4,25 s (antes: 5 a cada 5 s) |
| Combate | Precisão aprimorada | Dano do lápis 20 → 25 |
| Combate | Rajada reforçada | Rajada dispara 7 lápis (antes: 5) |
| Mobilidade e defesa | Esquiva aprimorada | Recarga da esquiva 1,25 s → 0,92 s (a proteção continua só durante o movimento) |
| Mobilidade e defesa | Escudo otimizado | Escudo dura 2,5 s → 3,2 s e recarrega em 10,5 s (antes: 12 s) |

Há limites máximos/mínimos em `cfg.mel.lim`. A **revanche** e o tutorial usam sempre os valores originais (sem melhorias).

### Revanche

Depois de vencer um confronto ele fica liberado na revanche (quem já tinha concluído o jogo antes mantém a revanche contra o Pedro). Com mais de um chefe liberado aparece a escolha do chefe. "Só a luta" ou "com a história". A revanche não concede melhorias. O duelo isolado com o Pedro continua tendo recordes próprios; a revanche dos outros chefes não altera recordes.

### Salvamento (versão 2)

- `SAVE_VERSAO` passou de 1 para 2. Campos novos com valores padrão seguros: `rec_pedro` (recordes do duelo com o Pedro) e `campanha` (`concluida`, `vitorias`, `chefes` [0/1 por confronto], `melhorias_usadas`, só histórico: não concede bônus).
- `rec` agora guarda os recordes da **campanha completa** (tempo total e média dos 3 confrontos para a nota).
- **Migração v1 → v2** (`save_migrar`): o `rec` antigo vai para `rec_pedro`; `campanha_completa` verdadeiro marca o Pedro como derrotado. Opções, conquistas, códice e estatísticas são preservados pela mesclagem existente. Não foi possível reproduzir um arquivo `.sav` real aqui; a migração só foi revisada no código.
- Nada de instâncias ou IDs temporários é salvo.

### Arquivos novos e alterados

- **Novos:** `scripts/src_campanha` (estado, melhorias, fluxo, arena, HUD), `scripts/src_chefes` (IA dos dois chefes), `obj_boss2`, `obj_boss3`, `obj_zona`, `obj_muro`, `obj_modulo`, `obj_decor`, `obj_preparo`, `rm_preparo`, sprites `spr_guardiao`, `spr_guardiao_atq`, `spr_automato`, `spr_automato_atq`, `spr_muro` (pixel art gerada por script, com 4 quadros de animação).
- **Alterados:** `src_jogo` (balanceamento novo, limpeza no fim da luta, blindagem do chefe, painel de cientista só na 1ª vez), `src_progresso` (`partida_encerrar` por confronto), `src_save` (v2 e migração), `src_telas` (recordes e resumo), `src_cenas` (cenas dos novos confrontos), `obj_boss` (redireciona para o chefe do confronto), `obj_player` (aplica melhorias), `obj_controle`, `obj_menu`, `obj_morte`, `obj_spawner`, `obj_balaboss` (`giro` e `vida` opcionais).

### Verificação e limitações

- Feito: revisão estática (chaves/parênteses balanceados, todas as funções chamadas existem no projeto ou são nativas do GML, `.yy` novos validados como JSON e comparados com recursos existentes, registro no `.yyp`).
- **Não feito:** compilar e executar no GameMaker; testes de jogo (fluxo completo, derrotas, dificuldades, gamepad, pausa, salvamento real). Isso precisa ser validado na IDE.
- Se o GameMaker reclamar de algum recurso novo ao abrir, o `.resource_order` do projeto é regenerado automaticamente.
- Balanceamento (HP, avisos, dano) não foi jogado; ajuste em `global.cfg` (`boss2`, `boss3`, `mel`).

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

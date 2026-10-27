# easy-building (26.3 — Fabric)

Port do [easy-building-minecraft-mod](https://github.com/marianolarre/easy-building-minecraft-mod) para
**Minecraft 26.3** no **Fabric**.

## Build

```powershell
.\gradlew.bat build
```

Saída em `build\libs\easy-building-26.3.0+fabric.jar`.

| | |
|---|---|
| Minecraft | 26.3 |
| Java | 25 |
| Fabric Loader | 0.19.5+ |
| Fabric API | 0.161.0+26.3 |
| Loom | 1.16-SNAPSHOT |

## Mudanças em relação ao port 26.2

O 26.3 **trocou LWJGL por SDL** (o `lwjgl-glfw` saiu do `version.json` e entrou o `lwjgl-sdl`), então
a tecla de atalho teve de ser migrada:

| 26.2 | 26.3 |
|---|---|
| `org.lwjgl.glfw.GLFW.GLFW_KEY_LEFT_ALT` | `InputConstants.KEY_LALT` |
| `InputConstants.Type.KEYSYM` | `InputConstants.Type.KEYBOARD` |

Todo o resto da renderização (`submitCustomGeometry` da feature rendering API) continua igual ao 26.2.

## Mudanças em relação ao mod original

- Renderização migrada para a API de features do 26.2+ (`LevelRenderEvents` + `submitCustomGeometry`).
- Linhas de pré-visualização mais grossas (mais visíveis).
- O quadrado de pré-visualização muda de cor conforme o destino:
  - **Branco**: posição livre e dentro do alcance.
  - **Vermelho**: fora de alcance.
  - **Laranja**: já existe um bloco que não pode ser substituído.
- `fabric.mod.json` com metadados reais (o original ainda tinha os placeholders do template do Loom).

## Crash de desconectar

Sair de um mundo deixava o "plane mode" ligado com `player` nulo, e o tick seguinte estourava um
`NullPointerException`. O tick agora limpa esse estado quando `player` ou `level` somem, e o modo
começa desligado no próximo mundo. O [`fix_easybuilding`](https://github.com/Mateus-repo/fix-easybuilding)
deixou de ser necessário.

## Licença

O mod original é MIT.

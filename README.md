# 🎧 Corrigindo microfones fantasmas no Linux com HDAJackRetask (ALSA Tools GUI)

Você já viu seu Linux detectar múltiplos microfones mesmo tendo apenas um? 😖 Esse tutorial mostra como eliminar essas “entradas fantasmas” usando o `hdajackretask`, uma ferramenta poderosa que permite reconfigurar as portas de áudio no nível do hardware.

---

## 📦 1. Instalação do ALSA Tools GUI

### Debian, Ubuntu, Linux Mint:
```bash
sudo apt update
sudo apt install alsa-tools-gui
```

## Arch Linux / Manjaro:
```bash
sudo pacman -S alsa-tools
```

## Fedora:
```bash
sudo dnf install alsa-tools-gui
```
> 💡 Obs: No Fedora, talvez você precise habilitar o repositório RPM Fusion.

## 🛠️ 2. Acessando o HDAJackRetask

Abra o terminal e execute:
```bash
sudo hdajackretask
```

## 🎚️ 3. Desativando entradas de áudio duplicadas (microfones “fantasmas”)

Depois de abrir o `hdajackretask`, siga este passo a passo para corrigir as entradas fantasmas detectadas incorretamente:

1. **Selecione seu codec de áudio**
   - Geralmente será algo como `Realtek ALCxxx` na lista no topo do programa.

2. **Habilite a visualização de pinos ocultos**
   - Marque a opção **"Show unconnected pins"** para exibir todos os pinos disponíveis, mesmo os que não estão conectados fisicamente.

3. **Identifique os pinos fantasmas**
   - Procure por pinos que aparecem como:
     - **"Not connected"**
     - Mas que estão definidos como funções de microfone (ex: “Mic Jack” ou “Black Mic”).

4. **Aplique o "Override"**
   - Para cada um desses pinos problemáticos:
     - Marque a caixa **"Override"**.
     - No menu suspenso ao lado, selecione **"Not Connected"**.

5. **Mantenha apenas o pino real do microfone ativado**
   - O microfone interno real costuma ser o `Internal Mic` (frequentemente Pin ID `0x12`).
   - **Não aplique override neste pino** se ele estiver funcionando corretamente.

6. **Aplicar mudanças**
   - Clique em **“Apply now”** para testar as alterações.
   - Em seguida, clique em **“Install boot override”** para que a mudança permaneça após reiniciar o computador.

> 💡 Dica: Se algo der errado, você pode abrir o `hdajackretask` novamente e reverter as alterações desmarcando os overrides aplicados.


![jack-config](https://github.com/user-attachments/assets/7b2f4cb2-6175-45f7-89d1-5daf52750436)




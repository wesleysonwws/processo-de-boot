## 🔄 Detalhamento do Processo de Boot do Linux

Esta seção descreve, passo a passo, o que acontece desde o momento em que o computador é ligado até o sistema Linux estar pronto para uso.

---

### 1️⃣ Power On & POST
O POST faz parte do processo executado pelo BIOS/UEFI.
Ao pressionar o botão de ligar, o computador recebe energia e o firmware inicia o **POST (Power-On Self-Test)**.

O POST é responsável por:
- Testar a memória RAM
- Verificar CPU
- Inicializar dispositivos básicos
- Garantir que o hardware essencial está funcionando

Caso algum erro crítico seja encontrado, o boot é interrompido.

---

### 2️⃣ BIOS / UEFI

Após o POST, o **BIOS ou UEFI** assume o controle do sistema.

Suas principais funções são:
- Detectar dispositivos conectados
- Definir a ordem de boot
- Localizar um dispositivo inicializável
- Carregar o bootloader na memória

Em sistemas modernos, o UEFI substitui o BIOS tradicional e utiliza a partição EFI.

---

### 3️⃣ Bootloader (GRUB)

O **GRUB (Grand Unified Bootloader)** é o carregador de boot mais comum no Linux.

Ele é responsável por:
- Exibir o menu de sistemas operacionais
- Carregar o kernel Linux (`vmlinuz`)
- Carregar o `initramfs`
- Passar parâmetros para o kernel

O GRUB é um dos primeiros softwares executados após o firmware.

---

### 4️⃣ Kernel (vmlinuz)

O **kernel Linux** é o núcleo do sistema operacional.

O arquivo `vmlinuz` é o kernel em formato compactado e contém:
- Gerenciamento de CPU
- Controle de memória
- Drivers essenciais
- Comunicação com hardware

Após ser carregado pelo GRUB, o kernel assume o controle total do sistema.

---

### 5️⃣ initramfs

O **initramfs** (Initial RAM Filesystem) é um sistema de arquivos temporário carregado na memória RAM.

Sua função é:
- Disponibilizar módulos essenciais
- Preparar o ambiente inicial
- Permitir que o kernel localize e monte o sistema de arquivos raiz (/)

Depois que o sistema raiz é montado, o initramfs é descartado.

---

### 6️⃣ Montagem do sistema de arquivos raiz (/)

Nesta etapa, o kernel monta o **root filesystem (/)**, que contém:
- Diretórios do FHS
- Binários essenciais
- Bibliotecas
- Arquivos de configuração

A partir desse ponto, o sistema já tem acesso ao ambiente Linux real.

---

### 7️⃣ systemd (PID 1)

Após montar o sistema raiz, o kernel inicia o **systemd**, que se torna o processo de número **PID 1**.

O systemd é responsável por:
- Inicializar serviços
- Gerenciar processos
- Controlar targets (níveis de execução)
- Garantir que o sistema chegue a um estado operacional

---

### 8️⃣ Serviços e Targets

O systemd ativa serviços conforme o target configurado, como:
- `multi-user.target`
- `graphical.target`

Exemplos de serviços:
- Rede
- Logs
- Login
- Interface gráfica (se houver)

---

### 9️⃣ Login e Sistema Pronto

Após todos os serviços necessários serem iniciados, o sistema apresenta:
- Tela de login (GUI ou terminal)
- Prompt de usuário

---
## 🧠 Resumo do Fluxo de Boot
Power On
  
↓

POST

↓

BIOS / UEFI

↓

GRUB

↓

Kernel (vmlinuz)

↓

initramfs

↓

/

↓

systemd (PID 1)

↓

Serviços

↓

Login

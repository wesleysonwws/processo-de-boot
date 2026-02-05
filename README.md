# Processo de Boot do Linux
Este repositório contém um estudo detalhado sobre o **processo de boot** em sistemas Linux — desde o momento em que o PC é ligado até o sistema estar pronto para uso.  
O objetivo é explicar cada etapa com clareza e exemplos simples, como um material de estudo pessoal e profissional.

---

## 📚 O que você encontrará aqui

- ✨ O que acontece ao ligar o computador
- 🛠️ BIOS/UEFI e POST
- 🚀 Bootloader (GRUB)
- 🧠 Kernel e initramfs
- ⚙️ systemd como PID 1
- 🧾 Diagramas e sequência do processo
- 📂 Estrutura do diretório /boot
- ⏱️ Análise do tempo de boot
- 🛠️ Troubleshooting e Recovery Mode
---

## 🧠 Visão geral do processo

O processo de boot do Linux segue as etapas abaixo:

1. **Power On & POST**
2. **BIOS / UEFI**
3. **Bootloader (GRUB)**
4. **Kernel (`vmlinuz`)**
5. **initramfs**
6. **Montagem do / (root filesystem)**
7. **systemd (PID 1)**
8. **Serviços e Targets**
9. **Login / Sistema pronto**
    
---
## 📂 Arquivos detalhados

**. 🔄 Detalhamento completo → boot-process.md**

**. ⚙️ Configuração do GRUB → config-grub.md**

**. 📂 Estrutura do /boot → boot-directory.md**

**. ⏱️ Análise de boot → boot-analysis.md**

**. 🛠️ Troubleshooting → boot-troubleshooting.md**

---
Todo o conteúdo técnico detalhado está documentado nos arquivos individuais deste repositório.

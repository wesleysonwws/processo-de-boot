# ⏱️ Análise do Tempo de Boot no Linux

Esta seção apresenta a análise prática do tempo de inicialização
do sistema Linux.

O objetivo é medir o tempo total de boot, identificar gargalos
e analisar serviços que impactam a inicialização do sistema.

---

## 🧠 Visão geral do tempo de boot

O tempo de inicialização do Linux é dividido em quatro etapas principais:

- **Firmware** → BIOS / UEFI
- **Bootloader** → GRUB
- **Kernel** → Inicialização do núcleo
- **Userspace** → systemd + serviços

---

## 🔧 Medindo o tempo total de boot

Para visualizar o tempo geral de inicialização, foi utilizado o comando:

```bash
systemd-analyze

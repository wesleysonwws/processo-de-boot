# 🛠️ Troubleshooting de Boot no Linux

Esta seção apresenta técnicas práticas de diagnóstico e resolução de falhas durante o processo de inicialização do Linux.

O objetivo é identificar problemas que impedem ou atrasam o boot do sistema, analisando logs, serviços, kernel e erros envolvidos na inicialização.

---

## 🧠 Visão Geral de Falhas de Boot

Falhas no processo de inicialização podem ocorrer em diferentes etapas:

- **Firmware (BIOS/UEFI)** → Hardware não detectado ou falha no POST  
- **Bootloader (GRUB)** → Sistema não carrega o kernel  
- **Kernel** → Kernel Panic ou travamentos  
- **Init / systemd** → Serviços falhando na inicialização  
- **Filesystem** → Partições não montadas  

Cada etapa exige métodos específicos de diagnóstico.

---

## 🚨 Sintomas Comuns

Alguns sinais indicam problemas no boot:

- Tela preta após ligar  
- Erros do GRUB  
- Kernel Panic  
- Travamento em “Starting …”  
- Boot extremamente lento  
- Entrada em Emergency Mode  
- Falha na montagem de discos  

---

## 🔎 Análise de Logs do Boot

A primeira etapa do troubleshooting é a verificação de logs.

### Boot atual

```bash
journalctl -b

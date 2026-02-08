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

Esses sintomas ajudam a identificar em qual etapa do boot
o problema está ocorrendo

---
## 🔎 Análise de Logs do Boot

A primeira etapa do troubleshooting é a verificação de logs.

### Boot atual

```bash
journalctl -b

---

Para visualizar somente mensagens de erro do boot atual:
journalctl -p err -b

Também é possível incluir avisos (warnings):
journalctl -p warning -b

Isso facilita a identificação de falhas críticas sem precisar analisar todo o log.


Para listar serviços que falharam durante a inicialização:
systemctl --failed

Esse comando exibe:
. Serviços que não iniciaram corretamente
. Estado atual
. Descrição da falha

É um dos principais comandos de troubleshooting com systemd.

Para investigar um serviço específico:
systemctl status nome-do-servico

Exemplo:
systemctl status docker.service

A saída mostra:

. Logs recentes do serviço

. Código de erro

. Tempo de execução

. Dependências envolvidas

O Kernel Panic é uma falha crítica onde o kernel não consegue continuar
a execução do sistema.

Sintomas comuns:

Tela preta com mensagens técnicas

Travamento total do sistema

Necessidade de reinicialização manual

Para analisar mensagens do kernel:

dmesg | less

Esse comando exibe logs gerados diretamente pelo kernel.


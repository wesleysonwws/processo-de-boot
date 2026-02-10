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

Esses sintomas ajudam a identificar em qual etapa do boot o problema está ocorrendo.

---
## 🔎 Análise de Logs do Boot

A primeira etapa do troubleshooting é a verificação de logs.

### Boot atual

    journalctl -b

#### Apenas erros do boot

    journalctl -p err -b


Também é possível incluir avisos:

    journalctl -p warning -b

Isso facilita a identificação de falhas críticas sem precisar analisar todo o log.

---

## ⚙️ Serviços que Falharam no Boot

Para listar serviços que falharam durante a inicialização:

    systemctl --failed

Esse comando exibe:

- Serviços que não iniciaram corretamente  
- Estado atual  
- Descrição da falha  

É um dos principais comandos de troubleshooting com systemd.

---

### Analisar serviço específico

    systemctl status nome-do-servico

Exemplo:

    systemctl status docker.service

A saída mostra:

- Logs recentes do serviço  
- Código de erro  
- Tempo de execução  
- Dependências envolvidas  

---

## 💥 Kernel Panic

O Kernel Panic é uma falha crítica onde o kernel não consegue continuar a execução do sistema.

### Sintomas comuns

- Tela preta com mensagens técnicas  
- Travamento total do sistema  
- Necessidade de reinicialização manual  

---

### Análise de mensagens do kernel

    dmesg | less

Esse comando exibe logs gerados diretamente pelo kernel, permitindo identificar drivers, falhas de hardware ou erros de inicialização.

---

## 🐢 Análise de Tempo de Boot

Para verificar o tempo total de inicialização:

    systemd-analyze

---

### Serviços mais lentos

    systemd-analyze blame

Lista os serviços que mais demoraram para iniciar.

---

### Cadeia crítica do boot

    systemd-analyze critical-chain

Mostra a sequência de serviços que impactam diretamente o tempo de boot.

---

## 💾 Problemas de Disco e Filesystem

Falhas em disco podem impedir o boot.

### Sintomas

- Entrada em Emergency Mode  
- Erros de mount  
- Falha ao carregar partições  

---

### Diagnóstico

    lsblk

    cat /etc/fstab

---

### Correção de filesystem

    fsck /dev/sda1

> Substituir pela partição correta conforme o ambiente.

---

## 🧰 Comandos Gerais de Diagnóstico

Ver versão do kernel em uso:

    uname -r

Listar arquivos de boot:

    ls /boot

Serviços carregados:

    systemctl list-units --type=service

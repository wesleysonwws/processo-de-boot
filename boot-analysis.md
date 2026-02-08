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
```

---

## 📊 Exemplo de saída

```
Startup finished in 5.321s (firmware) + 2.114s (loader) + 3.876s (kernel) + 12.445s (userspace) = 23.756s
```

---

## 🧾 Interpretação

- **Firmware** → Tempo gasto pelo BIOS/UEFI  
- **Loader** → Tempo do GRUB  
- **Kernel** → Inicialização do kernel  
- **Userspace** → Serviços e systemd  

O valor final representa o tempo total até o sistema ficar operacional.

---

## 🐢 Identificando serviços mais lentos

Para verificar quais serviços mais impactam o boot:

```bash
systemd-analyze blame
```
---

## 📊 Exemplo de saída do blame

```
8.432s NetworkManager.service
6.210s firewalld.service
4.115s dev-sda1.device
2.998s docker.service
1.554s sshd.service
```

---

## 🧾 Análise

O comando `systemd-analyze blame` lista os serviços em ordem do mais lento
para o mais rápido durante a inicialização.

Isso permite:

- Identificar gargalos de boot  
- Analisar serviços desnecessários  
- Otimizar o tempo de inicialização  

Serviços de rede e firewall costumam impactar significativamente
o tempo de boot, dependendo da configuração do sistema.

---

## 🔗 Cadeia crítica de inicialização

Para visualizar a ordem de carregamento e dependências dos serviços:

```bash
systemd-analyze critical-chain
```

---

### 📊 Exemplo de saída

```
graphical.target @12.445s
└─multi-user.target @12.430s
  └─docker.service @9.120s +2.998s
    └─network.target @8.950s
```

---

## 🧾 Interpretação

O `critical-chain` mostra:

- Serviços críticos para o boot  
- Dependências entre serviços  
- Tempo individual de execução  
- Impacto direto no tempo final  

É útil para entender atrasos causados por serviços dependentes.

---

## 📈 Gráfico visual do processo de boot

Também é possível gerar um gráfico completo da inicialização:

```bash
systemd-analyze plot > boot.svg
```

---

O arquivo `boot.svg` pode ser aberto no navegador e exibe
uma linha do tempo visual com todos os serviços carregados
durante o boot.

Esse gráfico facilita a identificação de:

- Serviços lentos  
- Paralelismo de inicialização  
- Dependências  
- Gargalos visuais


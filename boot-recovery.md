# 🧰 Boot Recovery no Linux

Guia de recuperação do sistema quando o Linux não consegue inicializar normalmente.

O objetivo é restaurar o boot e corrigir falhas em componentes críticos como GRUB, kernel e filesystem.

---

## 🧠 Quando usar Boot Recovery

Utilize recuperação em cenários como:

- Erros no GRUB  
- Sistema não encontrado  
- Kernel Panic  
- Falha em `/etc/fstab`  
- Partições corrompidas  
- Bootloader apagado  
- Migração ou clonagem de disco  

---

## 💿 Acesso via Live CD / USB

Inicie o sistema por uma mídia externa:

Exemplos:

- Ubuntu Live  
- Debian Live  
- Fedora Live  
- Linux Mint  

Após iniciar em modo Live, abra o terminal.

---

## 🔎 Identificar Partições

```bash
lsblk

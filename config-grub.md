## ⚙️ Configuração do GRUB

O GRUB é o bootloader responsável por carregar o kernel Linux na memória
Nesta etapa, foi realizada a edição do arquivo `/etc/default/grub`
para personalização do comportamento de inicialização do sistema.



## Comandos iniciais 
```bash
sudo su

ls -l /boot/grub2/grub.cfg

vi /etc/default/grub
 ```



A imagem abaixo apresenta o menu do GRUB no momento do boot, antes do carregamento do kernel Linux.

### 📸 Menu de inicialização do GRUB
<img width="1300" height="296" alt="grub1" src="https://github.com/user-attachments/assets/1506ef3f-23ae-4387-abc4-723caeb5d551" />

A imagem acima mostra a configuração de inicialização do GRUB, onde temos
diversas funções descritas como:

GRUB_TIMEOUT=5: Define quantos segundos o GRUB espera antes de iniciar o 
sistema padrão.

GRUB_DEFAULT=0: Define qual entrada do GRUB será carregada por padrão.
O numero corresponde á ordem no menu(começa em 0). A opção de 0 ou 1
onde você tem muitos opções para iniciar o seu sistema.

GRUB_DISABLE_SUBMENU=true: Desativa submenus no GRUB
e todas as entradas aparecem direto na tela principal.

Deixando claro que Neste sistema foi utilizado GRUB_DEFAULT=saved,
que permite ao GRUB lembrar a última opção selecionada.
Alternativamente,é possível definir um valor numérico como 0, que 
corresponde à primeira entrada do menu.

### 📸 Mudanças de inicialização do GRUB
<img width="1294" height="371" alt="grub2" src="https://github.com/user-attachments/assets/33004172-4ac9-4327-83d6-4cf2247d3e46" />

A imagem acima já mostra as mudanças das configuração sendo feitas como

o GRUB_TIMEOUT onde coloquei 10 segundos para iniciar o sistema padrão.

Foram testadas duas formas de definição do `GRUB_DEFAULT` para a entrada
padrão do sistema.

GRUB_DISABLE_RECOVERY true para O GRUB não mostra a opção recovery no 
menu e usuários não conseguem iniciar o sistema em modo de
recuperação facilmente.


### 📸 Atualizando as mudanças
<img width="982" height="184" alt="grub3" src="https://github.com/user-attachments/assets/6c543984-a202-4afd-bb7e-a06771068bee" />

A imagem acima já mostra o comando bash: grub2-mkconfig -o /boot/grub2/grub.cfg;
que atualizar as mudanças feitas e mostra que foi um sucesso e feito as 
mudanças e assim atualiza

### 📸 Conclusão
<img width="721" height="402" alt="grub4" src="https://github.com/user-attachments/assets/64986406-f6f0-4913-bfb5-29bcbb3b38eb" />

A imagem acima mostra o bash:reboot , funcionou certo o tempo de 10 segundos 
e as opções novas de inicialização tudo concluido. 
Inicialmente o tempo estava configurado para 5 segundos e, posteriormente,
foi ajustado para 10 segundos para facilitar a escolha manual no boot.



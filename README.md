# Laboratório de Instalação
 
Simuladores interativos para treinar a formatação e a instalação de sistemas operacionais direto no navegador, tela por tela, sem risco nenhum para o computador.
 
Cada simulador reproduz o caminho real de uma instalação, do menu de boot até a área de trabalho. Ao lado da tela fica um painel que explica o que está acontecendo, dá dicas e registra cada decisão tomada. Discos, chaves de produto, redes Wi-Fi e senhas são todos fictícios.
 
![HTML](https://img.shields.io/badge/HTML%2BCSS%2BJS-puro-e34f26)
![Sem dependências](https://img.shields.io/badge/depend%C3%AAncias-nenhuma-2ea44f)
![Idioma](https://img.shields.io/badge/idioma-pt--BR-0a6cbd)
 
## Simuladores
 
| Sistema | O que dá para treinar |
|---|---|
| **Windows 11** | Menu de boot UEFI (F12), idioma e teclado ABNT2, chave do produto e escolha da edição, instalação personalizada, exclusão e criação de partições com os avisos reais, cópia dos arquivos, reinícios e configuração inicial (rede, nome do PC, conta local, senha, privacidade). |
| **Ubuntu 26.04 LTS** | GRUB do pendrive e *safe graphics*, instalador completo, Wi-Fi ou modo offline, drivers de terceiros e o aviso do MOK no Secure Boot. Três caminhos de disco: ao lado do Windows (dual boot com divisão de espaço), apagar o disco (com LVM, criptografia LUKS, ZFS ou TPM) e particionamento manual com validação de `/` e `/boot/efi`. Depois, conta, fuso horário, menu de dual boot, desbloqueio do disco e primeiro login. |
 
### Recursos em comum
 
- **Erros de verdade:** o simulador deixa você errar como na vida real. Perder a janela do POST inicia o sistema antigo, tentar instalar na partição EFI é bloqueado e formatar a EFI no dual boot gera aviso.
- **Painel de etapas:** mostra em que fase da instalação você está e o que falta.
- **Registro de ações:** guarda um log com horário de tudo o que foi feito.
- **Velocidade ajustável:** 1×, 4× ou 12×, para não esperar a barra de progresso inteira.
- **Resumo final:** na área de trabalho aparece um resumo das escolhas feitas.
- **Tema claro e escuro:** segue a preferência do sistema.
- **Uso no celular:** as páginas funcionam também em telas pequenas.
## Como usar
 
**Online:** abra o site publicado no GitHub Pages e escolha um simulador na página principal.
 
**No seu computador:** baixe os arquivos, mantenha os três na mesma pasta e abra o `index.html` no navegador. Não precisa instalar nada nem rodar servidor.
 
## Estrutura
 
```
laboratorio-instalacao/
├── index.html              # página principal com os cards
├── simulador-win11.html    # simulador do Windows 11
├── simulador-ubuntu.html   # simulador do Ubuntu 26.04 LTS
└── README.md
```
 
Cada página é um único arquivo HTML autocontido, com estilos e scripts embutidos. A única coisa externa é a fonte, carregada do Google Fonts. Sem internet, o navegador usa uma fonte do sistema e tudo continua funcionando.
 
## Publicar no GitHub Pages
 
1. Envie os arquivos para a raiz de um repositório **público**.
2. Vá em **Settings → Pages** e escolha **Deploy from a branch**, branch `main` e pasta `/ (root)`.
3. Em poucos minutos o site estará em `https://seu-usuario.github.io/nome-do-repositorio/`.
## Adicionar um novo simulador
 
1. Crie o arquivo do simulador na mesma pasta (por exemplo `simulador-debian.html`). Os simuladores existentes servem de base: as telas ficam no objeto `SC`, e cada tela define a fase, o texto do guia e o HTML.
2. No `index.html`, acrescente uma entrada na lista `SIMS`:
```js
{id:'debian', nome:'Debian', ver:'13 · Trixie', tela:'ubu', status:'on',
 url:'simulador-debian.html',
 desc:'Descrição curta do que o simulador cobre.',
 etapas:8, tempo:'~6 min', nivel:'Intermediário',
 tags:['Netinst','Particionamento','Usuário root']}
```
 
Use `status:'soon'` e `url:null` para mostrar o card como "Em breve" enquanto o simulador não fica pronto. O campo `tela` escolhe a miniatura do card: `win` para uma janela estilo Windows ou `ubu` para uma estilo GNOME.
 
## Ideias para o futuro
 
- Simuladores para Debian, Fedora e Linux Mint
- Modo prova: um cenário com objetivo (por exemplo, "instale o Ubuntu mantendo o Windows") e correção no final
- Tela de configuração da UEFI (ordem de boot, Secure Boot, TPM)
- Ferramentas de recuperação do Windows e o `diskpart` no prompt de comando
## Aviso
 
Este é um projeto educacional e independente, sem ligação com a Microsoft ou a Canonical. Windows é marca registrada da Microsoft Corporation e Ubuntu é marca registrada da Canonical Ltd. As telas são recriações simplificadas para fins de treino e não reproduzem exatamente cada versão dos instaladores. Antes de formatar um computador de verdade, faça backup dos seus arquivos.

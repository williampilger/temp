# Site Betonart Invadido/Derrubado



## Primeiro contato: `06/09/2023 -> Luciana`

O site foi tirado do ar ha cerca  9dias, e a plataforma da hospedagem não permite restaurar dados de mais que 7 dias.



## Análise do ocorrido / Causa da parada

Pela minha análise, alguém com acesso ao FTP deixou um arquivo PHP infectado (`lock3.php`) com o intuito de um dia executá-lo e tirar todo o site do ar. O que ele faz?
- Se copia para um diretório temporário do Linux;
- Remove restrições de tempo de execução (permitindo que ele mesmo rode sem restrição)
- Remove a possibilidade do usuário impedir ele de continuar (se alguém chama uma URL e fecha a guia, por exemplo, ele para de executar. Nesse caso não).
- Busca por arquivos `.htaccess` e `index.php` e substitui todo o conteúdo pelo próprio conteúdo novamente.


## Consequências
Todos os arquivos `index` e `htaccess` foram perdidos. Se não houve um backup, existem duas possibilidades:
- **1** - Se o site tiver sido feito em WordPress (ou ferramenta semelhante), basta passar uma nova instalação e recuperar tudo
- **2** - Se temos o contato do desenvolvedor que criou isso, podemos pedir uma cópia desses arquivos estáticos e sobrescrever.

Se não é possível atender uma das possibilidade citadas acima, infelizmente é impossível reverter. Pode-se tentar a recriação dos arquivos index e htaccess, por eles não serem muitos (aparentemente), mas isso pode não funcionar bem, e pode não ser possível também. Levaria muito mais tempo para avaliar.



## Arquivos Infectados (Sophos Scan)

| Arquivo | Detecção |
| --- | --- |
| \public_html\store.php | PHP/Agent-BJQM detectada |
| \public_html\.index.php | PHP/Agent-BJQM detectada |
| \public_html\infos.php | PHP/Agent-BJQM detectada |
| \public_html\lock3.php | Troj/PHP-DK detectada |

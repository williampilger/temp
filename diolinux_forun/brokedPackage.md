# Pacote está quebrado ou não está completamente instalado

### Meu Hardware e sistema

- Hardware
  - Processador: **Intel® Core™ i5-4460 CPU @ 3.20GHz × 4**
  - Placa Mãe: **Gigabyte Technology Co., Ltd. To be filled by O.E.M.**
- Software
  - Sistema: **Pop!OS 22.04 LTS**
  - GNOME: **42.2**
  - Wind. System: **X11**
  - Kernel: **5.18.10-76051810-generic**

### Problema

Ao instalar/remover/atualizar qualquer pacote no sistema (via terminal, pois a PopShop simplesmente fecha quando tento alguma dessas operações), estou recebendo um erro referente ao pacote `libglib2.0-0:i386` que estaria quebrado.

Um `sudo dpkg-reconfigure libglib2.0-0:i386` também não funciona.

Executando o `sudo apt-get upgrade` obtenho o seguinte retorno:

```txt
Lendo listas de pacotes... Pronto
Construindo árvore de dependências... Pronto
Lendo informação de estado... Pronto        
Você pode querer executar 'apt --fix-broken install' para corrigí-los.
Os pacotes a seguir têm dependências desencontradas:
 gir1.2-mutter-10 : Depende: libmutter-10-0 (= 42.2-0ubuntu1pop1~1656366415~22.04~8e50951) mas 42.3-1ubuntu1pop1~1658401497~22.04~928bf97 está instalado
E: Dependências desencontradas. Tente 'apt --fix-broken install' sem nenhum pacote (ou especifique uma solução).
```

Executanto então o `sudo apt --fix-broken install`, obtenho:

```txt
Lendo listas de pacotes...
Construindo árvore de dependências...
Lendo informação de estado...
Corrigindo dependências... Pronto
Os seguintes pacotes foram instalados automaticamente e já não são necessários:
  libgtkglext1 libjffi-java libjffi-jni libopenaptx0
  linux-headers-5.16.19-76051619 linux-headers-5.16.19-76051619-generic
  linux-image-5.16.19-76051619-generic linux-modules-5.16.19-76051619-generic
  pipewire-audio-client-libraries
Utilize 'sudo apt autoremove' para os remover.
Os pacotes adicionais seguintes serão instalados:
  gir1.2-mutter-10
Os pacotes a seguir serão atualizados:
  gir1.2-mutter-10
1 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 102 não atualizados.
63 pacotes não totalmente instalados ou removidos.
É preciso baixar 0 B/183 kB de arquivos.
Depois desta operação, 1.024 B adicionais de espaço em disco serão usados.
dpkg: problemas com dependências impedem o processamento de triggers para libglib2.0-0:i386:
 libglib2.0-0:i386 depende de libc6 (>= 2.34); porém:
  Pacote libc6:i386 não está configurado ainda.

dpkg: erro ao processar o pacote libglib2.0-0:i386 (--configure):
 problemas com dependências - a deixar triggers por processar
dpkg: problemas com dependências impedem o processamento de triggers para libglib2.0-0:i386:
 libglib2.0-0:i386 depende de libc6 (>= 2.34); porém:
  Pacote libc6:i386 não está configurado ainda.
 [...]
dpkg: erro ao processar o pacote libglib2.0-0:i386 (--configure):
 problemas com dependências - a deixar triggers por processar
dpkg: demasiados erros, a parar
Erros foram encontrados durante o processamento de:
 libglib2.0-0:i386
 libglib2.0-0:i386
 [...]
Processamento parou porque havia muitos erros.
```
 **obs:** Acima em dois pontos eu coloquei `[...]` apenas para não repetir as inúmeras vezes que o mesmo erro aparece.
 
 Tenho a impressão de que o gerenciador de pacotes tenha sido danificado, alguém já passou por isso e saberia me dar uma luz?

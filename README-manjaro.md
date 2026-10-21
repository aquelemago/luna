# Quake no Manjaro

Como compilar e rodar o Quake (renderer por software, X11) no Manjaro Linux.

## 1. Pacotes

O Quake é um programa de 32 bits, então precisa do gcc com suporte a 32 bits e das
bibliotecas `lib32-*`:

```sh
# pacotes
sudo pacman -S --needed gcc make lib32-gcc-libs lib32-glibc lib32-libx11 lib32-libxext
```

## 2. Compilar

Na raiz do repositório:

```sh
# build
cd WinQuake && make -f Makefile.linuxi386 build_release
```

O binário fica em `WinQuake/releasei386-glibc/bin/quake.x11`.

## 3. Dados do jogo

O código é livre (GPL), mas os dados do jogo não. Use o `pak0.pak` da versão
shareware (ou o seu Quake original) e coloque em:

```
~/quake/id1/pak0.pak
```

## 4. Rodar

Na raiz do repositório:

```sh
# run
./WinQuake/releasei386-glibc/bin/quake.x11 -basedir ~/quake
```

Não são necessárias as opções `-nosound` nem `-mem`:

- sem dispositivo de som (o Manjaro não tem `/dev/dsp`), o jogo avisa
  `Sound disabled: no audio device` e segue sem som;
- a memória padrão é de 64 MB (`-mem <MB>` ainda funciona para mudar).

## Limitações conhecidas

Sem som, janela pequena (sem tela cheia nem OpenGL) e controles padrão de 1996
(setas para andar, sem mouse look).

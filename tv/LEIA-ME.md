# Saurito TV (a TV da sala na app)

A app lê `https://saurito.com/tv/lista.json` sempre que alguém abre a TV. Para pôr um vídeo novo **não é preciso OTA**:

0. **Sem selo da Play** (andre 28/11): na TV ninguém precisa de instalar a app. Fazer a versão TV com `redes/videos/tv-saurito/montar-tv.py` (pasta do projeto): abertura "TV Saurito" + vídeo sem o selo + fecho "TV Saurito". Já faz os passos 1 e 2.
1. Comprimir o vídeo vertical para 540x960 (fica 1-13 MB):
   `ffmpeg -i ORIGINAL.mp4 -vf "scale=540:960,fps=30" -c:v libx264 -profile:v main -preset slow -crf 27 -maxrate 1400k -bufsize 2800k -pix_fmt yuv420p -c:a aac -b:a 96k -movflags +faststart tv/NOME.mp4`
2. Capa: `ffmpeg -ss 3 -i ORIGINAL.mp4 -frames:v 1 -vf scale=270:480 -q:v 5 tv/NOME.jpg`
3. Acrescentar uma linha em `lista.json` (a ordem da lista é a ordem na TV; o primeiro é o que toca ao abrir).
4. Juntar no `main`. O GitHub Pages publica em ~1 minuto.

Regras: vídeos do Saurito (peluche, ou clipes de música aprovados pelo andre); nunca o selo nem o fecho da Play; ficheiros .mp4 até ~15 MB (o GitHub recusa >100 MB e cada visualização gasta dados a quem vê). Máximo 30 vídeos na lista.

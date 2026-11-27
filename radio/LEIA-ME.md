# Rádio do Saurito: músicas fora do OTA

As músicas novas do rádio da app ficam aqui (https://saurito.com/radio/) em vez de irem dentro do OTA.
A app toca-as diretamente daqui quando a pessoa as escolhe (precisa de internet; sem rede passa à seguinte).

Formato: mp3 96 kbps estéreo, 44,1 kHz, volume a -19 LUFS (igual às músicas que já vão na app).

Para pôr uma música nova:
1. `ffmpeg -i original.m4a -af loudnorm=I=-19:TP=-1.5:LRA=11 -ar 44100 -ac 2 -b:a 96k radio/nome.mp3`
2. Juntar aqui no site.
3. Acrescentar a linha em `radio.js` (ESTACOES, com `url`) na app: é só código, o OTA fica leve.

| Ficheiro | Música | Estilo |
|---|---|---|
| lagarto.mp3 | Lagarto do Asfalto | rap anos 90 |
| ninguem.mp3 | Ninguém Segura o Saurito | rock pesado anos 70 |
| escamas.mp3 | Escamas de Cor | rock psicodélico |

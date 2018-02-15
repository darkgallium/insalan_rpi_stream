# insalan_rpi_stream

Ce projet vise à pouvoir fournir un flux vidéo en direct de divers spots de l'INSALAN (scène, joueurs...) utilisable par les streameurs et l'équipe scène.

## Cahier des charges

- Fournir une bonne qualité d'image (>720p) 
- Fournir une image fluide (>30 fps) 
- Avoir une latence acceptable entre la captation et la diffusion (<1min pour les streameurs et le plus fluide possible pour la scène)
- Utiliser des Raspberry Pi comme dispositifs de captation d'image.

## Implémentation

- 1 à 4 Raspberry Pi (sachant qu'au moins 2 sont des Pi1), 3 webcam Microsoft FullHD et 1 PiCam 720p pour la captation.
- 1 Serveur chargé de la réception et de l'encodage (raw/h264 -> flv) des flux envoyés par les Raspberry et chargé de la diffusion de l'image par protocole RTMP.

## État d'avancement

- [x] Installer et configurer au moins un Raspberry Pi pour les tests.
- [x] Streamer une image fluide de qualité acceptable entre un Raspberry et un PC (avec gstreamer de bout en bout).
- [x] Diffuser un flux vidéo RTMP d'une webcam et d'une PiCam *relativement* satisfaisant.
- [ ] Améliorer la qualité et la fluidité du stream.
- [ ] Trouver un serveur sur lequel on effectuera le transcodage lors de la *vraie* INSALAN.
- [ ] Installer et configurer le *vrai* serveur de diffusion.
- [ ] Décider de ce qu'on doit diffuser.

## Prérequis

- gstreamer1.0 (et les plugins d'accélération à l'encodage gstreamer1.0-omx* sur les Raspberry Pis)
- nginx et [nginx-rtmp-module](https://github.com/arut/nginx-rtmp-module) sur le serveur de transcodage

## Utilisation

- Lancez les scripts adéquats sur les hosts adéquats (dossier raspberry_side => scripts à lancer sur les raspberry, dossier server_side => scripts à lancer sur le serveur de diffusion)
- Se connecter (avec VLC par exemple), au flux généré, qui devrait ressembler a rtmp://addr_serv_diff:1935/live
- Profit!


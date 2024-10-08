---
title: "Como usar rtorrent des de cero"
date: "2015-08-25"
categories: 
  - "manual"
tags: 
  - "manual-2"
  - "rtorrent"
  - "torrent"
  - "tutorial"
---

Viviendo en Alemania no puedo usar bitorrent sin que me llegue una factura por más de 500€ por bajar contenido que tiene copyright. Por lo que finalmente conseguí un servidor dónde tal cosa puede hacerse. El problema es que no tengo GUI por lo que tuve que buscar un cliente bittorrent para bajarme las cosas. Sin GUI, rtorrent era la primera opción que encontré. Al principio parece un poco complicado pero sabiendo los cuatro comandos básicos no ocasiona problemas.

Para iniciar el cliente de torrent:

```
$ rtorrent
```

Para poner un archivo en la cola de descargas tienes que presionar **intro, pegar el enlace de magnet y darle a intro otra vez**. Una vez has hecho esto tienes el archivo en espera por lo que para iniciarlo usas las flechas arriba y abajo para localizar el archivo y con **Control+S empiezas la descarga**. Si por algún motivo te dice que has movido el archivo (a mi me lo dice sin motivo) lo puedes solucionar con Control+E. Puedes cerrar el programa con Control+Q. **El fichero de configuración tiene que colocarse en ~/.rtorrent.rc** y yo tengo el siguiente (por si lo quieres usar de base o [del que me copié](https://gist.github.com/bryanjswift/1525912)).

```
# This is an example resource file for rTorrent. Copy to
 # ~/.rtorrent.rc and enable/modify the options as needed. Remember to
 # uncomment the options you wish to enable.
 # Maximum and minimum number of peers to connect to per torrent.
 min_peers = 1
 max_peers = 20
 # Same as above but for seeding completed torrents (-1 = same as downloading)
 min_peers_seed = 1
 max_peers_seed = 20
 # Maximum number of uploads single torrent may use
 max_uploads = 10
 # Maximum number of simultaneous downloads
 max_downloads_global = 10
 # Maximum number of simultaneous uploads
 max_uploads_global = 20
 # Global upload and download rate in KiB. "0" for unlimited.
 download_rate = 0
 upload_rate = 300
 # Default directory to save the downloaded torrents.
 directory = /home/rocreguant/rTorrStuff/Downloads
 # Default session directory. Make sure you don't run multiple instance
 # of rtorrent using the same session directory. Perhaps using a
 # relative path?
 session = /home/rocreguant/rTorrStuff/session
 # Watch a directory for new torrents, and stop those that have been
 # deleted.
 schedule = watch_directory,5,5,load_start=./rtactive/*.torrent
 schedule = tied_directory,6,5,start_tied=
 schedule = untied_directory,7,5,stop_untied=
 # Close torrents when diskspace is low.
 schedule = low_diskspace,5,60,close_low_diskspace=2000M
 # Periodically save session data
 schedule = session_save,240,300,session_save=
 # Enable the default ratio group.
 ratio.enable=
 # Change the limits, the defaults should be sufficient.
 # Upload to a minimum ratio of 4.0
 ratio.min.set=400
 # Upload to a maximum ratio of 20.0
 ratio.max.set=2000
 # Upload a minimum of 250 MB
 ratio.upload.set=250M
 # When seeding ratio is reached close the torrent
 system.method.set = group.seeding.ratio.command, d.close=
 # Move files to ./unsorted when download completes
 system.method.set_key = event.download.finished,move_complete,"execute=mv,-n,$d.get_base_path=,./unsorted/;d.set_directory=./unsorted/"
 # Port range to use for listening.
 port_range = 60125-64125
 # Start opening ports at a random position within the port range.
 port_random = yes
 # Encryption options, set to none (default) or any combination of the following:
 # allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
 #
 # The example value allows incoming encrypted connections, starts unencrypted
 # outgoing connections but retries with encryption if they fail, preferring
 # plaintext to RC4 encryption after the encrypted handshake
 #
 encryption = allow_incoming,try_outgoing,enable_retry,prefer_plaintext
 # Sort the main view by ratio
 view.sort_current = main,greater=d.get_ratio=
 view.sort_new = main,less=d.get_ratio=
 view.sort = main
 # Sort the seeding view by the upload rate and only show torrents with peers
 view.sort_current = seeding,greater=d.get_up_rate=
 view.filter = seeding,"and=d.get_complete=,d.get_peers_connected="
 view.sort_new = seeding,less=d.get_up_rate=
 view.sort = seeding
 # Sort the leeching view by name
 view.sort_current = leeching,greater=d.get_name=
 view.sort_new = leeching,greater=d.get_name=
 view.sort = leeching
 # Filter the active view by connected peers
 view.sort_current = active,less=d.get_name=
 view.sort_new = leeching,less=d.get_name=
 view.filter = active,d.get_peers_connected=
 view.sort = active
 schedule = sort_main,11,5,view.sort=main
 schedule = sort_seeding,12,5,view.sort=seeding
 schedule = sort_leeching,13,5,view.sort=leeching
 schedule = sort_active,14,5,view.sort=active
 # Enable DHT support for trackerless torrents or when all trackers are down.
 # May be set to "disable" (completely disable DHT), "off" (do not start DHT),
 # "auto" (start and stop DHT as needed), or "on" (start DHT immediately).
 # The default is "off". For DHT to work, a session directory must be defined.
 #
 #dht = auto
 # UDP port to use for DHT.
 #
 dht_port = 63425
 # Enable peer exchange (for torrents not marked private)
 #
 #peer_exchange = yes
```

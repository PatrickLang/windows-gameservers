# Game Servers in Windows Containers


## ZDaemon

To build:

```
docker build -t zdaemon .
```

You need to have the IWADs (and optionally PWADs) somewhere on your machine,
then bind mount it to c:\zserv\wads. My gaming machine has doom1.wad, doom2.wad and a bunch of others in 
C:\ZDaemon\wads\, so these steps below work for me

To Run:

```
docker run -it -v C:\ZDaemon\wads:c:\zserv\wads zdaemon
```
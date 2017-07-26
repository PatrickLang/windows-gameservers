# Game Servers in Windows Containers


## DOOM ports

### ZDaemon

For more info, go to http://www.zdaemon.org 

**Work in progress**

- [*] Build steps
- [ ] Port mapping needed?
- [ ] How to connect on local LAN

#### To build

```
docker build -t zdaemon .
```

You need to have the IWADs (and optionally PWADs) somewhere on your machine,
then bind mount it to c:\zserv\wads. My gaming machine has doom1.wad, doom2.wad and a bunch of others in 
C:\ZDaemon\wads\, so these steps below work for me

#### To Run

```
docker run -it -p 10666:10666 -v C:\ZDaemon\wads:c:\wads zdaemon
```


### Zandronum

For more info go to https://zandronum.com/

**Work in progress**

- [ ] Build steps
- [ ] Port mapping needed?
- [ ] How to connect on local LAN
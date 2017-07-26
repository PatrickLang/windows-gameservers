FROM microsoft/windowsservercore as build
RUN mkdir c:\temp
WORKDIR c:\\temp
ADD http://downloads.zdaemon.org/zserv110b07_win32.20151014.7z c:\\temp\\zserv110b07_win32.20151014.7z
ADD http://7-zip.org/a/7z1604-x64.exe c:\\temp\\7z1604-x64.exe
RUN c:\temp\7z1604-x64.exe /S /D=c:\7zip
RUN c:\7zip\7z.exe e zserv110b07_win32.20151014.7z

FROM microsoft/windowsservercore
COPY --from=build /temp/zserv.cfg /zserv/zserv.cfg
COPY --from=build /temp/zserv.exe /zserv/zserv.exe
COPY --from=build /temp/zdaemon.wad /zserv/zdaemon.wad
COPY --from=build /temp/bots.cfg /zserv/bots.cfg
RUN setx /m WADDIR c:\wads
WORKDIR c:\\zserv
CMD zserv.exe
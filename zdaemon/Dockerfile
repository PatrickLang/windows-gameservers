FROM microsoft/windowsservercore as build
ARG ZDAEMONSRC=http://downloads.zdaemon.org/zdaemon110b08_win32_bin.7z
ARG SEVENZIPSRC=http://7-zip.org/a/7z1604-x64.exe
RUN mkdir c:\temp
WORKDIR c:\\temp
ADD ${ZDAEMONSRC} c:\\temp\\zserv.7z
ADD ${SEVENZIPSRC} c:\\temp\\7z-sfx.exe
RUN c:\temp\7z-sfx.exe /S /D=c:\7zip
RUN dir c:\temp
RUN c:\7zip\7z.exe x zserv.7z

FROM microsoft/windowsservercore
RUN setx /m WADDIR c:\wads
WORKDIR c:\\zserv
EXPOSE 10666
COPY --from=build /temp/zserv.cfg /zserv/zserv.cfg
COPY --from=build /temp/zserv.exe /zserv/zserv.exe
COPY --from=build /temp/zdaemon.wad /zserv/zdaemon.wad
COPY --from=build /temp/bots.cfg /zserv/bots.cfg
CMD zserv.exe
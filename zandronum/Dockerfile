FROM microsoft/windowsservercore as build
RUN mkdir c:\temp
WORKDIR c:\\temp
ADD https://zandronum.com/downloads/zandronum2.1.2-win32-base.zip c:\\temp\\zandronum2.1.2-win32-base.zip
ADD http://7-zip.org/a/7z1604-x64.exe c:\\temp\\7z1604-x64.exe
RUN c:\temp\7z1604-x64.exe /S /D=c:\7zip
RUN c:\7zip\7z.exe e zandronum2.1.2-win32-base.zip

FROM microsoft/windowsservercore
COPY --from=build /temp/zandronum.exe /zandronum/zandronum.exe
COPY --from=build /temp/skulltag_actors.pk3 /zandronum/skulltag_actors.pk3
COPY --from=build /temp/zandronum.pk3 /zandronum/zandronum.pk3
COPY --from=build /temp/fmodex.dll /zandronum/fmodex.dll
RUN setx /m WADDIR c:\wads
WORKDIR c:\\zandronum
CMD zandronum.exe -host
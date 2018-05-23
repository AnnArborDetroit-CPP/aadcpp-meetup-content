# escape=`

FROM microsoft/windowsservercore-insider:10.0.17134.1

ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

# Install Build Tools excluding workloads and components with known issues.
RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --add Microsoft.VisualStudio.Workload.VCTools --includeRecommended --includeOptional `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0
 
WORKDIR "C:\Users\ContainerAdministrator"





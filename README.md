# IdentityServer4---Signing-Cert-Setup-2012R2

- Download Windows SDK 7.1

https://stackoverflow.com/questions/32091593/cannot-install-windows-sdk-7-1-on-windows-10/35357470

### https://www.microsoft.com/en-us/download/details.aspx?id=8442

https://stackoverflow.com/questions/20115186/what-sdk-version-to-download/22987999#22987999
GRMSDK_EN_DVD.iso is a version for x86 environment.
GRMSDKX_EN_DVD.iso is a version for x64 environment.
GRMSDKIAI_EN_DVD.iso is a version for Itanium environment.

- Run Regedit to edit the .NET versions

https://stackoverflow.com/questions/32091593/cannot-install-windows-sdk-7-1-on-windows-10/35357470

Lots of hassle with permissions.

- Go to Setup\ and run SDKSetup.exe

- Install .NET Development - Tools ONLY

- Open a command prompt

cd C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin

makecert -r -pe -n "CN=CertName" -b 01/01/2015 -e 01/01/2039 -eku 1.3.6.1.5.5.7.3.3 -sky signature -a sha256 -len 2048 -ss my -sr LocalMachine

https://brockallen.com/2015/06/01/makecert-and-creating-ssl-or-signing-certificates/
http://amilspage.com/signing-certificates-idsv4/

makecert -n "CN=IdentityServerCN" -a sha256 -sv IdentityServer4Auth.pvk -r IdentityServer4Auth.cer
pvk2pfx -pvk IdentityServer4Auth.pvk -spc IdentityServer4Auth.cer -po -pfx IdentityServer4Auth.pfx

File
makecert -r -pe -n "CN=MyCertName" -b 01/01/2015 -e 01/01/2039 -eku 1.3.6.1.5.5.7.3.3 -sky signature -a sha256 -len 2048 mycert.cer

Import
makecert -r -pe -n "CN=MyCert" -b 01/01/2015 -e 01/01/2039 -eku 1.3.6.1.5.5.7.3.3 -sky signature -a sha256 -len 2048 -ss my -sr LocalMachine

pvk2pfx -pvk IdentityServer4Auth.pvk -spc IdentityServer4Auth.cer -po -pfx IdentityServer4Auth.pfx

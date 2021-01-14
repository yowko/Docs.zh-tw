---
title: 產生 Self-Signed 憑證總覽
description: 概述 Microsoft dotnet dev 憑證工具，其可為 .NET Core 和 ASP.NET Core 專案新增功能，以及其他使用自我簽署憑證的選項。
author: angee
ms.date: 11/19/2020
ms.openlocfilehash: d1675abb7d584b72d981f9db739e02269abe662c
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189137"
---
# <a name="generate-self-signed-certificates-with-the-net-cli"></a>使用 .NET CLI 產生自我簽署憑證

使用自我簽署憑證時，有不同的方式可建立和使用它們來進行開發和測試案例。  在本指南中，您將會討論如何使用的自我簽署憑證 `dotnet dev-certs` ，以及和之類的其他選項 `PowerShell` `OpenSSL` 。

然後，您可以使用範例（例如容器中裝載的 [ASP.NET Core 應用程式](https://github.com/dotnet/dotnet-docker/blob/master/samples/run-aspnetcore-https-development.md) ）來驗證憑證是否會載入。

## <a name="prerequisites"></a>先決條件

在範例中，您可以使用 .NET Core 3.1 或 .NET 5。

針對 `dotnet dev-certs` ，請務必安裝適當版本的 .net：

* [在 Windows 上安裝 .NET](../install/windows.md)
* [在 Linux 上安裝 .NET](../install/linux.md)
* [在 macOS 上安裝 .NET](../install/macos.md)

此範例需要 docker [17.06](https://docs.docker.com/release-notes/docker-ce) 或更新版本的 [docker 用戶端](https://www.docker.com/products/docker)。

## <a name="prepare-sample-app"></a>準備範例應用程式

您必須根據想要用於測試的執行時間（ [.Net Core 3.1](#net-core-31-sample-app) 或 [.net 5](#net-5-sample-app)）來準備範例應用程式。

在本指南中，您將使用 [範例應用程式](https://hub.docker.com/_/microsoft-dotnet-samples) ，並在適當的位置進行變更。

### <a name="net-core-31-sample-app"></a>.NET Core 3.1 範例應用程式

取得範例應用程式。

```console
git clone https://github.com/dotnet/dotnet-docker/
```

在本機流覽至存放庫，並在編輯器中開啟工作區。

> [!NOTE]
> 如果您想要使用 dotnet publish 參數來 *修剪* 部署，您應該確保包含適當的相依性以支援 SSL 憑證。
更新 [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) ，以確定容器中包含適當的元件。 如需參考，請參閱在針對獨立式部署使用修剪時，如何更新 .csproj 檔案以 [支援 ssl 憑證](../deploying/trim-self-contained.md#support-for-ssl-certificates) 。

請確定 `aspnetapp.csproj` 包含適當的目標架構：

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>.netcoreapp3.1</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

修改 Dockerfile，以確保執行時間指向 .NET Core 3.1：

```Dockerfile
# https://hub.docker.com/_/microsoft-dotnet-core
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /source

# copy csproj and restore as distinct layers
COPY *.sln .
COPY aspnetapp/*.csproj ./aspnetapp/
RUN dotnet restore

# copy everything else and build app
COPY aspnetapp/. ./aspnetapp/
WORKDIR /source/aspnetapp
RUN dotnet publish -c release -o /app --no-restore

# final stage/image
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT ["dotnet", "aspnetapp.dll"]
```

請確定您是指向範例應用程式。

```console
cd .\dotnet-docker\samples\aspnetapp
```

在本機建立容器以進行測試。

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

### <a name="net-5-sample-app"></a>.NET 5 範例應用程式

在本指南中，您應該檢查 .NET 5 的 [範例 aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) 。

檢查範例應用程式 [Dockerfile](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/Dockerfile) 是否使用 .net 5。

視主機作業系統而定，可能需要更新 ASP.NET 執行時間。 例如， `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` 在 Dockerfile 中變更為，將有助於以適當的 Windows 執行時間為目標。

例如，這將有助於在 Windows 上測試憑證：

```Dockerfile
# https://hub.docker.com/_/microsoft-dotnet
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /source

# copy csproj and restore as distinct layers
COPY *.sln .
COPY aspnetapp/*.csproj ./aspnetapp/
RUN dotnet restore -r win-x64

# copy everything else and build app
COPY aspnetapp/. ./aspnetapp/
WORKDIR /source/aspnetapp
RUN dotnet publish -c release -o /app -r win-x64 --self-contained false --no-restore

# final stage/image
# Uses the 2009 release; 2004, 1909, and 1809 are other choices
FROM mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT ["aspnetapp"]

```

如果我們要在 Linux 上測試憑證，您可以使用現有的 Dockerfile。

請確定 `aspnetapp.csproj` 包含適當的目標架構：

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

> [!NOTE]
> 如果您想要使用 `dotnet publish` 參數來 *修剪* 部署，請確定已包含支援 SSL 憑證的適當相依性。
更新 [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) ，以確定容器中包含適當的元件。 如需參考，請參閱在針對獨立式部署使用修剪時，如何更新 .csproj 檔案以 [支援 ssl 憑證](../deploying/trim-self-contained.md#support-for-ssl-certificates) 。

請確定您是指向範例應用程式。

```console
cd .\dotnet-docker\samples\aspnetapp
```

在本機建立容器以進行測試。

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

## <a name="create-a-self-signed-certificate"></a>建立自我簽署憑證

您可以建立自我簽署的憑證：

- [使用 dotnet dev 憑證](#with-dotnet-dev-certs)
- [透過 PowerShell](#with-powershell)
- [使用 OpenSSL](#with-openssl)

### <a name="with-dotnet-dev-certs"></a>使用 dotnet dev 憑證

您可以使用 `dotnet dev-certs` 來處理自我簽署憑證。 此範例會使用 PowerShell 主控台。

```console
dotnet dev-certs https -ep $env:USERPROFILE\.aspnet\https\aspnetapp.pfx -p crypticpassword
dotnet dev-certs https --trust
```

> [!NOTE]
> 憑證名稱，在此情況下， *aspnetapp* 必須符合專案元件名稱。 `crypticpassword` 可做為您自己選擇之密碼的獨立。 如果主控台傳回「有效的 HTTPS 憑證已存在」，表示您的存放區中已經有受信任的憑證。 您可以使用 MMC 主控台來匯出它。

設定憑證的應用程式密碼：

```console
dotnet user-secrets -p aspnetapp\aspnetapp.csproj set "Kestrel:Certificates:Development:Password" "crypticpassword"
```

> [!NOTE]
> 注意：密碼必須符合憑證所用的密碼。

使用針對 HTTPS 設定的 ASP.NET Core 來執行容器映射：

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -v $env:APPDATA\microsoft\UserSecrets\:C:\Users\ContainerUser\AppData\Roaming\microsoft\UserSecrets -v $env:USERPROFILE\.aspnet\https:C:\Users\ContainerUser\AppData\Roaming\ASP.NET\Https mcr.microsoft.com/dotnet/samples:aspnetapp
```

應用程式啟動之後，請 `https://localhost:8001` 在您的網頁瀏覽器中流覽至。

#### <a name="clean-up"></a>清除

如果秘密和憑證不在使用中，請務必將其清除。

```console
dotnet user-secrets remove "Kestrel:Certificates:Development:Password" -p aspnetapp\aspnetapp.csproj
dotnet dev-certs https --clean
```

### <a name="with-powershell"></a>透過 PowerShell

您可以使用 PowerShell 來產生自我簽署憑證。 [PKI 用戶端](/powershell/module/pkiclient/new-selfsignedcertificate?preserve-view=true&view=win10-ps)可以用來產生自我簽署憑證。

```powershell
$cert = New-SelfSignedCertificate -DnsName @("contoso.com", "www.contoso.com") -CertStoreLocation "cert:\LocalMachine\My"
```

將會產生憑證，但基於測試目的，您應該將它放在憑證存放區中，以在瀏覽器中進行測試。

```powershell
$certKeyPath = "c:\certs\contoso.com.pfx"
$password = ConvertTo-SecureString 'password' -AsPlainText -Force
$cert | Export-PfxCertificate -FilePath $certKeyPath -Password $password
$rootCert = $(Import-PfxCertificate -FilePath $certKeyPath -CertStoreLocation 'Cert:\LocalMachine\Root' -Password $password)
```

此時，應該可以從 [MMC 嵌入式管理](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)單元查看憑證。

您可以在 Windows 子系統 Linux 版 (WSL) 中執行範例容器：

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> 請注意，磁片區掛接可能會以不同的主機為基礎來處理檔案路徑。  例如，在 WSL 中，我們可能會將 */c/certs* 取代為 */mnt/c/certs*。

如果您使用先前為 Windows 建立的容器，則 [執行] 命令看起來會如下所示：

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

應用程式啟動後，請在瀏覽器中流覽至 contoso.com:8001。

請確定主項目目已更新，以便 `contoso.com` 在適當的 ip 位址上接聽 (例如 127.0.0.1) 。 如果無法辨識憑證，請確定主機上的容器所載入的憑證也受信任，而且有適當的 SAN/DNS 專案 `contoso.com` 。

#### <a name="clean-up"></a>清除

```powershell
$cert | Remove-Item
Get-ChildItem $certFilePath | Remove-Item
$rootCert | Remove-item
```

### <a name="with-openssl"></a>使用 OpenSSL

您可以使用 [OpenSSL](https://www.openssl.org/) 來建立自我簽署憑證。 此範例將搭配使用 WSL/Ubuntu 和 bash shell `OpenSSL` 。

這會產生 .crt 和金鑰。

```bash
PARENT="contoso.com"
openssl req \
-x509 \
-newkey rsa:4096 \
-sha256 \
-days 365 \
-nodes \
-keyout $PARENT.key \
-out $PARENT.crt \
-subj "/CN=${PARENT}" \
-extensions v3_ca \
-extensions v3_req \
-config <( \
  echo '[req]'; \
  echo 'default_bits= 4096'; \
  echo 'distinguished_name=req'; \
  echo 'x509_extension = v3_ca'; \
  echo 'req_extensions = v3_req'; \
  echo '[v3_req]'; \
  echo 'basicConstraints = CA:FALSE'; \
  echo 'keyUsage = nonRepudiation, digitalSignature, keyEncipherment'; \
  echo 'subjectAltName = @alt_names'; \
  echo '[ alt_names ]'; \
  echo "DNS.1 = www.${PARENT}"; \
  echo "DNS.2 = ${PARENT}"; \
  echo '[ v3_ca ]'; \
  echo 'subjectKeyIdentifier=hash'; \
  echo 'authorityKeyIdentifier=keyid:always,issuer'; \
  echo 'basicConstraints = critical, CA:TRUE, pathlen:0'; \
  echo 'keyUsage = critical, cRLSign, keyCertSign'; \
  echo 'extendedKeyUsage = serverAuth, clientAuth')

openssl x509 -noout -text -in $PARENT.crt
```

若要取得 .pfx，請使用下列命令：

```bash
openssl pkcs12 -export -out $PARENT.pfx -inkey $PARENT.key -in $PARENT.crt
```

> [!NOTE]
> Aspnetcore 3.1 範例將使用 `.pfx` 和密碼。 從 `.net 5` 執行時間開始，Kestrel 也可以採用 `.crt` 和 PEM 編碼的檔案 `.key` 。

視主機作業系統而定，憑證將必須受信任。 在 Linux 主機上，「信任」憑證是不同的，而且發行版本相依。

基於本指南的目的，以下是使用 PowerShell 的 Windows 範例：

```powershell
Import-Certificate -FilePath $certFilePath -CertStoreLocation 'Cert:\LocalMachine\Root'
```

若為 .NET Core 3.1，請在 WSL 中執行下列命令：

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/path/to/certs/:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

從 .NET 5 開始，Kestrel 可以採用 `.crt` 和 PEM 編碼的檔案 `.key` 。 您可以使用下列適用于 .NET 5 的命令來執行範例：

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=/https/contoso.com.key -v /c/path/to/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> 請注意，在 WSL 中，磁片區掛接路徑可能會根據設定而變更。

針對 Windows 中的 .NET Core 3.1，請在中執行下列命令 `Powershell` ：

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

針對 Windows 中的 .NET 5，請在 PowerShell 中執行下列命令：

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=c:\https\contoso.com.key -v c:\certs:C:\https aspnetapp:my-sample
```

應用程式啟動後，請在瀏覽器中流覽至 contoso.com:8001。

請確定主項目目已更新，以便 `contoso.com` 在適當的 ip 位址上接聽 (例如 127.0.0.1) 。 如果無法辨識憑證，請確定主機上的容器所載入的憑證也受信任，而且有適當的 SAN/DNS 專案 `contoso.com` 。

#### <a name="clean-up"></a>清除

完成測試之後，請務必清除自我簽署的憑證。

```powershell
Get-ChildItem $certFilePath | Remove-Item
```

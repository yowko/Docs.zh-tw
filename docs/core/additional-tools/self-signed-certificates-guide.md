---
title: 產生 Self-Signed 憑證總覽
description: 概述 Microsoft dotnet dev 憑證工具，其可為 .NET Core 和 ASP.NET Core 專案新增功能，以及其他使用自我簽署憑證的選項。
author: angee
ms.date: 11/19/2020
ms.openlocfilehash: 15bbe3997ca34b503074595fa027bc6dfff1c0a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760606"
---
# <a name="generate-self-signed-certificates-with-the-net-cli"></a><span data-ttu-id="53ecb-103">使用 .NET CLI 產生自我簽署憑證</span><span class="sxs-lookup"><span data-stu-id="53ecb-103">Generate self-signed certificates with the .NET CLI</span></span>

<span data-ttu-id="53ecb-104">使用自我簽署憑證時，有不同的方式可建立和使用它們來進行開發和測試案例。</span><span class="sxs-lookup"><span data-stu-id="53ecb-104">When using self-signed certificates, there's different ways to create and use them for development and testing scenarios.</span></span>  <span data-ttu-id="53ecb-105">在本指南中，您將會討論如何使用的自我簽署憑證 `dotnet dev-certs` ，以及和之類的其他選項 `PowerShell` `OpenSSL` 。</span><span class="sxs-lookup"><span data-stu-id="53ecb-105">In this guide, you'll cover using self-signed certificates with `dotnet dev-certs`, and other options like `PowerShell` and `OpenSSL`.</span></span>

<span data-ttu-id="53ecb-106">然後，您可以使用範例（例如容器中裝載的 [ASP.NET Core 應用程式](https://github.com/dotnet/dotnet-docker/blob/master/samples/run-aspnetcore-https-development.md) ）來驗證憑證是否會載入。</span><span class="sxs-lookup"><span data-stu-id="53ecb-106">You can then validate that the certificate will load using an example such as an [ASP.NET Core app](https://github.com/dotnet/dotnet-docker/blob/master/samples/run-aspnetcore-https-development.md) hosted in a container.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="53ecb-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="53ecb-107">Prerequisites</span></span>

<span data-ttu-id="53ecb-108">在範例中，您可以使用 `.netcore 3.1` 或 `.net 5` 。</span><span class="sxs-lookup"><span data-stu-id="53ecb-108">In the sample, you can utilize either `.netcore 3.1` or `.net 5`.</span></span>

<span data-ttu-id="53ecb-109">針對 `dotnet dev-certs` ，請務必安裝適當的版本 `dotnet` ：</span><span class="sxs-lookup"><span data-stu-id="53ecb-109">For `dotnet dev-certs`, be sure to have the appropriate version of `dotnet` installed:</span></span>

* [<span data-ttu-id="53ecb-110">在 Windows 上安裝 dotnet</span><span class="sxs-lookup"><span data-stu-id="53ecb-110">Install dotnet on Windows</span></span>](../install/windows.md)
* [<span data-ttu-id="53ecb-111">在 Linux 上安裝 dotnet</span><span class="sxs-lookup"><span data-stu-id="53ecb-111">Install dotnet on Linux</span></span>](../install/linux.md)
* [<span data-ttu-id="53ecb-112">在 macOS 上安裝 dotnet</span><span class="sxs-lookup"><span data-stu-id="53ecb-112">Install dotnet on macOS</span></span>](../install/macos.md)

<span data-ttu-id="53ecb-113">此範例需要 docker [17.06](https://docs.docker.com/release-notes/docker-ce) 或更新版本的 [docker 用戶端](https://www.docker.com/products/docker)。</span><span class="sxs-lookup"><span data-stu-id="53ecb-113">This sample requires [Docker 17.06](https://docs.docker.com/release-notes/docker-ce) or later of the [Docker client](https://www.docker.com/products/docker).</span></span>

## <a name="prepare-sample-app"></a><span data-ttu-id="53ecb-114">準備範例應用程式</span><span class="sxs-lookup"><span data-stu-id="53ecb-114">Prepare sample app</span></span>

<span data-ttu-id="53ecb-115">您必須根據想要用於測試的執行時間來準備範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="53ecb-115">You'll need to prepare the sample app depending on which runtime you'd like to use for testing.</span></span>

<span data-ttu-id="53ecb-116">在本指南中，您將使用 [範例應用程式](https://hub.docker.com/_/microsoft-dotnet-samples) ，並在適當的位置進行變更。</span><span class="sxs-lookup"><span data-stu-id="53ecb-116">For this guide, you'll be using a [sample app](https://hub.docker.com/_/microsoft-dotnet-samples) and make changes where appropriate.</span></span>

### <a name="prepare-net-core-31-sample-app"></a><span data-ttu-id="53ecb-117">準備 .NET Core 3.1 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="53ecb-117">Prepare .NET Core 3.1 sample app</span></span>

<span data-ttu-id="53ecb-118">取得範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="53ecb-118">Get the sample app.</span></span>

```console
git clone https://github.com/dotnet/dotnet-docker/
```

<span data-ttu-id="53ecb-119">在本機流覽至存放庫，並在編輯器中開啟工作區。</span><span class="sxs-lookup"><span data-stu-id="53ecb-119">Navigate to the repository locally and open up the workspace in an editor.</span></span>

> [!NOTE]
> <span data-ttu-id="53ecb-120">如果您想要使用 dotnet publish 參數來 *修剪* 部署，您應該確保包含適當的相依性以支援 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="53ecb-120">If you're looking to use dotnet publish parameters to *trim* the deployment, you should make sure that the appropriate dependencies are included for supporting SSL certificates.</span></span>
<span data-ttu-id="53ecb-121">更新 [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) ，以確定容器中包含適當的元件。</span><span class="sxs-lookup"><span data-stu-id="53ecb-121">Update the [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) to ensure that the appropriate assemblies are included in the container.</span></span> <span data-ttu-id="53ecb-122">如需參考，請參閱在針對獨立式部署使用修剪時，如何更新 .csproj 檔案以 [支援 ssl 憑證](../deploying/trim-self-contained.md#support-for-ssl-certificates) 。</span><span class="sxs-lookup"><span data-stu-id="53ecb-122">For reference, check how to update the .csproj file to [support ssl certificates](../deploying/trim-self-contained.md#support-for-ssl-certificates) when using trimming for self-contained deployments.</span></span>

<span data-ttu-id="53ecb-123">請確定 `aspnetapp.csproj` 包含適當的目標架構：</span><span class="sxs-lookup"><span data-stu-id="53ecb-123">Make sure the `aspnetapp.csproj` includes the appropriate target framework:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>.netcoreapp3.1</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

<span data-ttu-id="53ecb-124">請修改 Dockerfile，以確定執行時間指向. netcore 3.1：</span><span class="sxs-lookup"><span data-stu-id="53ecb-124">Modify the Dockerfile to make sure the runtime points to .netcore 3.1:</span></span>

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

<span data-ttu-id="53ecb-125">請確定您是指向範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="53ecb-125">Make sure you're pointing to the sample app.</span></span>

```console
cd .\dotnet-docker\samples\aspnetapp
```

<span data-ttu-id="53ecb-126">在本機建立容器以進行測試。</span><span class="sxs-lookup"><span data-stu-id="53ecb-126">Build the container for testing locally.</span></span>

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

### <a name="prepare-net-5-sample-app"></a><span data-ttu-id="53ecb-127">準備 .NET 5 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="53ecb-127">Prepare .NET 5 sample app</span></span>

<span data-ttu-id="53ecb-128">在本指南中，您應該檢查 .net 5 的 [範例 aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) 。</span><span class="sxs-lookup"><span data-stu-id="53ecb-128">For this guide, the [sample aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) should be checked for .net 5.</span></span>

<span data-ttu-id="53ecb-129">檢查範例應用程式 [Dockerfile](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/Dockerfile) 是否使用 .net 5。</span><span class="sxs-lookup"><span data-stu-id="53ecb-129">Check sample app [Dockerfile](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/Dockerfile) is using .net 5.</span></span>

<span data-ttu-id="53ecb-130">視主機作業系統而定，aspnet 執行時間可能需要更新。</span><span class="sxs-lookup"><span data-stu-id="53ecb-130">Depending on the host os, the aspnet runtime may need to be updated.</span></span> <span data-ttu-id="53ecb-131">例如， `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` 在 Dockerfile 中變更為，將有助於以適當的 Windows 執行時間為目標。</span><span class="sxs-lookup"><span data-stu-id="53ecb-131">For example, changing from `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` to `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` in the Dockerfile will help with targeting the appropriate Windows runtime.</span></span>

<span data-ttu-id="53ecb-132">例如，這將有助於在 Windows 上測試憑證：</span><span class="sxs-lookup"><span data-stu-id="53ecb-132">For example, this will help with testing the certificates on Windows:</span></span>

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

<span data-ttu-id="53ecb-133">如果我們要在 Linux 上測試憑證，您可以使用現有的 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="53ecb-133">If we're testing the certificates on Linux, you can use the existing Dockerfile.</span></span>

<span data-ttu-id="53ecb-134">請確定 `aspnetapp.csproj` 包含適當的目標架構：</span><span class="sxs-lookup"><span data-stu-id="53ecb-134">Make sure the `aspnetapp.csproj` includes the appropriate target framework:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

> [!NOTE]
> <span data-ttu-id="53ecb-135">如果您想要使用 dotnet publish 參數來 *修剪* 部署，您應該確保包含適當的相依性以支援 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="53ecb-135">If you're looking to use dotnet publish parameters to *trim* the deployment, you should make sure that the appropriate dependencies are included for supporting SSL certificates.</span></span>
<span data-ttu-id="53ecb-136">更新 [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) ，以確定容器中包含適當的元件。</span><span class="sxs-lookup"><span data-stu-id="53ecb-136">Update the [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) to ensure that the appropriate assemblies are included in the container.</span></span> <span data-ttu-id="53ecb-137">如需參考，請參閱在針對獨立式部署使用修剪時，如何更新 .csproj 檔案以 [支援 ssl 憑證](../deploying/trim-self-contained.md#support-for-ssl-certificates) 。</span><span class="sxs-lookup"><span data-stu-id="53ecb-137">For reference, check how to update the .csproj file to [support ssl certificates](../deploying/trim-self-contained.md#support-for-ssl-certificates) when using trimming for self-contained deployments.</span></span>

<span data-ttu-id="53ecb-138">請確定您是指向範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="53ecb-138">Make sure you're pointing to the sample app.</span></span>

```console
cd .\dotnet-docker\samples\aspnetapp
```

<span data-ttu-id="53ecb-139">在本機建立容器以進行測試。</span><span class="sxs-lookup"><span data-stu-id="53ecb-139">Build the container for testing locally.</span></span>

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

## <a name="create-a-self-signed-certificate-with-dotnet-dev-certs"></a><span data-ttu-id="53ecb-140">使用 dotnet dev 憑證建立自我簽署憑證</span><span class="sxs-lookup"><span data-stu-id="53ecb-140">Create a self-signed certificate with dotnet dev-certs</span></span>

<span data-ttu-id="53ecb-141">您可以使用 `dotnet dev-certs` 來處理自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="53ecb-141">You can use `dotnet dev-certs` to work with self-signed certificates.</span></span> <span data-ttu-id="53ecb-142">此範例會使用 PowerShell 主控台。</span><span class="sxs-lookup"><span data-stu-id="53ecb-142">This example uses a PowerShell console.</span></span>

```console
dotnet dev-certs https -ep $env:USERPROFILE\.aspnet\https\aspnetapp.pfx -p crypticpassword
dotnet dev-certs https --trust
```

> [!NOTE]
> <span data-ttu-id="53ecb-143">憑證名稱，在此情況下， *aspnetapp* 必須符合專案元件名稱。</span><span class="sxs-lookup"><span data-stu-id="53ecb-143">The certificate name, in this case *aspnetapp*.pfx must match the project assembly name.</span></span> <span data-ttu-id="53ecb-144">`crypticpassword` 可做為您自己選擇之密碼的獨立。</span><span class="sxs-lookup"><span data-stu-id="53ecb-144">`crypticpassword` is used as a stand-in for a password of your own choosing.</span></span> <span data-ttu-id="53ecb-145">如果主控台傳回「有效的 HTTPS 憑證已存在」，表示您的存放區中已經有受信任的憑證。</span><span class="sxs-lookup"><span data-stu-id="53ecb-145">If console returns "A valid HTTPS certificate is already present.", a trusted certificate already exists in your store.</span></span> <span data-ttu-id="53ecb-146">您可以使用 MMC 主控台來匯出它。</span><span class="sxs-lookup"><span data-stu-id="53ecb-146">It can be exported using MMC Console.</span></span>

<span data-ttu-id="53ecb-147">設定憑證的應用程式密碼：</span><span class="sxs-lookup"><span data-stu-id="53ecb-147">Configure application secrets, for the certificate:</span></span>

```console
dotnet user-secrets -p aspnetapp\aspnetapp.csproj set "Kestrel:Certificates:Development:Password" "crypticpassword"
```

> [!NOTE]
> <span data-ttu-id="53ecb-148">注意：密碼必須符合憑證所用的密碼。</span><span class="sxs-lookup"><span data-stu-id="53ecb-148">Note: The password must match the password used for the certificate.</span></span>

<span data-ttu-id="53ecb-149">使用針對 HTTPS 設定的 ASP.NET Core 來執行容器映射：</span><span class="sxs-lookup"><span data-stu-id="53ecb-149">Run the container image with ASP.NET Core configured for HTTPS:</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -v $env:APPDATA\microsoft\UserSecrets\:C:\Users\ContainerUser\AppData\Roaming\microsoft\UserSecrets -v $env:USERPROFILE\.aspnet\https:C:\Users\ContainerUser\AppData\Roaming\ASP.NET\Https mcr.microsoft.com/dotnet/samples:aspnetapp
```

<span data-ttu-id="53ecb-150">應用程式啟動之後，請 `https://localhost:8001` 在您的網頁瀏覽器中流覽至。</span><span class="sxs-lookup"><span data-stu-id="53ecb-150">Once the application starts, navigate to `https://localhost:8001` in your web browser.</span></span>

### <a name="clean-up"></a><span data-ttu-id="53ecb-151">清除</span><span class="sxs-lookup"><span data-stu-id="53ecb-151">Clean up</span></span>

<span data-ttu-id="53ecb-152">如果秘密和憑證不在使用中，請務必將其清除。</span><span class="sxs-lookup"><span data-stu-id="53ecb-152">If the secrets and certificates are not in use, be sure to clean them up.</span></span>

```console
dotnet user-secrets remove "Kestrel:Certificates:Development:Password" -p aspnetapp\aspnetapp.csproj
dotnet dev-certs https --clean
```

## <a name="create-a-self-signed-certificate-with-powershell"></a><span data-ttu-id="53ecb-153">使用 PowerShell 建立自我簽署憑證</span><span class="sxs-lookup"><span data-stu-id="53ecb-153">Create a self-signed certificate with PowerShell</span></span>

<span data-ttu-id="53ecb-154">您可以使用 PowerShell 來產生自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="53ecb-154">You can use PowerShell to generate self-signed certificates.</span></span> <span data-ttu-id="53ecb-155">[PKI 用戶端](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps&preserver-view=true)可以用來產生自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="53ecb-155">The [PKI Client](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps&preserver-view=true) can be used to generate a self-signed certificate.</span></span>

```powershell
$cert = New-SelfSignedCertificate -DnsName @("contoso.com", "www.contoso.com") -CertStoreLocation "cert:\LocalMachine\My"
```

<span data-ttu-id="53ecb-156">將會產生憑證，但基於測試目的，您應該將它放在憑證存放區中，以在瀏覽器中進行測試。</span><span class="sxs-lookup"><span data-stu-id="53ecb-156">The certificate will be generated, but for the purposes of testing, should be placed in a cert store for testing in a browser.</span></span>

```powershell
$certKeyPath = "c:\certs\contoso.com.pfx"
$password = ConvertTo-SecureString 'password' -AsPlainText -Force
$cert | Export-PfxCertificate -FilePath $certKeyPath -Password $password
$rootCert = $(Import-PfxCertificate -FilePath $certKeyPath -CertStoreLocation 'Cert:\LocalMachine\Root' -Password $password)
```

<span data-ttu-id="53ecb-157">此時，應該可以從 [MMC 嵌入式管理](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)單元查看憑證。</span><span class="sxs-lookup"><span data-stu-id="53ecb-157">At this point, the certificates should be viewable from an [MMC snap-in](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

<span data-ttu-id="53ecb-158">您可以在 Windows 子系統 Linux 版 (WSL) 中執行範例容器：</span><span class="sxs-lookup"><span data-stu-id="53ecb-158">You can run the sample container in Windows Subsystem for Linux (WSL):</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> <span data-ttu-id="53ecb-159">請注意，磁片區掛接可能會以不同的主機為基礎來處理檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="53ecb-159">Note that with the volume mount the file path could be handled differently based on host.</span></span>  <span data-ttu-id="53ecb-160">例如，在 WSL 中，我們可能會將 */c/certs* 取代為 */mnt/c/certs*。</span><span class="sxs-lookup"><span data-stu-id="53ecb-160">For example, in WSL we may replace */c/certs* with */mnt/c/certs*.</span></span>

<span data-ttu-id="53ecb-161">如果您使用先前為 Windows 建立的容器，則 [執行] 命令看起來會如下所示：</span><span class="sxs-lookup"><span data-stu-id="53ecb-161">If you're using the container built earlier for Windows, the run command would look like the following:</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="53ecb-162">應用程式啟動後，請在瀏覽器中流覽至 contoso.com:8001。</span><span class="sxs-lookup"><span data-stu-id="53ecb-162">Once the application is up, navigate to contoso.com:8001 in a browser.</span></span>

<span data-ttu-id="53ecb-163">請確定主項目目已更新，以便 `contoso.com` 在適當的 ip 位址上接聽 (例如 127.0.0.1) 。</span><span class="sxs-lookup"><span data-stu-id="53ecb-163">Be sure that the host entries are updated for `contoso.com` to answer on  the appropriate ip address (for example 127.0.0.1).</span></span> <span data-ttu-id="53ecb-164">如果無法辨識憑證，請確定主機上的容器所載入的憑證也受信任，而且有適當的 SAN/DNS 專案 `contoso.com` 。</span><span class="sxs-lookup"><span data-stu-id="53ecb-164">If the certificate isn't recognized, make sure that the certificate that is loaded with the container is also trusted on the host, and that there's appropriate SAN / DNS entries for `contoso.com`.</span></span>

### <a name="clean-up"></a><span data-ttu-id="53ecb-165">清除</span><span class="sxs-lookup"><span data-stu-id="53ecb-165">Clean up</span></span>

```powershell
$cert | Remove-Item
Get-ChildItem $certFilePath | Remove-Item
$rootCert | Remove-item
```

## <a name="create-a-self-signed-certificate-with-openssl"></a><span data-ttu-id="53ecb-166">使用 OpenSSL 建立自我簽署憑證</span><span class="sxs-lookup"><span data-stu-id="53ecb-166">Create a self-signed certificate with OpenSSL</span></span>

<span data-ttu-id="53ecb-167">您可以使用 [OpenSSL](https://www.openssl.org/) 來建立自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="53ecb-167">You can use [OpenSSL](https://www.openssl.org/) to create self-signed certificates.</span></span> <span data-ttu-id="53ecb-168">此範例將搭配使用 WSL/Ubuntu 和 bash shell `OpenSSL` 。</span><span class="sxs-lookup"><span data-stu-id="53ecb-168">This example will use WSL / Ubuntu and a bash shell with `OpenSSL`.</span></span>

<span data-ttu-id="53ecb-169">這會產生 .crt 和金鑰。</span><span class="sxs-lookup"><span data-stu-id="53ecb-169">This will generate a .crt and a .key.</span></span>

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

<span data-ttu-id="53ecb-170">若要取得 .pfx，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="53ecb-170">To get a .pfx, use the following command:</span></span>

```bash
openssl pkcs12 -export -out $PARENT.pfx -inkey $PARENT.key -in $PARENT.crt
```

> [!NOTE]
> <span data-ttu-id="53ecb-171">Aspnetcore 3.1 範例將使用 `.pfx` 和密碼。</span><span class="sxs-lookup"><span data-stu-id="53ecb-171">The .aspnetcore 3.1 example will use `.pfx` and a password.</span></span> <span data-ttu-id="53ecb-172">從 `.net 5` 執行時間開始，Kestrel 也可以採用 `.crt` 和 PEM 編碼的檔案 `.key` 。</span><span class="sxs-lookup"><span data-stu-id="53ecb-172">Starting with the `.net 5` runtime, Kestrel can also take `.crt` and PEM-encoded `.key` files.</span></span>

<span data-ttu-id="53ecb-173">視主機作業系統而定，憑證將必須受信任。</span><span class="sxs-lookup"><span data-stu-id="53ecb-173">Depending on the host os, the certificate will need to be trusted.</span></span> <span data-ttu-id="53ecb-174">在 Linux 主機上，「信任」憑證是不同的，而且發行版本相依。</span><span class="sxs-lookup"><span data-stu-id="53ecb-174">On a Linux host, 'trusting' the certificate is different and distro dependent.</span></span>

<span data-ttu-id="53ecb-175">基於本指南的目的，以下是使用 PowerShell 的 Windows 範例：</span><span class="sxs-lookup"><span data-stu-id="53ecb-175">For the purposes of this guide, here's an example in Windows using PowerShell:</span></span>

```powershell
Import-Certificate -FilePath $certFilePath -CertStoreLocation 'Cert:\LocalMachine\Root'
```

<span data-ttu-id="53ecb-176">若為 .NET Core 3.1，請在 WSL 中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="53ecb-176">For .NET Core 3.1, run the following command in WSL:</span></span>

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/path/to/certs/:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

<span data-ttu-id="53ecb-177">從 .NET 5 開始，Kestrel 可以採用 `.crt` 和 PEM 編碼的檔案 `.key` 。</span><span class="sxs-lookup"><span data-stu-id="53ecb-177">Starting with .NET 5, Kestrel can take the `.crt` and PEM-encoded `.key` files.</span></span> <span data-ttu-id="53ecb-178">您可以使用下列適用于 .NET 5 的命令來執行範例：</span><span class="sxs-lookup"><span data-stu-id="53ecb-178">You can run the sample with the following command for .NET 5:</span></span>

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=/https/contoso.com.key -v /c/path/to/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> <span data-ttu-id="53ecb-179">請注意，在 WSL 中，磁片區掛接路徑可能會根據設定而變更。</span><span class="sxs-lookup"><span data-stu-id="53ecb-179">Note that in WSL, the volume mount path may change depending on the configuration.</span></span>

<span data-ttu-id="53ecb-180">針對 Windows 中的 .NET Core 3.1，請在中執行下列命令 `Powershell` ：</span><span class="sxs-lookup"><span data-stu-id="53ecb-180">For .NET Core 3.1 in Windows, run the following command in `Powershell`:</span></span>

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="53ecb-181">針對 Windows 中的 .NET 5，請在 PowerShell 中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="53ecb-181">For .NET 5 in Windows, run the following command in PowerShell:</span></span>

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=c:\https\contoso.com.key -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="53ecb-182">應用程式啟動後，請在瀏覽器中流覽至 contoso.com:8001。</span><span class="sxs-lookup"><span data-stu-id="53ecb-182">Once the application is up, navigate to contoso.com:8001 in a browser.</span></span>

<span data-ttu-id="53ecb-183">請確定主項目目已更新，以便 `contoso.com` 在適當的 ip 位址上接聽 (例如 127.0.0.1) 。</span><span class="sxs-lookup"><span data-stu-id="53ecb-183">Be sure that the host entries are updated for `contoso.com` to answer on  the appropriate ip address (for example 127.0.0.1).</span></span> <span data-ttu-id="53ecb-184">如果無法辨識憑證，請確定主機上的容器所載入的憑證也受信任，而且有適當的 SAN/DNS 專案 `contoso.com` 。</span><span class="sxs-lookup"><span data-stu-id="53ecb-184">If the certificate isn't recognized, make sure that the certificate that is loaded with the container is also trusted on the host, and that there's appropriate SAN / DNS entries for `contoso.com`.</span></span>

### <a name="clean-up"></a><span data-ttu-id="53ecb-185">清除</span><span class="sxs-lookup"><span data-stu-id="53ecb-185">Clean up</span></span>

<span data-ttu-id="53ecb-186">完成測試之後，請務必清除自我簽署的憑證。</span><span class="sxs-lookup"><span data-stu-id="53ecb-186">Be sure to clean up the self-signed certificates once done testing.</span></span>

```powershell
Get-ChildItem $certFilePath | Remove-Item
```

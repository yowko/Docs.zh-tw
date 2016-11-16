---
title: "將 ASP.NET MVC 應用程式遷移到 Windows 容器"
description: "了解如何擷取現有的 ASP.NET MVC 應用程式並在 Windows Docker 容器中執行"
keywords: "Windows Docker 容器, Docker, ASP.NET MVC"
author: BillWagner
manager: wpickett
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net-framework-4.6
ms.technology: dotnet-mvc
ms.devlang: dotnet
ms.assetid: c9f1d52c-b4bd-4b5d-b7f9-8f9ceaf778c4
translationtype: Human Translation
ms.sourcegitcommit: 15c55a87beb64f265a164db918c7721c7690fadf
ms.openlocfilehash: bde267042883d2f25848747047845a16b181e549

---

# <a name="migrating-aspnet-mvc-applications-to-windows-containers"></a>將 ASP.NET MVC 應用程式遷移到 Windows 容器

若要在 Windows 容器中執行現有的 .NET Framework 架構應用程式，您必須建立包含應用程式的 Docker 映像，並啟動要執行該映像的一或多個容器。 本主題說明您必須執行才能擷取現有 [ASP.NET MVC 應用程式](http://www.asp.net/mvc) 並部署到 Windows 容器中的工作。

您將從現有的 ASP.NET MVC 應用程式開始。 然後使用 Visual Studio 建立已發行的資產。 您將使用 Docker 建立映像，該映像包含您的應用程式，而且會在啟動時執行該應用程式。 完成後，您可以將瀏覽器連線到 Windows 容器中正在執行的網站，並確認應用程式正在執行。

本文假設您具備 Docker 的基本知識。 如果不熟悉這些概念，您可以閱讀 Docker 網站上的 [Docker Overview](https://docs.docker.com/engine/understanding-docker/)，以深入了解 Docker 架構。

您將在容器中執行的應用程式是隨機回答問題的簡單網站。 此應用程式是未支援驗證的基本 MVC 應用程式，或資料庫儲存體，讓您著重於將 Web 層移至容器。 未來的主題將說明如何移動和管理容器化應用程式中的永續性儲存體。

移動您的應用程式包含下列步驟：

1. [建立發行工作以建置映像資產](#publish-script)
2. [建立用以執行應用程式的 Docker 映像](#build-the-image)
3. [啟動執行映像的 Docker 容器](#start-a-container)
4. [使用瀏覽器確認應用程式](#verify-in-the-browser)

完成的應用程式位於 [GitHub 上的 dotnet/core-docs 儲存機制](https://github.com/dotnet/docs/tree/master/samples/framework/docker/MVCRandomAnswerGenerator)。

## <a name="prerequisites"></a>必要條件

您的開發電腦至少必須執行 [Windows 10 年度更新版](https://www.microsoft.com/en-us/software-download/windows10/)或 [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server)。 

開始之前，您必須安裝 [Docker for Windows](https://docs.docker.com/docker-for-windows/) 1.12 Beta 26 版或更新版本。 目前只有 Beta 版提供 Windows 容器支援。

> [!IMPORTANT]
> 如果您使用 Windows Server 2016，您必須遵循[容器主機部署 - Windows Server](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/deployment/deployment) 的指示，才能執行 Docker 容器。

安裝並啟動 Docker 之後，您必須以滑鼠右鍵按一下系統匣圖示，然後選取 [切換至 Windows 容器]，才能執行以 Windows 為基礎的 Docker 映像。 此命令需要幾秒鐘的時間執行：

![Windows 容器][windows-container]

## <a name="publish-script"></a>發行指令碼

第一個步驟是取得您必須載入一個位置之 Docker 映像的所有資產。 幸運的是，您可以使用 Visual Studio 的 [發行] 命令來建立應用程式的發行設定檔。 此設定檔會將所有資產放在一個樹狀目錄中，您將在本教學課程稍後複製此目錄到目標映像。

**發行步驟**

1. 以滑鼠右鍵按一下 Visual Studio 中的 Web 專案，然後選取 [發行]。
2. 按一下 [自訂設定檔] 按鈕，然後選取 [檔案系統] 作為方法。
3. 選擇目錄。 依照慣例，下載的範例會使用 `bin/PublishOutput`。

![發行連線][publish-connection]

接下來，開啟 [設定] 索引標籤的 [檔案發行選項] 區段。 選取 [發行期間預先編譯]。 此最佳化表示您要編譯 Docker 容器中的檢視，您將複製預先編譯的檢視。

![發行設定][publish-settings]

按一下 [發行]，Visual Studio 會將所有需要的資產複製到目的資料夾。 

## <a name="build-the-image"></a>建立映像

您會在 Dockerfile 中定義 Docker 映像，其中包含基礎映像、任何其他元件、您要執行之應用程式及其他組態映像的相關指示。  Dockerfile 是建立映像之 `docker build` 命令的輸入。

您將以位於 [Docker Hub](https://hub.docker.com/r/microsoft/aspnet/) 上的 `microsft/aspnet` 映像為基礎來建立映像。
基礎映像 `microsoft/aspnet` 是 Windows Server 映像。 除了 Windows Server Core 之外，它也已安裝並啟用 IIS 和 ASP.NET 4.6.2。 當您在容器中執行此映像時，它將會自動啟動 IIS，而且任何安裝的網站都將啟動。

建立映像的 Dockerfile 看起來像這樣：

```
# The `FROM` instruction specifies the base image. You are
# extending the `microsoft/aspnet` image.

FROM microsoft/aspnet

# Next, this Dockerfile creates a directory for your application
RUN mkdir C:\randomanswers

# configure the new site in IIS.
RUN powershell -NoProfile -Command \
    Import-module IISAdministration; \
    New-IISSite -Name "ASPNET" -PhysicalPath C:\randomanswers -BindingInformation "*:8000:"

# This instruction tells the container to listen on port 8000. 
EXPOSE 8000

# The final instruction copies the site you published earlier into the container.
ADD containerImage/ /randomanswers
```

此 Dockerfile 中沒有 `ENTRYPOINT` 命令。 您不需要此命令。
基礎映像可確保當容器啟動時，IIS 會啟動。 

接下來，您必須執行 Docker 的建立命令來建立映像，以執行您的 ASP.NET 應用程式。 若要這樣做，請開啟 PowerShell 視窗，然後在方案目錄中輸入下列命令：

```
docker build -t mvcrandomanswers .
```

此命令將遵循 Dockerfile 中的指示建立新的映像。 這可能包括從 [Docker Hub](http://hub.docker.com) 提取基礎映像，然後它會將應用程式加入該映像。

該命令完成之後，您可以執行 `docker images` 命令來了解新映像的相關資訊：

```
REPOSITORY                    TAG                 IMAGE ID            CREATED             SIZE
mvcrandomanswers              latest              86838648aab6        2 minutes ago       8.104 GB
```

您電腦上的映像識別碼會有所不同。 現在，讓我們執行應用程式。

## <a name="start-a-container"></a>啟動容器

您可以執行下列 `docker run` 命令來啟動容器：

```
docker run -d -p 8000:8000 --name randomanswers mvcrandomanswers
```

`-d` 引數會指示 Docker 在離線模式中啟動映像。 這表示 Docker 映像可在與目前殼層中斷連線的情況下執行。

`-p 8000:8000` 引數會指示 Docker 如何對應傳入通訊埠。 在此範例中，我們將在主機和容器上使用通訊埠 8000。

`--name randomanswers` 提供執行中容器的名稱。 您可以使用此名稱，而不是大多數命令中的容器識別碼。

`mvcrandomanswers` 是要啟動之映像的名稱。

## <a name="verify-in-the-browser"></a>在瀏覽器中確認

> [!NOTE]
> 在目前的版本中，您無法使用 `http://localhost` 瀏覽至您的網站。 這是因為 WinNAT 中的已知行為，未來將會解決此問題。 在解決此問題之前，您必須使用容器的 IP 位址。

容器啟動之後，您必須尋找其 IP 位址，才能從瀏覽器連線到您正在執行的容器：

```
docker inspect -f "{{ .NetworkSettings.Networks.nat.IPAddress }}" randomanswers
172.31.194.61
```

您可以使用 IPv4 位址及上述範例中已設定的通訊埠 (8000) `http://172.31.194.61:8000`，連線到執行中的容器。 在您的瀏覽器中輸入該 URL，您應該會看到執行中的網站。

> [!NOTE]
> 某些 VPN 或 Proxy 軟體可能會阻止您瀏覽至您的網站。
> 您可以暫時停用，以確保您的容器可以正常運作。

GitHub 上的範例目錄包含 [PowerShell 指令碼](https://github.com/dotnet/docs/tree/master/samples/framework/docker/MVCRandomAnswerGenerator/run.ps1)，可為您執行這些命令。 開啟 PowerShell 視窗，將目錄變更為您的方案目錄，然後輸入：

```
./run.ps1
```

它會建立映像、顯示您電腦上的映像清單、啟動容器，然後顯示該容器的 IP 位址。 

如果您想要在完成後停止容器，請發出 `docker
stop` 命令：

```
docker stop randomanswers
```

若要移除容器，請發出 `docker rm` 命令：

```
docker rm randomanswers
```

## <a name="summary"></a>總結

在本主題中，您已了解在 Windows Server 容器中移動及執行現有 ASP.NET MVC 應用程式的步驟。 執行現有的應用程式不需要對您的應用程式進行任何變更。 您必須執行工作來發行您的應用程式、建立 Docker 映像，並在新的容器中啟動該映像。 利用 Windows Server 容器是將您現有的應用程式遷移到此環境的最簡單路徑。

[windows-container]: media/aspnetmvc/SwitchContainer.png "切換至 Windows 容器"
[publish-connection]: media/aspnetmvc/PublishConnection.png "發行至檔案系統"
[publish-settings]: media/aspnetmvc/PublishSettings.png "發行設定"



<!--HONumber=Nov16_HO1-->



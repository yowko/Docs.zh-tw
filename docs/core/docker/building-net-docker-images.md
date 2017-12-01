---
title: "建置 .NET Core Docker 映像"
description: "了解 Docker 映像和 .NET Core"
keywords: ".NET、.NET Core、Docker"
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.openlocfilehash: 3ec2d5a58b46e332de41b618f1c3fac663b29bee
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2017
---
# <a name="building-docker-images-for-net-core-applications"></a>建置 .NET Core 應用程式的 Docker 映像

 在本教學課程中，我們會著重在如何使用.NET 核心上 Docker。 首先，我們會探討不同的 Docker images 提供及維護 Microsoft，並使用案例。 然後，我們會了解如何建置和 dockerize ASP.NET Core 應用程式。

本教學課程的過程中，您了解：
> [!div class="checklist"]
> * 深入了解 Microsoft.NET Core Docker 映像 
> * 取得 ASP.NET Core Dockerize 範例應用程式
> * 在本機上執行 ASP.NET 範例應用程式
> * 建置及執行範例，以 Docker 的 Linux 容器
> * 建置及執行範例，以 Docker for Windows 容器

## <a name="docker-image-optimizations"></a>Docker 映像最佳化

在建置開發人員的 Docker 映像時，我們會著重在三個主要案例︰

* 用來開發 .NET Core 應用程式的映像
* 用來建置 .NET Core 應用程式的映像
* 用來執行 .NET Core 應用程式的映像

為何是三個映像？
當開發、 建置及執行容器化應用程式時，我們會有不同的優先權。

* **開發：**優先順序著重於快速地逐一查看變更，以及偵錯所做的變更的功能。 映像大小並不重要，而是可以變更您的程式碼並快速看到它們嗎？

* **組建中：**此映像包含編譯您的應用程式，其中包含編譯器及最佳化的二進位檔的任何其他相依性所需的所有項目。  您可以使用建置映像來建立您放入實際執行映像的資產。 會用於建置映像，持續整合，或在建置環境。 這個方法可讓組建代理程式可編譯及建立應用程式 （具有所有必要的相依性） 中建置的映像執行個體。 組建代理程式只需要知道如何執行此 Docker 映像。

* **生產環境：**方式快速部署和啟動您的映像嗎？ 此映像很小，因此從 Docker 登錄您的 Docker 主機的網路效能會最佳化。 準備好執行的內容可用最短的時間完成 Docker 執行到處理結果。 Docker 模型中，不需要動態程式碼編譯。 您放置在此映像中的內容會限於執行應用程式所需的二進位檔和內容。

    例如，`dotnet publish`輸出包含：

    * 已編譯的二進位檔
    * .js 和.css 檔案


要包含的原因`dotnet publish`生產映像中的命令輸出都是要保留其 ' 大小為最小值。

某些.NET Core 映像共用層之間不同的標記，以便下載最新的標籤是一個相當輕便的程序。 如果您已經在電腦上有較舊的版本，此架構會減少所需的磁碟空間。

當多個應用程式使用同一部電腦上的通用映像時，常見的映像之間會共用記憶體。 影像必須是共用相同。

## <a name="docker-image-variations"></a>Docker 映像變化

為了達成上述目標，我們會提供下的映像變異[ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/)。

* `microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) 這個映像包含.NET Core SDK，其中包含.NET Core 和命令列工具 (CLI)。 此映像會對應至**開發案例**。 您可以使用此映像的本機開發、 偵錯和執行單元測試。 此映像也可用於**建置**案例。 使用`microsoft/dotnet:sdk`一律提供最新版本。

> [!TIP]
> 您不確定您的需求有關，如果您想要使用`microsoft/dotnet:<version>-sdk`映像。 做為 「 既定 」 影像，它的設計是要做為擲回離開容器 （裝載您的原始程式碼，啟動容器啟動應用程式），以及做為基礎的映像，以建立從其他映像。

* `microsoft/dotnet:<version>-runtime`： 此映像包含.NET Core （執行階段和程式庫），而且會在執行.NET Core 應用程式的最佳化**生產**。

## <a name="alternative-images"></a>替代的映像

除了開發、建置和生產環境的最佳化案例，我們還提供其他映像︰

* `microsoft/dotnet:<version>-runtime-deps`:**執行階段 deps**映像包含作業系統的所有原生.NET Core 所需的相依性。 此映像為[各自獨立的應用程式](https://docs.microsoft.com/dotnet/core/deploying/index)。

每個變體的最新版本︰

* `microsoft/dotnet`或`microsoft/dotnet:latest`（別名 SDK 映像）
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a>若要瀏覽範例

* [此範例中 ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp)示範建置 Docker images，適用於 ASP.NET Core 實際執行的應用程式的最佳作法模式。 範例適用於 Linux 和 Windows 容器。

* 這個.NET Core Docker 範例會示範的最佳作法模式[建置.NET Core 應用程式的實際執行的 Docker 映像。](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)

## <a name="your-first-aspnet-core-docker-app"></a>第一個 ASP.NET Core Docker 應用程式

本教學課程，可讓您使用 ASP.NET Core Docker 範例應用程式，我們想要 dockerize 應用程式。 這個 ASP.NET Core Docker 範例應用程式示範如何建置 Docker images，適用於 ASP.NET Core 實際執行的應用程式的最佳作法模式。 範例適用於 Linux 和 Windows 容器。

範例 Dockerfile 建立 ASP.NET Core 執行階段 Docker 基底映像所依據的 ASP.NET Core 應用程式 Docker 映像。

它會使用[Docker 多階段建置功能](https://docs.docker.com/engine/userguide/eng-image/multistage-build/)至：

* 建立容器，根據在範例**較大**ASP.NET Core 建置 Docker 基底映像 
* 複製到 Docker 映像為基礎的最後一個組建結果**小**ASP.NET Core Docker 執行階段基底映像

> [!Note]
> 建置映像包含建置應用程式，但不會執行階段映像的必要的工具。

### <a name="prerequisites"></a>必要條件

若要建置並執行，安裝下列項目：

#### <a name="net-core-20-sdk"></a>.NET 核心 2.0 SDK

* 安裝[.NET Core SDK 2.0](https://www.microsoft.com/net/core)。

* 如果您還沒有這麼做，請安裝您最愛的程式碼編輯器 中。

> [!TIP]
> 需要安裝的程式碼編輯器？ 再試一次[Visual Studio](https://visualstudio.com/downloads)！

#### <a name="installing-docker-client"></a>安裝 Docker 用戶端

安裝[Docker 17.06](https://docs.docker.com/release-notes/docker-ce/)或更新版本的 Docker 用戶端。

Docker 用戶端可以安裝在：

* Linux 散發套件

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/)。

#### <a name="installing-git-for-sample-repository"></a>安裝適用於範例儲存機制的 Git

* 安裝[git](https://git-scm.com/download)如果您想要複製儲存機制。

### <a name="getting-the-sample-application"></a>取得範例應用程式

取得範例的最簡單方式是藉由複製[範例儲存機制](https://github.com/dotnet/dotnet-docker-samples)使用 git，請使用下列指示： 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

您也可以下載.NET Core Docker 範例儲存機制從 zip （它是小型的） 儲存機制。

### <a name="run-the-aspnet-app-locally"></a>在本機執行的 ASP.NET 應用程式

針對參考點，在將應用程式放入容器前，要先在本機執行應用程式。

您可以建置及執行應用程式在本機使用.NET 核心 2.0 SDK 使用下列命令 （的指示會假設儲存機制的根目錄）：

```console
cd aspnetapp
dotnet run
```

在應用程式啟動之後，請瀏覽**http://localhost:5000/** web 瀏覽器中。

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a>建置及執行範例，以 Docker 的 Linux 容器

您可以建置及執行 Docker 使用 Linux 容器，使用下列命令 （的指示會假設儲存機制的根目錄） 中的範例：

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!Note] `docker run` '-P' 引數對應連接埠的通訊埠 80 的容器中本機電腦上的 5000 (連接埠對應表單`host:container`)。 如需詳細資訊，請參閱[執行 docker](https://docs.docker.com/engine/reference/commandline/exec/)命令列參數的參考。

在應用程式啟動之後，請瀏覽**http://localhost:5000/** web 瀏覽器中。

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a>建置及執行範例，以 Docker for Windows 容器

您可以建置及執行 Docker 使用 Windows 容器，使用下列命令 （的指示會假設儲存機制的根目錄） 中的範例：

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> 您必須瀏覽至**容器 IP 位址**（相對於 http://localhost) 直接瀏覽器中使用 Windows 容器時。 您可以取得 IP 位址，您的容器進行下列步驟：

* 開啟另一個命令提示字元。
* 執行`docker ps`以查看您執行中的容器。 應該有"aspnetcore_sample 」 容器。
* 執行 `docker exec aspnetcore_sample ipconfig`。
* 複製的容器 IP 位址並貼到您的瀏覽器 (例如，172.29.245.43)。

> [!Note]
> Docker exec 支援雜湊或名稱識別的容器。 在本例中，會使用名稱 (aspnetcore_sample)。

請參閱下列如何取得執行中的 Windows 容器的 IP 位址的範例。

```console
docker exec aspnetcore_sample ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
```

> [!Note]
> Docker exec 執行新的命令在執行中的容器。 如需詳細資訊，請參閱[docker exec 參考](https://docs.docker.com/engine/reference/commandline/exec/)命令列參數。

您可以產生應用程式準備好要部署到生產環境使用在本機的[dotnet 發行](../tools/dotnet-publish.md)命令。

```console
dotnet publish -c release -o published
```

> [!Note]
> -C 的版本引數建置 （預設值是偵錯模式） 的發行模式中的應用程式。 如需詳細資訊，請參閱[dotnet 執行參考](../tools/dotnet-run.md)命令列參數。

您可以在執行應用程式**Windows**使用下列命令。

```console
dotnet published\aspnetapp.dll
```

您可以在執行應用程式**Linux**或**macOS**使用下列命令。

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a>此範例中使用的 docker 映像

在此範例中使用下列的 Docker 映像

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

恭喜您！ 只要有：
> [!div class="checklist"]
> * 學到的 Microsoft.NET Core Docker 映像
> * 取得 ASP.NET Core Dockerize 範例應用程式
> * 在本機執行 ASP.NET 範例應用程式
> * 建置和執行 Linux 容器與 Docker 的範例
> * 建置和執行範例與 Docker for Windows 容器


**接下來的步驟**

以下是一些您可以採取的後續步驟：

* [使用 Visual Studio Docker 工具](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [將從 Azure 容器登錄至 Azure 容器執行個體的 Docker 映像部署](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [使用 Visual Studio 程式碼進行偵錯](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [未授權者手上取得使用 Visual Studio for Mac、 容器和無伺服器的程式碼在雲端中](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [開始使用 Docker 和 Visual Studio for Mac 實驗室](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!Note]
> 如果您沒有 Azure 訂用帳戶，[立即註冊](https://azure.microsoft.com/free/?b=16.48)免費 30 天的帳戶和 Azure 信用額度試用 Azure 服務的任何組合中的 get 美金 200。

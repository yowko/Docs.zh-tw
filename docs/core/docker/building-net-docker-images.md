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
ms.workload:
- dotnetcore
ms.openlocfilehash: 2b1a57fe264eda0a4d3186c7be8b0de01bd5f0a9
ms.sourcegitcommit: c1904b0437605a90e5aa65b4abd7e048000e349d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2018
---
# <a name="building-docker-images-for-net-core-applications"></a>建置 .NET Core 應用程式的 Docker 映像

 在本教學課程中，著重在如何於 Docker 上使用 .NET Core。 首先，我們會探討 Microsoft 所提供及維護的不同 Docker 映像，以及使用案例。 我們接著會了解如何建置和 Docker 化 ASP.NET Core 應用程式。

您會在本教學課程中了解︰
> [!div class="checklist"]
> * 了解 Microsoft .NET Core Docker 映像 
> * 取得要 Docker 化的 ASP.NET Core 範例應用程式
> * 在本機執行 ASP.NET 範例應用程式
> * 使用 Docker for Linux 容器來建置並執行範例
> * 使用 Docker for Windows 容器來建置並執行範例

## <a name="docker-image-optimizations"></a>Docker 映像最佳化

在建置開發人員的 Docker 映像時，我們會著重在三個主要案例︰

* 用來開發 .NET Core 應用程式的映像
* 用來建置 .NET Core 應用程式的映像
* 用來執行 .NET Core 應用程式的映像

為何是三個映像？
在開發、建置和執行容器化應用程式時，我們有不同的優先考量。

* **開發︰**優先順序快速聚焦於逐一查看變更以及偵錯變更的能力。 映像大小不那麼重要，而是變更及查看程式碼的速度。

* **建置：**此映像包含編譯您應用程式所需的所有項目，其中包含編譯器以及最佳化二進位檔的任何其他相依性。  您可以使用組建映像來建立您放入生產映像的資產。 組建映像將用於持續整合或組建環境。 此方法可讓組建代理程式在組建映像執行個體中編譯和建置應用程式 (含所有必要相依性)。 組建代理程式只需要知道如何執行此 Docker 映像。

* **生產︰**多快可以部署和啟動映像？ 此映像很小，因此最小化從 Docker 登錄到 Docker 主機的網路效能。 準備好執行的內容可用最短的時間完成 Docker 執行到處理結果。 在 Docker 模型中，不需要動態程式碼編譯。 您放置在此映像中的內容會限於執行應用程式所需的二進位檔和內容。

    例如，`dotnet publish` 輸出包含：

    * 已編譯的二進位檔
    * .js 和 .css 檔案


在生產映像中包含 `dotnet publish` 命令輸出的原因是要將其大小保持最小值。

有些 .NET Core 映像共用不同標記之間的層，因此下載最新標記是相當輕量的程序。 如果您的電腦上已經有舊版本，則此架構會減少所需的磁碟空間。

多個應用程式使用同一部電腦上的通用映像時，通用映像之間會共用記憶體。 映像必須相同才能共用。

## <a name="docker-image-variations"></a>Docker 映像變化

為達成上述目標，我們在 [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/) 下提供映像變化。

* `microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) 此映像包含具有 .NET Core 和命令列工具 (CLI) 的 .NET Core SDK。 此映像會對應至**開發案例**。 您可以使用此映像進行本機開發、偵錯和單元測試。 此映像也可用於**建置**案例。 使用 `microsoft/dotnet:sdk` 一律可以提供最新版本。

> [!TIP]
> 如果您不確定需求，則需要使用 `microsoft/dotnet:<version>-sdk` 映像。 作為「既定」映像，其設計是要用作擲離容器 (裝載原始程式碼，並啟動容器來啟動應用程式)，以及用作從中建置其他映像的基底映像。

* `microsoft/dotnet:<version>-runtime`：此映像包含.NET Core (執行階段和程式庫)，以及最佳化以在**生產**中執行 .NET Core 應用程式。

## <a name="alternative-images"></a>替代的映像

除了開發、建置和生產環境的最佳化案例，我們還提供其他映像︰

* `microsoft/dotnet:<version>-runtime-deps`：**runtime-deps** 映像包含作業系統與 .NET Core 所需的所有原生相依性。 此映像適用於[獨立應用程式](https://docs.microsoft.com/dotnet/core/deploying/index)。

每個變體的最新版本︰

* `microsoft/dotnet` 或 `microsoft/dotnet:latest` (SDK 映像的別名)
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a>要探索的範例

* [此 ASP.NET Core Docker 範例](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) \(英文\) 示範建置適用於生產之 ASP.NET Core 應用程式的 Docker 映像的最佳做法模式。 該範例可與 Linux 或 Windows 容器搭配使用。

* 此 .NET Core Docker 範例示範[建置適用於生產之 .NET Core 應用程式的 Docker 映像](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) \(英文\) 的最佳做法模式。

## <a name="your-first-aspnet-core-docker-app"></a>第一個 ASP.NET Core Docker 應用程式

在本教學課程中，將 ASP.NET Core Docker 範例應用程式用於要 Docker 化的應用程式。 此 ASP.NET Core Docker 範例應用程式示範建置適用於生產的 ASP.NET Core 應用程式之 Docker 映像的最佳做法模式。 該範例可與 Linux 或 Windows 容器搭配使用。

範例 Dockerfile 會根據 ASP.NET Core 執行階段 Docker 基底映像來建立 ASP.NET Core 應用程式 Docker 映像。

它會使用 [Docker 多階段建置功能](https://docs.docker.com/engine/userguide/eng-image/multistage-build/)來：

* 根據**較大的** ASP.NET Core 建置 Docker 基底映像，以在容器中建置範例 
* 根據**較小的** ASP.NET Core Docker 執行階段基底映像，以將最終建置結果複製至 Docker 映像

> [!NOTE]
> 組建映像包含建置應用程式但未建置執行階段映像的必要工具。

### <a name="prerequisites"></a>必要條件

若要建置並執行，請安裝下列項目：

#### <a name="net-core-20-sdk"></a>.NET Core 2.0 SDK

* 安裝 [.NET Core SDK 2.0](https://www.microsoft.com/net/core)。

* 如果您還沒有這麼做，請安裝您慣用的程式碼編輯器。

> [!TIP]
> 需要安裝程式碼編輯器嗎？ 試用 [Visual Studio](https://visualstudio.com/downloads)！

#### <a name="installing-docker-client"></a>安裝 Docker 用戶端

安裝 [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) 或更新版本的 Docker 用戶端。

Docker 用戶端可以安裝於：

* Linux 散發

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/).

#### <a name="installing-git-for-sample-repository"></a>安裝適用於範例存放庫的 Git

* 如果您要複製存放庫，請安裝 [git](https://git-scm.com/download)。

### <a name="getting-the-sample-application"></a>取得範例應用程式

取得範例的最簡單方式是使用 git 並使用下列指示，以複製[範例存放庫](https://github.com/dotnet/dotnet-docker-samples)： 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

您也可以從 .NET Core Docker 範例存放庫中，將存放庫下載為 zip (較小)。

### <a name="run-the-aspnet-app-locally"></a>在本機執行 ASP.NET 應用程式

針對參考點，在將應用程式放入容器前，要先在本機執行應用程式。

您可以使用 .NET Core 2.0 SDK 並使用下列命令，以在本機建置和執行應用程式 (這些指示假設存放庫的根目錄)：

```console
cd aspnetapp
dotnet run
```

應用程式啟動之後，請在網頁瀏覽器中瀏覽 **http://localhost:5000**。

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a>使用 Docker for Linux 容器來建置並執行範例

您可以使用 Linux 容器並使用下列命令，以在 Docker 中建置和執行範例 (這些指示假設存放庫的根目錄)：

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> `docker run` '-p' 引數會將您本機電腦上的連接埠 5000 對應至容器中的連接埠 80 (連接埠對應形式為 `host:container`)。 如需詳細資訊，請參閱命令列參數的 [docker run reference](https://docs.docker.com/engine/reference/commandline/exec/)。

應用程式啟動之後，請在網頁瀏覽器中瀏覽 **http://localhost:5000**。

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a>使用 Docker for Windows 容器來建置並執行範例

您可以使用 Windows 容器並使用下列命令，以在 Docker 中建置和執行範例 (這些示假設存放庫的根目錄)：

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> 使用 Windows 容器時，您必須在瀏覽器中直接巡覽至**容器 IP 位址** (相對於 http://localhost)。 您可以使用下列步驟來取得容器的 IP 位址：

* 開啟另一個命令提示字元。
* 執行 `docker ps` 以查看您的執行中容器。 其中應該會有 "aspnetcore_sample" 容器。
* 執行 `docker exec aspnetcore_sample ipconfig`。
* 複製容器 IP 位址，並將其貼入瀏覽器 (例如，172.29.245.43)。

> [!NOTE]
> Docker exec 支援使用名稱或雜湊來識別容器。 在我們的範例中，使用名稱 (aspnetcore_sample)。

請參閱下列有關如何取得執行中 Windows 容器的 IP 位址的範例。

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

> [!NOTE]
> Docker exec 會在執行中容器內執行新的命令。 如需詳細資訊，請參閱命令列參數的 [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/)。

您可以使用 [dotnet publish](../tools/dotnet-publish.md) 命令，以在本機產生準備好部署至生產環境的應用程式。

```console
dotnet publish -c release -o published
```

> [!NOTE]
> -c release 引數會以發行模式建置應用程式 (預設值是偵錯模式)。 如需詳細資訊，請參閱命令列參數的 [dotnet run reference](../tools/dotnet-run.md)。

您可以使用下列命令，在 **Windows** 上執行應用程式。

```console
dotnet published\aspnetapp.dll
```

您可以使用下列命令，在 **Linux** 或 **macOS** 上執行應用程式。

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a>此範例中所使用的 Docker 映像

在此範例中，使用下列 Docker 映像

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

恭喜您！ 您已：
> [!div class="checklist"]
> * 了解 Microsoft .NET Core Docker 映像
> * 取得要 Docker 化的 ASP.NET Core 範例應用程式
> * 在本機執行 ASP.NET 範例應用程式
> * 使用 Docker for Linux 容器來建置並執行範例
> * 使用 Docker for Windows 容器來建置並執行範例


**後續步驟**

以下是一些您可以採取的後續步驟：

* [使用 Visual Studio Docker 工具](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [將 Docker 映像從 Azure Container Registry 部署到 Azure 容器執行個體](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/) \(英文\)
* [使用 Visual Studio Code 進行偵錯](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) \(英文\) 
* [開始使用 Visual Studio for Mac、容器，以及雲端中的無伺服器程式碼](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments) \(英文\)
* [開始使用 Docker 和 Visual Studio for Mac 實驗室](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started) \(英文\)

> [!NOTE]
> 如果您沒有 Azure 訂用帳戶，請[立即註冊](https://azure.microsoft.com/free/?b=16.48)可免費使用 30 天的帳戶，並獲得 $200 美元的 Azure 點數來試用其他的 Azure 服務組合。

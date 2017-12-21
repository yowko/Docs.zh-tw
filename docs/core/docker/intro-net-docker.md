---
title: ".NET 和 Docker 簡介"
description: "了解 Docker 和 .NET Core"
keywords: ".NET、.NET Core、Docker"
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
manager: wpickett
ms.custom: mvc
ms.openlocfilehash: ce02033a7994d48494b4e627f1ed8f1dea4caadb
ms.sourcegitcommit: 5bfcb8d341239df251351f318038d31cdc9159d7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="introduction-to-net-and-docker"></a>.NET 和 Docker 簡介

本文提供在 Docker 上使用 .NET 的簡介和概念背景。

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a>Docker：封裝您的應用程式以在任何位置部署及執行

[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) 是一個開放的平台，可讓開發人員和系統管理員在稱為[容器](https://www.docker.com/what-container) \(英文\) 的鬆散隔離環境中，建立[映像](https://docs.docker.com/glossary/?term=image) \(英文\)、遞送及執行分散式應用程式。 此作法能在開發、QA 和生產環境之間，實現有效率的應用程式生命週期管理。
 
[Docker 平台](https://docs.docker.com/engine/docker-overview/#the-docker-platform) \(英文\) 使用 [Docker 引擎](https://docs.docker.com/engine/docker-overview/#docker-engine) \(英文\) 來將應用程式快速建置及封裝為 [Docker 映像](https://docs.docker.com/glossary/?term=image) \(英文\)，映像是使用以 [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) \(英文\) 格式撰寫的檔案來建立，並於後續會將它部署到[分層式容器](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers) \(英文\) 並在其中執行。

您可以建立自己的[分層式映像](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) \(英文\) 作為 Dockerfile，或使用來自 [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub) \(英文\) 等[登錄](https://docs.docker.com/glossary/?term=registry) \(英文\) 的現有分層式映像。

在[進行容器化應用程式或微服務的架構設計及建置](../../standard/microservices-architecture/architect-microservice-container-applications/index.md)時，[Docker 容器、映像和登錄之間的關係](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md)是相當重要的概念。 此作法能大幅縮短開發和部署之間的時間。

### <a name="further-reading-and-watching"></a>延伸閱讀 (及觀賞)

* [Windows 型容器：具企業級控制的新式應用程式開發。](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be) \(英文\)
* [Docker 概觀](https://docs.docker.com/engine/docker-overview/) \(英文\)
* [Windows 容器上的 Dockerfile](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile.md)
* [撰寫 Dockerfile 的最佳做法](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/) \(英文\)
* [建置 .NET Core 應用程式的 Docker 映像](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a>取得.NET Docker 映像

官方 .NET Docker 映像是由 Microsoft 所建立及最佳化。 它們在 Docker Hub 上的 Microsoft 存放庫中公開提供。 視 .NET 版本和 OS 版本而定，每個存放庫可能會包含多個映像。 大部分的映像存放庫提供大量的標籤，來協助您選取特定的架構版本和 OS (Linux 發行版本或 Windows 版本)。

## <a name="scenario-based-guidance"></a>以案例為基礎的指引

Microsoft 針對 .NET 存放庫的目的，是要提供細微且專注的存放庫，以代表特定的案例或工作負載。

`microsoft/aspnetcore` 映像已針對 Docker 上的 ASP.NET Core 應用程式進行最佳化，使容器可以更快速地啟動。

.NET Core 映像 (`microsoft/dotnet`) 則適用於以 .NET Core 為基礎的主控台應用程式。 例如，批次處理、Azure WebJobs 及其他主控台案例，都應使用最佳化的 .NET Core 映像。

最明顯的 Docker 和 .NET 應用程式水平使用案例，是將它們用於生產部署和裝載。 結果顯示生產只是單一案例，而其他案例也同樣有用。 這些案例並非 .NET 特定，但應該適用於大部分的開發人員平台。

* **低負擔安裝**：不須在本機安裝就能試用 .NET。 只要下載具有 .NET 的 Docker 映像即可。

* **在容器中開發**：您可以在一致的環境中開發，來使開發環境與生產環境相似 (避免開發人員電腦上的全域狀態等問題)。 Visual Studio Tools for Docker 甚至可讓您直接從 Visual Studio 啟動容器。

* **在容器中測試**：您可以在容器中測試，以減少因環境設定不正確，或是因上一個測試所遺留的變更所造成的失敗。

* **在容器中建置**：您可以在容器中建置程式碼，以免除針對多個環境正確設定共用組建電腦的必要性，並改為採用 "BYOC" (自備容器) 的作法。

* **在所有環境中部署**：您可以透過所有環境部署映像。 此作法可減少因設定差異所造成的失敗，通常是因外部設定而變更映像行為 (例如插入環境變數)。

可協助針對 Docker 容器開發在 .NET Core 和 .NET Framework 之間進行決定的[一般指引](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md)。

### <a name="common-docker-development-scenarios"></a>常見的 Docker 開發案例

#### <a name="net-core"></a>.NET Core

**.NET Core 資源**

 挑選符合感興趣之案例的 .NET Core 範例。 所有範例指示都會描述如何從 Windows、Linux 或 macOS 主機將 Windows 或 Linux Docker 映像設為目標。

範例使用 .NET Core 2.0。 它們會在適當之處使用 Docker [多階段建置](https://github.com/dotnet/announcements/issues/18) \(英文\) 和[多架構標籤](https://github.com/dotnet/announcements/issues/14) \(英文\)。

* [Docker Hub 上的 .NET Core 映像](https://hub.docker.com/r/microsoft/dotnet/) \(英文\)

* [將 .NET Core 應用程式 Docker 化](https://docs.docker.com/engine/examples/dotnetcore/) \(英文\)

* 此 .NET Core Docker 範例示範如何[在您的 .NET Core 開發程序中使用 Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev) \(英文\)。 該範例可與 Linux 或 Windows 容器搭配使用。

* 此 .NET Core Docker 範例示範[建置適用於生產之 .NET Core 應用程式的 Docker 映像](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) \(英文\) 的最佳做法模式。 該範例可與 Linux 或 Windows 容器搭配使用。

* 此 [.NET Core Docker 範例](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) \(英文\) 示範建置[獨立 .NET Core 應用程式](../deploying/index.md)的 Docker 映像的最佳做法模式。 用於最小的生產容器，而沒有因[在容器之間共用基礎映像](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/) \(英文\) 所產生的優點。 不過，可共用較底層的 Docker 層。

#### <a name="arm32--raspberry-pi"></a>ARM32 / Raspberry Pi

* [.NET Core 執行階段 ARM32 組建宣告](https://github.com/dotnet/announcements/issues/29) \(英文\)

* [Docker Hub 上的 ARM32 / Raspberry Pi .NET Core 映像](https://hub.docker.com/r/microsoft/dotnet/) \(英文\)

* [GitHub 上的 ARM32 / Raspberry Pi .NET Core Docker 範例](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi) \(英文\)

#### <a name="net-framework"></a>.NET Framework

* [Docker Hub 上的 .NET Framework 映像](https://hub.docker.com/r/microsoft/dotnet-framework/) \(英文\)

此存放庫包含示範各種 .NET Framework Docker 設定的範例。 您可以使用這些映像作為自己 Docker 映像的基礎。

**.NET Framework 4.7**

[dotnet-framework:4.7 範例](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) \(英文\) 示範 [.NET Framework 4.7](../../framework/whats-new/index.md#v47) 的基本 "Hello World" 使用方式。 它示範如何仰賴 [.NET Framework 4.7 Docker 映像](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile) \(英文\) 建置及部署該應用程式。

**.NET Framework 4.6.2**

[dotnet-framework:4.6.2 範例](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) \(英文\) 示範 [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462) 的基本 "Hello World" 使用方式。 它示範如何仰賴 [.NET Framework 4.6.2 Docker 映像](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2) \(英文\) 建置及部署該應用程式。

**.NET Framework 3.5**

 [dotnet-framework:3.5 範例](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) \(英文\) 示範 [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5) \(英文\) 的基本 "Hello World" 使用方式。 它示範如何仰賴 Docker 中的 .NET Framework 3.5 建置及部署專案。

#### <a name="aspnet-core"></a>ASP.NET Core

* [此 ASP.NET Core Docker 範例](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) \(英文\) 示範建置適用於生產之 ASP.NET Core 應用程式的 Docker 映像的最佳做法模式。 該範例可與 Linux 或 Windows 容器搭配使用。

* [Docker Hub 上的 ASP.NET Core 映像](https://hub.docker.com/r/microsoft/aspnetcore-build/) \(英文\)

* [GitHub 上的 ASP.NET Core 映像](https://github.com/aspnet/aspnet-docker) \(英文\)

#### <a name="aspnet-framework"></a>ASP.NET Framework

* [Docker Hub 上的 ASP.NET Framework 映像](https://hub.docker.com/r/microsoft/aspnet/) \(英文\)

* [.NET Framework 4.6.2 範例上的 ASP.NET Web Form 應用程式](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp) \(英文\)

#### <a name="windows-communication-framework-wcf"></a>Windows Communication Framework (WCF)

* [Docker Hub 上的 Windows Communication Framework (WCF) 映像](https://hub.docker.com/r/microsoft/wcf/) \(英文\)

* [GitHub 上的 Windows Communication Framework (WCF) 映像](https://github.com/microsoft/iis-docker) \(英文\)

* [使用 .NET Full Framework 4.6.2 的 Windows Communication Framework (WCF) Docker 範例](https://github.com/Microsoft/wcf-docker-samples) \(英文\)

#### <a name="internet-information-server-iis"></a>Internet Information Server (IIS)

* [Docker Hub 上的 Internet Information Server (IIS) 映像](https://hub.docker.com/r/microsoft/iis/) \(英文\)

* [GitHub 上的 Internet Information Server (IIS) 映像](https://github.com/microsoft/wcf-docker) \(英文\)

### <a name="interact-with-other-microsoft-stack-container-images"></a>與其他 Microsoft 堆疊容器映像互動

#### <a name="microsoft-sql-server"></a>Microsoft SQL Server

* [透過 Docker 快速入門執行適用於 Linux 的 Microsoft SQL Server 2017 容器映像](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker) \(機器翻譯\)

* [Docker Hub 上適用於 Linux 的 Microsoft SQL Server 映像](https://hub.docker.com/r/microsoft/mssql-server-windows/) \(英文\)

* [Docker Hub 上適用於 Windows 容器的 Microsoft SQL Server 映像](https://hub.docker.com/r/microsoft/mssql-server-windows/) \(英文\)

* [Docker Hub 上適用於 Windows 容器的 Microsoft SQL Server Express 版本映像](https://hub.docker.com/r/microsoft/mssql-server-windows-express/) \(英文\)

* [Docker Hub 上適用於 Windows 容器的 Microsoft SQL Server Developer 版本映像](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/) \(英文\)

#### <a name="visual-studio-team-services-vsts-agent"></a>Visual Studio Team Services (VSTS) 代理程式

* [Docker Hub 上的 Visual Studio Team Services (VSTS) 代理程式映像](https://hub.docker.com/r/microsoft/vsts-agent/) \(英文\)

* [GitHub 上的 Visual Studio Team Services (VSTS) 代理程式映像](https://github.com/Microsoft/vsts-agent-docker) \(英文\)

#### <a name="operations-management-suite-oms-linux-agent"></a>Operations Management Suite (OMS) Linux 代理程式

* [Operations Management Suite (OMS) Linux 代理程式概觀](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview) \(英文\)

* [Docker Hub 上的 Operations Management Suite (OMS) 映像](https://hub.docker.com/r/microsoft/vsts-agent/) \(英文\)

* [GitHub 上的 Operations Management Suite (OMS) 映像](https://github.com/Microsoft/OMS-docker) \(英文\)

#### <a name="microsoft-azure-command-line-interface-cli"></a>Microsoft Azure 命令列介面 (CLI)

* [Docker Hub 上的 Microsoft Azure 命令列介面 (CLI) 映像](https://hub.docker.com/r/microsoft/azure-cli/) \(英文\) 

* [GitHub 上的 Microsoft Azure 命令列介面 (CLI) 映像](https://github.com/Microsoft/OMS-docker) \(英文\)

> [!NOTE]
> 如果您沒有 Azure 訂用帳戶，請[立即註冊](https://azure.microsoft.com/free/?b=16.48)可免費使用 30 天的帳戶，並獲得 $200 美元的 Azure 點數來試用其他的 Azure 服務組合。

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a>Microsoft Azure Cosmos DB 模擬器 (僅限 Windows 容器)

* [Docker Hub 上的 Microsoft Azure Cosmos DB 模擬器映像](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) \(英文\) 

* [將 Azure Cosmos DB 模擬器用於本機開發及測試](/azure/cosmos-db/local-emulator.md#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a>探索豐富的 Docker 開發生態系統

在了解 Docker 平台和不同的 Docker 映像之後，您接著可以探索豐富的 Docker 生態系統。 以下連結能提供 Microsoft 工具支援容器開發的方式。

* [搭配使用 .NET 和 Docker](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/) \(英文\)
* [設計和開發多容器和微服務 .NET 應用程式](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* [Visual Studio Code Docker 擴充功能](https://code.visualstudio.com/docs/languages/dockerfile) \(英文\)
* [了解如何使用 Azure Service Fabric](/azure/service-fabric/index.md)
* [Service Fabric 使用者入門範例](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/) \(英文\)
* [Windows 容器的優點](/virtualization/windowscontainers/about/index.md#video-overview)
* [使用 Visual Studio Docker 工具](/aspnet/core/publishing/visual-studio-tools-for-docker/index.md)
* [將 Docker 映像從 Azure Container Registry 部署到 Azure 容器執行個體](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/) \(英文\)
* [使用 Visual Studio Code 進行偵錯](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) \(英文\)
* [開始使用 Visual Studio for Mac、容器，以及雲端中的無伺服器程式碼](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments) \(英文\)
* [開始使用 Docker 和 Visual Studio for Mac 實驗室](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started) \(英文\)

## <a name="next-steps"></a>後續步驟

* [了解 .NET Core 的 Docker 基本概念](docker-basics-dotnet-core.md)
* [建置 .NET Core Docker 映像](building-net-docker-images.md)
\
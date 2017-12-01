---
title: ".NET 和 Docker 簡介"
description: "了解 Docker 和.NET 核心"
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
ms.openlocfilehash: 1c9ce7a008c86d1c245ce8b7d616e05fcb3d4bbc
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="introduction-to-net-and-docker"></a>.NET 和 Docker 簡介

 本文章提供簡介與使用.NET docker 的概念背景。 

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a>Docker： 封裝您的應用程式部署和執行任何位置

[Docker](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-defined)是開放式平台，可讓開發人員和管理員建置[映像](https://docs.docker.com/glossary/?term=image)、 出貨，和呼叫鬆散隔離環境中執行分散式應用程式[容器](https://www.docker.com/what-container). 這個方法可讓開發、 品管及生產環境之間的有效的應用程式生命週期管理。
 
[Docker 平台](https://docs.docker.com/engine/docker-overview/#the-docker-platform)使用[Docker 引擎](https://docs.docker.com/engine/docker-overview/#docker-engine)快速建置並封裝為應用程式[Docker images](https://docs.docker.com/glossary/?term=image)使用檔案寫入建立[Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile)格式，然後部署及執行[分層容器](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers)。

您可以建立您自己[分層映像](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers)dockerfiles 或使用現有從[登錄](https://docs.docker.com/glossary/?term=registry)、 like [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub)。

[Docker 容器、 影像和登錄之間的關聯性](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries)是重要的概念時[架構和建置容器化應用程式或 microservices](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/)。 這種方法可大幅縮短開發到部署之間的時間。

### <a name="further-reading-and-watching"></a>進一步閱讀 （和觀賞）

* [Windows 容器： 企業級控制與現代化應用程式開發。](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [Docker 概觀](https://docs.docker.com/engine/docker-overview/)
* [Windows 容器上的 Dockerfile](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [寫入 Dockerfiles 的最佳作法](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [.NET Core 應用程式的建置 Docker 映像](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a>取得.NET Docker 映像

建立和最佳化 microsoft 官方.NET Docker 映像。 它們會公開使用銜接站集線器上的 Microsoft 儲存機制中。 每個儲存機制可以包含多個映像，根據.NET 版本和作業系統版本上。 大部分的映像儲存機制提供更詳盡的標記，可協助您選取特定的 framework 版本和作業系統 （Linux distro 或 Windows 版本）。

## <a name="scenario-based-guidance"></a>案例基礎指引

.NET 的儲存機制的 Microsoft 的目的是讓細微和焦點代表特定案例或工作負載的儲存機制。

`microsoft/aspnetcore`映像適合用於 ASP.NET Core 應用程式上 Docker，因此可以更快速啟動容器。

.NET Core 映像 (`microsoft/dotnet`) 是針對.NET 核心為基礎的主控台應用程式。 例如，批次程序、 Azure Webjob 和其他主控台案例應該使用最佳化的.NET Core 映像。

使用 Docker 和.NET 應用程式的最明顯的水平案例適用於生產環境部署和裝載。 其實生產狀況下只有一個，和其他項目同樣適合。 這些案例不是特定的.NET 中，但應套用至大部分的開發人員平台。

* **低人事安裝**— 您可以試用.NET 而不是本機安裝。 剛才下載.NET 中它的 Docker 映的像。

* **開發在容器中**— 您可以開發一致性的環境中進行開發和生產環境類似 （避免程式開發人員電腦上的全域狀態等問題）。 Visual Studio Tools for Docker 甚至可讓您直接從 Visual Studio 啟動容器。

* **測試容器中**— 您可以測試在容器中，減少因為設定不正確的環境而發生失敗或其他變更遺留從最後一次測試。

* **在容器中建立**— 您可以建置程式碼，在容器中，需要正確地設定多個環境中共用的組建電腦，但改為將移至"BYOC"（攜帶您自己的容器） 的方法。

* **在所有環境中的部署**— 您可以透過您的環境的所有部署映像。 這種方法可減少由於設定的差異，通常會透過外部組態 （例如，插入的環境變數） 的映像行為變更失敗。

[一般指引](https://docs.microsoft.com/dotnet/standard/microservices-architecture/net-core-net-framework-containers/general-guidance)Docker 容器開發的.NET Core 和.NET Framework 之間決定。

### <a name="common-docker-development-scenarios"></a>常見的 Docker 開發案例

#### <a name="net-core"></a>.NET Core

**.NET 核心資源**

 挑選適合您案例感興趣的.NET Core 範例。 所有範例的指示都說明如何從 Windows、 Linux 或 macOS 主機的 Windows 或 Linux Docker 映像的目標。

這些範例會使用.NET 核心 2.0。 在使用 Docker[多階段建置](https://github.com/dotnet/announcements/issues/18)和[多 arch 標記](https://github.com/dotnet/announcements/issues/14)適當的位置。

* [.NET core 映像上 DockerHub](https://hub.docker.com/r/microsoft/dotnet/)

* [Dockerize.NET Core 應用程式](https://docs.docker.com/engine/examples/dotnetcore/)

* 這個.NET Core Docker 範例會示範如何[.NET Core 開發程序中使用 Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev)。 範例適用於 Linux 和 Windows 容器。

* 這個.NET Core Docker 範例會示範的最佳作法模式[建置.NET Core 應用程式的實際執行的 Docker 映像。](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) 範例適用於 Linux 和 Windows 容器。

* 這[.NET Core Docker 範例](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained)示範建立 Docker 映像的最佳作法模式[各自獨立的.NET Core 應用程式](https://docs.microsoft.com/dotnet/core/deploying/)。 用於沒有獲益最小的生產容器[共用容器之間的基本映像](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/)。 不過，較低的 Docker 層無法共用。

#### <a name="arm32--raspberry-pi"></a>ARM32 覆盆子 Pi /

* [.NET 核心執行階段 ARM32 組建通知](https://github.com/dotnet/announcements/issues/29)

* [ARM32 / 覆盆子 Pi.NET Core 映像上 DockerHub](https://hub.docker.com/r/microsoft/dotnet/)

* [ARM32 / 木莓澆 Pi.NET Core Docker GitHub 上的範例](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a>.NET Framework

* [.NET framework 映像上 DockerHub](https://hub.docker.com/r/microsoft/dotnet-framework/)這個儲存機制包含範例會示範各種不同的.NET Framework Docker 設定。 您可以使用這些映像為基礎的 Docker 映像。

**.NET framework 4.7**

[ [Dotnet-架構： 4.7 範例](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7)示範基本"hello world"的使用方式[.NET Framework 4.7](https://docs.microsoft.com/dotnet/framework/whats-new/index#introducing-the-net-framework-47)。 它會示範如何建置和部署應用程式依賴[.NET Framework 4.7 docker 映像](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile)。

**.NET framework 4.6.2**

[Dotnet-架構： 4.6.2 範例](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2)示範基本"hello world"的使用方式[.NET Framework 4.6.2](https://docs.microsoft.com/dotnet/framework/whats-new/index#whats-new-in-the-net-framework-462)。 它會示範如何建置和部署應用程式依賴[.NET Framework 4.6.2 docker 映像](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2)。

**.NET framework 3.5**

 [Dotnet-framework: 3.5 範例](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5)示範基本"hello world"的使用方式[.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5)。 它會顯示如何建置和部署上的 Docker 的.NET Framework 3.5 的專案。

#### <a name="aspnet-core"></a>ASP.NET Core

* [此範例中 ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp)示範建置 Docker images，適用於 ASP.NET Core 實際執行的應用程式的最佳作法模式。 範例適用於 Linux 和 Windows 容器。

* [ASP.NET Core 映像上 DockerHub](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [GitHub 上的 ASP.NET Core 映像](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a>ASP.NET 架構 

* [ASP.NET Framework DockerHub 上的映像](https://hub.docker.com/r/microsoft/aspnet/)

* [在.NET Framework 4.6.2 範例 ASP.NET Web Form 應用程式](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a>Windows Communication Framework (WCF)

* [Windows Communication Framework (WCF) 映像上 DockerHub](https://hub.docker.com/r/microsoft/wcf/)

* [GitHub 上的 Windows Communication Framework (WCF) 映像](https://github.com/microsoft/iis-docker)

* [使用.NET Full Framework 4.6.2 Windows Communication Framework (WCF) Docker 範例](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a>Internet Information Server (IIS)

* [Internet Information Server (IIS) 上 DockerHub 的映像](https://hub.docker.com/r/microsoft/iis/)

* [GitHub 上的 Internet Information Server (IIS) 映像](https://github.com/microsoft/wcf-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a>與其他 Microsoft 堆疊容器映像互動

#### <a name="microsoft-sql-server"></a>Microsoft SQL Server

* [執行 Microsoft SQL Server Linux 2017 容器映像使用 Docker 快速入門](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [Microsoft SQL Server 上 DockerHub Linux 映像](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Microsoft SQL Server 的 Windows 容器映像上 DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Microsoft SQL Server Express Edition DockerHub 上的 Windows 容器映像](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [Microsoft SQL Server Developer Edition DockerHub 上的 Windows 容器映像](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a>Visual Studio Team Services (VSTS) 代理程式

* [Visual Studio Team Services (VSTS) 代理程式映像上 DockerHub](https://hub.docker.com/r/microsoft/vsts-agent/)

* [GitHub 上的 visual Studio Team Services (VSTS) 代理程式映像](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a>Operations Management Suite (OMS) Linux 代理程式

* [Operations Management Suite (OMS) Linux 代理程式概觀](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)

* [Operations Management Suite (OMS) 的映像上 DockerHub](https://hub.docker.com/r/microsoft/vsts-agent/) 

* [GitHub 上的 operations Management Suite (OMS) 映像](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a>Microsoft Azure 命令列介面 (CLI)

* [Microsoft Azure 命令列介面 (CLI) 映像上 DockerHub](Docker image for Microsoft Azure Command Line Interface) 

* [GitHub 上的 Microsoft Azure 命令列介面 (CLI) 映像](https://github.com/Microsoft/OMS-docker)

> [!Note]
> 如果您沒有 Azure 訂用帳戶，[立即註冊](https://azure.microsoft.com/free/?b=16.48)免費 30 天的帳戶和 Azure 信用額度試用 Azure 服務的任何組合中的 get 美金 200。
>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a>Microsoft Azure Cosmos DB 模擬器 （Windows 容器）

* [Microsoft Azure Cosmos DB 模擬器映像上 DockerHub](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [使用 Azure Cosmos DB 模擬器進行本機開發和測試](https://docs.microsoft.com/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a>瀏覽豐富的 Docker 開發生態系統

現在您已經學會關於 Docker 平台和不同的 Docker 映像下, 一個步驟就是瀏覽豐富的 Docker 生態系統。 下列連結會顯示您的 Microsoft 工具做容器開發的補充。

* [同時使用.NET 和 Docker](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/) 
* [設計和開發多容器和微服務為基礎的.NET 應用程式](../standard/microservices-architecture/multi-container-microservice-net-applications)
* [Visual Studio 程式碼的 Docker 擴充功能](https://code.visualstudio.com/docs/languages/dockerfile) 
* [了解如何使用 Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/) 
* [取得 Service Fabric 啟動範例](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [Windows 容器的優點](https://docs.microsoft.com/virtualization/windowscontainers/about/index#video-overview)
* [使用 Visual Studio Docker 工具](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [將從 Azure 容器登錄至 Azure 容器執行個體的 Docker 映像部署](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [使用 Visual Studio 程式碼進行偵錯](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [未授權者手上取得使用 Visual Studio for Mac、 容器和無伺服器的程式碼在雲端中](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [開始使用 Docker 和 Visual Studio for Mac 實驗室](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a>後續步驟

* [了解 Docker 與.NET Core 的基本概念](../docker/docker-basics-dotnet-core.md)
* [建置.NET Core Docker 映像](../docker/building-net-docker-images)
---
title: "官方.NET Docker 映像"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |官方.NET Docker 映像"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 6f14bd0cf55a552f3881d755ebe7389f000975d8
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="official-net-docker-images"></a>官方.NET Docker 映像

官方.NET Docker 映像會建立和最佳化的 Microsoft 的 Docker 映像。 它們是 Microsoft 的儲存機制中公開可用[Docker Hub](https://hub.docker.com/u/microsoft/)。 每個儲存機制可以包含多個映像，根據.NET 版本，並根據作業系統和版本 （Linux Debian、 Linux Alpine、 Windows Nano Server、 Windows Server Core 等）。

Microsoft 的願景.NET 的儲存機制是讓細微且已取得焦點的儲存機制，其中儲存機制代表特定案例或工作負載。 比方說， [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)應該使用映像，因為這些 ASP.NET Core 映像提供的其他最佳化作業是容器，使用 ASP.NET Core docker，可以更快開始時。

相反地，.NET Core 映像 (microsoft/dotnet) 是針對.NET 核心為基礎的主控台應用程式。 例如，批次程序、 Azure Webjob 和其他主控台案例應該使用.NET Core。 這些映像不包含 ASP.NET Core 堆疊，造成較小的容器映像。

大部分的映像儲存機制提供更詳盡的標記幫助您選取不只是特定的 framework 版本，還可選擇的作業系統 （Linux distro 或 Windows 版本）。

如需由 Microsoft 提供的官方.NET Docker 映像的進一步資訊，請參閱[.NET Docker Images 摘要](https://aka.ms/dotnetdockerimages)。

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>開發與實際執行的.NET core 和 Docker 映像最佳化

在開發人員建置 Docker images，Microsoft 會著重於以下案例：

-   若要使用的映像*開發*和建置.NET Core 應用程式。

-   若要使用的映像*執行*.NET Core 應用程式。

為什麼多個映像嗎？ 當開發、 建置及執行容器化應用程式時，通常會有不同的優先權。 透過這些個別的工作提供不同的映像，Microsoft 會有助於最佳化的開發、 建置和部署應用程式的個別處理程序。

### <a name="during-development-and-build"></a>在開發和組建

在開發期間，重要的是您可以逐一如何快速查看變更，以及偵錯所做的變更的功能。 無法變更您的程式碼和快速查看變更的功能一樣重要影像的大小。 有些工具和 [容器組建代理程式]，使用程式開發 ASP.NET Core 映像 （microsoft/aspnetcore-建置），在開發期間，並建立處理程序時發生。 建置在 Docker 容器的內部時, 的重要層面是編譯您的應用程式所需的項目。 這包括編譯器和.NET 相依性，以及像 npm web 開發相依性的 Gulp、 Bower。

這種類型的組建映像為何如此重要？ 您無法部署此映像到生產環境。 相反地，它是您用來建置您的內容到生產環境的映像的映像。 此映像會使用持續整合 (CI) 環境中建置環境。 比方說，而不是以手動方式直接在組建代理程式上安裝所有應用程式相依性主應用程式 (例如，VM)、 組建代理程式會具現化的.NET Core 建置映像建置的應用程式所需的所有依存性。 組建代理程式只需要知道如何執行此 Docker 映像。 這可簡化 CI 環境，並使其更容易預測。

### <a name="in-production"></a>在生產環境中

在生產環境中重要的是如何快速部署和啟動您的實際執行.NET Core 映像為基礎的容器。 因此，執行階段僅映像會根據[microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)很小，使它可以快速在網路上傳輸從 Docker 登錄您的 Docker 主機。 內容已準備好執行時，啟用最短的時間，使其無法啟動處理結果的容器。 在 Docker 模型中，您就不必從 C 編譯\#程式碼中，有當您執行 dotnet 組建或 dotnet 發行時使用組建容器。

此最佳化的映像在您放入的二進位檔和執行應用程式所需的其他內容。 Dotnet 所建立的內容，例如發行只包含已編譯的.NET 二進位檔、 影像、.js、 和.css 檔案。 經過一段時間，您會看到包含預先 jit 封裝映像。

雖然有多個版本的.NET Core 和 ASP.NET Core 映像，但它們都共用一或多個圖層，其中包括基底的階層。 因此，儲存映像所需的磁碟空間數量很它只包含自訂映像和其基底映像之間的差異。 結果是快速從登錄中提取映像。

當您瀏覽在 Docker Hub.NET 映像儲存機制時，您會發現多個映像版本的分類或加上標記。 這些標記可協助決定要根據版本需要下表中一樣使用，哪一個：

-   microsoft /**aspnetcore:2.0**

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   microsoft /**aspnetcore-2.0 組建：**

        ASP.NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
[上一個](net-容器-os-targets.md) [下一步] (.../architect-microservice-container-applications/index.md)

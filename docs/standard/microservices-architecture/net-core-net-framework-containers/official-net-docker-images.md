---
title: 官方 .NET Docker 映像
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 官方 .NET Docker 映像
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: bb2190a4fae6f8a26b220fd12ecb9f65ea6f4b96
ms.sourcegitcommit: 6c480773ae896f45af4671fb3e26611a50e4dd81
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251112"
---
# <a name="official-net-docker-images"></a>官方 .NET Docker 映像

官方 .NET Docker 映像是 Microsoft 建立及最佳化的 .NET Docker 映像。 [它們在 Docker Hub 上的 Microsoft 存放庫中公開提供](https://hub.docker.com/u/microsoft/)。 每個存放庫可以包含多個映像，視 .NET 版本及作業系統與版本而定 (Linux Debian、Linux Alpine、Windows Nano Server、Windows Server Core 等等)。

從 .NET Core 2.1 開始，所有的 .NET Core 映像 (包含 ASP.NET Core) 都可以在 Docker Hub 的 [.NET Core 映像存放庫](https://hub.docker.com/r/microsoft/dotnet/) \(英文\) 取得。

大部分的映像存放庫會提供大量的標籤，不僅協助您選取特定的架構版本，還協助您選擇作業系統 (Linux 發行版本或 Windows 版本)。


## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>開發與生產環境的 .NET core 和 Docker 映像最佳化比較

在建置開發人員 Docker 映像時，Microsoft 會著重在下列主要案例︰

-   映像用來「開發」與建置 .NET Core 應用程式。

-   映像用來「執行」.NET Core 應用程式。

為何有多個映像？ 在開發、建置及執行容器化應用程式時，您通常有不同的優先考量。 透過提供這些個別工作的不同映像，Microsoft 會協助最佳化開發、建置及部署應用程式的個別處理程序。

### <a name="during-development-and-build"></a>開發與建置期間

開發期間的重點是，您逐一查看變更的速度以及偵錯變更的能力。 映像大小的重要性，不如變更程式碼及快速查看變更的能力。 有些工具和「組建代理程式容器」會在開發與建置程序期間使用開發 ASP.NET Core 映像 (**microsoft/dotnet:2.1-sdk**)。 在 Docker 容器內部建置時，重要的層面是為編譯應用程式所需要的項目。 這包括編譯器和任何其他 .NET 相依性，加上 Web 開發相依性。

這種組建映像為何如此重要？ 您不會將此映像部署到生產環境。 此映像是您用來建置要放入生產環境映像的內容。 當您使用 Docker 多階段組建時，此映像會用於您的持續整合 (CI) 環境或建置環境。

### <a name="in-production"></a>生產環境

生產環境的重點是部署和啟動以生產環境 .NET Core 映像為基礎之容器的速度。 因此，以 **microsoft/dotnet:2.1-aspnetcore-runtime** 為基礎的僅執行階段映像很小，方便它快速從您的 Docker 登錄跨越網路到 Docker 主機。 準備好執行的內容可用最短的時間完成啟動容器到處理結果的流程。 在 Docker 模型中不必編譯 C\# 程式碼，因為當您使用組建容器執行 Dotnet 組建或 Dotnet 發行時就有了。

在此最佳化的映像中，您只放入執行應用程式所需的二進位檔和其他內容。 例如，Dotnet 發佈所建立的內容只包含已編譯的 .NET 二進位檔、映像、.js 和 .css 檔案。 一段時間後，您會看到包含預先 JIT 編譯套件的映像。

雖然有多種版本的 .NET Core 和 ASP.NET Core 映像，但它們全都共用一或多個圖層，包括基底圖層。 因此，儲存映像所需的磁碟空間量很小，僅為您自訂映像及其基底映像之間的差異。 結果是可從登錄快速提取映像。

當您瀏覽 Docker Hub 的 .NET 映像存放庫時，您會發現以標籤分類或標記的多個映像版本。 這些標籤可協助您根據需要的版本決定使用的版本，如同下表中的這些：

-   microsoft/dotnet:**2.1-aspnetcore-runtime**

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   microsoft/**dotnet:2.1-sdk**

        .NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
[上一頁] (net-container-os-targets.md) [下一頁] (../architect-microservice-container-applications/index.md)

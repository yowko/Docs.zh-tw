---
title: 官方 .NET Docker 映像
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 官方 .NET Docker 映像
ms.date: 01/30/2020
ms.openlocfilehash: 50a50587b35f811859841c4e049f40cb99479372
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501871"
---
# <a name="official-net-docker-images"></a>官方 .NET Docker 映像

官方 .NET Docker 映像是 Microsoft 建立及最佳化的 .NET Docker 映像。 它們在[Docker Hub](https://hub.docker.com/u/microsoft/)上的 Microsoft 存儲庫中公開提供。 每個存放庫可以包含多個映像，視 .NET 版本及作業系統與版本而定 (Linux Debian、Linux Alpine、Windows Nano Server、Windows Server Core 等等)。

自 .NET 核心 2.1 起，所有 .NET 核心映射（包括 ASP.NET核心映射）都可以在 Docker <https://hub.docker.com/_/microsoft-dotnet-core/>Hub 處 .NET Core 映射存儲庫： 上。

自2018年5月以來，微軟圖像被[聯合在微軟容器註冊表](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)。 官方目錄仍然僅在 Docker Hub 中可用，在那裡您將找到用於拉取映射的更新位址。

大多數映射存儲庫提供廣泛的標記，以説明您不僅選擇特定的框架版本，而且還選擇作業系統（Linux 發行版本或 Windows 版本）。

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>開發與生產環境的 .NET core 和 Docker 映像最佳化比較

在建置開發人員 Docker 映像時，Microsoft 會著重在下列主要案例︰

- 映像用來「開發」** 與建置 .NET Core 應用程式。

- 映像用來「執行」**.NET Core 應用程式。

為何有多個映像？ 在開發、建置及執行容器化應用程式時，您通常有不同的優先考量。 透過提供這些個別工作的不同映像，Microsoft 會協助最佳化開發、建置及部署應用程式的個別處理程序。

### <a name="during-development-and-build"></a>開發與建置期間

開發期間的重點是，您逐一查看變更的速度以及偵錯變更的能力。 圖像的大小不如對代碼進行更改並快速查看更改的能力重要。 一些工具和"構建代理容器"，在開發和構建過程中使用開發 .NET Core 映射 *（mcr.microsoft.com/dotnet/core/sdk:3.1*）。 在 Docker 容器內生成時，重要的方面是編譯應用所需的元素。 這包括編譯器和任何其他 .NET 相依性。

這種組建映像為何如此重要？ 您不會將此映射部署到生產。 相反，它是用於構建放置在生產映射中的內容的圖像。 使用 Docker 多階段生成時，此映射將用於連續集成 （CI） 環境或生成環境。

### <a name="in-production"></a>生產環境

生產環境的重點是部署和啟動以生產環境 .NET Core 映像為基礎之容器的速度。 因此，基於*mcr.microsoft.com/dotnet/core/aspnet:3.1*的僅運行時映射很小，因此它可以從 Docker 註冊表快速通過網路傳播到 Docker 主機。 準備好執行的內容可用最短的時間完成啟動容器到處理結果的流程。 在 Docker 模型中不必編譯 C\# 程式碼，因為當您使用組建容器執行 Dotnet 組建或 Dotnet 發行時就有了。

在此優化的映射中，您只放置運行應用程式所需的二進位檔案和其他內容。 例如，由 創建`dotnet publish`的內容僅包含已編譯的 .NET 二進位檔案、圖像、.js 和 .css 檔。 經過一段時間，您會看到映像包含預先以 jit 編譯 (在執行階段發生的從 IL 到原生編譯) 的套件。

雖然有多種版本的 .NET Core 和 ASP.NET Core 映像，但它們全都共用一或多個圖層，包括基底圖層。 因此，儲存映像所需的磁碟空間量很小，僅為您自訂映像及其基底映像之間的差異。 結果是可從登錄快速提取映像。

當您瀏覽 Docker Hub 的 .NET 映像存放庫時，您會發現以標籤分類或標記的多個映像版本。 這些標籤可協助您根據需要的版本決定使用的版本，如同下表中的這些：

| 映像 | 註解 |
|-------|----------|
| mcr.microsoft.com/dotnet/core/aspnet：**3.1** | Linux 和 Windows 上的 ASP.NET Core，具有僅執行階段和 ASP.NET Core 最佳化 (多架構) |
| mcr.microsoft.com/dotnet/core/sdk：**3.1** | Linux 和 Windows 上的 .NET Core，包含 SDK (多架構) |

> [!div class="step-by-step"]
> [上一個](net-container-os-targets.md)
> [下一個](../architect-microservice-container-applications/index.md)

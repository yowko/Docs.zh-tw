---
title: 官方 .NET Docker 映像
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 官方 .NET Docker 映像
ms.date: 01/13/2021
ms.openlocfilehash: 072e565260bf81c123ee837ccca46fbdf7c67361
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065118"
---
# <a name="official-net-docker-images"></a>官方 .NET Docker 映像

官方 .NET Docker 映像是 Microsoft 建立及最佳化的 .NET Docker 映像。 這些都可在 [Docker Hub](https://hub.docker.com/u/microsoft/)的 Microsoft 存放庫中公開使用。 每個存放庫可以包含多個映像，視 .NET 版本及作業系統與版本而定 (Linux Debian、Linux Alpine、Windows Nano Server、Windows Server Core 等等)。

從 .NET Core 2.1 開始，所有 .NET Core 或更新版本的映射（包括 ASP.NET Core）都可在 .NET 映射存放庫的 Docker Hub 取得： <https://hub.docker.com/_/microsoft-dotnet/> 。

自2018年5月起，microsoft 映射已 [在 Microsoft Container Registry 中進行整合](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)。 官方目錄仍只能在 Docker Hub 中使用，而您會在該處找到提取映射的更新位址。

大部分的映射存放庫都提供廣泛的標記，以協助您只選取特定的架構版本，也可以選擇作業系統 (Linux 發行版本或 Windows 版本) 。

## <a name="net-and-docker-image-optimizations-for-development-versus-production"></a>適用于開發與生產環境的 .NET 和 Docker 映射優化

在建置開發人員 Docker 映像時，Microsoft 會著重在下列主要案例︰

- 用來 *開發* 和建立 .net 應用程式的映射。

- 用來 *執行* .net 應用程式的映射。

為何有多個映像？ 在開發、建置及執行容器化應用程式時，您通常有不同的優先考量。 透過提供這些個別工作的不同映像，Microsoft 會協助最佳化開發、建置及部署應用程式的個別處理程序。

### <a name="during-development-and-build"></a>開發與建置期間

開發期間的重點是，您逐一查看變更的速度以及偵錯變更的能力。 影像的大小並不重要，因為能夠對程式碼進行變更並快速查看變更。 某些工具和「組建代理程式容器」會在開發和建立程式期間使用開發 .NET 映射 (*mcr.microsoft.com/dotnet/sdk:5.0*) 。 在 Docker 容器內建立時，重要層面是編譯應用程式所需的元素。 這包括編譯器和任何其他 .NET 相依性。

這種組建映像為何如此重要？ 您不會將此映射部署到生產環境。 相反地，它是您用來建立放置於生產映射中的內容的映射。 當您使用 Docker 多階段組建時，此映射會用於持續整合 (CI) 環境或組建環境。

### <a name="in-production"></a>生產環境

在生產環境中，最重要的是您可以根據實際執行的 .NET 映射來部署和啟動容器的速度。 因此，以 *mcr.microsoft.com/dotnet/aspnet:5.0* 為基礎的僅限執行時間映射很小，因此它可以在網路上快速地從您的 docker 登錄移動到您的 docker 主機。 準備好執行的內容可用最短的時間完成啟動容器到處理結果的流程。 在 Docker 模型中不必編譯 C\# 程式碼，因為當您使用組建容器執行 Dotnet 組建或 Dotnet 發行時就有了。

在此優化映射中，您只會放入執行應用程式所需的二進位檔和其他內容。 例如，所建立的內容 `dotnet publish` 只包含已編譯的 .net 二進位檔、影像、.js 和 .css 檔案。 經過一段時間，您會看到映像包含預先以 jit 編譯 (在執行階段發生的從 IL 到原生編譯) 的套件。

雖然有多個版本的 .NET 和 ASP.NET Core 的映射，但它們全都共用一或多個圖層，包括基底層。 因此，儲存映像所需的磁碟空間量很小，僅為您自訂映像及其基底映像之間的差異。 結果是可從登錄快速提取映像。

當您瀏覽 Docker Hub 的 .NET 映像存放庫時，您會發現以標籤分類或標記的多個映像版本。 這些標籤可協助您根據需要的版本決定使用的版本，如同下表中的這些：

| 映像 | 註解 |
|-------|----------|
| mcr.microsoft.com/dotnet/aspnet：**5.0** | Linux 和 Windows 上的 ASP.NET Core，具有僅執行階段和 ASP.NET Core 最佳化 (多架構) |
| mcr.microsoft.com/dotnet/sdk：**5.0** | Linux 和 Windows 上的 .NET 5 包含 Sdk， (多架構的)  |

> [!div class="step-by-step"]
> [上一個](net-container-os-targets.md) 
> [下一步](../architect-microservice-container-applications/index.md)

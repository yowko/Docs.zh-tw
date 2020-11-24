---
title: 針對 .NET 容器要設為目標的作業系統
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 .NET 容器要設為目標的作業系統
ms.date: 01/30/2020
ms.openlocfilehash: 1f52dcb4da6509be7e771af353daea9cfc97306c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688454"
---
# <a name="what-os-to-target-with-net-containers"></a>針對 .NET 容器要設為目標的作業系統

考量到 Docker 支援的作業系統多樣性及 .NET Framework 和 .NET Core 之間的不同，建議您根據您使用的架構來瞄準特定 OS 和特定的版本。

針對 Windows，您可以使用 Windows Server Core 或 Windows Nano Server。 這些 Windows 版本提供了 .NET Framework 或 .NET Core 各自所需的不同特性 (Windows Server 中的 IIS 與 Nano Server 中的自我裝載網頁伺服器，例如 Kestrel)。

針對 Linux，有多個發佈可供使用，且受到正式 .NET Docker 映像的支援 (例如 Debian)。

在圖 3-1 中，您可以看到根據使用的 .NET Framework，可能使用的 OS 版本。

![顯示哪些作業系統與 .NET 容器搭配使用的圖表。](./media/net-container-os-targets/targeting-operating-systems.png)

**圖3-1。** 根據 .NET Framework 版本決定要設為目標的作業系統

當您部署舊版 .NET Framework 應用程式時，您必須以 Windows Server Core 為目標，與繼承應用程式和 IIS 相容，但它有較大的影像。 在部署 .NET Core 應用程式時，您能夠以 Windows Nano Server 為目標，因為它已經過雲端最佳化、使用 Kestrel，且較為輕巧而啟動速度較快。 此外，支援 Debian、Alpine 和其他項目的 Linux 也可作為目標。 也會使用 Kestrel、較小且更快速地啟動。

若您想要使用不同的 Linux 發佈或 Microsoft 未支援的版本，您也可以建立您自己的 Docker 映像。 例如，您可以建立讓 ASP.NET Core 在傳統式 .NET Framework 及 Windows Server Core 上執行的映像 (並非 Docker 的常見案例)。

> [!IMPORTANT]
> 當您使用 Windows Server Core 映射時，可能會發現某些 Dll 遺失，相較于完整的 Windows 映像。 您可以藉由建立自訂 Server Core 映射，在映射建立時新增遺失的檔案，如此 [GitHub 批註](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448)中所述，您可以解決此問題。

當您將映像名稱新增至您的 Dockerfile 檔案時，您可以根據使用的標籤選取作業系統及版本，如下列範例中所示：

| 映像 | 註解 |
|-------|----------|
| mcr.microsoft.com/dotnet/runtime:3.1 | .NET Core 3.1 多架構：支援 Linux 和 Windows Nano Server，視 Docker 主機而定。 |
| mcr.microsoft.com/dotnet/aspnet:3.1 | ASP.NET Core 3.1 多架構：支援 Linux 和 Windows Nano Server，視 Docker 主機而定。 <br/> aspnetcore 映像有幾項針對 ASP.NET Core 所做的最佳化。 |
| mcr.microsoft.com/dotnet/aspnet:3.1-buster-slim | 僅限 .NET Core 3.1 執行時間-僅限於 Linux Debian 發行版本 |
| mcr.microsoft.com/dotnet/aspnet:3.1-nanoserver-1809 | 僅限 .NET Core 3.1 執行時間-僅限於 Windows Nano Server (Windows Server 1809 版)  |

## <a name="additional-resources"></a>其他資源

- **BitmapDecoder 失敗，因為 GitHub 問題缺少 WindowsCodecsExt.dll ()**  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> [上一個](container-framework-choice-factors.md) 
> [下一步](official-net-docker-images.md)

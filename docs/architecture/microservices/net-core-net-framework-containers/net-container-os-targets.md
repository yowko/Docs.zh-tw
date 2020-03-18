---
title: 針對 .NET 容器要設為目標的作業系統
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 .NET 容器要設為目標的作業系統
ms.date: 01/30/2020
ms.openlocfilehash: a09e3981ece478a9795c0f27acc98d604864cdd5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501855"
---
# <a name="what-os-to-target-with-net-containers"></a>針對 .NET 容器要設為目標的作業系統

考量到 Docker 支援的作業系統多樣性及 .NET Framework 和 .NET Core 之間的不同，建議您根據您使用的架構來瞄準特定 OS 和特定的版本。

針對 Windows，您可以使用 Windows Server Core 或 Windows Nano Server。 這些 Windows 版本提供了 .NET Framework 或 .NET Core 各自所需的不同特性 (Windows Server 中的 IIS 與 Nano Server 中的自我裝載網頁伺服器，例如 Kestrel)。

針對 Linux，有多個發佈可供使用，且受到正式 .NET Docker 映像的支援 (例如 Debian)。

在圖 3-1 中，您可以看到根據使用的 .NET Framework，可能使用的 OS 版本。

![顯示要與哪個 .NET 容器使用哪些作業系統的圖表。](./media/net-container-os-targets/targeting-operating-systems.png)

**圖 3-1。** 根據 .NET Framework 版本決定要設為目標的作業系統

部署舊版 .NET 框架應用程式時，必須針對 Windows 伺服器核心，與舊應用和 IIS 相容，但它具有更大的映射。 在部署 .NET Core 應用程式時，您能夠以 Windows Nano Server 為目標，因為它已經過雲端最佳化、使用 Kestrel，且較為輕巧而啟動速度較快。 此外，支援 Debian、Alpine 和其他項目的 Linux 也可作為目標。 也使用Kestrel，更小，啟動更快。

若您想要使用不同的 Linux 發佈或 Microsoft 未支援的版本，您也可以建立您自己的 Docker 映像。 例如，您可以建立讓 ASP.NET Core 在傳統式 .NET Framework 及 Windows Server Core 上執行的映像 (並非 Docker 的常見案例)。

> [!IMPORTANT]
> 使用 Windows 伺服器核心映射時，您可能會發現與完整的 Windows 映像相比，某些 DLL 缺失。 您可能可以通過創建自訂伺服器核心映射、在映射生成時添加缺少的檔來解決此問題，如此[GitHub 注釋](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448)中所述。

當您將映像名稱新增至您的 Dockerfile 檔案時，您可以根據使用的標籤選取作業系統及版本，如下列範例中所示：

| 映像 | 註解 |
|-------|----------|
| mcr.microsoft.com/dotnet/core/runtime:3.1 | .NET Core 3.1 多體系結構：支援 Linux 和 Windows Nano 伺服器，具體取決於 Docker 主機。 |
| mcr.microsoft.com/dotnet/core/aspnet:3.1 | ASP.NET核心 3.1 多體系結構：支援 Linux 和 Windows Nano 伺服器，具體取決於 Docker 主機。 <br/> aspnetcore 映像有幾項針對 ASP.NET Core 所做的最佳化。 |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim | .NET 核心 3.1 僅在 Linux Debian 發行版本上運行時 |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1809 | .NET 核心 3.1 僅在 Windows Nano 伺服器上運行時（Windows 伺服器版本 1809） |

## <a name="additional-resources"></a>其他資源

- **由於缺少 WindowsCodecsExt.dll（GitHub 問題），位映射解碼器失敗**  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> [上一個](container-framework-choice-factors.md)
> [下一個](official-net-docker-images.md)

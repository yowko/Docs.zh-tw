---
title: 針對 .NET 容器要設為目標的作業系統
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 .NET 容器要設為目標的作業系統
ms.date: 01/13/2021
ms.openlocfilehash: 1b914d9afca9ade37f13e639f73001b91f338d26
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187975"
---
# <a name="what-os-to-target-with-net-containers"></a>針對 .NET 容器要設為目標的作業系統

由於 Docker 支援的作業系統多樣性以及 .NET Framework 與 .NET 5 之間的差異，您應該根據您所使用的架構，將目標設為特定的 OS 和特定版本。

針對 Windows，您可以使用 Windows Server Core 或 Windows Nano Server。 這些 Windows 版本在 Windows Server Core (的 IIS 與自我裝載的 web 伺服器（例如 Nano) Server 中的 Kestrel）（例如，.NET Framework 或 .NET 5 可能需要的）之間提供不同的特性。

針對 Linux，有多個發佈可供使用，且受到正式 .NET Docker 映像的支援 (例如 Debian)。

在圖3-1 中，您可以根據所使用的 .NET framework，查看可能的作業系統版本。

![顯示哪些作業系統與 .NET 容器搭配使用的圖表。](./media/net-container-os-targets/targeting-operating-systems.png)

**圖3-1。** 根據 .NET Framework 版本決定要設為目標的作業系統

當您部署舊版 .NET Framework 應用程式時，您必須以 Windows Server Core 為目標，與繼承應用程式和 IIS 相容，但它有較大的影像。 部署 .NET 5 應用程式時，您可以將目標設為雲端優化的 Windows Nano Server，使用 Kestrel 且較小且更快速地啟動。 您也可以以 Linux 為目標，支援 Debian、Alpine 和其他專案。 也會使用 Kestrel、較小且更快速地啟動。

若您想要使用不同的 Linux 發佈或 Microsoft 未支援的版本，您也可以建立您自己的 Docker 映像。 例如，您可以建立讓 ASP.NET Core 在傳統式 .NET Framework 及 Windows Server Core 上執行的映像 (並非 Docker 的常見案例)。

> [!IMPORTANT]
> 當您使用 Windows Server Core 映射時，可能會發現某些 Dll 遺失，相較于完整的 Windows 映像。 您可以藉由建立自訂 Server Core 映射，在映射建立時新增遺失的檔案，如此 [GitHub 批註](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448)中所述，您可以解決此問題。

當您將映像名稱新增至您的 Dockerfile 檔案時，您可以根據使用的標籤選取作業系統及版本，如下列範例中所示：

| 映像 | 註解 |
|-------|----------|
| mcr.microsoft.com/dotnet/runtime:5.0 | .NET 5 多重架構：支援 Linux 和 Windows Nano Server，視 Docker 主機而定。 |
| mcr.microsoft.com/dotnet/aspnet:5.0 | ASP.NET Core 5.0 多架構：支援 Linux 和 Windows Nano Server，視 Docker 主機而定。 <br/> aspnetcore 映像有幾項針對 ASP.NET Core 所做的最佳化。 |
| mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim | .NET 5 執行時間-僅適用于 Linux Debian 發行版本 |
| mcr.microsoft.com/dotnet/aspnet:5.0-nanoserver-1809 | 僅限 .NET 5 執行時間-僅限 Windows Nano Server (Windows Server 1809 版)  |

## <a name="additional-resources"></a>其他資源

- **BitmapDecoder 失敗，因為 GitHub 問題缺少 WindowsCodecsExt.dll ()**  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> [上一個](container-framework-choice-factors.md) 
> [下一步](official-net-docker-images.md)

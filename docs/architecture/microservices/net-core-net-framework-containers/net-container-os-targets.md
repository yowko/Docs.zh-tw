---
title: 針對 .NET 容器要設為目標的作業系統
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 .NET 容器要設為目標的作業系統
ms.date: 01/07/2019
ms.openlocfilehash: 6f160aeba5257722490788271e6f89359342cc0d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675755"
---
# <a name="what-os-to-target-with-net-containers"></a>針對 .NET 容器要設為目標的作業系統

考量到 Docker 支援的作業系統多樣性及 .NET Framework 和 .NET Core 之間的不同，建議您根據您使用的架構來瞄準特定 OS 和特定的版本。

針對 Windows，您可以使用 Windows Server Core 或 Windows Nano Server。 這些 Windows 版本提供了 .NET Framework 或 .NET Core 各自所需的不同特性 (Windows Server 中的 IIS 與 Nano Server 中的自我裝載網頁伺服器，例如 Kestrel)。

針對 Linux，有多個發佈可供使用，且受到正式 .NET Docker 映像的支援 (例如 Debian)。

在圖 3-1 中，您可以看到根據使用的 .NET Framework，可能使用的 OS 版本。

![在部署舊版 .NET Framework 應用程式時，您必須以相容於舊版應用程式和 IIS、且具有較大映像的 Windows Server Core 為目標。 在部署 .NET Core 應用程式時，您能夠以 Windows Nano Server 為目標，因為它已經過雲端最佳化、使用 Kestrel，且較為輕巧而啟動速度較快。 此外，支援 Debian、Alpine 和其他項目的 Linux 也可作為目標。 它同樣也使用 Kestrel，且較為輕巧而啟動速度較快。](./media/image1.png)

**圖 3-1** 根據 .NET Framework 版本決定要設為目標的作業系統

若您想要使用不同的 Linux 發佈或 Microsoft 未支援的版本，您也可以建立您自己的 Docker 映像。 例如，您可以建立讓 ASP.NET Core 在傳統式 .NET Framework 及 Windows Server Core 上執行的映像 (並非 Docker 的常見案例)。

當您將映像名稱新增至您的 Dockerfile 檔案時，您可以根據使用的標籤選取作業系統及版本，如下列範例中所示：

<table>
<thead>
<tr class="header">
<th>Image</th>
<th>註解</th>
</tr>
</thead>
<tbody>
<tr>
<td>mcr.microsoft.com/dotnet/core/runtime:2.2</td>
<td>.NET Core 2.2 多重架構：支援 Linux 和 Windows Nano Server，視 Docker 主機而定。</td>
</tr>
<tr class="odd">
<td>mcr.microsoft.com/dotnet/core/aspnet:2.2</td>
<td><p>ASP.NET Core 2.2 多重架構：支援 Linux 和 Windows Nano Server，視 Docker 主機而定。</p>
<p>aspnetcore 映像有幾項針對 ASP.NET Core 所做的最佳化。</p></td>
</tr>
<tr class="even">
<td>mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</td>
<td>.NET Core 2.2 執行階段 - 僅限於 Linux Alpine 發行版本上</td>
</tr>
<tr class="odd">
<td>mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</td>
<td>.NET Core 2.2 執行階段 - 僅限於 Windows Nano Server (Windows Server 1803 版) 上</td>
</tr>
</tbody>
</table>

> [!div class="step-by-step"]
> [上一頁](container-framework-choice-factors.md)
> [下一頁](official-net-docker-images.md)

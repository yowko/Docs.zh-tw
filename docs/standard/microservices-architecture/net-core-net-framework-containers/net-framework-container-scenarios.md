---
title: 針對 Docker 容器選擇 .NET Framework 的時機
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 Docker 容器選擇 .NET Framework 的時機
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 128801fbe49a3f7618b1cedc814b7663d57df624
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195329"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>針對 Docker 容器選擇 .NET Framework 的時機

儘管 .NET Core 可為新的應用程式和應用程式模式提供顯著的優點，但 .NET Framework 仍然是許多現有案例的首選。

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>將現有應用程式直接移轉至 Windows Server 容器

您可能只想要使用 Docker 容器來簡化部署，即使未建立微服務也是一樣。 例如，您可能想要使用 Docker 來改善 DevOps 工作流程；容器可讓您更適當地隔離測試環境，也可以去除移至生產環境時遺失相依性所造成的部署問題。 如果是這些情況，則即使您要部署整合型應用程式，還是可以將 Docker 和 Windows 容器合理地用於目前 .NET Framework 應用程式。

在大部分情況下，於此案例中，您不需要將現有應用程式移轉至 .NET Core；您可以使用包含傳統 .NET Framework 的 Docker 容器。 不過，建議您在擴充現有應用程式時使用 .NET Core，例如，在 ASP.NET Core 中寫入新的服務。

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>使用不適用於 .NET Core 的協力廠商 .NET 程式庫或 NuGet 套件

協力廠商程式庫會快速採行 [.NET Standard](../../net-standard.md)，以跨所有 .NET 類別 (包含 .NET Core) 共用程式碼。 使用 .NET Standard 程式庫 2.0 和更新版本，跨不同架構的 API 介面相容性已明顯變好，而且在 .NET Core 2.x 中，應用程式也可以直接參考現有 .NET Framework 程式庫 (請參閱[相容性修正](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#net-framework-461-supporting-net-standard-20))。

此外，在 2017 年 11 月已發行 [Windows 相容性套件](../../../core/porting/windows-compat-pack.md)以擴充在 Windows 上的 .NET Standard 2.0 適用的 API 介面。 透過此套件，只需要些許修改甚至不需修改，大部分的現有程式碼即可重新編譯為 .NET Standard 2.x，以在 Windows 上執行。

不過，即使自 .NET Standard 2.0 和 .NET Core 2.1 開始有該例外進展，仍然可能有特定 NuGet 套件需要執行 Windows 而且可能不支援 .NET Core 的情況。 如果這些套件對您的應用程式十分重要，則需要在 Windows 容器上使用 .NET Framework。

## <a name="using-net-technologies-not-available-for-net-core"></a>使用不適用於 .NET Core 的 .NET 技術 

部分 .NET Framework 技術在最新版本的 .NET Core (撰寫本文時為 2.1 版) 中未提供。 這其中有一些可在更新的 .NET Core 版本 (.NET Core 2.x) 中使用，但其他則不適用於 .NET Core 設為目標的新應用程式模式，而且可能永遠無法使用。

下列清單顯示 .NET Core 2.x 中未提供的大部分技術：

-   ASP.NET Web Form。 只有在 .NET Framework 上才能使用這項技術。 目前並未規劃將 ASP.NET Web Form 帶入 .NET Core。

-   WCF 服務。 即使有 [WCF-Client 程式庫](https://github.com/dotnet/wcf)可從 .NET Core 使用 WCF 服務，但截至 2017 年中，WCF 伺服器實作還是只能在 .NET Framework 上進行。 此案例有可能在未來的 .NET Core 版本中納入，此外也有某些 API 可望在 [Windows 相容性套件](../../../core/porting/windows-compat-pack.md)中納入。

-   工作流程相關服務。 Windows Workflow Foundation (WF)、工作流程服務 (WCF + 單一服務中的 WF) 和 WCF Data Services (先前稱為 ADO.NET Data Services) 僅適用於 .NET Framework。 目前未計劃將它們帶到 .NET Core。

除了正式 [.NET Core 藍圖](https://github.com/aspnet/Home/wiki/Roadmap)中所列的技術之外，也可能會將其他功能移植至 .NET Core。 如需完整清單，請查看 CoreFX GitHub 網站上標記為 [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) 的項目。 請注意，這份清單並不代表 Microsoft 承諾要將這些元件帶入 .NET Core - 這些項目只是擷取社群的要求。 如果您關心上方所列的任何元件，請考慮參與 GitHub 上的討論，讓我們可以聽到您的心聲。 如果您認為缺少了什麼，請[在 CoreFX 儲存機制中提問新的問題](https://github.com/dotnet/corefx/issues/new)。

即使 .NET Core 3 (在撰寫本文時正在籌備中) 將納入許多現有 .NET Framework API 的支援，但這些支援視桌面而定，因此目前在容器的領域中並無實際效用。

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>使用不支援 .NET Core 的平台或 API

某些 Microsoft 或協力廠商平台不支援 .NET Core。 例如，部分 Azure 服務提供尚無法在 .NET Core 上使用的 SDK。 這是暫時性的，因為所有 Azure 服務最終都會使用 .NET Core。 例如，[Azure DocumentDB SDK for .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) 已在 2016 年 11 月 16 日發行為預覽版，但現在已公開上市 (GA) 為穩定版本。

同時，如果 Azure 中的任何平台或服務仍然不支援 .NET Core 與其用戶端 API，您可以在 .NET Framework 上使用 Azure 服務或用戶端 SDK 中的對等 REST API。

### <a name="additional-resources"></a>其他資源

-   **.NET Core 指南**  
    [https://docs.microsoft.com/dotnet/core/index](../../../core/index.md)

-   **從 .NET Framework 移植到 .NET Core**  
    [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

-   **Docker 上的 .NET Framework 指南**  
    [https://docs.microsoft.com/dotnet/framework/docker/](../../../framework/docker/index.md)

-   **.NET 偵錯概觀**  
    [https://docs.microsoft.com/dotnet/standard/components](../../components.md)




>[!div class="step-by-step"]
[上一頁](net-core-container-scenarios.md)
[下一頁](container-framework-choice-factors.md)

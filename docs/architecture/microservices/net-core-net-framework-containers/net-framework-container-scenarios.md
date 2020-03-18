---
title: 針對 Docker 容器選擇 .NET Framework 的時機
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 Docker 容器選擇 .NET Framework 的時機
ms.date: 01/30/2020
ms.openlocfilehash: dfb1e8883fc9c3d9235672bc2885858bfb64afa5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501966"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>針對 Docker 容器選擇 .NET Framework 的時機

儘管 .NET Core 可為新的應用程式和應用程式模式提供顯著的優點，但 .NET Framework 仍然是許多現有案例的首選。

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>將現有應用程式直接移轉至 Windows Server 容器

您可能只想要使用 Docker 容器來簡化部署，即使未建立微服務也是一樣。 例如，您可能想要使用 Docker 來改善 DevOps 工作流程；容器可讓您更適當地隔離測試環境，也可以去除移至生產環境時遺失相依性所造成的部署問題。 如果是這些情況，則即使您要部署整合型應用程式，還是可以將 Docker 和 Windows 容器合理地用於目前 .NET Framework 應用程式。

在大部分情況下，於此案例中，您不需要將現有應用程式移轉至 .NET Core；您可以使用包含傳統 .NET Framework 的 Docker 容器。 不過，建議您在擴充現有應用程式時使用 .NET Core，例如，在 ASP.NET Core 中寫入新的服務。

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>使用不適用於 .NET Core 的協力廠商 .NET 程式庫或 NuGet 套件

協力廠商庫正在迅速接受[.NET 標準](../../../standard/net-standard.md)，它支援跨所有 .NET 風格（包括 .NET Core）的代碼共用。 隨著 .NET 標準 2.0 及更高版本，不同框架的 API 表面相容性已顯著增強。 此外，.NET Core 2.x 和較新的應用程式還可以直接引用現有的 .NET 框架庫（請參閱[.NET 框架 4.6.1，支援 .NET 標準 2.0）。](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)

此外[，Windows 相容性包](../../../core/porting/windows-compat-pack.md)擴展了適用于 Windows 上的 .NET 標準 2.0 的 API 曲面。 透過此套件，只需要些許修改甚至不需修改，大部分的現有程式碼即可重新編譯為 .NET Standard 2.x，以在 Windows 上執行。

不過，即使自 .NET Standard 2.0 和 .NET Core 2.1 開始有該例外進展，仍然可能有特定 NuGet 套件需要執行 Windows 而且可能不支援 .NET Core 的情況。 如果這些套件對您的應用程式十分重要，則需要在 Windows 容器上使用 .NET Framework。

## <a name="using-net-technologies-not-available-for-net-core"></a>使用不適用於 .NET Core 的 .NET 技術

某些 .NET 框架技術在當前版本的 .NET Core 中不可用（本文本文本文本文本文本文本文本文本文本文本文本文本文本文本文本文本文本文本文本文所售時為 3.1 版）。 其中一些可能在以後的版本中可用，但另一些模式不符合 .NET Core 所針對的新應用程式模式，可能永遠不會可用。

下面的清單顯示了 .NET Core 3.1 中不可用的大多數技術：

- ASP.NET Web Form。 只有在 .NET Framework 上才能使用這項技術。 目前並未規劃將 ASP.NET Web Form 帶入 .NET Core。

- WCF 服務。 即使[WCF-Client 庫](https://github.com/dotnet/wcf)可從 .NET Core 使用 WCF 服務，但從 2020 年 2 月到 2020 年 2 月，WCF 伺服器實現僅在 .NET 框架上可用。 此案例有可能在未來的 .NET Core 版本中納入，此外也有某些 API 可望在 [Windows 相容性套件](../../../core/porting/windows-compat-pack.md)中納入。

- 工作流程相關服務。 Windows Workflow Foundation (WF)、工作流程服務 (WCF + 單一服務中的 WF) 和 WCF Data Services (先前稱為 ADO.NET Data Services) 僅適用於 .NET Framework。 目前未計劃將它們帶到 .NET Core。

除了官方[.NET Core 路線圖](https://github.com/dotnet/core/blob/master/roadmap.md)中列出的技術外，其他功能可能移植到 .NET Core 或新的[統一 .NET 平臺](https://devblogs.microsoft.com/dotnet/introducing-net-5/)。 您可以考慮參與 GitHub 的討論，以便可以聽到您的聲音。 如果您認為缺少某些內容，則在[dotnet/運行時](https://github.com/dotnet/runtime/issues/new)GitHub 存儲庫中提交新問題。

## <a name="using-a-platform-or-api-that-doesnt-support-net-core"></a>使用不支援 .NET 核心的平臺或 API

某些 Microsoft 和協力廠商平臺不支援 .NET Core。 例如，某些 Azure 服務提供的 SDK 尚不可用，無法在 .NET Core 上使用。 大多數 Azure SDK 最終應移植到 .NET Core/標準，但有些可能由於各種原因不會。 您可以在[Azure SDK 最新版本](https://azure.github.io/azure-sdk/releases/latest/index.html)頁中查看可用的 Azure SDK。

同時，如果 Azure 中的任何平台或服務仍然不支援 .NET Core 與其用戶端 API，您可以在 .NET Framework 上使用 Azure 服務或用戶端 SDK 中的對等 REST API。

### <a name="additional-resources"></a>其他資源

- **.NET 核心指南** \
  [https://docs.microsoft.com/dotnet/core/index](../../../core/index.md)

- **從 .NET 框架移植到 .NET 核心** \
  [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **.NET 芯上 Docker 指南** \
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **.NET 元件概述** \
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[上一個](net-core-container-scenarios.md)
>[下一個](container-framework-choice-factors.md)

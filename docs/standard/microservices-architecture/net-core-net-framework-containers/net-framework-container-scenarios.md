---
title: "針對 Docker 容器選擇 .NET Framework 的時機"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 針對 Docker 容器選擇 .NET Framework 的時機"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fcfb78bf521107b14d7796235f52c836f48f41fe
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>針對 Docker 容器選擇 .NET Framework 的時機

儘管 .NET Core 可為新的應用程式和應用程式模式提供顯著的優點，但 .NET Framework 仍然是許多現有案例的首選。

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>將現有應用程式直接移轉至 Windows Server 容器

您可能只想要使用 Docker 容器來簡化部署，即使未建立微服務也是一樣。 例如，您可能想要使用 Docker 來改善 DevOps 工作流程；容器可讓您更適當地隔離測試環境，也可以去除移至生產環境時遺失相依性所造成的部署問題。 如果是這些情況，則即使您要部署整合型應用程式，還是可以將 Docker 和 Windows 容器合理地用於目前 .NET Framework 應用程式。

在大部分情況下，於此案例中，您不需要將現有應用程式移轉至 .NET Core；您可以使用包含傳統 .NET Framework 的 Docker 容器。 不過，建議您在擴充現有應用程式時使用 .NET Core，例如，在 ASP.NET Core 中寫入新的服務。

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>使用不適用於 .NET Core 的協力廠商 .NET 程式庫或 NuGet 套件

協力廠商程式庫會快速採行 [.NET Standard](https://docs.microsoft.com/dotnet/standard/net-standard)，以跨所有 .NET 類別 (包含 .NET Core) 共用程式碼。 使用 .NET Standard 程式庫 2.0 和以上版本，跨不同架構的 API 介面功能已明顯變大，而且，在 .NET Core 2.0 中，應用程式也可以直接參考現有 .NET Framework 程式庫 (請參閱[相容性修正](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work))。

不過，即使自 .NET Standard 2.0 和 .NET Core 2.0 開始有該例外進展，仍然可能有特定 NuGet 套件需要執行 Windows 而且可能不支援 .NET Core 的情況。 如果這些套件對您的應用程式十分重要，則需要在 Windows 容器上使用 .NET Framework。

## <a name="using-net-technologies-not-available-for-net-core"></a>使用不適用於 .NET Core 的 .NET 技術 

部分 .NET Framework 技術不適用於目前版本的 .NET Core (撰寫本文時的 2.0 版)。 這其中有一些可在更新的 .NET Core 版本 (.NET Core 2.x) 中使用，但其他則不適用於 .NET Core 設為目標的新應用程式模式，而且可能永遠無法使用。

下列清單顯示 .NET Core 2.0 中未提供的大部分技術：

-   ASP.NET Web Form。 只有在 .NET Framework 上才能使用這項技術。 目前並未規劃將 ASP.NET Web Form 帶入 .NET Core。

-   WCF 服務。 即使 [WCF-Client 程式庫](https://github.com/dotnet/wcf)可從 .NET Core 使用 WCF 服務時也是一樣。 自 2017 年年中開始，才能在 .NET Framework 上使用 WCF 伺服器實作。 .NET Core 的未來版本可能會考慮這項案例。

-   工作流程相關服務。 Windows Workflow Foundation (WF)、工作流程服務 (WCF + 單一服務中的 WF) 和 WCF Data Services (先前稱為 ADO.NET Data Services) 僅適用於 .NET Framework。 目前未計劃將它們帶到 .NET Core。

除了正式 [.NET Core 藍圖](https://github.com/aspnet/Home/wiki/Roadmap)中所列的技術之外，也可能會將其他功能移植至 .NET Core。 如需完整清單，請查看 CoreFX GitHub 網站上標記為 [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) 的項目。 請注意，這份清單並不代表 Microsoft 承諾要將這些元件帶入 .NET Core - 這些項目只是擷取社群的要求。 如果您關心上方所列的任何元件，請考慮參與 GitHub 上的討論，讓我們可以聽到您的心聲。 如果您認為缺少了什麼，請[在 CoreFX 儲存機制中提問新的問題](https://github.com/dotnet/corefx/issues/new)。

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>使用不支援 .NET Core 的平台或 API

某些 Microsoft 或協力廠商平台不支援 .NET Core。 例如，部分 Azure 服務提供尚無法在 .NET Core 上使用的 SDK。 這是暫時性的，因為所有 Azure 服務最終都會使用 .NET Core。 例如，[Azure DocumentDB SDK for .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) 已在 2016 年 11 月 16 日發行為預覽版，但現在已公開上市 (GA) 為穩定版本。

同時，如果 Azure 中的任何平台或服務仍然不支援 .NET Core 與其用戶端 API，則您可以在 .NET Framework 上使用 Azure 服務或用戶端 SDK 中的對等 REST API。

### <a name="additional-resources"></a>其他資源

-   **.NET Core 指南**
    [*https://docs.microsoft.com/dotnet/core/index*](https://docs.microsoft.com/dotnet/core/index)

-   **從 .NET Framework 移轉到 .NET Core**
    [*https://docs.microsoft.com/dotnet/core/porting/index*](https://docs.microsoft.com/dotnet/core/porting/index)

-   **Docker 上的 .NET Framework 指南**
    [*https://docs.microsoft.com/dotnet/framework/docker/*](https://docs.microsoft.com/dotnet/framework/docker/)

-   **.NET 元件概觀**
    [*https://docs.microsoft.com/dotnet/standard/components*](https://docs.microsoft.com/dotnet/standard/components)




>[!div class="step-by-step"]
[上一個] (net-core-container-scenarios.md) [下一個] (container-framework-choice-factors.md)

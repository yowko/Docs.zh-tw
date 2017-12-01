---
title: "選擇.NET Framework 的 Docker 容器的時機"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |選擇.NET Framework 的 Docker 容器的時機"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1bf1f055f040e7f3dc575b7a04140ebf0c599f98
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>選擇.NET Framework 的 Docker 容器的時機

.NET Core 提供重要的優點，新的應用程式和應用程式模式，而.NET Framework 仍將是不錯的選擇，許多現有的案例。

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>將現有的應用程式移轉到 Windows Server 容器的直接

您可能想要使用 Docker 容器只是為了簡化部署，，即使您沒有建立 microservices。 例如，可能是您想要改善您的 DevOps 工作流程使用 Docker，容器可讓您更好的隔離的測試環境和也可免除部署移至生產環境時，遺失的相依性所造成的問題。 在這些情況下，即使您要部署整合的應用程式，它使用合理 Docker 與 Windows 容器目前的.NET Framework 應用程式。

在大部分情況下，此案例中，您不需要移轉到.NET Core; 現有應用程式您可以使用包含傳統的.NET Framework 的 Docker 容器。 不過，建議的方法是使用.NET Core，當您擴充現有的應用程式，例如 ASP.NET Core 中撰寫新的服務。

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>使用適用於.NET Core 的第三方.NET 程式庫或無法使用的 NuGet 封裝

協力廠商程式庫會快速採用[.NET 標準](https://docs.microsoft.com/dotnet/standard/net-standard)，可讓在所有的.NET 版本，包括.NET Core 之間共用的程式碼。 以.NET 標準程式庫 2.0 版或超過 API 介面跨不同架構的相容性變得更大，而.NET Core 2.0 應用程式也可以直接參考現有的.NET Framework 程式庫 (請參閱[相容填充碼](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work))。

不過，即使是使用.NET 標準 2.0 和.NET 核心 2.0 自該例外狀況的進展，可能有某些 NuGet 封裝需要執行的 Windows，而且可能不支援.NET Core。 如果這些封裝您的應用程式的關鍵，您將需要使用.NET Framework 上 Windows 容器。

## <a name="usingnet-technologies-not-available-for-net-core"></a>沒有適用於.NET Core 的 Using.NET 技術 

某些.NET Framework 技術不適用於目前版本的.NET Core （2.0 版撰寫本文時）。 其中部分可在更新的.NET Core 版本 (.NET Core 2.x)，但其他人不會套用到新的應用程式模式.NET Core 的目標，而且可能永遠不會使用。

下列清單顯示大部分的.NET Core 2.0 中未提供的技術：

-   ASP.NET Web Form。 只有在.NET Framework 上使用這項技術。 目前並未規劃將 ASP.NET Web Form 帶入 .NET Core。

-   WCF 服務。 即使[WCF 用戶端程式庫](https://github.com/dotnet/wcf)皆可使用.NET core 的 WCF 服務。 為準，mid 2017，WCF 伺服器實作才會使用.NET Framework 上。 這種情況下可能會視為未來版本的.NET Core。

-   工作流程相關的服務。 Windows Workflow Foundation (WF)、 工作流程服務 （WCF + 單一服務中的 WF） 和 WCF 資料服務 （先前稱為 ADO.NET Data Services），只能使用.NET Framework 為基礎。 目前沒有計劃以將它們帶到.NET Core。

除了技術之外列入正式[.NET Core 藍圖](https://github.com/aspnet/Home/wiki/Roadmap)，其他功能可能移植到.NET Core。 如需完整清單，查看 標記為的項目[連接埠-核心](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core)CoreFX GitHub 網站上。 請注意，這份清單不代表 microsoft 承諾會將這些元件帶到.NET Core — 項目只會擷取來自社群的要求。 如果您在意任何上列的元件，請考慮參與 GitHub 上的討論，以便可以聽到語音。 如果您認為缺少了什麼，請[在 CoreFX 儲存機制中提問新的問題](https://github.com/dotnet/corefx/issues/new)。

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>使用平台或應用程式開發介面中不支援.NET Core

某些 Microsoft 或第三方平台不支援.NET Core。 例如，部分 Azure 服務所提供的 SDK，尚無法使用.NET 核心上的耗用量。 這是暫時性的，因為所有 Azure 服務最終將會使用.NET 核心。 例如， [Azure DocumentDB SDK for.NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1)已於 2016 年 11 月 16 日預覽發行，但現在是上市 (GA) 做為穩定版本。

在此同時，如果任何平台或服務在 Azure 中的使用其用戶端應用程式開發介面不支援仍然.NET Core，您可以使用對等的 REST API 從 Azure 服務或用戶端 SDK.NET Framework 為基礎。

### <a name="additional-resources"></a>其他資源

-   **.NET core 指南**
    [*https://docs.microsoft.com/dotnet/core/index*](https://docs.microsoft.com/dotnet/core/index)

-   **從.NET Framework 移植到.NET Core**
    [*https://docs.microsoft.com/dotnet/core/porting/index*](https://docs.microsoft.com/dotnet/core/porting/index)

-   **.NET framework 上 Docker 指南**
    [*https://docs.microsoft.com/dotnet/framework/docker/*](https://docs.microsoft.com/dotnet/framework/docker/)

-   **.NET 元件概觀**
    [*https://docs.microsoft.com/dotnet/standard/components*](https://docs.microsoft.com/dotnet/standard/components)




>[!div class="step-by-step"]
[上一個](net-核心-容器-scenarios.md) [下一步] (容器-架構-選擇-factors.md)

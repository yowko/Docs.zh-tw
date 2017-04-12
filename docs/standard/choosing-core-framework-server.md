---
title: "針對伺服器應用程式在 .NET Core 和 .NET Framework 之間進行選擇"
description: "本指南說明您在 .NET 中建置伺服器應用程式時應考量要使用哪種 .NET 類別。"
keywords: .NET, .NET Core, .NET Framework
author: cartermp
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 155553e4-89a2-418d-be88-4e75f6c3cc69
translationtype: Human Translation
ms.sourcegitcommit: 405bac1faa446687a4acdcf2d5536ee31f31f246
ms.openlocfilehash: 7151c87d373afce88c83239499ba33980383ab98
ms.lasthandoff: 03/15/2017

---

# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>針對伺服器應用程式在 .NET Core 和 .NET Framework 之間進行選擇

有兩個支援的執行階段選項，可使用 .NET 來建置伺服器端應用程式：.NET Framework 及.NET Core。 這兩者共用許多相同的 .NET 平台元件，而您可以在這兩者間共用程式碼。 不過，兩者間有一些基本差異，而您的選擇取決於您想要完成的目標。  本文提供有關每一個選項使用時機的指引。

在下列情況中，您應該針對伺服器應用程式使用 .NET Core：

* 您有跨平台需求。
* 您的目標為微服務。
* 您正在使用 Docker 容器。
* 您需要高效能且可調整的系統。
* 您需要依應用程式讓 .NET 版本並存。

在下列情況中，您應該針對伺服器應用程式使用 .NET Framework：

* 您的應用程式目前使用的是 .NET Framework (建議為擴充，而不是移轉)
* 您需要使用的協力廠商 .NET 程式庫或 NuGet 套件不適用 .NET Core。
* 您需要使用的 .NET 技術不適用 .NET Core。
* 您需要使用不支援 .NET Core 的平台。

## <a name="when-to-choose-net-core"></a>選擇 .NET Core 的時機

以下將更詳盡說明先前所述之挑選 .NET Core 的理由。

### <a name="cross-platform-needs"></a>跨平台需求

很明顯地，如果您的目標是讓應用程式 (Web/服務) 應該能夠跨平台 (Windows、Linux 和 macOS) 執行，最好的選擇就是使用 .NET Core。

.NET Core 也支援先前所述的作業系統做為您的開發工作站。 Visual Studio 提供適用於 Windows 的整合式開發環境 (IDE)。  您也可以在 macOS、Linux 和 Windows 上使用 Visual Studio 程式碼，其完全支援 .NET Core (包括 IntelliSense 和偵錯)。 您還可以使用大多數的協力廠商編輯器 (例如 Sublime、Emacs、VI) 來將目標設定為 .NET Core，而且可以使用開放原始碼的 [Omnisharp](http://www.omnisharp.net/) 專案來取得編輯器 IntelliSense。 您也可以避免使用任何程式碼編輯器，並直接使用 .NET Core 的命令列工具 (適用於所有支援的平台)。

### <a name="microservices-architecture"></a>微服務架構

如果您擁有微服務導向的系統，該系統是由多個獨立、可動態擴充、具狀態或無狀態的微服務所組成，則 .NET Core 是最佳候選項目。 .NET Core 是輕量型的，而且可將其 API 介面最小化到微服務的範圍。 微服務架構也可讓您跨越服務界限混用技術，從而能夠基於新的微服務逐漸接受 .NET Core，新的微服務可以與利用 .NET Framework、Java、Ruby 或其他整合型技術所開發的其他微服務或服務同時存留。

您可以使用的基礎結構平台有很多。 對於大型且複雜的微服務系統，您可以使用 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)。 針對無狀態的微服務，您也可以使用其他像是 [Azure App Service](https://azure.microsoft.com/services/app-service/) 的產品。 以 Docker 為依據的微服務替代方案也符合任何一種微服務方法，如下所述。 所有的這些平台均支援 .NET Core，並使其更適合用來裝載您的微服務。

### <a name="containers"></a>容器

儘管容器也可以用來將 Web 應用程式或服務裝入容器中 (其會遵循任何架構模式)，但它們通常會與微服務架構搭配使用。 您可以使用適用於 Windows 的 .NET Framework容器，但是 .NET Core 的模組化和輕量型性質可使容器更加完美。 建立和部署容器時，使用 .NET Core 的映像大小遠小於 .NET Framework。 舉例來說，因為它是跨平台的，您可以將伺服器應用程式部署到 Linux Docker 容器。

您接著可在自己的 Linux 或 Windows 基礎結構中裝載 Docker 容器，或使用雲端服務 (例如 [Azure Container Service](https://azure.microsoft.com/services/container-service/))，其可在雲端中管理、協調及調整您的容器型應用程式。

### <a name="a-need-for-high-performance-and-scalable-systems"></a>需要高效能且可調整的系統

當您的系統需要最佳效能和延展性時，.NET Core 和 ASP.NET Core 就是最好的選擇。 ASP.NET Core 的功能勝過 ASP.NET 10 倍，並且在像 Java servlets、Go 和 node.js 等微服務領域中領先其他熱門的業界技術。

這對於微服務架構特別重要，您可以在其中執行數百個微服務。 透過 ASP.NET Core，您就能使用較低數目的伺服器/VM 來執行系統，最終能省下基礎結構與裝載的相關成本。

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>需要針對每個應用程式層級並存各個 .NET 版本

如果您想要能夠在 .NET 的各種架構版本上安裝具有相依性的應用程式，您需要使用 .NET Core，以提供 100% 的並存。 在同一部電腦上輕易並存安裝不同版本的 .NET Core，可讓您在相同伺服器上擁有多個服務，每個均位於它自己的 .NET Core 版本上，以消除有關應用程式升級和 IT 操作人員的風險並節省相關開支。

## <a name="when-to-choose-net-framework"></a>選擇 .NET Framework 的時機

儘管 .NET Core 可為新的應用程式和應用程式模式提供顯著的優點，但 .NET Framework 仍將持續為許多現有案例的首選，也就是 .NET Core 將不會取代它來用於所有的伺服器應用程式。

### <a name="current-net-framework-applications"></a>目前的 .NET Framework 應用程式

在大多數的情況中，您不需將現有的應用程式移轉到 .NET Core， 而是建議您在擴充現有的應用程式時使用 .NET Core，例如，在 ASP.NET Core 中寫入新的 Web 服務。

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>需要使用的協力廠商的 .NET 程式庫或 NuGet 套件不適用 .NET Core

程式庫會快速採行 .NET Standard，以便跨所有 .NET 類別 (包括 .NET Core) 共用程式碼。 透過 .NET Standard 2.0，這甚至更加簡單，因為 .NET Core API 介面將明顯變大，而 .NET Core 應用程式可以直接使用現有的 .NET Framework 程式庫。 但此轉換不是即時的，因此我們建議您先檢查應用程式所需的特定程式庫，然後再以其他方式進行決策。

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>需要使用的 .NET 技術不適用 .NET Core

某些 .NET Framework 技術無法在 .NET Core 中使用。 這其中有一些可在更新的 .NET Core 版本中使用，但其他的則不適用於由 .NET Core 設為目標的應用程式模式，且可能永遠無法使用。 下列清單顯示 .NET Core 1.0 中找不到的最常見技術：

* ASP.NET Web Form 應用程式：ASP.NET Web Form 僅適用於 .NET Framework，因此您無法針對此案例使用 ASP.NET Core /.NET Core。 目前並未規劃將 ASP.NET Web Form 帶入 .NET Core。

* ASP.NET Web Pages 應用程式：雖然已規劃將其隨附於未來版本中 (如 [.NET Core 藍圖](https://github.com/aspnet/Home/wiki/Roadmap)所述)，但 ASP.NET Core 1.0 中並未隨附 ASP.NET Web Pages。

* ASP.NET SignalR 伺服器/用戶端實作。 在 .NET Core 1.0 版本發行時程 (2016 年 6 月) 中，儘管已規劃要將其隨附於未來版本中 (如 [.NET Core 藍圖](https://github.com/aspnet/Home/wiki/Roadmap)所述)，但 ASP.NET SignalR 不適用於 ASP.NET Core (不論是用戶端或伺服器)。 預覽狀態適用於[伺服器端](https://github.com/aspnet/SignalR-Server)和[用戶端程式庫](https://github.com/aspnet/SignalR-Client-Net) GitHub 儲存機制。

* WCF 服務實作。 即使已有 [WCF 用戶端程式庫](https://github.com/dotnet/wcf) 可從 .NET Core 使用 WCF 服務，但截至 2016 年 6 月，WCF 伺服器實作還是只能在 .NET Framework 上使用。 此案例不是 .NET Core 目前計劃的一部分，但未來會納入考慮。

* 工作流程相關的服務︰Windows Workflow Foundation (WF)、工作流程服務 (WCF + 單一服務中的 WF) 和 WCF Data Services (先前稱為 "ADO.NET Data Services") 僅適用於 .NET Framework，目前並未計劃將其帶入 .NET Core。

* Windows Presentation Foundation (WPF) 和 Windows Forms：WPF 與 Windows Forms 應用程式只能在 .NET Framework 上使用。 沒有計畫要將它們移植到 .NET Core。 

* 語言支援︰Visual Basic 和 F# 目前並未擁有任何支援 .NET Core 的工具，但將於 Visual Studio 2017 和更新版本的 Visual Studio 中支援這兩者。

除了官方藍圖，還有一些其他要移植到 .NET Core 的架構 - 如需完整清單，請參閱標記為 [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) 的 CoreFX 問題。 請注意，這份清單並不代表 Microsoft 承諾要將這些元件帶入 .NET Core - 它們只是代表社群的期望。 話雖如此，如果您關心上方所列的任何元件，請考慮參與 GitHub 上的討論，讓我們可以聽到您的心聲。 如果您認為缺少了什麼，請[在 CoreFX 儲存機制中提問新的問題](https://github.com/dotnet/corefx/issues/new)。

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>必須使用不支援 .NET Core 的平台

某些 Microsoft 或協力廠商平台不支援 .NET Core。 例如，某些 Azure 服務 (例如 Service Fabric Stateful Reliable Services 和 Service Fabric Reliable Actors) 需要 .NET Framework。 部分其他服務提供尚無法在 .NET Core 上使用的 SDK。 這是過渡期，因為所有的 Azure 服務都會使用 .NET Core。 在此同時，您永遠都能使用對等的 REST API，而非用戶端 SDK。

## <a name="further-resources"></a>其他資源

* [.NET Core 指南](../core/index.md)
* [從 .NET Framework 移植到 .NET Core](../core/porting/index.md)
* [Docker 上的 .NET Framework 指南](../framework/index.md)
* [.NET 偵錯概觀](components.md)


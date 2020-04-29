---
title: 針對伺服器應用程式在 .NET Core 和 .NET Framework 之間進行選擇
description: 協助您決定建立伺服器應用程式時所要使用之 .NET 執行方式的指南。
author: cartermp
ms.date: 04/28/2020
ms.openlocfilehash: 30157276bce53ed44dca5b660172e5556dab14f8
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507438"
---
# <a name="net-core-vs-net-framework-for-server-apps"></a>適用于伺服器應用程式的 .NET Core 與 .NET Framework

有兩個支援的 .NET 組建可用於建立伺服器端應用程式： .NET Framework 和 .NET Core。 這兩者共用許多相同的元件，而您可以在這兩者間共用程式碼。 不過，兩者間有一些基本差異，而您的選擇取決於您想要完成的目標。 本文提供有關每一個選項使用時機的指引。

在下列情況中，請針對伺服器應用程式使用 .NET Core：

- 您有跨平台需求。
- 您的目標是微服務。
- 您使用的是 Docker 容器。
- 您需要高效能且可調整的系統。
- 您需要依應用程式讓 .NET 版本並存。

在下列情況中，請針對伺服器應用程式使用 .NET Framework：

- 您的應用程式目前使用 .NET Framework (建議進行擴充，而不是移轉)。
- 您的應用程式使用不適用於 .NET Core 的協力廠商 .NET 程式庫或 NuGet 套件。
- 您的應用程式使用不適用於 .NET Core 的 .NET 技術。
- 您的應用程式使用不支援 .NET Core 的平台。 Windows、macOS 和 Linux 都支援 .NET Core。

## <a name="when-to-choose-net-core"></a>選擇 .NET Core 的時機

下列各節將更詳盡說明先前所述之挑選 .NET Core 的理由。

### <a name="cross-platform-needs"></a>跨平台需求

如果您的應用程式 (Web/服務) 必須在多個平台 (Windows、Linux 和 macOS) 上執行，請使用 .NET Core。

.NET Core 支援先前所述的作業系統作為您的開發工作站。 Visual Studio 提供適用於 Windows 和 macOS 的整合式開發環境 (IDE)。 您也可以使用 Visual Studio Code，其在 macOS、Linux 和 Windows 上執行。 Visual Studio Code 支援 .NET Core，包括 IntelliSense 和偵錯。 大多數的協力廠商編輯器 (例如 Sublime、Emacs 和 VI) 都可搭配 .NET Core 使用。 這些協力廠商編輯器會透過 [Omnisharp](https://www.omnisharp.net/) 取得編輯器 IntelliSense。 您也可以避免任何程式碼編輯器，並直接使用[.NET Core CLI](../core/tools/index.md)（適用于所有支援的平臺）。

### <a name="microservices-architecture"></a>微服務架構

微服務架構可讓您跨越服務界限混用技術。 此技術混合可讓新的微服務逐步採用 .NET Core，以便與其他微服務或服務搭配使用。 例如，您可以混合使用 .NET Framework、Java、Ruby 或其他單一技術所開發的微服務或服務。

您可以使用的基礎結構平台有很多。 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) 是針對大型且複雜的微服務系統所設計。 [Azure App Service](https://azure.microsoft.com/services/app-service/) 是無狀態微服務的理想選擇。 以 Docker 為依據的微服務替代方案符合任何一種微服務方法，如[容器](#containers)一節中所述。 所有的這些平台均支援 .NET Core，並使其更適合用來裝載您的微服務。

如需微服務架構的詳細資訊，請參閱[.Net 微服務。容器化 .NET 應用程式的架構](../architecture/microservices/index.md)。

### <a name="containers"></a>容器

容器通常會與微服務架構搭配使用。 容器也可用來將遵循任何架構模式的 Web 應用程式或服務容器化。 .NET Framework 可用於 Windows 容器，但 .NET Core 的模組化和輕量型本質讓它成為容器的更佳選擇。 建立和部署容器時，使用 .NET Core 的映像大小遠小於 .NET Framework。 舉例來說，因為它是跨平台的，您可以將伺服器應用程式部署到 Linux Docker 容器。

您可以在自己的 Linux 或 Windows 基礎結構中，或在 [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) 等雲端服務中裝載 Docker 容器。 Azure Kubernetes Service 可在雲端中管理、協調及調整容器型應用程式。

### <a name="high-performance-and-scalable-systems"></a>高效能且可調整的系統

當您的系統需要最佳效能和延展性時，.NET Core 和 ASP.NET Core 就是最好的選擇。 Windows Server 和 Linux 的高效能伺服器執行階段讓 .NET 成為 [TechEmpower 基準測試](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext)中效能最高的 Web 架構。

效能和延展性對於微服務架構特別重要，其中可執行數百個微服務。 透過 ASP.NET Core，您就能使用較低數目的伺服器/虛擬機器 (VM) 來執行系統。 減少的伺服器/VM 能省下基礎結構與裝載的相關成本。

### <a name="side-by-side-net-versions-per-application-level"></a>每個應用層級的並存 .NET 版本

若要在不同版本的 .NET 上安裝具有相依性的應用程式，建議使用 .NET Core。 .NET Core 支援在同一部電腦上並存安裝不同版本的 .NET Core 執行時間。 此並存安裝可讓您在相同伺服器上擁有多個服務，每個服務在各自的 .NET Core 版本上。 它也會在應用程式升級和 IT 作業方面降低風險並省下成本。

不可能使用 .NET Framework 進行並存安裝。 這是 Windows 元件，而且一次只能有一個版本存在於一部機器上。 .NET Framework 的每個版本都會取代先前的版本。 如果您安裝的應用程式是以較新版本的 .NET Framework 為目標，則可能會中斷電腦上執行的現有應用程式，因為先前的版本已被取代。

## <a name="when-to-choose-net-framework"></a>選擇 .NET Framework 的時機

.NET Core 可為新的應用程式和應用程式模式提供顯著的優點。 不過，.NET Framework 會繼續成為許多現有案例的自然選擇，因此，所有伺服器應用程式的 .NET Core 都不會取代 .NET Framework。

### <a name="current-net-framework-applications"></a>目前的 .NET Framework 應用程式

在大多數的情況中，您不需將現有的應用程式移轉到 .NET Core， 而是建議您在擴充現有的應用程式時使用 .NET Core，例如，在 ASP.NET Core 中寫入新的 Web 服務。

### <a name="aspnet-core-on-net-framework"></a>.NET Framework 上的 ASP.NET Core

如需有關 .NET Framework 上 ASP.NET Core 支援的詳細資訊，請參閱[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。

### <a name="third-party-libraries-or-nuget-packages-not-available-for-net-core"></a>不適用於 .NET Core 的協力廠商程式庫或 NuGet 套件

程式庫會快速採用 .NET Standard。 .NET Standard 可讓您跨所有 .NET 的程式碼（包括 .NET Core）共用程式碼。 透過 .NET Standard 2.0，甚至會更容易達成：

- API 介面變得更大。
- 它引進了 .NET Framework 的相容性模式。

  此相容性模式可讓 .NET Standard 和 .NET Core 專案參考 .NET Framework 程式庫。 若要深入了解相容性模式，請參閱 [Announcing .NET Standard 2.0](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/) (宣告 .NET Standard 2.0)。

只有當程式庫或 NuGet 套件使用 .NET Standard 或 .NET Core 中無法提供的技術時，才需要使用 .NET Framework。

### <a name="net-technologies-not-available-for-net-core"></a>.Net Core 無法使用的 .NET 技術

某些 .NET Framework 技術無法在 .NET Core 中使用。 這其中有一些技術可在更新的 .NET Core 版本中使用。 其他技術則不適用於由 .NET Core 設為目標的新應用程式模式，且可能永遠無法使用。 下列清單顯示 .NET Core 中找不到的最常見技術：

- ASP.NET Web Forms 應用程式： ASP.NET Web form 僅適用于 .NET Framework。 ASP.NET Core 無法用於 ASP.NET Web Forms。 目前並未規劃將 ASP.NET Web Forms 帶入 .NET Core。

- ASP.NET Web Pages 應用程式：ASP.NET Web Pages 未隨附於 ASP.NET Core 中。

- WCF 服務實作。 即使有[wcf 用戶端程式庫](https://github.com/dotnet/wcf)可從 .net CORE 使用 wcf 服務，但目前只有 .NET FRAMEWORK 提供 wcf 伺服器。 此案例不屬於 .NET Core 的目前計畫，但未來將會考慮到。

- 工作流程相關的服務： Windows Workflow Foundation （WF）、工作流程服務（WCF + 單一服務中的 WF）和 WCF Data Services （之前稱為 "ADO.NET 資料服務"）僅適用于 .NET Framework。 不打算將這些技術帶入 .NET Core。

- 語言支援：.NET Core 目前支援 Visual Basic 和 F#，但不是所有專案類型都提供支援。 如需支援的專案範本清單，請參閱 [dotnet new 的範本選項](../core/tools/dotnet-new.md#arguments)。

### <a name="platform-doesnt-support-net-core"></a>平臺不支援 .NET Core

某些 Microsoft 或協力廠商平台不支援 .NET Core。 部分 Azure 服務提供尚無法在 .NET Core 上使用的 SDK。 這是過渡期，因為所有的 Azure 服務都會使用 .NET Core。 在此同時，您可以使用對等的 REST API，而不是用戶端 SDK。

## <a name="see-also"></a>請參閱

- [在 ASP.NET 和 ASP.NET Core 之間進行選擇](/aspnet/core/choose-aspnet-framework)
- [將目標指向 .NET Framework 的 ASP.NET Core](/aspnet/core/introduction-to-aspnet-core#aspnet-core-targeting-net-framework)
- [目標 Framework](frameworks.md)
- [.NET Core 指南](../core/index.yml)
- [從 .NET Framework 移植到 .NET Core](../core/porting/index.md)
- [.NET 和 Docker 簡介](../core/docker/introduction.md)
- [.NET 偵錯概觀](components.md)
- [.NET 微服務。容器化 .NET 應用程式的架構](../architecture/microservices/index.md)

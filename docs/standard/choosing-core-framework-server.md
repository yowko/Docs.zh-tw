---
title: 針對伺服器應用程式在 .NET 5 和 .NET Framework 之間進行選擇
description: 此指南可協助您決定在建立伺服器應用程式時，要使用哪一個 .NET 執行。
author: cartermp
ms.date: 10/06/2020
ms.openlocfilehash: d9dce0343f9d37e976472b818e896a5b0a661e76
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160447"
---
# <a name="net-5-vs-net-framework-for-server-apps"></a>.NET 5 與伺服器應用程式的 .NET Framework

有兩個支援的 .NET 組建可用於建立伺服器端應用程式： .NET Framework 和 .NET 5 (包括 .NET Core) 。 這兩者共用許多相同的元件，而您可以在這兩者間共用程式碼。 不過，兩者間有一些基本差異，而您的選擇取決於您想要完成的目標。 本文提供有關每一個選項使用時機的指引。

在下列情況中，為您的伺服器應用程式使用 .NET 5：

- 您有跨平台需求。
- 您的目標是微服務。
- 您使用的是 Docker 容器。
- 您需要高效能且可調整的系統。
- 您需要依應用程式讓 .NET 版本並存。

在下列情況中，請針對伺服器應用程式使用 .NET Framework：

- 您的應用程式目前使用 .NET Framework (建議進行擴充，而不是移轉)。
- 您的應用程式使用協力廠商 .NET 程式庫或不適用於 .NET 5 的 NuGet 套件。
- 您的應用程式會使用 .net 5 無法使用的 .NET 技術。
- 您的應用程式使用不支援 .NET 5 的平臺。

## <a name="when-to-choose-net-5"></a>選擇 .NET 5 的時機

下列各節會詳細說明先前所述挑選 .NET 5 的原因。

### <a name="cross-platform-needs"></a>跨平台需求

如果您的應用程式 (web/服務) 需要在多個平臺上執行 (Windows、Linux 和 macOS) ，請使用 .NET 5。

.NET 5 支援先前所述的作業系統作為您的開發工作站。 Visual Studio 提供適用於 Windows 和 macOS 的整合式開發環境 (IDE)。 您也可以使用 Visual Studio Code，其在 macOS、Linux 和 Windows 上執行。 Visual Studio Code 支援 .NET 5，包括 IntelliSense 和調試。 大部分的協力廠商編輯器（例如 Sublime、Emacs 和 VI）都會使用 .NET 5。 這些協力廠商編輯器會透過 [Omnisharp](https://www.omnisharp.net/) 取得編輯器 IntelliSense。 您也可以避免使用任何程式碼編輯器，並直接使用 [.NET Core CLI](../core/tools/index.md)（適用于所有支援的平臺）。

### <a name="microservices-architecture"></a>微服務架構

微服務架構可讓您跨越服務界限混用技術。 這項技術混合可針對可與其他微服務或服務搭配使用的新微服務，逐漸採用 .NET 5。 例如，您可以混合使用 .NET Framework、Java、Ruby 或其他單一技術所開發的微服務或服務。

您可以使用的基礎結構平台有很多。 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) 是針對大型且複雜的微服務系統所設計。 [Azure App Service](https://azure.microsoft.com/services/app-service/) 是無狀態微服務的理想選擇。 以 Docker 為依據的微服務替代方案符合任何一種微服務方法，如[容器](#containers)一節中所述。 所有這些平臺都支援 .NET 5，並讓它們適合用來裝載您的微服務。

如需微服務架構的詳細資訊，請參閱 [.Net 微服務。容器化 .NET 應用程式的架構](../architecture/microservices/index.md)。

### <a name="containers"></a>容器

容器通常會與微服務架構搭配使用。 容器也可用來將遵循任何架構模式的 Web 應用程式或服務容器化。 .NET Framework 可用於 Windows 容器，但 .NET 5 的模組化和輕量本質讓它成為容器的較佳選擇。 當您建立和部署容器時，其映射的大小會比 .NET Framework 的 .NET 5 小很多。 舉例來說，因為它是跨平台的，您可以將伺服器應用程式部署到 Linux Docker 容器。

您可以在自己的 Linux 或 Windows 基礎結構中，或在 [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) 等雲端服務中裝載 Docker 容器。 Azure Kubernetes Service 可在雲端中管理、協調及調整容器型應用程式。

### <a name="high-performance-and-scalable-systems"></a>高效能且可擴充的系統

當您的系統需要最佳效能和擴充性時，.NET 5 和 ASP.NET Core 是您的最佳選擇。 Windows Server 和 Linux 的高效能伺服器執行階段讓 .NET 成為 [TechEmpower 基準測試](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext)中效能最高的 Web 架構。

效能和延展性對於微服務架構特別重要，其中可執行數百個微服務。 透過 ASP.NET Core，您就能使用較低數目的伺服器/虛擬機器 (VM) 來執行系統。 減少的伺服器/VM 能省下基礎結構與裝載的相關成本。

### <a name="side-by-side-net-versions-per-application-level"></a>每個應用層級的並存 .NET 版本

若要在不同版本的 .NET 上安裝具有相依性的應用程式，建議使用 .NET 5。 .NET 5 支援在同一部電腦上並存安裝不同版本的 .NET 5 執行時間。 此並存安裝允許同一部伺服器上有多個服務，每個服務都位於自己的 .NET 5 版本 (或 .NET Core 2.1 或 3.1) 。 它也會在應用程式升級和 IT 作業方面降低風險並省下成本。

.NET Framework 無法並存安裝。 它是 Windows 元件，而且一次只能有一個版本存在於一部電腦上。 .NET Framework 的每個版本都會取代先前的版本。 如果您安裝的新應用程式以較新的 .NET Framework 版本為目標，您可能會中斷在電腦上執行的現有應用程式，因為先前的版本已被取代。

## <a name="when-to-choose-net-framework"></a>選擇 .NET Framework 的時機

.NET 5 可為新的應用程式和應用程式模式提供顯著的優點。 不過，.NET Framework 會持續成為許多現有案例的自然選擇，因此在所有伺服器應用程式中，.NET Framework 不會被 .NET 5 取代。

### <a name="current-net-framework-applications"></a>目前的 .NET Framework 應用程式

在大多數情況下，您不需要將現有的應用程式遷移到 .NET 5。 相反地，建議的方法是在擴充現有的應用程式時使用 .NET 5，例如在 ASP.NET Core 中撰寫新的 web 服務。

### <a name="third-party-libraries-or-nuget-packages-not-available-for-net-5"></a>.NET 5 無法使用的協力廠商程式庫或 NuGet 套件

.NET Standard 可讓您跨所有 .NET 執行（包括 .NET 5）共用程式碼。 在 .NET Standard 2.0 中，相容性模式可讓 .NET Standard 和 .NET 5 專案參考 .NET Framework 程式庫。 如需詳細資訊，請參閱 [.NET Framework 程式庫的支援](whats-new/whats-new-in-dotnet-standard.md#support-for-net-framework-libraries)。

只有當程式庫或 NuGet 套件使用 .NET Standard 或 .NET 5 中無法使用的技術時，才需要使用 .NET Framework。

### <a name="net-technologies-not-available-for-net-5"></a>.Net 5 無法使用的 .NET 技術

某些 .NET Framework 技術無法在 .NET 5 中使用。 下列清單顯示在 .NET 5 中找不到的最常見技術：

- ASP.NET Web Forms 的應用程式： ASP.NET Web Forms 僅適用于 .NET Framework。 ASP.NET Core 無法用於 ASP.NET Web Forms。

- ASP.NET Web Pages 應用程式：ASP.NET Web Pages 未隨附於 ASP.NET Core 中。

- WCF 服務實作。 即使有 [wcf 用戶端程式庫](https://github.com/dotnet/wcf) 可從 .net 5 取用 wcf 服務，但 wcf 伺服器的執行目前只在 .NET Framework 中提供。

- 工作流程相關的服務： Windows Workflow Foundation (WF) 、工作流程服務 (單一服務) 中的 WCF + WF，而 WCF Data Services (之前稱為「ADO.NET 資料服務」 ) 僅適用于 .NET Framework。

- 語言支援：目前在 .NET 5 中支援 Visual Basic 和 F #，但並非所有專案類型都支援。 如需支援的專案範本清單，請參閱 [dotnet new 的範本選項](../core/tools/dotnet-new.md#arguments)。

如需詳細資訊，請參閱 [.net 5 中無法使用的 .NET Framework 技術](../core/porting/net-framework-tech-unavailable.md)。

### <a name="platform-doesnt-support-net-5"></a>平臺不支援 .NET 5

某些 Microsoft 或協力廠商平臺不支援 .NET 5。 某些 Azure 服務提供尚未在 .NET 5 上使用的 SDK。 在這種情況下，您可以使用對等的 REST API，而不是用戶端 SDK。

## <a name="see-also"></a>另請參閱

- [在 ASP.NET 和 ASP.NET Core 之間進行選擇](/aspnet/core/choose-aspnet-framework)
- [將目標指向 .NET Framework 的 ASP.NET Core](/aspnet/core/introduction-to-aspnet-core?view=aspnetcore-2.2&preserve-view=true#aspnet-core-targeting-net-framework)
- [目標架構](frameworks.md)
- [.NET 簡介](../core/introduction.md)
- [從 .NET Framework 移植到 .NET 5](../core/porting/index.md)
- [.NET 和 Docker 簡介](../core/docker/introduction.md)
- [.NET 偵錯概觀](components.md)
- [.NET 微服務。容器化 .NET 應用程式的架構](../architecture/microservices/index.md)

---
title: 針對 Docker 容器選擇 .NET Framework 的時機
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 Docker 容器選擇 .NET Framework 的時機
ms.date: 01/30/2020
ms.openlocfilehash: 116ba02878a60487f1af3c2b2e084307fad29618
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414418"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>針對 Docker 容器選擇 .NET Framework 的時機

儘管 .NET Core 可為新的應用程式和應用程式模式提供顯著的優點，但 .NET Framework 仍然是許多現有案例的首選。

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>將現有應用程式直接移轉至 Windows Server 容器

您可能只想要使用 Docker 容器來簡化部署，即使未建立微服務也是一樣。 例如，您可能想要使用 Docker 來改善 DevOps 工作流程；容器可讓您更適當地隔離測試環境，也可以去除移至生產環境時遺失相依性所造成的部署問題。 如果是這些情況，則即使您要部署整合型應用程式，還是可以將 Docker 和 Windows 容器合理地用於目前 .NET Framework 應用程式。

在大部分情況下，於此案例中，您不需要將現有應用程式移轉至 .NET Core；您可以使用包含傳統 .NET Framework 的 Docker 容器。 不過，建議您在擴充現有應用程式時使用 .NET Core，例如，在 ASP.NET Core 中寫入新的服務。

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>使用不適用於 .NET Core 的協力廠商 .NET 程式庫或 NuGet 套件

協力廠商程式庫快速採用 [.NET Standard](../../../standard/net-standard.md)，讓您可以在所有 .net 類別（包括 .net Core）共用程式碼。 使用 .NET Standard 2.0 和更新版本，跨不同架構的 API 介面相容性已變得更大。 更多的是，.NET Core 2.x 和更新版本的應用程式也可以直接參考現有的 .NET Framework 程式庫 (請參閱 [.NET Framework 支援 .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)) 的4.6.1。

此外， [Windows 相容性套件](../../../core/porting/windows-compat-pack.md) 也會擴充 windows 上適用于 .NET Standard 2.0 的 API 介面。 透過此套件，只需要些許修改甚至不需修改，大部分的現有程式碼即可重新編譯為 .NET Standard 2.x，以在 Windows 上執行。

不過，即使自 .NET Standard 2.0 和 .NET Core 2.1 開始有該例外進展，仍然可能有特定 NuGet 套件需要執行 Windows 而且可能不支援 .NET Core 的情況。 如果這些套件對您的應用程式十分重要，則需要在 Windows 容器上使用 .NET Framework。

## <a name="using-net-technologies-not-available-for-net-core"></a>使用不適用於 .NET Core 的 .NET 技術

在此撰寫) 之前，目前版本的 .NET Core (3.1 版無法使用部分 .NET Framework 技術。 其中有些可能會在較新版本中提供使用，但其他則不符合 .NET Core 目標的新應用程式模式，且可能永遠無法使用。

下列清單顯示 .NET Core 3.1 中無法使用的大部分技術：

- ASP.NET Web Form。 只有在 .NET Framework 上才能使用這項技術。 目前並未規劃將 ASP.NET Web Form 帶入 .NET Core。

- WCF 服務。 即使有 [Wcf 用戶端程式庫](https://github.com/dotnet/wcf) 可用來從 .net CORE 取用 wcf 服務，從2020年2月開始，wcf 伺服器的執行只在 .NET Framework 上才可使用。 此案例有可能在未來的 .NET Core 版本中納入，此外也有某些 API 可望在 [Windows 相容性套件](../../../core/porting/windows-compat-pack.md)中納入。

- 工作流程相關服務。 Windows Workflow Foundation (WF)、工作流程服務 (WCF + 單一服務中的 WF) 和 WCF Data Services (先前稱為 ADO.NET Data Services) 僅適用於 .NET Framework。 目前未計劃將它們帶到 .NET Core。

除了官方 [.Net core 藍圖](https://github.com/dotnet/core/blob/master/roadmap.md)中所列的技術之外，其他功能也可能移植到 .net core 或全新的 [統一 .net 平臺](https://devblogs.microsoft.com/dotnet/introducing-net-5/)。 您可以考慮參與 GitHub 上的討論，以便聽取您的心聲。 如果您認為缺少了什麼，請在 [dotnet/runtime](https://github.com/dotnet/runtime/issues/new) GitHub 存放庫中提出新的問題。

## <a name="using-a-platform-or-api-that-doesnt-support-net-core"></a>使用不支援 .NET Core 的平臺或 API

某些 Microsoft 和協力廠商平臺不支援 .NET Core。 例如，有些 Azure 服務提供的 SDK 尚無法在 .NET Core 上使用。 大部分的 Azure SDK 最終應該會移植到 .NET Core/Standard，但有些可能不會有各種原因。 您可以在 [AZURE Sdk 最新版本](https://azure.github.io/azure-sdk/releases/latest/index.html) 頁面中查看可用的 azure sdk。

同時，如果 Azure 中的任何平台或服務仍然不支援 .NET Core 與其用戶端 API，您可以在 .NET Framework 上使用 Azure 服務或用戶端 SDK 中的對等 REST API。

### <a name="additional-resources"></a>其他資源

- **.NET 基礎** \
  [https://docs.microsoft.com/dotnet/fundamentals](../../../fundamentals/index.yml)

- **從 .NET Framework 移植到 .NET Core** \
  [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **Docker 上的 .NET Core 指南** \
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **.NET 元件總覽** \
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[上一個](net-core-container-scenarios.md) 
>[下一步](container-framework-choice-factors.md)

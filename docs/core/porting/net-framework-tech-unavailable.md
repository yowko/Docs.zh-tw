---
title: .NET Core 上無法使用的 .NET Framework 技術
description: 了解無法在 .NET Core 上使用的 .NET Framework 技術
author: cartermp
ms.author: mairaw
ms.date: 04/30/2019
ms.openlocfilehash: bfeea58f4d80b789a7174a77e0784f2326906416
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737099"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>.NET Core 上無法使用的 .NET Framework 技術

有幾種 .NET Framework 程式庫可用的功能並無法搭配 .NET Core 使用，例如 AppDomain、遠端、程式碼存取安全性 (CAS) 和安全性透明。 如果您的程式庫會依賴一或多個這些技術，請考慮使用下述的替代方法。 如需 API 相容性的詳細資訊，請參閱 CoreFX 小組在 GitHub 上維護的[行為變更/相容性中斷及過時/舊版 API 的清單](https://github.com/dotnet/corefx/wiki/ApiCompat) \(英文\)。

目前未實作的 API或技術，並不代表我們是刻意不支援它。 您應先搜尋 .NET Core 的 GitHub 存放庫，確認所發生的某項問題是否為設計原理所致，但若無法證明，請在 GitHub 的 [dotnet/corefx repository issues](https://github.com/dotnet/corefx/issues) (dotnet/corefx 存放庫問題) 中提問，尋求特定的 API 和技術。 [移植要求的相關問題](https://github.com/dotnet/corefx/labels/port-to-core) \(英文\) 會以 `port-to-core` 標籤標記。

## <a name="appdomains"></a>AppDomain

應用程式定義域 (AppDomain) 可將應用程式互相隔離。 AppDomain 需要執行階段支援，且通常具有較高的成本。 目前不支援建立其他應用程式定義域。 我們並未計畫於未來加入此功能。 若要隔離程式碼，建議使用不同的處理序或使用容器作為替代方法。 若要以動態方式載入組件，建議使用新的 <xref:System.Runtime.Loader.AssemblyLoadContext> 類別。

為了讓從 .NET Framework 移轉程式碼更加輕鬆，.NET Core 會公開部分 <xref:System.AppDomain> API 介面。 某些 API 會正常運作 (例如 <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>)，某些成員不會執行任何動作 (例如 <xref:System.AppDomain.SetCachePath%2A>)，而其中某些會擲回 <xref:System.PlatformNotSupportedException> (例如 <xref:System.AppDomain.CreateDomain%2A>)。 檢查您在 [dotnet/corefx GitHub repository](https://github.com/dotnet/corefx) (dotnet/corefx GitHub 存放庫) 中，對 [`System.AppDomain` reference source](https://github.com/dotnet/corefx/blob/master/src/Common/src/CoreLib/System/AppDomain.cs) (`System.AppDomain` 參考來源) 使用的類型，確定選取符合您實作版本的分支。

## <a name="remoting"></a>遠端處理

.NET 遠端處理已被識別為有問題的架構。 該功能是用於目前已不支援的跨 AppDomain 通訊。 此外，遠端處理需要執行階段支援，因此維護成本相當高昂。 基於這些原因，.NET Core 上並不支援 .NET 遠端處理，且我們也未計畫於未來支援該功能。

如需進行跨處理序通訊，請考慮使用處理序間通訊 (IPC) 機制來代替遠端處理，例如 <xref:System.IO.Pipes> 或 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 類別。

針對跨機器通訊，請使用以網路為基礎的替代方案。 最好是使用額外負荷較低的純文字通訊協定，例如 HTTP。 [Kestrel Web 伺服器](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel) \(英文\) 是 ASP.NET Core 所使用的 Web 伺服器，也是此情況下可考慮使用的選項。 針對以網路基礎的跨機器案例，也可以考慮使用 <xref:System.Net.Sockets>。 如需更多選項，請參閱 [.NET Open Source Developer Projects:Messaging](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging) (.NET 開放原始碼開發人員專案：傳訊)。

## <a name="code-access-security-cas"></a>程式碼存取安全性 (CAS)

依賴執行階段或架構來限制受控應用程式或程式庫可使用或執行之資源的沙箱功能，[在 .NET Framework 上並不受支援](~/docs/framework/misc/code-access-security.md)，因此 .NET Core 也不予支援。 .NET Framework 和執行階段中發生太多提高權限的情況，因而無法繼續將 CAS 視為安全性界限。 此外，CAS 會讓實作更為複雜，且經常會對不需要使用它的應用程式，正確性與效能之間帶來潛在的相互影響。

請使用作業系統提供的安全性界限 (例如虛擬化、容器或使用者帳戶) 以一組最小權限執行處理序。

## <a name="security-transparency"></a>安全性透明度

與 CAS 類似，安全性透明度會以宣告方式區隔沙箱化程式碼和安全性關鍵程式碼，但已[不再支援作為安全性界限](~/docs/framework/misc/security-transparent-code.md)。 Silverlight 會大量使用這項功能。 

使用由作業系統提供的安全性界線 (例如虛擬化、容器或使用者帳戶) 來以最少的權限集合執行處理序。

## <a name="systementerpriseservices"></a>System.EnterpriseServices

.NET Core 不支援 System.EnterpriseServices (COM+)。

>[!div class="step-by-step"]
>[下一步](third-party-deps.md)

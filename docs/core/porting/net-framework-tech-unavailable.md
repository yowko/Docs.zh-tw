---
title: .NET Core 上無法使用的 .NET Framework 技術
titleSuffix: ''
description: 了解無法在 .NET Core 上使用的 .NET Framework 技術
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: b75d946b9436b1075a068494b941fbdea5970e42
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795595"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>.NET Core 上無法使用的 .NET Framework 技術

.NET Framework 程式庫可用的數種技術無法與 .NET Core 搭配使用，例如 Appdomain、遠端、代碼啟用安全性（CAS）、安全性透明度和 System.enterpriseservices。 如果您的程式庫會依賴一或多個這些技術，請考慮使用下述的替代方法。 如需有關 API 相容性的詳細資訊，請參閱[.Net Core 重大變更](../compatibility/breaking-changes.md)。

目前未實作的 API或技術，並不代表我們是刻意不支援它。 搜尋適用于 .NET Core 的 GitHub 存放庫，以查看您所遇到的特定問題是否為設計。 如果找不到這類指標，請在[dotnet/runtime 存放庫](https://github.com/dotnet/runtime/issues)中提出問題，以要求特定的 api 和技術。

## <a name="appdomains"></a>AppDomain

應用程式定義域 (AppDomain) 可將應用程式互相隔離。 Appdomain 需要執行時間支援，而且通常很昂貴。 不支援建立額外的應用程式域，而且未來不會有新增這項功能的計畫。 針對程式碼隔離，請使用個別的進程或容器作為替代方案。 若要以動態方式載入元件<xref:System.Runtime.Loader.AssemblyLoadContext> ，請使用類別。

為了讓從 .NET Framework 移轉程式碼更加輕鬆，.NET Core 會公開部分 <xref:System.AppDomain> API 介面。 某些 API 會正常運作 (例如 <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>)，某些成員不會執行任何動作 (例如 <xref:System.AppDomain.SetCachePath%2A>)，而其中某些會擲回 <xref:System.PlatformNotSupportedException> (例如 <xref:System.AppDomain.CreateDomain%2A>)。 在[dotnet/runtime GitHub 存放庫](https://github.com/dotnet/runtime)中，檢查您用於[ `System.AppDomain`參考來源](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs)的類型。 請務必選取符合您所執行版本的分支。

## <a name="remoting"></a>遠端

.NET 遠端處理已被識別為有問題的架構。 該功能是用於目前已不支援的跨 AppDomain 通訊。 此外，遠端處理需要執行階段支援，因此維護成本相當高昂。 基於這些原因，.NET Core 上並不支援 .NET 遠端處理，且我們也未計畫於未來支援該功能。

對於跨進程的通訊，請考慮使用處理序間通訊（IPC）機制做為遠端處理的替代方法<xref:System.IO.Pipes> ，例如類別<xref:System.IO.MemoryMappedFiles.MemoryMappedFile>或類別。

針對跨機器通訊，請使用以網路為基礎的替代方案。 最好是使用額外負荷較低的純文字通訊協定，例如 HTTP。 [Kestrel Web 伺服器](/aspnet/core/fundamentals/servers/kestrel) \(英文\) 是 ASP.NET Core 所使用的 Web 伺服器，也是此情況下可考慮使用的選項。 此外，請考慮<xref:System.Net.Sockets>針對以網路為基礎的跨電腦案例使用。 如需更多選項，請參閱 [.NET 開放原始碼開發人員專案：傳訊](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging) \(英文\)。

## <a name="code-access-security-cas"></a>程式碼存取安全性 (CAS)

依賴執行階段或架構來限制受控應用程式或程式庫可使用或執行之資源的沙箱功能，[在 .NET Framework 上並不受支援](../../framework/misc/code-access-security.md)，因此 .NET Core 也不予支援。 .NET Framework 和執行階段中發生太多提高權限的情況，因而無法繼續將 CAS 視為安全性界限。 此外，CAS 會讓實作更為複雜，且經常會對不需要使用它的應用程式，正確性與效能之間帶來潛在的相互影響。

使用作業系統所提供的安全性界限（例如虛擬化、容器或使用者帳戶），以最小許可權集執行處理常式。

## <a name="security-transparency"></a>安全性透明度

與 CAS 類似，安全性透明度會以宣告方式區隔沙箱化程式碼和安全性關鍵程式碼，但已[不再支援作為安全性界限](../../framework/misc/security-transparent-code.md)。 Silverlight 會大量使用這項功能。

使用作業系統所提供的安全性界限（例如虛擬化、容器或使用者帳戶）來執行具有最低許可權集的進程。

## <a name="systementerpriseservices"></a>System.EnterpriseServices

.NET Core 不支援 System.EnterpriseServices (COM+)。

## <a name="see-also"></a>請參閱

- [從 .NET Framework 移植到 .NET Core 的總覽](index.md)

---
title: 在 .NET Core 和 .NET 5 + 上無法使用 .NET Framework 技術
titleSuffix: ''
description: 瞭解 .NET Core 和 .NET 5.0 和更新版本上無法使用的 .NET Framework 技術。
author: cartermp
ms.date: 10/13/2020
ms.openlocfilehash: 492aace9db3dc3acef18e995f10b7b5fbe251558
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161032"
---
# <a name="net-framework-technologies-unavailable-on-net-core-and-net-5"></a>在 .NET Core 和 .NET 5 + 上無法使用 .NET Framework 技術

.NET Framework 程式庫所提供的數種技術，無法與 .NET Core 和 .NET 5.0 和更新版本搭配使用，例如應用程式域、遠端處理、代碼啟用安全性 (CAS) 、安全性透明度和 <xref:System.EnterpriseServices?displayProperty=fullName> 。 如果您的程式庫依賴一或多個這些技術，請考慮此處所述的替代方法。 如需 API 相容性的詳細資訊，請參閱 [.net 中的重大變更](../compatibility/breaking-changes.md)。

> [!TIP]
> 目前未實作的 API或技術，並不代表我們是刻意不支援它。 搜尋 .NET GitHub 存放庫，以查看您遇到的特定問題是否為設計。 如果您找不到這類指標，請在 [dotnet/runtime 存放庫](https://github.com/dotnet/runtime/issues) 中提出問題，以要求特定的 api 和技術。

## <a name="application-domains"></a>應用程式網域

應用程式定義域 (AppDomain) 可將應用程式互相隔離。 Appdomain 需要執行時間支援，且通常很昂貴。 不支援建立其他應用程式域，而且未來並沒有任何計畫可新增這項功能。 針對程式碼隔離，請使用個別的進程或容器做為替代方案。 若要以動態方式載入元件，請使用 <xref:System.Runtime.Loader.AssemblyLoadContext> 類別。

為了讓程式碼從 .NET Framework 更容易遷移，.NET 5 + 會公開一些 <xref:System.AppDomain> API 介面。 某些 API 會正常運作 (例如 <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>)，某些成員不會執行任何動作 (例如 <xref:System.AppDomain.SetCachePath%2A>)，而其中某些會擲回 <xref:System.PlatformNotSupportedException> (例如 <xref:System.AppDomain.CreateDomain%2A>)。 在[dotnet/Runtime GitHub 存放庫](https://github.com/dotnet/runtime)中，檢查您用於[ `System.AppDomain` 參考來源](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs)的類型。 請務必選取符合您的已執行版本的分支。

## <a name="remoting"></a>遠端

.NET 遠端處理被視為有問題的架構。 它是用來跨應用程式域進行通訊，這些網域已不再受到支援。 此外，遠端處理需要執行時間支援，但維護成本昂貴。 基於這些理由，.net Core 和 .NET 5 + 不支援 .NET 遠端處理，而且我們不打算在未來新增其支援。

針對跨進程的通訊，請考慮 (IPC) 機制的處理序間通訊，作為遠端的替代方式，例如 <xref:System.IO.Pipes> 類別或 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 類別。

針對跨機器通訊，請使用以網路為基礎的替代方案。 最好是使用額外負荷較低的純文字通訊協定，例如 HTTP。 [Kestrel web 伺服器](/aspnet/core/fundamentals/servers/kestrel)是 ASP.NET Core 所使用的 web 伺服器，它是此處的選項。 此外，請考慮 <xref:System.Net.Sockets> 針對以網路為基礎的跨電腦案例使用。 如需更多選項，請參閱 [.NET 開放原始碼開發人員專案：傳訊](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging) \(英文\)。

## <a name="code-access-security-cas"></a>程式碼存取安全性 (CAS)

[在 .NET Framework 上](../../framework/misc/code-access-security.md)，不支援使用執行時間或架構來限制受管理應用程式或程式庫所使用或執行之資源的沙箱化，因此在 .net Core 和 .net 5 + 中也不支援。 .NET Framework 和執行階段中發生太多提高權限的情況，因而無法繼續將 CAS 視為安全性界限。 此外，CAS 會讓實作更為複雜，且經常會對不需要使用它的應用程式，正確性與效能之間帶來潛在的相互影響。

使用作業系統所提供的安全性界限（例如虛擬化、容器或使用者帳戶），以最少的許可權集執行處理常式。

## <a name="security-transparency"></a>安全性透明度

與 CAS 類似，安全性透明度會以宣告的方式將沙箱化程式碼與安全性關鍵程式碼分開，但不再 [支援做為安全性界限](../../framework/misc/security-transparent-code.md)。 Silverlight 會大量使用這項功能。

使用作業系統所提供的安全性界限（例如虛擬化、容器或使用者帳戶），以最少的許可權來執行進程。

## <a name="systementerpriseservices"></a>System.EnterpriseServices

<xref:System.EnterpriseServices?displayProperty=fullName> .NET Core 和 .NET 5 + 不支援 (COM +) 。

## <a name="see-also"></a>另請參閱

- [從 .NET Framework 移植到 .NET Core 的總覽](index.md)

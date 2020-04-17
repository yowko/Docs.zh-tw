---
title: .NET Core 上無法使用的 .NET Framework 技術
titleSuffix: ''
description: 了解無法在 .NET Core 上使用的 .NET Framework 技術
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: 7dfec63870950f12ec933ebf09041b3c8ce2cbb5
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607793"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>.NET Core 上無法使用的 .NET Framework 技術

.NET 框架庫可用的幾種技術不能與 .NET Core 一起使用,例如 AppDomains、遠端處理、代碼存取安全 (CAS)、安全透明度和 System.Enterprise 服務。 如果您的程式庫會依賴一或多個這些技術，請考慮使用下述的替代方法。 有關 API 相容性的詳細資訊,請參閱[.NET 核心中斷變更](../compatibility/breaking-changes.md)。

目前未實作的 API或技術，並不代表我們是刻意不支援它。 搜尋 GitHub 儲存函式庫.NET Core,查看您遇到的特定問題是否由設計。 如果未找到此類指標,請在[dotnet/執行時儲存庫](https://github.com/dotnet/runtime/issues)中提交問題,以請求特定的 API 和技術。 移植請求的問題用[埠到核心](https://github.com/dotnet/runtime/labels/port-to-core)標籤標記。

## <a name="appdomains"></a>AppDomain

應用程式定義域 (AppDomain) 可將應用程式互相隔離。 AppDomain 需要執行階段支援，且通常具有較高的成本。 不支援創建其他應用域,並且將來沒有添加此功能的計劃。 對於代碼隔離,請使用單獨的進程或容器作為替代方法。 要動態載入程式集,請使用類別<xref:System.Runtime.Loader.AssemblyLoadContext>。

為了讓從 .NET Framework 移轉程式碼更加輕鬆，.NET Core 會公開部分 <xref:System.AppDomain> API 介面。 某些 API 會正常運作 (例如 <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>)，某些成員不會執行任何動作 (例如 <xref:System.AppDomain.SetCachePath%2A>)，而其中某些會擲回 <xref:System.PlatformNotSupportedException> (例如 <xref:System.AppDomain.CreateDomain%2A>)。 對照[dotnet/執行時 GitHub 儲存庫](https://github.com/dotnet/runtime)中的[`System.AppDomain`引用源](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs)檢查您使用的類型。 請確保選擇與已實現版本匹配的分支。

## <a name="remoting"></a>遠端

.NET 遠端處理已被識別為有問題的架構。 該功能是用於目前已不支援的跨 AppDomain 通訊。 此外，遠端處理需要執行階段支援，因此維護成本相當高昂。 基於這些原因，.NET Core 上並不支援 .NET 遠端處理，且我們也未計畫於未來支援該功能。

對於跨進程的通信,請考慮進程間通信 (IPC) 機制作為遠端處理的替代方法<xref:System.IO.Pipes>,例如<xref:System.IO.MemoryMappedFiles.MemoryMappedFile>類或 類。

針對跨機器通訊，請使用以網路為基礎的替代方案。 最好是使用額外負荷較低的純文字通訊協定，例如 HTTP。 [Kestrel Web 伺服器](/aspnet/core/fundamentals/servers/kestrel) \(英文\) 是 ASP.NET Core 所使用的 Web 伺服器，也是此情況下可考慮使用的選項。 此外,請考慮將<xref:System.Net.Sockets>之用於基於網路的跨電腦方案。 如需更多選項，請參閱 [.NET 開放原始碼開發人員專案：傳訊](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging) \(英文\)。

## <a name="code-access-security-cas"></a>程式碼存取安全性 (CAS)

依賴執行階段或架構來限制受控應用程式或程式庫可使用或執行之資源的沙箱功能，[在 .NET Framework 上並不受支援](../../framework/misc/code-access-security.md)，因此 .NET Core 也不予支援。 .NET Framework 和執行階段中發生太多提高權限的情況，因而無法繼續將 CAS 視為安全性界限。 此外，CAS 會讓實作更為複雜，且經常會對不需要使用它的應用程式，正確性與效能之間帶來潛在的相互影響。

使用作業系統提供的安全邊界(如虛擬化、容器或使用者帳戶)運行具有最小許可權集的進程。

## <a name="security-transparency"></a>安全性透明度

與 CAS 類似，安全性透明度會以宣告方式區隔沙箱化程式碼和安全性關鍵程式碼，但已[不再支援作為安全性界限](../../framework/misc/security-transparent-code.md)。 Silverlight 會大量使用這項功能。

使用作業系統提供的安全邊界(如虛擬化、容器或使用者帳戶)運行具有最少許可權集的進程。

## <a name="systementerpriseservices"></a>System.EnterpriseServices

.NET Core 不支援 System.EnterpriseServices (COM+)。

## <a name="see-also"></a>另請參閱

- [從 .NET 框架移植到 .NET 核心的概述](../porting/index.md)

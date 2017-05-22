---
title: ".NET Framework 的新功能 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
caps.latest.revision: 292
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: fe9ab371ab8d3eee3778412e446b7aa30b42476b
ms.openlocfilehash: 416e97cd7f59b0fc63052673acee8b55a3c11c1f
ms.contentlocale: zh-tw
ms.lasthandoff: 05/19/2017

---

# <a name="whats-new-in-the-net-framework"></a>.NET Framework 中的新功能
<a name="introduction"></a> 此文章摘要說明下列 .NET Framework 版本的重要新功能和改進：  
 
[.NET Framework 4.7](#v47)   
[.NET Framework 4.6.2](#v462)   
[.NET Framework 4.6.1](#v461)   
[.NET 2015 和 .NET Framework 4.6](#v46)   
[.NET Framework 4.5.2](#v452)   
[.NET Framework 4.5.1](#v451)   
[.NET Framework 4.5](#core)   

此文章並不會提供每一個新功能的完整資料，且內容可能會隨時變更。 如需 .NET Framework 的一般資訊，請參閱[使用者入門](../../../docs/framework/get-started/index.md)。 若要了解支援的平台，請參閱[系統需求](~/docs/framework/get-started/system-requirements.md)。 如需下載連結和安裝指示，請參閱[安裝指南](../../../docs/framework/install/guide-for-developers.md)。

> [!NOTE]
> .NET Framework 小組也會不定期隨著 NuGet 發行相關功能，以擴充平台支援並引進新功能，例如不可變的集合和支援 SIMD 的向量類型。 如需詳細資訊，請參閱[其他類別庫和 API](../additional-apis/index.md) 以及 [.NET Framework 和不定期發行](~/docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)。 請參閱 .NET Framework 的 [NuGet 套件完整清單](https://blogs.msdn.microsoft.com/dotnet/p/nugetpackages/)，或訂閱[我們的摘要](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/)。

<a name="v47"></a> 
## <a name="introducing-the-net-framework-47"></a>.NET Framework 4.7 簡介

.NET Framework 4.7 建置於 .NET Framework 4.6、4.6.1 和 4.6.2 的基礎上，加入許多新的修正和多項新功能，同時保有產品的高穩定性。

### <a name="downloading-and-installing-the-net-framework-47"></a>下載並安裝 .NET Framework 4.7
 
您可以從下列位置下載 .NET Framework 4.7：

- [.NET Framework 4.7 Web 安裝程式](http://go.microsoft.com/fwlink/?LinkId=825299)

- [NET Framework 4.7 離線安裝程式](http://go.microsoft.com/fwlink/?LinkId=825303)

.NET Framework 4.7 可以安裝在 Windows 10、Windows 8.1、Windows 7，以及自 Windows Server 2008 R2 SP1 起的相對應伺服器平台上。 您可以使用 Web 安裝程式或離線安裝程式來安裝 .NET Framework 4.7。 針對大部分的使用者，我們建議使用 Web 安裝程式。

透過安裝 [.NET Framework 4.7 開發人員套件](http://go.microsoft.com/fwlink/?LinkId=825319)，即能以 Visual Studio 2012 或更新版本中的 .NET Framework 4.7 為目標。

### <a name="whats-new-in-the-net-framework-47"></a>.NET Framework 4.7 中的新增功能

.NET Framework 4.7 包含下列領域的新功能：

- [核心](#Core47)
- [網路功能](#net47)
- [ASP.NET](#ASP-NET47)
- [Windows Communication Foundation (WCF)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

如需 .NET Framework 4.7 中加入的新 API 清單，請參閱 GitHub 上的 [.NET Framework 4.7 API 變更 (英文)](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md)。 如需 .NET Framework 4.7 中的功能改進以及錯誤 (Bug) 修正清單，請參閱 GitHub 上的 [.NET Framework 4.7 變更清單 (英文)](http://gutithub.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md)。  如需詳細資訊，請參閱 .NET 部落格中的[宣佈推出 .NET Framework 4.7 (英文)](https://blogs.msdn.microsoft.com/dotnet/2017/04/05/announcing-the-net-framework-4-7/)。

<a name="Core47" />
#### <a name="core"></a>核心

.NET Framework 4.7 改進了 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 所執行的序列化：

**橢圓曲線密碼編譯 (ECC) 的增強功能***

在 .NET Framework 4.7 中，已將 `ImportParameters(ECParameters)` 方法新增到 <xref:System.Security.Cryptography.ECDsa> 和 <xref:System.Security.Cryptography.ECDiffieHellman> 類別，以允許物件代表已經建立的索引鍵。 也加入 `ExportParameters(Boolean)` 方法以使用明確的曲線參數匯出索引鍵。

.NET Framework 4.7 也新增了對其他曲線 (包括 Brainpool 曲線套件) 的支援，並已新增預先定義的定義，可透過新的 <xref:System.Security.Cryptography.ECDsa.Create%2A> 和 <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> Factory 方法輕鬆建立。

您可以在 GitHub 上看到 [.NET Framework 4.7 密碼編譯增強功能的範例](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e)。

**DataContractJsonSerializer 對控制字元有更好的支援**

在 .NET Framework 4.7 中，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 會將控制字元序列化以符合 ECMAScript 6 標準。 針對 .NET Framework 4.7 設計的應用程式預設會啟用此行為，而這對在 .NET Framework 4.7 環境下執行但針對舊版 .NET Framework 設計的應用程式則是選擇性功能。 如需詳細資訊，請參閱 [.NET Framework 4.7 中的重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)。

<a name="net47" />
#### <a name="networking"></a>網路功能

.NET Framework 4.7 新增與網路有關的下列功能︰

**TLS 通訊協定的預設作業系統支援***

<xref:System.Net.Security.SslStream?displayProperty=fullName> 和向上堆疊元件 (例如 HTTP、FTP 和 SMTP) 所使用的 TLS 堆疊可讓開發人員使用作業系統支援的預設 TLS 通訊協定。 開發人員不再需要為 TLS 版本進行硬式編碼。

<a name="ASP-NET47" />
#### <a name="aspnet"></a>ASP.NET

在 .NET Framework 4.7 中，ASP.NET 包含下列新功能：

**物件快取擴充性**

從 .NET Framework 4.7 開始，ASP.NET 加入一組新的 API 讓開發人員取代預設的 ASP.NET 實作以快取記憶體內部物件和監視記憶體。 如果 ASP.NET 實作不適用，開發人員現在可以取代下列三個元件當中的任何一個元件︰

- **物件快取存放區**。 開發人員可以使用新的 **ICacheStoreProvider** 介面，透過新的快取提供者組態區段，為 ASP.NET 應用程式插入新的物件快取實作。
 
- **記憶體監視**。 ASP.NET 中的預設記憶體監視器會在應用程式執行到接近針對處理序所設定的私用位元組上限時，或在電腦可用的總實體 RAM 不足時，通知應用程式。 接近這些限制時，就會引發通知。 對於某些應用程式，通知在太接近設定的限制時才引發，將無法提供有用的反應。 開發人員現在可以使用 <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=fullName> 屬性來撰寫自己的記憶體監視器，以取代預設的監視器。

- **記憶體限制反應**。 ASP.NET 預設會在快達到私用位元組處理限制時，嘗試修剪物件快取並定期呼叫 <xref:System.GC.Collect%2A?displayProperty=fullName>。 就某些應用程式而言，呼叫 <xref:System.GC.Collect%2A?displayProperty=fullName> 的頻率或所修剪的快取量會沒有效率。 開發人員現在可以向應用程式的記憶體監視器訂閱 **IObserver** 實作來取代或補充預設行為。

<a name="wcf47" />
#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

Windows Communication Foundation (WCF) 加入下列功能和變更：

**能夠將預設的訊息安全性設定設定為 TLS 1.1 或 TLS 1.2**

從 .NET Framework 4.7 開始， 除了 SSL 3.0 和 TSL 1.0 之外，WCF 還可讓您設定 TSL 1.1 或 TLS 1.2 作為預設的訊息安全性通訊協定。 這是選擇性的設定。若要啟用，您必須在應用程式組態檔中加入下列項目︰

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" /> 
</runtime>
```

**改進 WCF 應用程式和 WCF 序列化的可靠性**

WCF 包含許多可消除競爭情形的程式碼變更，因此可改善效能和序列化選項的可靠性。 它們包括：

- 在呼叫 **SocketConnection.BeginRead** 和 **SocketConnection.Read** 時更有效地支援混合非同步和同步程式碼。
- 改善中止與 **SharedConnectionListener** 和 **DuplexChannelBinder** 連線時的可靠性。
- 改善呼叫 <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=fullName> 方法時的序列化作業可靠性。
- 改善呼叫 **ChannelSynchronizer.RemoveWaiter** 方法移除等候者時的可靠性。

<a name="wf47" />
#### <a name="windows-forms"></a>Windows Forms

在 .NET Framework 4.7 中，Windows Forms 改善對高 DPI 監視器的支援。

**高 DPI 支援**

從針對 .NET Framework 4.7 設計的應用程式開始，.NET Framework 具備 Windows Forms 應用程式的高 DPI 與動態 DPI 支援。 高 DPI 支援可改善高 DPI 監視器上表單和控制項的配置和外觀。 動態 DPI 則可在使用者變更執行中應用程式的 DPI 或顯示比例時，變更表單和控制項的配置和外觀。

高 DPI 支援是選擇性功能，您可以在應用程式組態檔中定義 [\<System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) 區段來設定。 如需有關如何將高 DPI 支援和動態 DPI 支援加入至 Windows Forms 應用程式的詳細資訊，請參閱 [Windows Forms 中的高 DPI 支援](../winforms/high-dpi-support-in-windows-forms.md)。

<a name="WPF47"></a> 
#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

在 .NET Framework 4.7 中，WPF 包含下列增強功能︰

**根據 Windows WM_POINTER 訊息對觸控/手寫筆堆疊的支援**

您現在可以選擇根據 [WM_POINTER 訊息 (英文)](https://msdn.microsoft.com/library/windows/desktop/hh454903.aspx) 來使用觸控/手寫筆堆疊，而不是根據 Windows Ink Services Platform (WISP)。 這是 .NET Framework 中的選擇性功能。 如需詳細資訊，請參閱 [.NET Framework 4.7 中的重定目標變更](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md)。

**新的 WPF 列印 API 實作**

WPF 在 <xref:System.Printing.PrintQueue?displayProperty=fullName> 類別中的列印 API 會呼叫 Windows [列印文件套件 API](https://msdn.microsoft.com/library/windows/desktop/hh448418(v=vs.85).aspx)，而不是已被取代的 [XPS 列印 API](https://msdn.microsoft.com/library/windows/desktop/ff686814(v=vs.85).aspx)。 如需這項變更對應用程式相容性的影響，請參閱 [.NET Framework 4.7 中的重定目標變更](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md)。 

<a name="v462"></a> 
## <a name="whats-new-in-the-net-framework-462"></a>.NET Framework 4.6.2 的新功能

[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 包含下列領域的新功能：

- [ASP.NET](#ASPNET462)

- [字元類別](#Strings)

- [密碼編譯](#Crypto462)

- [SqlClient](#SQLClient)

- [Windows Communication Foundation](#WCF)

- [Windows Presentation Foundation (WPF)](#WPF462)

- [Windows Workflow Foundation (WF)](#WF462)

- [ClickOnce](#ClickOnce)

- [將 Windows Forms 和 WPF 應用程式轉換成 UWP 應用程式](#UWPConvert)

- [偵錯改進](#Debug462)

如需 .NET Framework 4.6.2 中加入的新 API 清單，請參閱 GitHub 上的 [.NET Framework 4.6.2 API 變更](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md)。 如需 .NET Framework 4..6.2 中的功能改進以及錯誤 (Bug) 修正清單，請參閱 GitHub 上的 [.NET Framework 4.6.2 變更清單 (英文)](http://go.microsoft.com/fwlink/?LinkId=708778)。  如需詳細資訊，請參閱 .NET 部落格中的[宣佈推出 .NET Framework 4.6.2 (英文)](https://blogs.msdn.microsoft.com/dotnet/2016/08/02/announcing-net-framework-4-6-2/)。

<a name="ASPNET462"></a> 
### <a name="aspnet"></a>ASP.NET
 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中，ASP.NET 會包含下列增強功能︰

 **改進對資料註解驗證程式的當地語系化錯誤訊息的支援**
資料註解驗證程式可讓您藉由將一或多個屬性新增至類別內容來執行驗證。 屬性的 <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=fullName> 項目定義了驗證失敗時的錯誤訊息文字。 從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，ASP.NET 可讓您輕鬆地將錯誤訊息當地語系化。 錯誤訊息將會當地語系化，如果︰

1.  <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=fullName> 提供在驗證屬性中。

2.  資源檔儲存在 App_LocalResources 資料夾中。

3.  當地語系化的資源檔名稱格式為 `DataAnnotation.Localization.{`*name*`}.resx`，其中 *name* 是文化特性名稱，格式為 *languageCode*`-`*country/regionCode* 或 *languageCode*。

4.  資源的索引鍵名稱是指派給 <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=fullName> 屬性的字串，其值是當地語系化的錯誤訊息。

 例如，下列資料註解屬性可針對無效評等，定義預設文化特性的錯誤訊息。

```csharp
public class RatingInfo
{
   [Required(ErrorMessage = "The rating must be between 1 and 10.")]
   [Display(Name = "Your Rating")]
   public int Rating { get; set; }
}
```

```vb
Public Class RatingInfo
   <Required(ErrorMessage = "The rating must be between 1 and 10.")>
   <Display(Name = "Your Rating")>
   Public Property Rating As Integer = 1
End Class
```

 然後，您可以建立 DataAnnotation.Localization.fr.resx 資源檔，其索引鍵為錯誤訊息字串，而其值為當地語系化的錯誤訊息。 檔案必須位於 `App.LocalResources` 資料夾中。 例如，下列是索引鍵和其法文 (fr) 當地語系化錯誤訊息的值︰

| 名稱                                 | 值                                     |
| ------------------------------------ | ----------------------------------------- |
| The rating must be between 1 and 10. | La note doit être comprise entre 1 et 10. |

 此檔案即可

 此外，資料註解當地語系化是可延伸的。 開發人員可以藉由實作 <xref:System.Web.Globalization.IStringLocalizerProvider> 介面，在資源檔以外的位置儲存當地語系化字串，而插入他們自己的字串當地語系化程式提供者。

 **對工作階段狀態存放區提供者的非同步支援**
 ASP.NET 現在可允許使用工作傳回方法，搭配工作階段狀態存放區提供者，藉此可讓 ASP.NET 應用程式獲得非同步處理的延展性優勢。 為了支援工作階段狀態存放區提供者的非同步作業，ASP.NET 包含新介面 <xref:System.Web.SessionState.ISessionStateModule?displayProperty=fullName>，它繼承自 <xref:System.Web.IHttpModule>，可讓開發人員實作自己的工作階段狀態模組和非同步工作階段存放區提供者。 介面定義如下：

```csharp
public interface ISessionStateModule : IHttpModule {
    void ReleaseSessionState(HttpContext context);
    Task ReleaseSessionStateAsync(HttpContext context);
}
```

 此外，<xref:System.Web.SessionState.SessionStateUtility> 類別包含兩個新方法：<xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> 和 <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>，它們可用來支援非同步作業。

 **對輸出快取提供者的非同步支援**
 從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，工作傳回方法可以用於輸出快取提供者，以提供非同步處理的延展性優勢。  實作這些方法的提供者能減少 Web 伺服器上的執行緒阻斷，並改善 ASP.NET 服務的延展性。

 已新增下列 API 來支援非同步輸出快取提供者︰

- <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=fullName> 類別，繼承自 <xref:System.Web.Caching.OutputCacheProvider?displayProperty=fullName>，並可讓開發人員實作非同步的輸出快取提供者。

- <xref:System.Web.Caching.OutputCacheUtility> 類別，可提供用於設定輸出快取的 helper 方法。

- <xref:System.Web.HttpCachePolicy?displayProperty=fullName> 類別內的 18 個新方法。 這些包括 <xref:System.Web.HttpCachePolicy.GetCacheability%2A>、<xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>、<xref:System.Web.HttpCachePolicy.GetETag%2A>、<xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>、<xref:System.Web.HttpCachePolicy.GetMaxAge%2A>、<xref:System.Web.HttpCachePolicy.GetMaxAge%2A>、<xref:System.Web.HttpCachePolicy.GetNoStore%2A>、<xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>、<xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>、<xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>、<xref:System.Web.HttpCachePolicy.GetRevalidation%2A>、<xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>、<xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>、<xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A> 和 <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>。

- <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=fullName> 類別內的 2 個新方法：<xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> 和 <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>。

- <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=fullName> 類別內的 2 個新方法：<xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> 和 <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>。

- <xref:System.Web.HttpCacheVaryByParams?displayProperty=fullName> 類別內的 2 個新方法：<xref:System.Web.HttpCacheVaryByParams.GetParams%2A> 和 <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>。

- <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=fullName> 類別中的 <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> 方法。

- <xref:System.Web.Caching.CacheDependency> 中的 <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> 方法。

<a name="Strings"></a> 
### <a name="character-categories"></a>字元類別
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中的字元是根據 [Unicode 標準 8.0.0 版](http://www.unicode.org/versions/Unicode8.0.0/)分類。 在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 和 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 中，字元是根據 Unicode 6.3 字元類別分類。

 對 Unicode 8.0 的支援僅限於 <xref:System.Globalization.CharUnicodeInfo> 類別的字元分類，以及依賴它的類型和方法。 這些包括 <xref:System.Globalization.StringInfo> 類別、多載 <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName> 方法，以及 .NET Framework 規則運算式引擎可辨識的[字元類別](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)。  字元和字串比較和排序不會受到這項變更的影響，並且會繼續依賴基礎作業系統，在 Windows 7 系統上則是依賴 .NET Framework 所提供的字元資料。

 若要了解從 Unicode 6.0 到 Unicode 7.0 的字元類別變更，請參閱 Unicode 協會網站上的 [The Unicode Standard, Version 7.0.0 (Unicode 標準 7.0.0 版)](http://www.unicode.org/versions/Unicode7.0.0/)。 若要了解從 Unicode 7.0 到 Unicode 8.0 的變更，請參閱 Unicode 協會網站上的 [The Unicode Standard, Version 8.0.0 (Unicode 標準 8.0.0 版)](http://www.unicode.org/versions/Unicode8.0.0/)。

<a name="Crypto462"></a> 
### <a name="cryptography"></a>密碼編譯
 **支援包含 FIPS 186-3 DSA 的 X509 憑證**
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 新增了對 DSA (數位簽章演算法) X509 憑證的支援，X509 憑證的金鑰超過 FIPS 186-2 1024 位元的限制。

 除了支援較大的 FIPS 186-3 金鑰大小，[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 也允許使用 SHA-2 系列雜湊演算法 (SHA256、SHA384 及 SHA512) 運算簽章。 FIPS 186-3 支援是由新的 <xref:System.Security.Cryptography.DSACng?displayProperty=fullName> 類別所提供。

 為了保持 .NET Framework 4.6 中 <xref:System.Security.Cryptography.RSA> 類別和 .NET Framework 4.6.1 中 <xref:System.Security.Cryptography.ECDsa> 類別的最新變更，[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中的 <xref:System.Security.Cryptography.DSA> 抽象基底類別有額外的方法，可讓呼叫者使用這項功能，而不用轉型。 您可以呼叫 <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=fullName> 擴充方法來簽署資料，如下列範例所示。

```csharp
public static byte[] SignDataDsaSha384(byte[] data, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPrivateKey())
    {
        return dsa.SignData(data, HashAlgorithmName.SHA384);
    }
}
```

```vb 
Public Shared Function SignDataDsaSha384(data As Byte(), cert As X509Certificate2) As Byte()
    Using DSA As DSA = cert.GetDSAPrivateKey()
        Return DSA.SignData(data, HashAlgorithmName.SHA384)
    End Using
End Function
```

 然後您可以呼叫 <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=fullName> 擴充方法來確認簽署的資料，如下列範例所示。

```csharp
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPublicKey())
    {
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);
    }
}
```

```vb
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean
    Using dsa As DSA = cert.GetDSAPublicKey()
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)
    End Using
End Function
```

 **ECDiffieHellman 金鑰衍生常式的輸入更加清楚**
 .NET Framework 3.5 以三個不同的金鑰衍生函式 (KDF) 常式，新增了對 Ellipic 曲線 Diffie-Hellman 金鑰協定的支援。 常式的輸入以及常式本身，是透過 <xref:System.Security.Cryptography.ECDiffieHellmanCng> 物件上的屬性設定。 但由於不是每個常式都會讀取每個輸入屬性，所以很有可能對過去的開發人員造成混淆。

 為了在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 解決這個問題，下列三種方法已加入 <xref:System.Security.Cryptography.ECDiffieHellman> 基底類別，以便更清楚地表示這些 KDF 常式和其輸入︰

|ECDiffieHellman 方法|描述|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|使用公式衍生金鑰內容<br /><br /> HASH(secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HASH(secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> 其中 *x* 是 EC Diffie-Hellman 演算法的計算結果。|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|使用公式衍生金鑰內容<br /><br /> HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> 其中 *x* 是 EC Diffie-Hellman 演算法的計算結果。|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|使用 TLS 似隨機函式 (PRF) 衍生演算法衍生金鑰內容。|

 **對必要金鑰對稱式加密的支援**
 Windows 密碼編譯程式庫 (CNG) 新增了對儲存必要對稱金鑰和使用硬體儲存之對稱金鑰的支援，[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 讓開發人員可以利用這項功能。  由於金鑰名稱和金鑰提供者的概念是因實作而定，使用此功能需要使用實體實作類型的建構函式，而不是慣用的 factory 方法 (例如呼叫 `Aes.Create`)。

 AES (<xref:System.Security.Cryptography.AesCng>) 及 3DES (<xref:System.Security.Cryptography.TripleDESCng>) 演算法具有必要金鑰的對稱加密支援。 例如: 

```csharp
public static byte[] EncryptDataWithPersistedKey(byte[] data, byte[] iv)
{
    using (Aes aes = new AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider))
    {
        aes.IV = iv;

        // Using the zero-argument overload is required to make use of the persisted key
        using (ICryptoTransform encryptor = aes.CreateEncryptor())
        {
            if (!encryptor.CanTransformMultipleBlocks)
            {
                throw new InvalidOperationException("This is a sample, this case wasn’t handled...");
            }

            return encryptor.TransformFinalBlock(data, 0, data.Length);
        }
    }
}
```

```vb 
Public Shared Function EncryptDataWithPersistedKey(data As Byte(), iv As Byte()) As Byte()
    Using Aes As Aes = New AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider)
        Aes.IV = iv

        ' Using the zero-argument overload Is required to make use of the persisted key
        Using encryptor As ICryptoTransform = Aes.CreateEncryptor()
            If Not encryptor.CanTransformMultipleBlocks Then
                Throw New InvalidOperationException("This is a sample, this case wasn’t handled...")
            End If
            Return encryptor.TransformFinalBlock(data, 0, data.Length)
        End Using
    End Using
End Function
```

 **SHA-2 雜湊的 SignedXml 支援**
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 在 <xref:System.Security.Cryptography.Xml.SignedXml> 類別中新增了對 RSA-SHA256、RSA-SHA384 和 RSA-SHA512 PKCS#1 簽章方法及 SHA256、SHA384 和 SHA512 參考摘要演算法的支援。

 URI 常數會公開在 <xref:System.Security.Cryptography.Xml.SignedXml>：

|SignedXml 欄位|常數|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|

 任何已註冊自訂 <xref:System.Security.Cryptography.SignatureDescription> 處理常式到 <xref:System.Security.Cryptography.CryptoConfig> 以新增這些演算法支援的程式，將會繼續如過去一般運作，但是因為現在有平台預設值，所以不再需要 <xref:System.Security.Cryptography.CryptoConfig> 註冊。

<a name="SQLClient"></a> 
### <a name="sqlclient"></a>SqlClient
 .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient?displayProperty=fullName>) 包含 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 的下列新功能：

 **Azure SQL 資料庫的連線共用和逾時**
 如果啟用連線共用且發生逾時或其他登入錯誤，則會快取例外狀況，而在接下來的 5 秒到 1 分鐘，任何後續連線嘗試都會擲回快取的例外狀況。  如需詳細資訊，請參閱 [SQL Server 連線共用 (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md)。

 連線到 Azure SQL 資料庫時，這個行為並不理想，因為連線嘗試可能會因暫時性錯誤而失敗，但暫時性錯誤通常很快就可復原。 為了進一步最佳化連線重試體驗，在 Azure SQL 資料庫連線失敗時，已移除連線集區封鎖期間行為。

 新增 `PoolBlockingPeriod` 關鍵字可讓您選取最適合您應用程式的封鎖期間。 這些值包括：

 `Auto`
 對於連線到 Azure SQL 資料庫的應用程式，已停用連線集區封鎖期間，而對於連線到任何其他 SQL Server 執行個體的應用程式，已啟用連線集區封鎖期間。 這是預設值。 如果伺服器端點名稱結尾是下列任一項，則會被視為 Azure SQL 資料庫︰

- .database.windows.net

- .database.chinacloudapi.cn

- .database.usgovcloudapi.net

- .database.cloudapi.de

 `AlwaysBlock` 一律啟用連線集區封鎖期間。

 `NeverBlock` 一律停用連線集區封鎖期間。

 **Always Encrypted 的增強功能** SQLClient 導入兩個 Always Encrypted 增強功能︰

- 為了改善對加密資料庫資料行的參數化查詢效能，現在會快取查詢參數的加密中繼資料。 當 <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=fullName> 屬性設定為 `true` (此為預設值) 時，如果多次呼叫相同的查詢，則用戶端只會從伺服器擷取一次參數中繼資料。

- 金鑰快取中的資料行加密金鑰項目現在會在可設定的時間間隔之後收回，而此時間間隔是使用 <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=fullName> 屬性設定。

<a name="WCF"></a> 
### <a name="windows-communication-foundation"></a>Windows Communication Foundation
 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中，Windows Communication Foundation 已在下列領域增強︰

 **支援使用 CNG 儲存之憑證的 WCF 傳輸安全性**
 WCF 傳輸安全性支援使用 Windows 密碼編譯程式庫 (CNG) 儲存的憑證。 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中，這項支援僅限於使用具有公開金鑰的憑證，且指數長度不能超過 32 位元。 當應用程式以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標時，這項功能預設為開啟。

 如果應用程式是以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和舊版為目標，但卻執行於 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 當中，則可將下列這一行加入 app.config 或 web.config 檔的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段。

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

這也可以用程式設計方式，以如下的程式碼完成︰

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

 **透過 DataContractJsonSerializer 類別更妥善支援多個日光節約時間調整規則**
 客戶可以使用應用程式組態設定，來判斷 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 類別是否支援對單一時區使用多個調整規則。 這是一個選擇性功能。 若要啟用它，請將下列設定加入您的 app.config 檔︰

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

啟用這項功能時，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 物件會使用 <xref:System.TimeZoneInfo> 類型，而非使用 <xref:System.TimeZone> 類型來還原序列化日期和時間資料。 <xref:System.TimeZoneInfo> 支援多個調整規則，如此可讓您使用歷史時區資料；<xref:System.TimeZone> 則否。

如需有關 <xref:System.TimeZoneInfo> 結構和時區調整的詳細資訊，請參閱[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)。

**支援在使用 XMLSerializer 類別進行序列化和還原序列化時保留 UTC 時間** 通常，當使用 <xref:System.Xml.Serialization.XmlSerializer> 類別將 UTC <xref:System.DateTime> 值序列化時，它會建立一個序列化時間字串，該字串會保留日期和時間，但會假設時間為當地時間。  例如，如果您藉由呼叫下列程式碼將 UTC 日期和時間具現化︰

```csharp
DateTime utc = new DateTime(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc);
```

```vb
Dim utc As New Date(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc)
```

針對時間晚於 UTC 八小時的系統而言，結果是序列化時間字串 "03:00:00.0000000-08:00"。  序列化值一律會還原序列化為本機日期和時間值。

 您可以使用應用程式組態設定來判斷當序列化和還原序列化 <xref:System.DateTime> 值時，<xref:System.Xml.Serialization.XmlSerializer> 是否保留 UTC 時區資訊︰

```xml 
<runtime>
     <AppContextSwitchOverrides 
          value="Switch.System.Runtime.Serialization.DisableSerializeUTCDateTimeToTimeAndDeserializeUTCTimeToUTCDateTime=false" />
</runtime>
```

啟用這項功能時，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 物件會使用 <xref:System.TimeZoneInfo> 類型，而非使用 <xref:System.TimeZone> 類型來還原序列化日期和時間資料。 <xref:System.TimeZoneInfo> 支援多個調整規則，如此可讓您使用歷史時區資料；<xref:System.TimeZone> 則否。

如需有關 <xref:System.TimeZoneInfo> 結構和時區調整的詳細資訊，請參閱[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)。

 **NetNamedPipeBinding 最符合項目**
 WCF 有新的應用程式設定，可以在用戶端應用程式上設定，以確保它們一律連線到在最符合所要求之 URI 上接聽的服務。 當此應用程式設定設為 `false` (預設值) 時，用戶端可以使用 <xref:System.ServiceModel.NetNamedPipeBinding> 來嘗試連接到正在接聽所要求 URI 子字串之 URI 的服務。

 例如，用戶端嘗試連接到接聽 `net.pipe://localhost/Service1` 的服務，但該電腦上以系統管理員權限執行的不同服務正在接聽 `net.pipe://localhost`。 當此應用程式設定是設為 `false` 時，用戶端會嘗試連線到錯誤的服務。 將應用程式設定設為 `true` 後，用戶端一律都會連接至最符合的服務。

> [!NOTE]
>  使用 <xref:System.ServiceModel.NetNamedPipeBinding> 的用戶端會根據服務的基底位址 (如果存在的話) 來尋找服務，而不是根據完整的端點位址。 為了確保此設定一律適用，服務應該使用唯一的基底位址。

 若要啟用此變更，請先將下列應用程式設定加入用戶端應用程式的 App.config 或 Web.config 檔案︰

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

 **SSL 3.0 不是預設的通訊協定**
 當使用 NetTcp 搭配傳輸安全性和憑證類型的認證時，SSL 3.0 已不再是用來交涉安全連線的預設通訊協定。 在大部分的情況下，應該不會影響現有的應用程式，因為 TLS 1.0 已包含在 NetTcp 的通訊協定清單中。 所有現有的用戶端應該能夠使用至少 TLS 1.0 來交涉連線。      如果需要 SSL3，請使用下列組態機制之一，將它加入交涉通訊協定的清單。

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=fullName> 屬性

- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=fullName> 屬性

- [\<netTcpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) 區段的 [\<transport>](../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) 區段

- [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) 區段的 [\<sslStreamSecurity>](../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) 區段

<a name="WPF462"></a> 
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中，Windows Presentation Foundation 已在下列領域增強︰

 **群組排序**
 使用 <xref:System.Windows.Data.CollectionView> 物件來分組資料的應用程式現在可以明確地宣告如何排序群組。 明確排序可以解決非直覺式排序的問題，此問題發生於應用程式以動態方式新增或移除群組時，或是變更分組時所干涉的項目屬性值時。 它也可以藉由將分組屬性的比較從完整集合排序移至群組排序，改善群組建立程序的效能。

 為了支援群組排序，新的 <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=fullName> 和 <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=fullName> 屬性會描述如何排序 <xref:System.ComponentModel.GroupDescription> 物件所產生的群組集合。 這相當於同名 <xref:System.Windows.Data.ListCollectionView> 屬性描述如何排序資料項目的方式。

 <xref:System.Windows.Data.PropertyGroupDescription> 類別的兩個新靜態屬性，<xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> 和 <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>，可用於大部分的案例。

 比方說，下列 XAML 會依年齡將資料分組、以遞增順序排序年齡群組，並依據姓氏將每個年齡群組內項目分組。

```xaml
<GroupDescriptions>
     <PropertyGroupDescription 
         PropertyName="Age" 
         CustomSort= 
              "{x:Static PropertyGroupDescription.CompareNamesAscending}"/>
     </PropertyGroupDescription>
</GroupDescriptions>

<SortDescriptions>
     <SortDescription PropertyName="LastName"/>
</SortDescriptions>
```

 **螢幕小鍵盤支援**
 螢幕小鍵盤支援可以啟用 WPF 應用程式中的焦點追蹤，方法是當可接受文字輸入的控制項觸控收到輸入時，自動叫用及關閉 Windows 10 中新的螢幕小鍵盤。

 在舊版的 .NET Framework 中，WPF 應用程式必須停用 WPF 畫筆/觸控筆勢支援，才能參加焦點追蹤。  如此一來，WPF 應用程式必須選擇完整 WPF 觸控支援，或是依賴 Windows 滑鼠升級。

 **個別監視器 DPI**
 為了針對 WPF 應用程式支援最近激增的高 DPI 和混合式 DPI 環境，[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 啟用了個別監視器感知。 如需如何啟用 WPF 應用程式之個別監視器 DPI 感知功能的詳細資訊，請參閱 GitHub 上的[範例和開發人員指南](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI)。

 在舊版 .NET Framework 中，WPF 應用程式是系統 DPI 感知。 換句話說，應用程式的 UI 會由作業系統進行適當的縮放，視應用程式呈現所在的監視器 DPI 而定。 ,

 若是在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 下執行的應用程式，您可以將組態陳述式加入應用程式組態檔的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，藉此停用 WPF 應用程式中的個別監視器 DPI 變更，如下所示︰

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462"></a> 
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)
 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中，Windows Workflow Foundation 已在下列領域增強︰

 **Re-hosted WF 設計工具中的 C# 運算式和 IntelliSense 支援**
 自 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 起，WF 在 Visual Studio 設計工具及程式碼工作流程中皆支援 C# 運算式。 Re-hosted 工作流程設計工具是 WF 的重要功能，可讓工作流程設計工具位於 Visual Studio 以外的應用程式中 (例如 WPF 中)。  Windows Workflow Foundation 提供在 Re-hosted 工作流程設計工具中支援 C# 運算式與 IntelliSense 的功能。 如需詳細資訊，請參閱 [Windows Workflow Foundation 部落格](http://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409)。

 `Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`
 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 之前的 .NET Framework 版本中，當客戶從 Visual Studio 重建工作流程專案時，WF 設計工具 IntelliSense 便會中斷。 雖然專案建置成功，但在設計工具中找不到工作流程類型，來自 IntelliSense 的遺漏工作流程類型警告也會出現在 [錯誤清單] 視窗中。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 解決了這個問題，並提供 IntelliSense。

 **開啟工作流程追蹤的工作流程 V1 應用程式現在在 FIPS 模式下執行**
 啟用 FIPS 合規性模式的電腦，現在可以順利執行工作流程 V1 樣式的應用程式，並開啟工作流程追蹤。 若要啟用這種情況，您必須在 app.config 檔案中進行下列變更︰

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

 如果未啟用這種情況，執行應用程式會繼續產生例外狀況，訊息為：「此實作不屬於 Windows Platform FIPS 已驗證密碼編譯演算法的一部分。」

 **搭配 Visual Studio 工作流程設計工具使用動態更新時的工作流程改進**
「工作流程設計工具」、「流程圖活動設計工具」及其他「工作流程活動設計工具」現在可順利載入和顯示在呼叫 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=fullName> 方法之後儲存的工作流程。 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 之前的 .NET Framework 的版本中，若要在 Visual Studio 中，針對在呼叫 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=fullName> 之後儲存的工作流程載入 XAML 檔案，可能會導致下列問題︰

- 工作流程設計工具無法正確載入 XAML 檔案 (當 <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=fullName> 在一行的結尾時)。

- 流程圖活動設計工具或其他工作流程活動設計工具可能會在預設位置顯示所有物件，而不是根據附加的屬性值。

<a name="ClickOnce"></a> 
### <a name="clickonce"></a>ClickOnce
 ClickOnce 已更新為除了已經支援的 TLS 1.0 通訊協定之外，還支援 TLS 1.1 和 TLS 1.2。 ClickOnce 會自動偵測需要哪個通訊協定。若要啟用 TLS 1.1 和 1.2 支援，並不需要在 ClickOnce 應用程式中執行額外的步驟。

<a name="UWPConvert"></a> 
### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>將 Windows Forms 和 WPF 應用程式轉換成 UWP 應用程式
 Windows 現在提供將現有 Windows 傳統型應用程式 (包括 WPF 和 Windows Forms 應用程式) 移植到通用 Windows 平台 (UWP) 的功能。 此技術可作為橋樑，讓您能逐漸將現有的程式碼基底移轉到 UWP，從而將您的應用程式帶到所有 Windows 10 裝置。

 轉換後的傳統型應用程式會取得類似於 UWP 應用程式的應用程式識別，如此便可存取 UWP API，以啟用例如動態磚和通知等功能。 應用程式會繼續和之前一樣運作，而且會以完全信任應用程式的形式執行。 應用程式轉換後，應用程式容器處理序可以加入現有的完全信任處理序，以新增調適性使用者介面。 當所有的功能都移至應用程式容器處理序時，便可以移除完全信任處理序，新的 UWP 應用程式也可以供所有 Windows 10 裝置使用。

<a name="Debug462"></a> 
### <a name="debugging-improvements"></a>偵錯改進
 *Unmanaged 偵錯 API* 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中已增強，可在擲回 <xref:System.NullReferenceException> 時執行額外的分析，因此可以判斷單行原始程式碼中哪個變數為 `null`。   為了支援這種情況，下列 API 已加入 Unmanaged 偵錯 API。

- [ICorDebugCode4](../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)、[ICorDebugVariableHome](../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) 和 [ICorDebugVariableHomeEnum](../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) 介面，它們會公開 Managed 變數的原生主資料夾。 這可讓偵錯工具在 <xref:System.NullReferenceException> 發生時執行某些程式碼流程分析，以及回溯判斷對應至原生位置且為 `null` 的 Managed 變數。

- [ICorDebugType2::GetTypeID](../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) 方法提供 ICorDebugType 到 [COR_TYPEID](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) 的對應，可讓偵錯工具取得 [COR_TYPEID](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)，而不需 ICorDebugType 的執行個體。 [COR_TYPEID](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) 上的現有 API 便可以用來判斷類型的類別配置。

<a name="v461"></a> 
## <a name="whats-new-in-the-net-framework-461"></a>.NET Framework 4.6.1 的新功能
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 包含下列領域的新功能：

- [加密](#Crypto)

- [ADO.NET](#ADO.NET461)

- [Windows Presentation Foundation (WPF)](#WPF461)

- [Windows Workflow Foundation](#WWF461)

- [程式碼剖析](#Profile461)

- [NGen](#NGEN461)

 如需 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 的詳細資訊，請參閱下列主題：

- [.NET Framework 4.6.1 變更清單](http://go.microsoft.com/fwlink/?LinkId=622964)

- [4.6.1 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)

- [.NET Framework API diff](http://go.microsoft.com/fwlink/?LinkId=622989) (於 GitHub)

<a name="Crypto"></a> 
### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>密碼編譯：支援包含 ECDSA 的 X509 憑證
 加入 X509 憑證 RSACng 支援的 .NET Framework 4.6。 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 加入了 ECDSA (橢圓曲線數位簽章演算法) X509 憑證的支援。

 ECDSA 提供較佳的效能，其密碼編譯演算法比 RSA 更安全，為傳輸層安全性 (TLS) 的效能和延展性提供了絕佳的選擇。 .NET Framework 實作會將呼叫包裝在現有的 Windows 功能中。

 下列範例程式碼示範使用 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 包含的 ECDSA X509 憑證新支援，產生位元組資料流的簽章是多麼的輕鬆。

 [!code-csharp[whatsnew.461.crypto#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)] [!code-vb[whatsnew.461.crypto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

 這為所需的程式碼提供標記的對比，以在 .NET Framework 4.6 中產生簽章。

 [!code-csharp[whatsnew.461.crypto#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)] [!code-vb[whatsnew.461.crypto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461"></a> 
### <a name="adonet"></a>ADO.NET
 下列項目已加入 ADO.NET：

 硬體保護金鑰的 Always Encrypted 支援：ADO.NET 現在支援在硬體安全模組 (HSM) 中以原生方式儲存 Always Encrypted 資料行主要金鑰。 透過此支援，客戶不需要撰寫自訂的資料行主要金鑰存放區提供者並向應用程式註冊，即可以使用儲存在 HSM 的非對稱金鑰。

 客戶必須在應用程式伺服器或用戶端電腦上安裝 HSM 廠商提供的 CSP 提供者或 CNG 金鑰存放區提供者，才能存取受到儲存在 HSM 之資料行主要金鑰保護的 Always Encrypted 資料。

 改善 AlwaysOn 的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> 連線行為：SqlClient 現在會自動提供更快的「AlwaysOn 可用性群組」(AG) 連線。 它會明確偵測應用程式是否連線到不同子網路上的 AlwaysOn 可用性群組 (AG)，並快速找到目前使用中的伺服器和提供伺服器連線。 在此版本之前，應用程式必須設定連接字串包含 `"MultisubnetFailover=true"`，以表示它要連線到 AlwaysOn 可用性群組。 如果不在 `true` 設定連接關鍵字，應用程式可能會在連接到 AlwaysOn 可用性群組時發生逾時狀況。 使用此版本，應用程式就「不再」需要將 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> 設定為 `true`。 如需 AlwaysOn 可用性群組的 SqlClient 支援詳細資訊，請參閱[高可用性、嚴重損壞修復的 SqlClient 支援](../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md)。

<a name="WPF461"></a> 
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 Windows Presentation Foundation 包含數個改進和變更。

 改善效能：[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 已修正引發觸控事件的延遲。 此外，<xref:System.Windows.Controls.RichTextBox> 控制項中的輸入也不會在快速輸入期間佔用呈現執行緒。

 改善拼字檢查：Windows 8.1 和更新版本已更新了 WPF 的拼字檢查程式，運用作業系統支援其他語言的拼字檢查。  Windows 8.1 之前的 Windows 版本功能沒有任何變更。

 如同舊版的 .NET Framework，依下列順序尋找資訊會偵測到 <xref:System.Windows.Controls.TextBox> 控制項或 <xref:System.Windows.Controls.RichTextBox> 區塊的語言：

- `xml:lang` (如有)。

- 目前的輸入語言。

- 目前的執行緒文化特性。

 如需 WPF 語言支援的其他資訊，請參閱[討論 .NET Framework 4.6.1 功能的 WPF 部落格文章 (英文)](http://go.microsoft.com/fwlink/?LinkID=691819)。

 每個使用者自訂字典的額外支援：在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 中，WPF 能夠辨識已全域註冊的自訂字典。 這是除了依照每個控制項登錄它們之外的可用功能。

 在舊版的 WPF 中，自訂的字典無法辨識 [已排除單字] 和 [自動校正] 清單。 Windows 8.1 和 Windows 10 透過可置於 `%AppData%\Microsoft\Spelling\<language tag>` 目錄之下使用的檔案支援它們。  下列規則適用於這些檔案：

- 檔案應有副檔名：.dic (用於加入的字詞)、.exc (用於排除的字詞) 或 .acl (用於自動校正)。

- 檔案應為以位元組順序標記 (BOM) 開始的 UTF-16 LE 純文字。

- 每一行的組成應為單字 (在新增和排除的字詞清單中)，或以分隔號 ("&#124;") 分隔的自動校正組合單字 (在 [自動校正] 單字清單中)。

- 系統將這些檔案視為唯讀，而且不會加以修改。

> [!NOTE]
>  WPF 拼字檢查 API 不直接支援這些新的檔案格式，而應用程式中向 WPF 提供的自訂字典應該繼續使用 .lex 檔案。

 範例：MSDN 上有多個 [WPF 範例](https://msdn.microsoft.com/library/ms771633.aspx)。 [開放原始碼 GitHub 存放庫](https://github.com/Microsoft/WPF-Samples)中也將匯入 200 多個最熱門的範例 (根據使用量而定)。 您可以回傳意見調查表或提交 [GitHub 問題](https://github.com/Microsoft/WPF-Samples/issues)，以協助我們改進範例。

 DirectX 擴充功能：WPF 包含一個 [NuGet 套件](http://go.microsoft.com/fwlink/?LinkID=691342)，此套件提供新的 <xref:System.Windows.Interop.D3DImage> 實作，可讓您輕鬆地與 DX10 和 Dx11 內容交互操作。 這個套件的程式碼為開放原始碼，並可於 [GitHub](https://github.com/Microsoft/WPFDXInterop) 取得。

<a name="WWF461"></a> 
### <a name="windows-workflow-foundation-transactions"></a>Windows Workflow Foundation：教學課程
 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=fullName> 方法現在可以使用 MSDTC 以外的分散式交易管理員升級交易。 要想這麼做，請將 GUID 交易升級程式識別碼指定給新的 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=fullName> 多載。 如果這項作業成功，交易的功能上就會放置一些限制。 一旦登錄了非 MSDTC 的交易升級程式，下列方法就會擲回 <xref:System.Transactions.TransactionPromotionException>，因為這些方法需要升級至 MSDTC：

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=fullName>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=fullName>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=fullName>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=fullName>

 一旦登錄了非 MSDTC 的交易升級程式，即必須使用它定義的通訊協定，將它用於未來的永久性登錄。 使用 <xref:System.Transactions.Transaction.PromoterType%2A> 屬性可取得交易升級程式的 <xref:System.Guid>。 當交易升級時，交易升級程式會提供 <xref:System.Byte> 陣列，表示升級的語彙基元。 應用程式可以 <xref:System.Transactions.Transaction.GetPromotedToken%2A> 方法取得非 MSDTC 已升級交易的已升級語彙基元。

 新 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=fullName> 多載的使用者必須遵循特定的呼叫序列，以便升級作業順利完成。 這些規則都會記錄在於方法的文件中。

<a name="Profile461"></a> 
### <a name="profiling"></a>程式碼剖析
 Unmanaged 程式碼剖析 API 已增強下列項目：

 為存取 [ICorProfilerInfo7](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) 介面中的 PDB 提供更好的支援：在 ASP.Net 5 中，由 Roslyn 在記憶體內編譯組件變得更加普遍。 對於製作程式碼剖析工具的開發人員，這表示過去在磁碟上序列化的 PDB 可能不再存在。 程式碼分析工具通常會使用 PDB 對應回工作原始程式行的程式碼，例如程式碼涵蓋範圍或逐行效能分析。 [ICorProfilerInfo7](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) 介面現在包含兩種新方法：[ICorProfilerInfo7::GetInMemorySymbolsLength](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) 和 [ICorProfilerInfo7::ReadInMemorySymbols](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)，讓這些分析工具能夠存取記憶體中的 PDB 資料。分析工具使用新的 API，即可取得記憶體內的 PDB 內容作為位元組陣列，然後予以處理或序列化至磁碟。

 具有 ICorProfiler 介面的更佳檢測方式：使用 `ICorProfiler` API 的 ReJit 功能進行動態檢測的程式碼分析工具，現在可以修改某些中繼資料。 這類工具過去可以隨時檢測 IL，但只能在模組載入時修改中繼資料。 因為 IL 參考中繼資料，這會限制能夠執行的檢測種類。 我們已新增 [ICorProfilerInfo7::ApplyMetaData](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) 方法，以支援在載入模組之後進行中繼資料子集的編輯；尤其還新增 `AssemblyRef`、`TypeRef`、`TypeSpec`、`MemberRef`、`MemberSpec` 和 `UserString` 記錄，藉此解除上述部分限制。 此變更讓更大範圍的即時檢測變成可能。

<a name="NGEN461"></a> 
### <a name="native-image-generator-ngen-pdbs"></a>原生映像產生器 PDB
 跨電腦事件追蹤可讓客戶分析電腦 A 的程式，並使用電腦 B 上對應的原始程式查看程式碼剖析資料。使用舊版的 .NET Framework 時，使用者會將所有模組和原生映像從剖析的機器複製到包含 IL PDB 的分析機器，以建立來源與原生的對應。 雖然這個程序能在檔案較小時運作良好 (例如手機應用程式)，但是桌上型系統的檔案可能非常巨大，而需要大量的複製時間。

 使用 Ngen PDB，NGen 可以建立包含 IL 與原生對應的 PDB，不必依賴 IL PDB。 在我們的跨電腦事件追蹤案例中，您只需要將電腦 A 產生的原生映像 PDB 複製到電腦 B，並使用[偵錯介面存取 API](https://msdn.microsoft.com/library/ee8x173s.aspx)，讀取 IL PDB 的來源與 IL 對應及原生映像 PDB 的 IL 與原生對應。 結合兩個對應可提供來源與原生對應。 由於原生映像 PDB 遠小於所有模組和原生映像，電腦 A 到電腦 B 的複製程序會更快。

<a name="v46"></a> 
## <a name="whats-new-in-net-2015"></a>.NET 2015 的新功能
 .NET 2015 導入了 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 和 .NET 核心。 其中一些新功能適用於兩者，另一些功能則專屬於 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 或 [!INCLUDE[net_core](../../../includes/net-core-md.md)]。

- **ASP.NET 5**

     .NET 2015 包含用於建置現代化雲端式應用程式的簡式 .NET 平台 ASP.NET 5。 這個平台已模組化，因此您只需要在應用程式中包含所需的功能。 這個平台可裝載於 IIS 上或自行裝載於自訂處理序中，而且您可以在同一部伺服器上執行具有不同 .NET Framework 版本的應用程式。 其中所包含的新環境組態系統是專為雲端部署所設計。

     MVC、Web API 和網頁已整合成單一架構，稱為 MVC 6。 您可以透過 Visual Studio 2015 中的新工具來建置 ASP.NET 5 應用程式。 您現有的應用程式可在新的 .NET Framework 上運作；不過若要建置使用 MVC 6 或 SignalR 3 的應用程式，您必須使用 Visual Studio 2015 中的專案系統。

     如需相關資訊，請參閱 [ASP.NET 5](http://go.microsoft.com/fwlink/?LinkId=518238)。

- **ASP.NET 更新**

    - **可非同步排清回應且以工作為基礎的 API**

         ASP.NET 現在提供一個以工作為基礎的簡單 API 來進行非同步回應清除，亦即 <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=fullName>，其可使用您語言的 `async/await` 支援來非同步清除回應。

    - `Model binding supports task-returning methods`

         [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 的 ASP.NET 中已加入模型繫結功能，可保障 Web Form 頁面和使用者控制項中以 CRUD 為基礎之資料作業方式的可延伸性並以程式碼為重心。 模型繫結系統現在支援由 <xref:System.Threading.Tasks.Task>傳回的模型繫結方法。 這項功能可讓 Web Form 開發人員在使用包括 Entity Framework 的較新版 ORM 時，透過簡單的資料繫結系統獲得非同步延展性的優勢。

         非同步模型繫結是由 `aspnet:EnableAsyncModelBinding` 組態設定所控制。

        ```
        <appSettings>
           <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
        </appSettings>
        ```

         若是目標為 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 的應用程式，它會預設為 `true`。 若是在目標為舊版 .NET Framework 但在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 上執行的應用程式，則預設為 `false`。 您可將組態設定設為 `true` 以將其啟用。

    - **HTTP/2 支援 (Windows 10)**

         [HTTP/2](http://www.wikipedia.org/wiki/HTTP/2) 是新版的 HTTP 通訊協定，可大幅改善連線的使用情況 (用戶端和伺服器之間較少往返)，並降低使用者網頁載入的延遲情形。  網頁 (與服務相反) 從 HTTP/2 獲益最明顯，因為通訊協定會針對做為單一體驗之一部分之要求的多個成品進行最佳化。 在 .NET Framework 4.6 中，HTTP/2 支援已加入 ASP.NET。 由於網路功能存在於多個層，因此 Windows、IIS 和 ASP.NET中需要新功能以啟用 HTTP/2。 您必須在 Windows 10 上執行才能搭配 ASP.NET 使用 HTTP/2。

         HTTP/2 也支援使用 <xref:System.Net.Http.HttpClient?displayProperty=fullName> API 的 Windows 10 通用平台 (UWP) 應用程式，並預設為啟用。

         為了提供一個在 ASP.NET 應用程式中使用 [PUSH_PROMISE](http://http2.github.io/http2-spec/#PUSH_PROMISE) 功能的方式，已將含有 <xref:System.Web.HttpResponse.PushPromise%28System.String%29> 和 <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29> 這兩個多載的新方法新增到 <xref:System.Web.HttpResponse> 類別。

        > [!NOTE]
        >  雖然 ASP.NET 5 支援 HTTP/2，但尚未加入 PUSH PROMISE 功能的支援。

         瀏覽器和網頁伺服器 (Windows 上的 IIS) 會執行所有工作。 您不需要為使用者進行任何繁重工作。

         大部分的[主要瀏覽器都支援 HTTP/2](http://www.wikipedia.org/wiki/HTTP/2)，因此如果您的伺服器也支援 HTTP/2，使用者便很可能獲得其中的益處。

    - **對權杖繫結通訊協定的支援**

         Microsoft 與 Google 合作推出了驗證的新方法，稱為[權杖繫結通訊協定](https://github.com/TokenBinding/Internet-Drafts)。 其是假設犯罪者可能竊取位於瀏覽器快取中的驗證權杖，並用來存取本應安全無虞的資源 (例如您的銀行帳戶)，而不需要掌握您的密碼或其他特殊權限。 新的通訊協定旨在減輕這個問題。

         權杖繫結通訊協定將在 Windows 10 中實作為瀏覽器功能。 ASP.NET 應用程式將會參與通訊協定，以便驗證權杖能驗證為合法。 用戶端和伺服器實作會建立通訊協定所指定的端對端保護。

    - **隨機字串雜湊演算法**

         .NET Framework 4.5 引進了[隨機字串雜湊演算法](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)。 不過，由於部分 ASP.NET 功能相依於穩定的雜湊程式碼，因此 ASP.NET 並不支援此演算法。 在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 中，現已支援隨機字串雜湊演算法。 若要啟用這項功能，請使用 `aspnet:UseRandomizedStringHashAlgorithm` 組態設定。

        ```
        <appSettings>
           <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
        </appSettings>
        ```

- **ADO.NET**

     ADO.NET 現在支援 SQL Server 2016 Community Technology Preview 2 (CTP2) 提供的 Always Encrypted 功能。 使用 Always Encrypted，SQL Server 可以對加密資料執行作業，而且最好的是加密金鑰是與應用程式一起位於客戶的受信任環境內，而不是伺服器上。 Always Encrypted 會保護客戶資料安全，因此，DBA 無法存取純文字資料。 資料的加密和解密透明地在驅動程式層級進行，以將變更現有應用程式的需求降到最少。 如需詳細資訊，請參閱 [Always Encrypted (資料庫引擎)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) 和 [Always Encrypted (用戶端開發)](/sql/relational-databases/security/encryption/always-encrypted-client-development)。

- **Managed 程式碼的 64 位元 JIT 編譯器**

     .NET Framework 4.6 提供 64 位元 JIT 編譯器的新版本 (原本的代號是 RyuJIT)。 全新的 64 位元編譯器比舊版 64 位元 JIT 編譯器更大幅提升效能。 在 .NET Framework 4.6 之上執行的 64 位元處理序即會啟用全新的 64 位元編譯器。 若您的應用程式是編譯為 64 位元或 AnyCPU 並在 64 位元作業系統上執行，則會以 64 位元處理序執行。 雖然我們已盡量讓新編譯器的轉換透明化，但仍可能會有行為上的變更。 如果您在使用新的 JIT 編譯器遇到任何問題，歡迎您直接向我們反應。 如果您有任何可能與新的 64 位元 JIT 編譯器相關的問題，請透過 [Microsoft Connect](http://connect.microsoft.com/) 連絡我們。

     新的 64 位元 JIT 編譯器也包含硬體 SIMD 加速功能，在與 <xref:System.Numerics> 命名空間中支援 SIMD 的類型結合時，可產生良好的效能改進。

- **組件載入器改進**

     現在，組件載入器會在載入對應的 NGEN 映像之後即卸載 IL 組件，因此可以更有效率地使用記憶體。 此變更會減少虛擬記憶體，這對大型的 32 位元應用程式 (例如 Visual Studio) 特別有幫助，也可節省實體記憶體。

- **基底類別程式庫變更**

     為了能夠在主要情況下使用，[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 已新增許多 API。 其中包括下列變更和新功能：

    - **IReadOnlyCollection\<T> 實作**

         額外的集合會實作 <xref:System.Collections.Generic.IReadOnlyCollection%601>，例如 <xref:System.Collections.Generic.Queue%601> 和 <xref:System.Collections.Generic.Stack%601>。

    - **CultureInfo.CurrentCulture 和 CultureInfo.CurrentUICulture**

         <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 屬性現在是讀寫，而不是唯讀。 如果您將新的 <xref:System.Globalization.CultureInfo> 物件指派給這些屬性，`Thread.CurrentThread.CurrentCulture` 屬性所定義的目前執行緒文化特性和 `Thread.CurrentThread.CurrentUICulture` 屬性所定義的目前 UI 執行緒文化特性也會隨著變更。

    - **記憶體回收 (GC) 的增強功能**

         <xref:System.GC> 類別現在包含 <xref:System.GC.TryStartNoGCRegion%2A> 和 <xref:System.GC.EndNoGCRegion%2A> 方法，可讓您在執行關鍵路徑期間不允許記憶體回收。

         <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=fullName> 方法的新多載可讓您控制是否要對小型物件堆積和大型物件堆積進行清理和壓縮，還是只要進行清理。

    - **啟用 SIMD 的類型**

         <xref:System.Numerics> 命名空間現在包含數種支援 SIMD 的類型，例如 <xref:System.Numerics.Matrix3x2>、<xref:System.Numerics.Matrix4x4>、<xref:System.Numerics.Plane>、<xref:System.Numerics.Quaternion>、<xref:System.Numerics.Vector2>、<xref:System.Numerics.Vector3> 和 <xref:System.Numerics.Vector4>。

         因為新的 64 位元 JIT 編譯器也包含硬體 SIMD 加速功能，所以在搭配支援 SIMD 的類型與新的 64 位元 JIT 編譯器時有特別顯著的效能改進。

    - **加密更新**

         目前正在更新 <xref:System.Security.Cryptography?displayProperty=fullName> API 以支援 [Windows CNG 密碼編譯 API](https://msdn.microsoft.com/library/windows/desktop/aa376214.aspx)。 舊版 .NET Framework 完全倚賴[舊版的 Windows 密碼編譯 API](https://msdn.microsoft.com/library/windows/desktop/aa380255.aspx)作為 <xref:System.Security.Cryptography?displayProperty=fullName> 實作的基礎。 我們已經要求支援 CNG API，因為它支援[現代的加密演算法](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx#suite_b_support)，這些演算法對特定類別的應用程式來說非常重要。

         .NET Framework 4.6 包含下列新的增強功能，可支援 Windows CNG 密碼編譯 API：

        - 一組適用於 `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` 和 `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` X509 憑證的擴充方法，其會在可能時傳回以 CNG 為基礎的實作，而不是以 CAPI 為基礎的實作 (有些智慧卡仍需要 CAPI，因此 API 可處理這類後援。)

        - <xref:System.Security.Cryptography.RSACng?displayProperty=fullName> 類別，可提供的 RSA 演算法的 CNG 實作。

        - RSA API 的增強功能，可讓一般動作不再需要轉型。 例如，當使用 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 物件來加密資料時，需使用類似舊版 .NET Framework 中的下列程式碼。

             [!code-csharp[WhatsNew.Casting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]    [!code-vb[WhatsNew.Casting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

             您可將使用 .NET Framework 4.6 中新加密 API 的程式碼改寫如下，以避免轉型。

             [!code-csharp[WhatsNew.Casting#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]    [!code-vb[WhatsNew.Casting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

    - **支援日期和時間的 UNIX 時間來回轉換**

         <xref:System.DateTimeOffset> 結構已加入下列新方法，以支援日期和時間值的 Unix 時間來回轉換：

        - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=fullName>

        - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=fullName>

        - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=fullName>

        - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=fullName>

    - **相容性參數**

         新 <xref:System.AppContext> 類別加入了新的相容性功能，可讓程式庫作者為使用者提供新功能的統一退出機制。 它會建立元件之間的鬆散結合合約，以便溝通退出要求。 變更現有的功能時，此功能通常特別重要。 相反地，已經有新功能的隱含選擇加入。

         使用 <xref:System.AppContext>，程式庫會定義並公開相容性參數，而依賴它們的程式碼則可以設定這些參數來影響程式庫行為。 根據預設，程式庫可提供新的功能，且它們只會在已設定此參數時變更它 (亦即，它們提供先前的功能)。

         應用程式 (或程式庫) 可以宣告相依程式庫定義之參數的值 (一律為 <xref:System.Boolean> 值)。 參數一律隱含為 `false`。 將參數設定為 `true` 可啟用它。 明確地將參數設定為 `false` 提供了新行為。

        ```csharp
        AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
        ```

         程式庫必須檢查取用者是否已宣告參數的值，然後適當地處理它。

        ```csharp
        if (!AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", out shouldThrow)) 
        {
           // This is the case where the switch value was not set by the application. 
           // The library can choose to get the value of shouldThrow by other means. 
           // If no overrides nor default values are specified, the value should be 'false'. 
           // A false value implies the latest behavior.
        }

           // The library can use the value of shouldThrow to throw exceptions or not.
           if (shouldThrow) 
           {
              // old code
           }
           else {
              // new code
           }
        }

        ```

         使用一致的參數格式很有幫助，因為它們是程式庫公開的正式合約。 以下是兩種明顯的格式。

        - *參數*.*命名空間*.*參數名稱*

        - *參數*.*程式庫*.*參數名稱*

    - **以工作為基礎的非同步模式 (TAP) 的變更**

         在以 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 為目標的應用程式中，<xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 物件會繼承呼叫端執行緒的文化特性和 UI 文化特性。 以舊版 .NET Framework 為目標或未以特定 .NET Framework 版本為目標的應用程式行為則不會受到影響。 如需詳細資訊，請參閱 <xref:System.Globalization.CultureInfo> 類別主題的＜文化特性和以工作為基礎的非同步作業＞一節。

         若某環境資料是指定之非同步控制流程的本機環境資料，例如 `async` 方法，則可用 <xref:System.Threading.AsyncLocal%601?displayProperty=fullName> 類別來表示。 它可以用來跨執行緒保存資料。 您也可以定義每當因 <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=fullName> 屬性已明確變更或因執行緒發生內容切換時而變更環境資料時，接收通知的回撥方法。

         以工作為基礎的非同步模式 (TAP) 中已加入 <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=fullName>、<xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=fullName> 和 <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=fullName> 三種便利的方法，可傳回特定狀態中已完成的工作。

         <xref:System.IO.Pipes.NamedPipeClientStream> 類別現可支援與其新的 <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A> 進行非同步通訊。 方法。

    - **EventSource 現在支援寫入事件記錄檔**

         不只電腦上建立的任何現有 ETW 工作階段，您現在還可以使用 <xref:System.Diagnostics.Tracing.EventSource> 類別，將管理或操作訊息記錄到事件記錄檔中。 以往，您必須使用 Microsoft.Diagnostics.Tracing.EventSource NuGet 套件，才能使用這項功能。 .NET Framework 4.6 現已內建此功能。

         NuGet 套件和 .NET Framework 4.6 已更新下列功能：

        - **動態事件**

             可「動態」定義事件，而不需建立事件方法。

        - **豐富型裝載**

             允許專用類別和陣列，以及基本類型做為裝載傳遞

        - **活動追蹤**

             可讓開始與結束事件使用識別碼來標記它們之間的事件，以代表目前作用中的所有活動。

         為了支援這些功能，已將多載 <xref:System.Diagnostics.Tracing.EventSource.Write%2A> 方法加入<xref:System.Diagnostics.Tracing.EventSource> 類別。

- **Windows Presentation Foundation (WPF)**

    - **HDPI 改進**

         現在，WPF 提供比 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 更好的 HDPI 支援。 已變更版面配置進位，以減少含邊界之控制項中的裁剪執行個體。 根據預設，這項功能只有當您將<xref:System.Runtime.Versioning.TargetFrameworkAttribute> 設為 .NET 4.6 時才會啟用。  如果應用程式是以舊版 Framework 為目標，但卻執行於 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 當中，則可將下列這一行加入 app.config 檔的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，以選擇加入新的行為：

        ```
        <AppContextSwitchOverrides
        value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
        />
        ```

         含不同 DPI 設定 (多 DPI 設定) 且跨多個監視器的 WPF 視窗，現可完全顯示，而不會有被遮蔽的區域。 您可將下列這一行加入 app.config 檔的 `<appSettings>` 區段，以選擇停用這項新的行為：

        ```
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>
        ```

         <xref:System.Windows.Input.Cursor?displayProperty=fullName> 已支援自動依據 DPI 設定載入正確的游標。

    - **觸控功能較佳**

         [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 已將客戶向 [Connect](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) 回報的觸控行為異常問題解決。 Windows 市集應用程式和 WPF 應用程式的點兩下臨界值現與 Windows 8.1 和更新版本相同。

    - **支援透明的子視窗**

         [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 中的 WPF 支援 Windows 8.1 和更新版本的透明子視窗功能。 這可讓您在最上層視窗中建立非矩形和透明的子視窗。 您可以將 <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=fullName> 屬性設為 `true`，藉此啟用這個功能。

- **Windows Communication Foundation (WCF)**

    - **SSL 支援**

         搭配使用 NetTcp 與傳輸安全性和用戶端驗證時，除了 SSL 3.0 和 TLS 1.0 之外，WCF 現在還支援 TLS 1.1 和 TLS 1.2 的 SSL 版。 現在，您可以選取要使用哪一種通訊協定，或停用較不安全的舊版通訊協定。 若要完成這項作業，您可設定 <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> 屬性或於組態檔中加入下列內容。

        ```
        <netTcpBinding>
           <binding>
              <security mode= "None|Transport|Message|TransportWithMessageCredential" >
                 <transport clientCredentialType="None|Windows|Certificate"
                            protectionLevel="None|Sign|EncryptAndSign"
                            sslProtocols="Ssl3|Tls1|Tls11|Tls12">
                    </transport>
              </security>
           </binding>
        </netTcpBinding>
        ```

    - **使用不同的 HTTP 連線傳送訊息**

         現在，WCF 可讓使用者使用不同的底層 HTTP 連線以確保成功傳送特定訊息。 執行此作業的方法有兩種：

        - **使用連線群組名稱前置詞**

             使用者可以指定字串，讓 WCF 做為可達到連線群組名稱的前置詞。 系統會使用不同的基礎 HTTP 連線來傳送含有不同前置詞的兩個訊息。 您可以將鍵/值組加入訊息的 <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=fullName> 屬性，以設定前置詞。 索引鍵是 "HttpTransportConnectionGroupNamePrefix"；值則為所需的前置詞。

        - **使用不同的通道處理站**

             使用者也可以啟用功能，針對使用不同通道處理站建立之通道所傳送的訊息，使用不同的底層 HTTP 連線。 若要啟用此功能，使用者必須將下列 `appSetting` 設定為 `true`：

            ```
            <appSettings>
               <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
            </appSettings>
            ```

- **Windows Workflow Foundation (WWF)**

     現在，若有未處理的「非通訊協定」書籤時，您可以指定工作流程服務在不按照順序的作業要求逾時之前會保存該要求的秒數。 「非通訊協定」書籤是指與未處理的 Receive 活動無關的書籤。 有些活動會在其實作中建立非通訊協定書籤，因此可能不容易察覺到非通訊協定書籤的存在。 這些活動包括 State 和 Pick。 因此如果您有使用狀態機器或包含 Pick 活動的工作流程服務實作，就很可能會有非通訊協定書籤。 您可將如下一行加入 app.config 檔案的 `appSettings` 區段，以指定間隔：

    ```
    <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
    ```

     預設值為 60 秒。 如果 `value` 設定為 0，系統會立即拒絕不按照順序的要求，並顯示如下的錯誤文字：

    ```
    Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees. 
    ```

     如果收到不按照順序的作業訊息，但沒有非通訊協定書籤時，也會收到相同的訊息。

     如果 `FilterResumeTimeoutInSeconds` 項目的值是非零，並有非通訊協定的書籤，而逾時間隔也已過期，則作業會失敗並顯示逾時訊息。

- **交易**

     現在，若交易導致衍生自 <xref:System.Transactions.TransactionException> 的例外狀況擲回時，您可以針對該交易包含分散式的交易識別碼。 您可以在 app.config 檔的`appSettings` 區段中加入下列索引鍵，以完成這項作業：

    ```
    <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/> 
    ```

     預設值是 `false`。

- **網路功能**

    - **通訊端重複使用**

         Windows 10 包含新的高延展性網路功能演算法，其可重複為對外 TCP 連線使用本機連接埠，以更妥善運用電腦資源。 .NET Framework 4.6 支援新的演算法，可讓 .NET 應用程式利用這個新行為。 在舊版的 Windows 中，並沒有人為的並行連線限制 (通常為動態連接埠範圍的預設大小 16,384)，因此當負載下的連接埠耗盡時，可能會限制服務的延展性。

         為了讓連接埠可以重複使用，在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 中加入了兩個新的 API，其可有效地移除並行連線的 64K 限制：

        - <xref:System.Net.Sockets.SocketOptionName?displayProperty=fullName> 列舉值。

        - <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=fullName> 屬性。

         除非 `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` 登錄機碼的 `HWRPortReuseOnSocketBind` 值設定為 0x1，否則 <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=fullName> 屬性皆預設為 `false`。 若要啟用 HTTP 連線上的本機連接埠重複使用，請將 <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=fullName> 屬性設為 `true`。 這會使得所有從 <xref:System.Net.Http.HttpClient> 和 <xref:System.Net.HttpWebRequest> 傳出的 TCP 通訊端連線都使用新的 Windows 10 通訊端選項 ([SO_REUSE_UNICASTPORT](https://msdn.microsoft.com/library/windows/desktop/ms740532.aspx))，而能夠重複使用本機連接埠。

         如果開發人員撰寫僅限通訊端的應用程式，即可在呼叫 <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=fullName> 之類的方法時指定 <xref:System.Net.Sockets.SocketOptionName?displayProperty=fullName> 選項，以讓對外的通訊端在繫結期間重複使用本機連接埠。

    - **支援國際網域名稱和 PunyCode**

         <xref:System.Uri> 類別中已加入新屬性 <xref:System.Uri.IdnHost%2A>，可更妥善支援國際化網域名稱和 PunyCode。

- **調整 Windows Forms 控制項的大小。**

     這項功能在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 中已擴充，現在包含 <xref:System.Windows.Forms.DomainUpDown>、<xref:System.Windows.Forms.NumericUpDown>、<xref:System.Windows.Forms.DataGridViewComboBoxColumn>、<xref:System.Windows.Forms.DataGridViewColumn> 和 <xref:System.Windows.Forms.ToolStripSplitButton> 類型，以及 <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> 屬性所指定的矩形，可在繪製 <xref:System.Drawing.Design.UITypeEditor> 時使用。

     這是一項選擇性功能。 若要啟用此功能，請將應用程式組態檔 (app.config) 中的 `EnableWindowsFormsHighDpiAutoResizing` 項目設定為 `true`：

    ```
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

- **字碼頁編碼方式的支援**

     [!INCLUDE[net_core](../../../includes/net-core-md.md)] 主要支援 Unicode 編碼方式，並且預設會提供字碼頁編碼方式的有限支援。 您可以透過使用 <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=fullName> 方法註冊字碼頁編碼方式，來加入 .NET Framework 中可用但不受 [!INCLUDE[net_core](../../../includes/net-core-md.md)] 支援之字碼頁編碼方式的支援。 如需詳細資訊，請參閱<xref:System.Text.CodePagesEncodingProvider?displayProperty=fullName>。

- **.NET Native**

     以 [!INCLUDE[net_core](../../../includes/net-core-md.md)] 為目標並以 C# 或 Visual Basic 撰寫的 Windows 10 應用程式，現在可以利用將應用程式編譯成機器碼的新技術，而不是使用 IL。 所產生之應用程式的特色是啟動和執行都更快。 如需詳細資訊，請參閱[使用 .NET Native 編譯應用程式](../../../docs/framework/net-native/index.md)。 如需 .NET Native 概觀，請參閱 [.NET Native 和編譯](../../../docs/framework/net-native/net-native-and-compilation.md)，其中探討 .NET Native 與 JIT 編譯和 NGEN 之間的差異，以及對您的程式碼所代表的意義。

     當您使用 Visual Studio 2015 編譯您的應用程式時，它們預設會編譯成機器碼。 如需詳細資訊，請參閱 [.NET Native 使用者入門](../../../docs/framework/net-native/getting-started-with-net-native.md)。

     為了支援對 .NET Native 應用程式進行偵錯，Unmanaged 偵錯 API 已新增許多介面和列舉。 如需詳細資訊，請參閱[偵錯 (Unmanaged API 參考)](../../../docs/framework/unmanaged-api/debugging/index.md) 主題。

- **開放原始碼 .NET Framework 套件**

     [!INCLUDE[net_core](../../../includes/net-core-md.md)] 套件 (例如不可變的集合)、[SIMD API](http://go.microsoft.com/fwlink/?LinkID=518639) 及網路功能 API (例如在 <xref:System.Net.Http> 命名空間中找到的 API) 現在都在 [GitHub](https://github.com/) 上以開放原始碼套件的形式提供。 若要存取這些程式碼，請參閱 GitHub 上的 [NetFx](http://go.microsoft.com/fwlink/?LinkID=518634)。 如需詳細資訊以及如何參與這些套件的建立，請前往 [itHub 上的 .NET 首頁](http://go.microsoft.com/fwlink/?LinkID=518635)，並參閱 [.NET Core 和開放原始碼](../../../docs/framework/get-started/net-core-and-open-source.md)。

 [回到頁首](#introduction)

<a name="v452"></a> 
## <a name="whats-new-in-the-net-framework-452"></a>.NET Framework 4.5.2 中的新增功能

- **ASP.NET 應用程式的全新 API。** 新的 <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=fullName> 和 <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=fullName> 方法可讓您在回應清除至用戶端應用程式時，檢查及修改回應標頭和狀態碼。 請考慮使用這些方法來取代 <xref:System.Web.HttpApplication.PreSendRequestHeaders> 和 <xref:System.Web.HttpApplication.PreSendRequestContent> 事件，這些方法的效率更高且更可靠。

     <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=fullName> 方法可讓您排程小型背景工作項目。 完成所有背景工作項目之前，ASP.NET 會追蹤這些項目，並防止 IIS 突然終止背景工作處理序。 此方法只能在 ASP.NET Managed 應用程式網域內呼叫。

     新的 <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=fullName> 和 <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=fullName> 屬性傳回布林值，指出是否已寫入回應標頭。 您可以使用這些屬性確定 <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=fullName> 等的 API 呼叫成功 (如果已寫入標頭，則擲回例外狀況)。

- **調整 Windows Forms 控制項的大小。** 此功能已擴充。 您現在可以使用系統 DPI 設定來調整下列其他控制項的元件大小 (例如下拉式方塊中的下拉式箭頭)：

     <xref:System.Windows.Forms.ComboBox>    <xref:System.Windows.Forms.ToolStripComboBox>    <xref:System.Windows.Forms.ToolStripMenuItem>    <xref:System.Windows.Forms.Cursor>    <xref:System.Windows.Forms.DataGridView>    <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

     這是一個選擇性功能。 若要啟用此功能，請將應用程式組態檔 (app.config) 中的 `EnableWindowsFormsHighDpiAutoResizing` 項目設定為 `true`：

    ```
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

- **新工作流程功能。** 使用 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> 方法 (進而實作 <xref:System.Transactions.IPromotableSinglePhaseNotification> 介面) 的資源管理員可使用新的 <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=fullName> 方法來要求下列作業：

    - 將交易提升至 Microsoft 分散式交易協調器 (MSDTC) 交易。

    - 以支援單一階段認可的永久性登記 <xref:System.Transactions.IPromotableSinglePhaseNotification> 取代 <xref:System.Transactions.ISinglePhaseNotification>。

     您可以在相同的應用程式網域中完成這些作業，而不需要任何額外的 Unmanaged 程式碼來與 MSDTC 互動以進行提升。 僅當 <xref:System.Transactions?displayProperty=fullName> 對可提升登記未實作之 <xref:System.Transactions.IPromotableSinglePhaseNotification>`Promote` 方法的呼叫未完成時，才會呼叫此新方法。

- **程式碼剖析改進。** 下列新的 Unmanaged 程式碼分析 API 提供更強大的程式碼分析功能：

     [COR_PRF_ASSEMBLY_REFERENCE_INFO 結構](../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) 
     [COR_PRF_HIGH_MONITOR 列舉](../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) 
     [GetAssemblyReferences 方法](../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) 
     [GetEventMask2 方法](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) 
     [SetEventMask2 方法](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) 
     [AddAssemblyReference 方法](../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

     之前的 `ICorProfiler` 實作支援相依組件的消極式載入。 新程式碼分析 API 要求可立即載入分析工具插入的相依組件，而不是在完全初始化應用程式之後才載入。 此變更不會影響現有 `ICorProfiler` API 的使用者。

- **偵錯改進。** 下列新的 Unmanaged 偵錯 API 提供與分析工具更佳的整合。 您現在可以存取分析工具插入的中繼資料，並存取偵錯傾印時編譯器 ReJIT 要求所產生的區域變數和程式碼。

     [SetWriteableMetadataUpdateMode 方法](../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) 
     [EnumerateLocalVariablesEx 方法](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) 
     [GetLocalVariableEx 方法](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) 
     [GetCodeEx 方法](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) 
     [GetActiveReJitRequestILCode 方法](../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md) 
     [GetInstrumentedILMap 方法](../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- **事件追蹤變更。** .NET Framework 4.5.2 可對更大的表面區域進行 Windows 事件追蹤 (ETW) 的跨處理序活動追蹤。 此功能可讓進階電源管理 (APM) 廠商提供輕量型工具，以精確追蹤跨執行緒之個別要求和活動的成本。  僅當 ETW 控制器啟用這些事件時，才會引發事件；因此，這些變更不會影響之前撰寫的 ETW 程式碼或停用 ETW 時所執行的程式碼。

- **升級交易並將它轉換成永久性登記**

     <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=fullName> 是新加入 .NET Framework 4.5.2 和 4.6 的 API：

    ```csharp
    [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]
    public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,
                                              IPromotableSinglePhaseNotification promotableNotification,
                                              ISinglePhaseNotification enlistmentNotification,
                                              EnlistmentOptions enlistmentOptions)
    ```

     此方法可讓先前由 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=fullName> 所建立的登錄用來回應 <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=fullName> 方法。 它會要求 `System.Transactions` 將交易升級為 MSDTC 交易，並將可升級登記「轉換」為永久性登記。 這個方法成功完成之後，<xref:System.Transactions.IPromotableSinglePhaseNotification> 介面將不再受 `System.Transactions` 參考，且會將任何未來的通知送至所提供的  <xref:System.Transactions.ISinglePhaseNotification> 介面。 登記必須做為永久性登記，才可支援交易記錄和復原。 如需詳細資訊，請參閱 <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=fullName>。 此外，登記必須支援 <xref:System.Transactions.ISinglePhaseNotification>。  只有在處理 <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=fullName> 呼叫時，「才」可以呼叫此方法。 若否，則會擲回 <xref:System.Transactions.TransactionException> 例外狀況。

 [回到頁首](#introduction)

<a name="v451"></a> 
## <a name="whats-new-in-the-net-framework-451"></a>.NET Framework 4.5.1 中的新增功能
 **2014 年 4 月更新**：

- [Visual Studio 2013 Update 2](http://go.microsoft.com/fwlink/p/?LinkId=393658) 包含可攜式類別庫範本的更新，以便針對下列情況提供支援：

    - 您可以使用以 Windows 8.1、Windows Phone 8.1 和 Windows Phone Silverlight 8.1 為目標之可攜式類別庫中的 Windows 執行階段 API。

    - 當您以 Windows 8.1 或 Windows Phone 8.1 為目標時，可將 XAML (Windows.UI.XAML 類別) 加入至可攜式類別庫中。 支援下列 XAML 範本：「空白網頁」、「資源字典」、「樣板化控制項」和「使用者控制項」。

    - 您可以建立可攜式 Windows 執行階段元件 (.winmd 檔案)，以便用於以 Windows 8.1 和 Windows Phone 8.1 為目標的市集應用程式。

    - 您可以像是可攜式類別庫一樣，重定 Windows 市集或 Windows Phone 市集類別庫的目標。

     如需這些變更的詳細資訊，請參閱[可攜式類別庫](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)。

- .NET Framework 內容集現在包含 [!INCLUDE[net_native](../../../includes/net-native-md.md)] (用於建置及部署 Windows 應用程式的先行編譯技術) 的文件。 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 會將您的應用程式直接編譯為機器碼 (而不是中繼語言 (IL)) 以提升效能。 如需詳細資訊，請參閱[使用 .NET Native 編譯應用程式](../../../docs/framework/net-native/index.md)。

- [.NET Framework 參考來源](http://referencesource.microsoft.com/)提供新瀏覽體驗和增強功能。 您現在可以在線上瀏覽 .NET Framework 原始程式碼、[下載參考](http://referencesource.microsoft.com/download.html)以供離線檢視，並在偵錯時逐步執行原始程式碼 (包含修補程式和更新)。 如需詳細資訊，請參閱部落格文章：[.NET 參考來源的新風貌 (英文)](https://blogs.msdn.microsoft.com/dotnet/2014/02/24/a-new-look-for-net-reference-source/)。

 .NET Framework 4.5.1 的核心新功能和增強功能包括：

- 組件的自動繫結重新導向。 從 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 開始，當您編譯鎖定 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 的應用程式時，如果您的應用程式或其元件參考相同組件的多個版本，就可能會將繫結重新導向加入至應用程式組態檔。 您也可以對鎖定舊版 .NET Framework 的專案啟用這項功能。 如需詳細資訊，請參閱[操作說明：啟用和停用自動繫結重新導向](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)。

- 可收集診斷資訊，協助開發人員改進伺服器和雲端應用程式效能的功能。 如需詳細資訊，請參閱 <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> 類別中的 <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> 和 <xref:System.Diagnostics.Tracing.EventSource> 方法。

- 可在記憶體回收期間明確壓縮大型物件堆積 (LOH) 的功能。 如需詳細資訊，請參閱 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=fullName> 屬性 (Property)。

- 其他效能改進功能包括 ASP.NET 應用程式暫止、多核心 JIT 改進功能，以及 .NET Framework 更新後應用程式更快速啟動。 如需詳細資訊，請參閱 [.NET Framework 4.5.1 公告 (英文)](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/)和 [ASP.NET 應用程式暫止 (英文)](https://blogs.msdn.microsoft.com/dotnet/2013/10/09/asp-net-app-suspend-responsive-shared-net-web-hosting/) 部落格文章。

 Windows Forms 的增強功能包括：

- 調整 Windows Forms 控制項的大小。 您可以透過在應用程式的應用程式組態檔中選擇加入一個項目，使用系統 DPI 設定來調整控制項的元件大小 (例如屬性方格中出現的圖示)。 目前支援此功能的 Windows Forms 控制項如下：

     <xref:System.Windows.Forms.PropertyGrid>    <xref:System.Windows.Forms.TreeView>    <xref:System.Windows.Forms.DataGridView> 的某些部分 (請參閱 [4.5.2 的新功能](#v452)以了解其他支援的控制項)

     若要啟用此功能，請將新的 \<appSettings> 元素加入組態檔 (app.config) 中，並將 `EnableWindowsFormsHighDpiAutoResizing` 元素設定為 `true`：

    ```
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

 在 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 中對您的 .NET Framework 應用程式進行偵錯時的改進功能包括：

- 在 Visual Studio Debugger 中傳回值。 當您在 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]中對 Managed 應用程式進行偵錯時，[自動變數] 視窗會顯示方法的傳回類型和值。 這項資訊適用於桌面、Windows 市集和 Windows Phone 應用程式。 如需詳細資訊，請參閱 MSDN Library 中的[檢查方法呼叫的傳回值](http://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f\(v=vs.120\).aspx)。

- 64 位元應用程式的 [編輯後繼續] 功能。 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 對桌面、Windows 市集和 Windows Phone 的 64 位元 Managed 應用程式支援 [編輯後繼續] 功能。 對 32 位元和 64 位元應用程式的現有限制仍然有效 (請參閱[支援的程式碼變更 (C#)](/visualstudio/debugger/supported-code-changes-csharp) 文章的最後一節)。

- 非同步感知偵錯。 為了在 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 中更為容易對非同步應用程式進行偵錯，呼叫堆疊會隱藏編譯器提供的基礎結構程式碼來支援非同步程式設計，以及提供邏輯父框架中的鍊結，讓您可以更清楚地了解邏輯程式執行的方式。 [工作] 視窗會取代 [平行工作] 視窗，並顯示與特定中斷點相關的工作，同時也會顯示應用程式中目前為作用中或已排程的任何其他工作。 您可以在 [.NET Framework 4.5.1 公告 (英文)](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/)的＜Async-aware debugging＞ (非同步感知偵錯) 一節中，閱讀此功能的相關資訊。

- 對 Windows 執行階段元件提供更佳的例外狀況支援。 在 [!INCLUDE[win81](../../../includes/win81-md.md)] 中，Windows 市集應用程式所引發的例外狀況會保留造成例外狀況之錯誤的資訊，甚至跨語言界限。 您可以在 [.NET Framework 4.5.1 公告](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/)的＜Windows 市集應用程式開發＞一節中，閱讀這項功能的相關資訊。 

 從 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 開始，您可以使用 [Managed 特性指引最佳化工具 (Mpgo.exe)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md)，針對 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式和桌面應用程式進行最佳化。

 如需 ASP.NET 4.5.1 的新功能，請參閱 ASP.NET 網站上的 [ASP.NET 4.5.1 和 Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094)。

 [回到頁首](#introduction)

<a name="core"></a> 
## <a name="whats-new-in-the-net-framework-45"></a>.NET Framework 4.5 中的新增功能

### <a name="core-new-features-and-improvements"></a>核心新功能和增強功能

- 可透過在部署期間偵測及關閉 .NET Framework 4 應用程式的方式，減少系統重新啟動次數的功能。 請參閱[在 .NET Framework 4.5 安裝期間減少系統重新啟動的次數](../../../docs/framework/deployment/reducing-system-restarts.md)。

- 在 64 位元平台上支援大於 2 GB 的陣列。 這項功能可以在應用程式組態檔中啟用。 請參閱 [\<gcAllowVeryLargeObjects> 元素](../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)，其中也列出物件大小和陣列大小的其他限制。

- 透過伺服器的背景記憶體回收改善效能。 當您在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中使用伺服器記憶體回收時，背景記憶體回收會自動啟用。 請參閱[記憶體回收的基本概念](../../../docs/standard/garbage-collection/fundamentals.md)主題的＜背景伺服器記憶體回收＞一節。

- 背景 Just-in-Time (JIT) 編譯，它可在多核心處理器上選擇性提供，以改善應用程式效能。 請參閱 <xref:System.Runtime.ProfileOptimization>。

- 可限制規則運算式引擎在逾時之前，嘗試解析規則運算式之時間長度的功能。 請參閱 <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=fullName> 屬性。

- 可定義應用程式定義域之預設文化特性的功能。 請參閱 <xref:System.Globalization.CultureInfo> 類別。

- 對 Unicode (UTF-16) 編碼的主控台支援。 請參閱 <xref:System.Console> 類別。

- 支援文化特性字串順序和比較資料的版本控制。 請參閱 <xref:System.Globalization.SortVersion> 類別。

- 改善擷取資源時的效能。 請參閱[封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)。

- 改善 Zip 壓縮，縮減壓縮檔的大小。 請參閱 <xref:System.IO.Compression?displayProperty=fullName> 命名空間。

- 可透過 <xref:System.Reflection.Context.CustomReflectionContext> 類別自訂反映內容以覆寫預設反映行為的功能。

- 在 <xref:System.Globalization.IdnMapping?displayProperty=fullName> 上使用 [!INCLUDE[win8](../../../includes/win8-md.md)] 類別時，支援 2008 版的應用程式國際化網域名稱 (Internationalized Domain Names in Applications，IDNA) 標準。

- 對作業系統委派字串比較，該字串比較會在 [!INCLUDE[win8](../../../includes/win8-md.md)] 上使用 .NET Framework 時實作 Unicode 6.0。 在其他平台上執行時，.NET Framework 會包含自己的字串比較資料 (該資料會實作 Unicode 5.x)。 請參閱 <xref:System.String> 類別以及 <xref:System.Globalization.SortVersion> 類別的＜備註＞一節。

- 可用每個應用程式定義域做為基準，計算字串之雜湊碼的功能。 請參閱 [\<UseRandomizedStringHashAlgorithm> 項目](../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)。

- 類型反映支援在 <xref:System.Type> 和 <xref:System.Reflection.TypeInfo> 類別之間分割。 請參閱[適用於 Windows 市集應用程式之 .NET Framework 中的反映](../../../docs/framework/reflection-and-codedom/reflection-for-windows-store-apps.md)。

### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)
 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，Managed Extensibility Framework (MEF) 提供下列新功能：

- 支援泛型類型。

- 以慣例為基礎的程式設計模型，可讓您依命名慣例而非屬性建立組件。

- 多個範圍。

- 可以在建立 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式時使用的 MEF 子集。 您可透過 NuGet Gallery 取得這個子集的[可下載套件](http://go.microsoft.com/fwlink/?LinkId=256238)。 若要安裝套件，請在 Visual Studio 中開啟您的專案，從 [專案] 功能表中選擇 [管理 NuGet 套件]，並於線上搜尋 `Microsoft.Composition` 套件。

 如需詳細資訊，請參閱 [Managed Extensibility Framework (MEF)](../../../docs/framework/mef/index.md)。

### <a name="asynchronous-file-operations"></a>非同步檔案作業
 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，C# 和 Visual Basic 語言已加入新的非同步功能。 這些功能會加入執行非同步作業的工作模型。 若要使用這個全新的模型，請使用 I/O 類別中的非同步方法。 請參閱[非同步檔案 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)。

<a name="tools"></a> 
### <a name="tools"></a>工具
 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，資源檔產生器 (Resgen.exe) 可讓您從 .NET Framework 組件內嵌的 .resources 檔建立 .resw 檔，以供 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式使用。 如需詳細資訊，請參閱 [Resgen.exe (資源檔產生器)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)。

 Managed 特性指引最佳化 (Mpgo.exe) 可讓您藉由最佳化原生映像組件，改善應用程式啟動時間、記憶體使用量 (工作集大小) 和輸送量。 命令列工具會產生原生映像應用程式組件的設定檔資料。 請參閱 [Mpgo.exe (Managed 特性指引最佳化工具)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md)。 從 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 開始，您可以使用 Mpgo.exe 最佳化 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式及桌面應用程式。

<a name="parallel"></a> 
### <a name="parallel-computing"></a>平行運算
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 針對平行計算提供了許多新功能和改進功能。 這些功能包括提升效能、增強控制、改善非同步程式設計的支援、全新的資料流程程式庫，以及改善平行偵錯與效能分析的支援。 請參閱「.NET 平行程式設計」部落格中的[.NET 4.5 中的平行處理原則新增功能 (英文)](http://go.microsoft.com/fwlink/?LinkId=235061)。

<a name="web"></a> 
### <a name="web"></a>Web
 ASP.NET 4.5 和 4.5.1 加入了 Web Forms、WebSocket 支援、非同步處理常式、效能增強功能及許多其他功能的模型繫結。 如需詳細資訊，請參閱下列資源：

- MSDN Library 中的 [ASP.NET 4.5 和 Visual Studio 2012](http://msdn.microsoft.com/library/ac9bb7f6-f094-4af7-bad0-acf49a5dbc55)。

- ASP.NET 網站上的 [ASP.NET 4.5.1 和 Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094)。

<a name="networking"></a> 
### <a name="networking"></a>網路功能
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 為 HTTP 應用程式提供了新的程式設計介面。 如需詳細資訊，請參閱新的 <xref:System.Net.Http?displayProperty=fullName> 和 <xref:System.Net.Http.Headers?displayProperty=fullName> 命名空間。

 另外還包括對新的程式設計介面的支援，可使用現有的 <xref:System.Net.HttpListener> 和相關類別接受 WebSocket 連接並進行互動。 如需詳細資訊，請參閱新的 <xref:System.Net.WebSockets> 命名空間和 <xref:System.Net.HttpListener> 類別。

 此外，[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 還包括下列網路改進功能：

- 符合 RFC 標準的 URI 支援。 如需詳細資訊，請參閱 <xref:System.Uri> 和相關類別。

- 支援國際化網域名稱 (IDN) 剖析。 如需詳細資訊，請參閱 <xref:System.Uri> 和相關類別。

- 支援電子郵件地址國際化 (EAI)。 如需詳細資訊，請參閱 <xref:System.Net.Mail>。

- 改進的 IPv6 支援。 如需詳細資訊，請參閱 <xref:System.Net.NetworkInformation>。

- 雙重模式通訊端支援。 如需詳細資訊，請參閱 <xref:System.Net.Sockets.Socket> 和 <xref:System.Net.Sockets.TcpListener> 類別。

<a name="client"></a> 
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，Windows Presentation Foundation (WPF) 包含以下層面的變更與改進功能：

- 新的 <xref:System.Windows.Controls.Ribbon.Ribbon> 控制項可以讓您實作功能區使用者介面，其中裝載了 [快速存取工具列]、[應用程式功能表] 及索引標籤。

- 新的 <xref:System.ComponentModel.INotifyDataErrorInfo> 介面支援同步和非同步資料驗證。

- <xref:System.Windows.Controls.VirtualizingPanel> 和 <xref:System.Windows.Threading.Dispatcher> 類別的新功能。

- 改善顯示大型群組資料集合時的效能，以及透過在非 UI 執行緒上存取集合提升效能。

- 靜態屬性的資料繫結、實作 <xref:System.Reflection.ICustomTypeProvider> 介面之自訂類型的資料繫結，以及從繫結運算式擷取資料繫結資訊。

- 隨著值變更重新調整資料的位置 (即時繪圖)。

- 可查看項目容器的資料內容是否已中斷連線的功能。

- 可設定屬性變更與資料來源更新之間應該經過之時間長度的功能。

- 改進對實作弱式事件模式的支援。 此外，事件現在可以接受標記延伸。

<a name="windows_communication_foundation"></a> 
### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)
 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中已加入下列功能，這些功能可讓寫入和維護 Windows Communication Foundation (WCF) 應用程式更容易：

- 簡化產生的組態檔。

- 支援合約優先開發。

- 可更輕鬆地設定 ASP.NET 相容性模式的功能。

- 預設傳輸屬性值中所做的變更，可降低必須設定這些屬性的可能性。

- 對 <xref:System.Xml.XmlDictionaryReaderQuotas> 類別的更新，可降低必須手動設定 XML 字典讀取器配額的可能性。

- Visual Studio 會在建置流程中驗證 WCF 組態檔，如此您就可以在執行應用程式之前偵測組態錯誤。

- 新增非同步資料流支援。

- 新增 HTTPS 通訊協定對應，如此就能更容易使用 Internet Information Services (IIS) 透過 HTTPS 公開端點。

- 可藉由將 `?singleWSDL` 附加至服務 URL 的方式，在單一 WSDL 文件中產生中繼資料的功能。

- Websocket 支援，可透過與 TCP 傳輸類似的效能特性在連接埠 80 與 443 之間進行真正的雙向通訊。

- 支援在程式碼中設定服務。

- XML 編輯器工具提示。

- <xref:System.ServiceModel.ChannelFactory> 快取支援。

- 支援二進位編碼器壓縮。

- 支援 UDP 傳輸，可讓開發人員撰寫使用「射後不理」(Fire and Forget) 傳訊功能的服務。 用戶端傳送訊息給服務，而不期待服務發出任何回應。

- 可在使用 HTTP 傳輸和傳輸安全性時，於單一 WCF 端點上支援多種驗證模式的功能。

- 支援使用國際化網域名稱 (IDN) 的 WCF 服務。

 如需詳細資訊，請參閱 [Windows Communication Foundation 中的新增功能](http://go.microsoft.com/fwlink/?LinkId=228173)。

<a name="windows_workflow_foundation"></a> 
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)
 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，Windows Workflow Foundation (WF) 已加入數項新功能，包括：

- 狀態機器工作流程，最初是在 .NET Framework 4.0.1 中引進 ([.NET Framework 4 Platform Update 1](http://go.microsoft.com/fwlink/?LinkID=215092))。 這項更新包括數個可讓開發人員建立狀態機器工作流程的新類別和活動。 這些類別和活動已針對 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 進行更新，並加入下列功能：

    - 可設定狀態中斷點的功能。

    - 可在工作流程設計工具中複製和貼上轉換的功能。

    - 設計工具支援建立共用的觸發程序轉換。

    - 建立狀態機器工作流程的活動，包括：<xref:System.Activities.Statements.StateMachine>、<xref:System.Activities.Statements.State> 和 <xref:System.Activities.Statements.Transition>。

- 增強的「工作流程設計工具」功能，如下所示：

    - 增強 Visual Studio 中的工作流程搜尋功能，包括「快速尋找」和「檔案中尋找」。

    - 可在第二個子活動加入至容器活動時自動建立「序列」活動，以及同時將這兩個活動包含在「序列」活動中的功能。

    - 平移支援，不需使用捲軸就能變更工作流程的可見部分。

    - 新的 [文件大綱] 檢視，這個檢視會以樹狀樣式大綱檢視顯示工作流程的元件，並讓您在 [文件大綱] 檢視中選取元件。

    - 可將註釋加入至活動的功能。

    - 可使用工作流程設計工具定義並取用活動委派的功能。

    - 在狀態機器和流程圖工作流程中自動連接和自動插入活動和轉換。

- 將工作流程的檢視狀態資訊儲存在 XAML 檔案的單一元素中，如此您就可以輕鬆尋找及編輯檢視狀態資訊。

- NoPersistScope 容器活動，可防止保存子活動。

- 支援 C# 運算式：

    - 使用 Visual Basic 的工作流程專案會使用 Visual Basic 運算式，而 C# 工作流程專案則會使用 C# 運算式。

    - 在 Visual Studio 2010 中建立且具有 Visual Basic 運算式的 C# 工作流程專案，能夠與使用 C# 運算式的 C# 工作流程專案相容。

- 版本控制增強功能：

    - 新的 <xref:System.Activities.WorkflowIdentity> 類別，可提供已保存工作流程執行個體與其工作流程定義之間的對應。

    - 多個工作流程版本在相同主機中並存執行，包括 <xref:System.ServiceModel.Activities.WorkflowServiceHost>。

    - 在動態更新中，修改所保存工作流程執行個體定義的功能。

- 開發合約優先 (Contract-first) 工作流程服務，可提供自動配合現有服務合約產生活動的支援。

 如需詳細資訊，請參閱 [Windows Workflow Foundation 的新功能](http://go.microsoft.com/fwlink/?LinkId=228176)。

<a name="tailored"></a> 
### [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]
 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式是專為特定尺寸所設計，並且會利用 Windows 作業系統的強大功能。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 或 4.5.1 的子集可於使用 C# 或 Visual Basic 建置適用於 Windows 的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式時提供。 這個子集稱為 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]，在 Windows 開發人員中心的[概觀](http://go.microsoft.com/fwlink/?LinkId=228491)中有相關說明。

<a name="portable"></a> 
### <a name="portable-class-libraries"></a>可攜式類別庫
 在 [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] (含) 以後版本中的可攜式類別庫專案可讓您撰寫及建置可在多個 .NET Framework 平台上執行的 Managed 組件。 使用可攜式類別庫專案時，可選擇做為目標的平台 (例如 Windows Phone 和 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)])。 專案中可用的類型和成員會自動限制為這些平台上的通用類型和成員。 如需詳細資訊，請參閱[可攜式類別庫](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)。

## <a name="see-also"></a>另請參閱
 [.NET Framework 和不定期發行](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)   
 [Visual Studio 2017 中的新功能](/visualstudio/ide/whats-new-in-visual-studio)   
 [ASP.NET](/aspnet)   
 [Visual C++ 中的新增功能](/cpp/what-s-new-for-visual-cpp-in-visual-studio) 


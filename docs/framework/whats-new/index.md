---
title: ".NET Framework 的新功能 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework-4.6
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
translationtype: Human Translation
ms.sourcegitcommit: 9460c8b6ca8db927af4064e3567eca34c1bf5c91
ms.openlocfilehash: 56bf5905fc9e4c676e2cf681c9135fddf88e5c89
ms.lasthandoff: 04/08/2017

---
# <a name="what39s-new-in-the-net-framework"></a>.NET Framework 的新功能
<a name="introduction"></a> 本文摘要說明下列 .NET Framework 版本的重要新功能和進：  
  
 [.NET Framework 4.7](#v47)   
 [.NET Framework 4.6.2](#v462)   
 [.NET Framework 4.6.1](#v461)   
 [.NET 2015 和 .NET Framework 4.6](#v46)   
 [.NET Framework 4.5.2](#v452)   
 [.NET Framework 4.5.1](#v451)   
 [.NET Framework 4.5](#core)  
  
 本文並不會提供每一項新功能的完整資料且內容可能會隨時變更。 如需 .NET Framework 的一般資訊，請參閱[使用者入門](http://msdn.microsoft.com/library/c693fd34-88fe-4d90-b332-19eeadf3b7e7)。 如需了解支援的平台，請參閱[系統需求](~/docs/framework/get-started/system-requirements.md)。 如需下載連結和安裝指示，請參閱[安裝指南](../../../docs/framework/install/guide-for-developers.md)。  
  
> [!NOTE]
>  .NET Framework 小組也會不定期隨著 NuGet 發行相關功能，以擴充平台支援並引進新功能，例如不可變的集合和啟用 SIMD 的向量類型。 如需詳細資訊，請參閱[其他類別庫和 API](http://msdn.microsoft.com/library/cf2d9006-b631-4e5d-81cd-20aab78c60f1) 以及 [.NET Framework 和不定期發行](~/docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)。 請參閱 .NET Framework 的 [NuGet 套件完整清單](http://blogs.msdn.com/b/dotnet/p/nugetpackages.aspx)，或訂閱[我們的摘要](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/)。  
  
<a name="v47"></a>   
## <a name="introducing-the-net-framework-47"></a>.NET Framework 4.7 簡介  
 .NET Framework 4.7 建置於 .NET Framework 4.6、4.6.1 和 4.6.2 的基礎上，加入許多新的修正和多項新功能，同時保有產品的高穩定性。  

> [!NOTE]
> 所有 Windows 10 Creators Update 系統上已預先安裝 .NET Framework 4.7。 此版本無法下載或安裝在其他 Windows 作業系統上。  

## <a name="whats-new-in-the-net-framework-47"></a>.NET Framework 4.7 的新功能

.NET Framework 4.7 包含下列領域的新功能：

- [核心](#Core47)
- [網路](#net47)
- [ASP.NET](#ASP-NET47)
- [Windows Communication Foundation (WCF)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

<a name="Core47" />
### <a name="core"></a>核心 ###

.NET Framework 4.7 透過 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 改善序列化：

**橢圓曲線加密 (ECC) 的增強功能***

在 .NET Framework 4.7 中已在 <xref:System.Security.Cryptography.ECDsa> 和 <xref:System.Security.Cryptography.ECDiffieHellman> 類別加入 `ImportParameters(ECParameters)` 方法，允許物件表示已建立的索引鍵。 也加入 `ExportParameters(Boolean)` 方法以使用明確的曲線參數匯出索引鍵。

.NET Framework 4.7 也支援其他曲線 (包括 Brainpool 曲線套件)，並且加入預先定義的定義，可透過新的 <xref:System.Security.Cryptography.ECDsa.Create%2A> 和 <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> Factory 方法輕鬆建立。

您可以在 GitHub 上看到 [.NET Framework 4.7 加密增強功能的範例](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e)。

**DataContractJsonSerializer 對控制字元有更好的支援**

在 .NET Framework 4.7 中，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 會序列化控制字元以遵循 ECMAScript 6 標準。 針對 .NET Framework 4.7 設計的應用程式預設會啟用此行為，而這對在 .NET Framework 4.7 環境下執行但針對舊版 .NET Framework 設計的應用程式也是選擇性功能。 如需詳細資訊，請參閱 [.NET Framework 4.7 中的重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)。

<a name="net47" />
### <a name="networking"></a>網路功能 ###

.NET Framework 4.7 新增與網路有關的下列功能︰

**TLS 通訊協定的預設作業系統支援***

由 <xref:System.Net.Security.SslStream?displayProperty=fullName> 和向上堆疊元件 (例如 HTTP、FTP 和 SMTP) 所使用的 TLS 堆疊，可讓開發人員使用作業系統支援的預設 TLS 通訊協定。 開發人員不再需要硬式編碼 TLS 版本。

<a name="ASP-NET47" />
### <a name="aspnet"></a>ASP.NET ###

在 .NET Framework 4.7 中，ASP.NET 包含下列新功能：

**物件快取擴充性**

從 .NET Framework 4.7 開始，ASP.NET 加入一組新的 API 讓開發人員取代預設的 ASP.NET 實作以快取記憶體內部物件和監視記憶體。 如果 ASP.NET 實作不適用，開發人員現在可以取代下列三個元件當中的任何一個元件︰

- **物件快取存放區**。 開發人員可以使用新的 **ICacheStoreProvider** 介面，透過新的快取提供者組態區段，為 ASP.NET 應用程式插入新的物件快取實作。
 
- **記憶體監視**。 ASP.NET 中的預設記憶體監視器會在應用程式執行到接近處理序所設定的私用位元組上限時，或在電腦可用的總實體 RAM 不足時，通知應用程式。 接近這些限制時，就會引發通知。 對於某些應用程式，通知在太接近設定的限制時才引發，將無法提供有用的反應。 開發人員現在可以使用 <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=fullName> 屬性撰寫自己的記憶體監視器，以取代預設的監視器。

- **記憶體限制反應**。 ASP.NET 預設會在接近私用位元組處理序限制時嘗試修剪物件快取，並定期呼叫 <xref:System.GC.Collect%2A?displayProperty=fullName>。 對於某些應用程式，呼叫 <xref:System.GC.Collect%2A?displayProperty=fullName> 的頻率或修剪的快取量沒有效率。 開發人員現在可以向應用程式的記憶體監視器訂閱 **IObserver** 實作來取代或補充預設行為。

<a name="wcf47" />
### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF) ###

Windows Communication Foundation (WCF) 加入下列功能和變更：

**能夠將預設的訊息安全性設定設定為 TLS 1.1 或 TLS 1.2**

從 .NET Framework 4.7 開始， 除了 SSL 3.0 和 TSL 1.0 之外，WCF 還可讓您設定 TSL 1.1 或 TLS 1.2 做為預設的訊息安全性通訊協定。 這是選擇性的設定。若要啟用，您必須在應用程式組態檔中加入下列項目︰

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" /> 
</runtime>
```

**改進 WCF 應用程式和 WCF 序列化的可靠性**

WCF 包含許多可消除競爭情形的程式碼變更，因此可改善效能和序列化選項的可靠性。 它們包括：

- 在呼叫 **SocketConnection.BeginRead** 和 **SocketConnection.Read** 時更有效地支援混合非同步和同步程式碼。
- 改善中止與 **SharedConnectionListener** 和 **DuplexChannelBinder** 連線時的可靠性。
- 改善呼叫 [FormatterServices.GetSerializableMembers] (assetId:///System.Runtime.Serialization.FormatterServices.GetSerializableMembers(System.Type??qualifyHint = True i autoUpgrade = False) 方法時序列化作業的可靠性。
- 改善呼叫 **ChannelSynchronizer.RemoveWaiter** 方法移除等候者時的可靠性。  

<a name="wf47" />
### <a name="windows-forms"></a>Windows Form ###

在 .NET Framework 4.7 中，Windows Forms 改善對高 DPI 監視器的支援。

**高 DPI 支援**

從針對 .NET Framework 4.7 設計的應用程式開始，.NET Framework 具備 Windows Forms 應用程式的高 DPI 與動態 DPI 支援。 高 DPI 支援改善高 DPI 監視器上表單和控制項的配置和外觀。 動態 DPI 則是在使用者變更執行中應用程式的 DPI 或顯示比例時，變更表單和控制項的配置和外觀。

高 DPI 支援是選擇性功能，您可以在應用程式組態檔中定義 [\<System.Windows.Forms.ConfigurationSection>](Windows%20Forms%20Configuration%20Section.md) 區段來設定。 如需有關如何將高 DPI 支援和動態 DPI 支援加入至 Windows Forms 應用程式的詳細資訊，請參閱 [Windows Forms 中的高 DPI 支援](High%20DPI%20Support%20In%20Windows%20Forms.md)。  

<a name="WPF47"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

在 .NET Framework 4.7 中，WPF 包含下列增強功能︰

**根據 Windows WM_POINTER 訊息對觸控/手寫筆堆疊的支援**

您現在可以選擇根據 [WM_POINTER 訊息 (英文)](https://msdn.microsoft.com/library/windows/desktop/hh454903(v=vs.85).aspx) 來使用觸控/手寫筆堆疊，而不是根據 Windows Ink Services Platform (WISP)。 這是 .NET Framework 的選擇性功能。 如需詳細資訊，請參閱 [.NET Framework 4.7 中的重定目標變更](Retargeting%20Changes%20in%20the%20.NET%20Framework%204.7.md)。

**新的 WPF 列印 API 實作**

WPF 在 [System.Printing.PrintQueue](assetId:///T:System.Printing.PrintQueue?qualifyHint=True&autoUpgrade=True) 類別中的列印 API 會呼叫 Windows [Print Document Package API (英文)](https://msdn.microsoft.com/library/windows/desktop/hh448418(v=vs.85).aspx) 而不是已被取代的 [XPS Print API (英文)](https://msdn.microsoft.com/library/windows/desktop/ff686814(v=vs.85).aspx)。 如需這項變更對應用程式相容性的影響，請參閱 [.NET Framework 4.7 中的重定目標變更](Retargeting%20Changes%20in%20the%20.NET%20Framework%204.7.md)。 

<a name="v462"></a>   
## <a name="whats-new-in-the-net-framework-462"></a>.NET Framework 4.6.2 的新功能  
.NET Framework 4.6.2 包含下列領域的新功能：  
  
-   [ASP.NET](#ASPNET462)  
  
-   [字元類別](#Strings)  
  
-   [加密](#Crypto462)  
  
-   [SqlClient](#SQLClient)  
  
-   [Windows Communication Foundation](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF462)  
  
-   [Windows Workflow Foundation (WF)](#WF462)  
  
-   [ClickOnce](#ClickOnce)  
  
-   [將 Windows Forms 和 WPF 應用程式轉換成 UWP 應用程式](#UWPConvert)  
  
-   [偵錯改進](#Debug462)  
  
 如需 .NET Framework 4.6.2 中加入的新 API 清單，請參閱 GitHub 上的 [.NET Framework 4.6.2 API 變更](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md)。 如需 .NET Framework 4.6.2 中的功能改進以及錯誤 (bug) 修正清單，請參閱 GitHub 上的 [.NET Framework 4.6.2 API 變更 (英文)](http://go.microsoft.com/fwlink/?LinkId=708778)。  如需詳細資訊，請參閱 .NET 部落格的[宣佈 .NET Framework 4.6.2](https://blogs.msdn.microsoft.com/dotnet/2016/08/02/announcing-net-framework-4-6-2/)。  
  
<a name="ASPNET462"></a>   
### <a name="aspnet"></a>ASP.NET  
 在 .NET Framework 4.6.2 中，ASP.NET 包含下列增強功能：  
  
 **改進對資料註解驗證程式的當地語系化錯誤訊息的支援**  
 資料註解驗證程式可讓您藉由將一或多個屬性加入類別內容來執行驗證。 屬性的 [ValidationAttribute.ErrorMessage](assetId:///P:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage?qualifyHint=True&autoUpgrade=True) 元素定義驗證失敗時的錯誤訊息文字。 從 .NET Framework 4.6.2 開始，ASP.NET 可讓您輕鬆地將錯誤訊息當地語系化。 錯誤訊息將會當地語系化，如果︰  
  
1.  驗證屬性中提供 [ValidationAttribute.ErrorMessage](assetId:///P:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage?qualifyHint=True&autoUpgrade=True)。  
  
2.  資源檔儲存在 App_LocalResources 資料夾中。  
  
3.  當地語系化的資源檔名稱格式為 `DataAnnotation.Localization.{`*name*`}.resx`，其中 *name* 是文化特性名稱，格式為 *languageCode*`-`*country/regionCode* 或 *languageCode*。  
  
4.  資源的索引鍵名稱是指派給 [ValidationAttribute.ErrorMessage](assetId:///P:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage?qualifyHint=True&autoUpgrade=True) 屬性的字串，其值是當地語系化的錯誤訊息。  
  
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
   \<Required(ErrorMessage = "The rating must be between 1 and 10.")>  
   \<Display(Name = "Your Rating")>  
   Public Property Rating As Integer = 1  
End Class  
  
```  
  
 然後，您可以建立 DataAnnotation.Localization.fr.resx 資源檔，其索引鍵為錯誤訊息字串，而其值為當地語系化的錯誤訊息。 檔案必須位於 `App.LocalResources` 資料夾中。 例如，下列是索引鍵和其法文 (fr) 當地語系化錯誤訊息的值︰  
  
|名稱|值|  
|----------|-----------|  
|The rating must be between 1 and 10.|La note doit être comprise entre 1 et 10.|  
  
 此檔案即可  
  
 此外，資料註解當地語系化是可延伸的。 開發人員可以藉由實作 [IStringLocalizerProvider](assetId:///T:System.Web.Globalization.IStringLocalizerProvider?qualifyHint=False&autoUpgrade=True) 介面，在資源檔以外的位置儲存當地語系化字串，而插入他們自己的字串當地語系化程式提供者。  
  
 **對工作階段狀態存放區提供者的非同步支援**  
 ASP.NET 現在可允許使用工作傳回方法，搭配工作階段狀態存放區提供者，藉此可讓 ASP.NET 應用程式獲得非同步處理的延展性優勢。 為了支援工作階段狀態存放區提供者的非同步作業，ASP.NET 包含新介面 [System.Web.SessionState.ISessionStateModule](assetId:///T:System.Web.SessionState.ISessionStateModule?qualifyHint=True&autoUpgrade=True)，它繼承自 [IHttpModule](assetId:///T:System.Web.IHttpModule?qualifyHint=False&autoUpgrade=True)，可讓開發人員實作自己的工作階段狀態模組和非同步工作階段存放區提供者。 介面定義如下：  
  
```csharp  
  
public interface ISessionStateModule : IHttpModule {  
    void ReleaseSessionState(HttpContext context);  
    Task ReleaseSessionStateAsync(HttpContext context);  
}  
  
```  
  
 此外，[SessionStateUtility](assetId:///T:System.Web.SessionState.SessionStateUtility?qualifyHint=False&autoUpgrade=True) 類別包含兩個新方法：[IsSessionStateReadOnly](assetId:///M:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly(System.Web.HttpContext)?qualifyHint=False&autoUpgrade=True) 和 [IsSessionStateRequired](assetId:///M:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired(System.Web.HttpContext)?qualifyHint=False&autoUpgrade=True)，可用來支援非同步作業。  
  
 **對輸出快取提供者的非同步支援**  
 從 .NET Framework 4.6.2 開始，工作傳回方法可以用於輸出快取提供者，以提供非同步處理的延展性優勢。  實作這些方法的提供者能減少 Web 伺服器上的執行緒阻斷，並改善 ASP.NET 服務的延展性。  
  
 已新增下列 API 來支援非同步輸出快取提供者︰  
  
-   [System.Web.Caching.OutputCacheProviderAsync](assetId:///T:System.Web.Caching.OutputCacheProviderAsync?qualifyHint=True&autoUpgrade=True) 類別繼承自 [System.Web.Caching.OutputCacheProvider](assetId:///T:System.Web.Caching.OutputCacheProvider?qualifyHint=True&autoUpgrade=True)，可讓開發人員實作非同步的輸出快取提供者。  
  
-   [OutputCacheUtility](assetId:///T:System.Web.Caching.OutputCacheUtility?qualifyHint=False&autoUpgrade=True) 類別可提供協助程式方法，以設定輸出快取。  
  
-   [System.Web.HttpCachePolicy](assetId:///T:System.Web.HttpCachePolicy?qualifyHint=True&autoUpgrade=True) 類別中的 18 個新方法。 這些方法包括 [GetCacheability](assetId:///M:System.Web.HttpCachePolicy.GetCacheability?qualifyHint=False&autoUpgrade=True)、[GetCacheExtensions](assetId:///M:System.Web.HttpCachePolicy.GetCacheExtensions?qualifyHint=False&autoUpgrade=True)、[GetETag](assetId:///M:System.Web.HttpCachePolicy.GetETag?qualifyHint=False&autoUpgrade=True)、[GetETagFromFileDependencies](assetId:///M:System.Web.HttpCachePolicy.GetETagFromFileDependencies?qualifyHint=False&autoUpgrade=True)、[GetMaxAge](assetId:///M:System.Web.HttpCachePolicy.GetMaxAge?qualifyHint=False&autoUpgrade=True)、[GetMaxAge](assetId:///M:System.Web.HttpCachePolicy.GetMaxAge?qualifyHint=False&autoUpgrade=True)、[GetNoStore](assetId:///M:System.Web.HttpCachePolicy.GetNoStore?qualifyHint=False&autoUpgrade=True)、[GetNoTransforms](assetId:///M:System.Web.HttpCachePolicy.GetNoTransforms?qualifyHint=False&autoUpgrade=True)、[GetOmitVaryStar](assetId:///M:System.Web.HttpCachePolicy.GetOmitVaryStar?qualifyHint=False&autoUpgrade=True)、[GetProxyMaxAge](assetId:///M:System.Web.HttpCachePolicy.GetProxyMaxAge?qualifyHint=False&autoUpgrade=True)、[GetRevalidation](assetId:///M:System.Web.HttpCachePolicy.GetRevalidation?qualifyHint=False&autoUpgrade=True)、[GetUtcLastModified](assetId:///M:System.Web.HttpCachePolicy.GetUtcLastModified?qualifyHint=False&autoUpgrade=True)、[GetVaryByCustom](assetId:///M:System.Web.HttpCachePolicy.GetVaryByCustom?qualifyHint=False&autoUpgrade=True)、[HasSlidingExpiration](assetId:///M:System.Web.HttpCachePolicy.HasSlidingExpiration?qualifyHint=False&autoUpgrade=True) 和 [IsValidUntilExpires](assetId:///M:System.Web.HttpCachePolicy.IsValidUntilExpires?qualifyHint=False&autoUpgrade=True)。  
  
-   [System.Web.HttpCacheVaryByContentEncodings](assetId:///T:System.Web.HttpCacheVaryByContentEncodings?qualifyHint=True&autoUpgrade=True) 類別中的 2 個新方法︰[GetContentEncodings](assetId:///M:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings?qualifyHint=False&autoUpgrade=True) 和 [SetContentEncodings](assetId:///M:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings(System.String[])?qualifyHint=False&autoUpgrade=True)。  
  
-   [System.Web.HttpCacheVaryByHeaders](assetId:///T:System.Web.HttpCacheVaryByHeaders?qualifyHint=True&autoUpgrade=True) 類別中的 2 個新方法︰[GetHeaders](assetId:///M:System.Web.HttpCacheVaryByHeaders.GetHeaders?qualifyHint=False&autoUpgrade=True) 和 [SetHeaders](assetId:///M:System.Web.HttpCacheVaryByHeaders.SetHeaders(System.String[])?qualifyHint=False&autoUpgrade=True)。  
  
-   [System.Web.HttpCacheVaryByParams](assetId:///T:System.Web.HttpCacheVaryByParams?qualifyHint=True&autoUpgrade=True) 類別中的 2 個新方法︰[GetParams](assetId:///M:System.Web.HttpCacheVaryByParams.GetParams?qualifyHint=False&autoUpgrade=True) 和 [SetParams](assetId:///M:System.Web.HttpCacheVaryByParams.SetParams(System.String[])?qualifyHint=False&autoUpgrade=True)。  
  
-   在 [System.Web.Caching.AggregateCacheDependency](assetId:///T:System.Web.Caching.AggregateCacheDependency?qualifyHint=True&autoUpgrade=True) 類別中的 [GetFileDependencies](assetId:///M:System.Web.Caching.AggregateCacheDependency.GetFileDependencies?qualifyHint=False&autoUpgrade=True) 方法。  
  
-   在 [CacheDependency](assetId:///T:System.Web.Caching.CacheDependency?qualifyHint=False&autoUpgrade=True) 中的 [GetFileDependencies](assetId:///M:System.Web.Caching.CacheDependency.GetFileDependencies?qualifyHint=False&autoUpgrade=True) 方法。  
  
<a name="Strings"></a>   
### <a name="character-categories"></a>字元類別  
 .NET Framework 4.6.2 中的字元是根據 [Unicode 標準 8.0.0 版 (英文)](http://www.unicode.org/versions/Unicode8.0.0/)分類。 在 .NET Framework 4.6 和 .NET Framework 4.6.1 中，字元是根據 Unicode 6.3 字元類別分類。  
  
 對 Unicode 8.0 的支援僅限於 [CharUnicodeInfo](assetId:///T:System.Globalization.CharUnicodeInfo?qualifyHint=False&autoUpgrade=True) 類別的字元分類，以及依賴它的類型和方法。 這些包括 [StringInfo](assetId:///T:System.Globalization.StringInfo?qualifyHint=False&autoUpgrade=True) 類別、多載的 [Char.GetUnicodeCategory](assetId:///M:System.Char.GetUnicodeCategory(System.Char)?qualifyHint=True&autoUpgrade=True) 方法，和 .NET Framework 規則運算式引擎可辨識的[字元類別](../Topic/Character%20Classes%20in%20Regular%20Expressions.md)。  字元和字串比較和排序不會受到這項變更的影響，並且會繼續依賴基礎作業系統，在 Windows 7 系統上則是依賴 .NET Framework 所提供的字元資料。  
  
 如需了解 Unicode 6.0 和 Unicode 7.0 之間的字元類別變更，請參閱 Unicode 協會網站上的 [The Unicode Standard, Version 7.0.0](http://www.unicode.org/versions/Unicode7.0.0/) (Unicode 標準 7.0.0 版)。 如需了解 Unicode 7.0 和 Unicode 8.0 之間的變更，請參閱 Unicode 協會網站上的 [The Unicode Standard, Version 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/) (Unicode 標準 8.0.0 版)。  
  
<a name="Crypto462"></a>   
### <a name="cryptography"></a>加密  
 **支援包含 FIPS 186-3 DSA 的 X509 憑證**  
 .NET Framework 4.6.2 新增對 DSA (數位簽章演算法) X509 憑證的支援，X509 憑證的金鑰超過 FIPS 186-2 1024 位元的限制。  
  
 除了支援較大的 FIPS 186-3 金鑰大小，.NET Framework 4.6.2 也允許使用 SHA-2 系列雜湊演算法 (SHA256、SHA384 及 SHA512) 的運算簽章。 新的 [System.Security.Cryptography.DSACng](assetId:///T:System.Security.Cryptography.DSACng?qualifyHint=True&autoUpgrade=True) 類別可支援 FIPS 186-3。  
  
 為了保持 .NET Framework 4.6 中 [RSA](assetId:///T:System.Security.Cryptography.RSA?qualifyHint=False&autoUpgrade=True) 類別和 .NET Framework 4.6.1 中 [ECDsa](assetId:///T:System.Security.Cryptography.ECDsa?qualifyHint=False&autoUpgrade=True) 類別的最新變更，.NET Framework 4.6.2 中的 [DSA](assetId:///T:System.Security.Cryptography.DSA?qualifyHint=False&autoUpgrade=True) 抽象基底類別有額外的方法，可讓呼叫者使用這項功能，而不用轉型。 您可以呼叫 [DSACertificateExtensions.GetDSAPrivateKey](assetId:///M:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?qualifyHint=True&autoUpgrade=True) 擴充方法來簽署資料，如下列範例所示。  
  
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
  
 然後您可以呼叫 [DSACertificateExtensions.GetDSAPublicKey](assetId:///M:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?qualifyHint=True&autoUpgrade=True) 擴充方法來驗證簽署的資料，如下列範例所示。  
  
```csharp  
  
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)  
{  
    using (DSA dsa = cert.GetDSAPublicKey())  
    {  
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);  
    }  
}  
  
```  
  
```  
  
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean  
    Using dsa As DSA = cert.GetDSAPublicKey()  
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)  
    End Using  
End Function  
  
```  
  
 **ECDiffieHellman 金鑰衍生常式的輸入更加清楚**  
 .NET Framework 3.5 以三個不同的金鑰衍生函式 (KDF) 常式，新增了對 Ellipic 曲線 Diffie-hellman 金鑰協定的支援。 常式的輸入以及常式本身，是透過 [ECDiffieHellmanCng](assetId:///T:System.Security.Cryptography.ECDiffieHellmanCng?qualifyHint=False&autoUpgrade=True) 物件上的屬性設定。 但由於不是每個常式都會讀取每個輸入屬性，所以很有可能對過去的開發人員造成混淆。  
  
 為了在 .NET Framework 4.6.2 中解決這個問題，我們已將下列三種方法新增至 [ECDiffieHellman](assetId:///T:System.Security.Cryptography.ECDiffieHellman?qualifyHint=False&autoUpgrade=True) 基底類別，以便更清楚地表示這些 KDF 常式和其輸入︰  
  
|ECDiffieHellman 方法|說明|  
|----------------------------|-----------------|  
|[DeriveKeyFromHash(ECDiffieHellmanPublicKey, HashAlgorithmName, Byte\[\], Byte\[\])](assetId:///M:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash(System.Security.Cryptography.ECDiffieHellmanPublicKey,System.Security.Cryptography.HashAlgorithmName,System.Byte[],System.Byte[])?qualifyHint=False&autoUpgrade=False)|使用公式衍生金鑰內容<br /><br /> HASH(secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HASH(secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> 其中 *x* 是 EC Diffie-Hellman 演算法的計算結果。|  
|[DeriveKeyFromHmac(ECDiffieHellmanPublicKey, HashAlgorithmName, Byte\[\], Byte\[\], Byte\[\])](assetId:///M:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac(System.Security.Cryptography.ECDiffieHellmanPublicKey,System.Security.Cryptography.HashAlgorithmName,System.Byte[],System.Byte[],System.Byte[])?qualifyHint=False&autoUpgrade=False)|使用公式衍生金鑰內容<br /><br /> HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> 其中 *x* 是 EC Diffie-Hellman 演算法的計算結果。|  
|[DeriveKeyTls(ECDiffieHellmanPublicKey, Byte\[\], Byte\[\])](assetId:///M:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls(System.Security.Cryptography.ECDiffieHellmanPublicKey,System.Byte[],System.Byte[])?qualifyHint=False&autoUpgrade=False)|使用 TLS 虛擬隨機函式 (PRF) 衍生演算法衍生金鑰內容。|  
  
 **對必要金鑰對稱式加密的支援**  
 Windows 加密程式庫 (CNG) 新增對儲存必要對稱金鑰和使用硬體儲存之對稱金鑰的支援，.NET Framework 4.6.2 讓開發人員可以利用這項功能。  由於金鑰名稱和金鑰提供者的概念是因實作而定，使用此功能需要使用實體實作類型的建構函式，而不是慣用的 factory 方法 (例如呼叫 `Aes.Create`)。  
  
 AES ([AesCng](assetId:///T:System.Security.Cryptography.AesCng?qualifyHint=False&autoUpgrade=True)) 及 3DES ([TripleDESCng](assetId:///T:System.Security.Cryptography.TripleDESCng?qualifyHint=False&autoUpgrade=True)) 演算法具有必要金鑰的對稱加密支援。 例如:   
  
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
 .NET Framework 4.6.2 對 RSA-SHA256、RSA-SHA384 和 RSA-SHA512 PKCS#1 簽章方法，和 SHA256、SHA384 及 SHA512 參照摘要演算法的 [SignedXml](assetId:///T:System.Security.Cryptography.Xml.SignedXml?qualifyHint=False&autoUpgrade=True) 類別新增支援。  
  
 URI 常數會公開在 [SignedXml](xref:System.Security.Cryptography.Xml.SignedXml?qualifyHint=False&autoUpgrade=True)：  
  
|SignedXml 欄位|常數|  
|---------------------|--------------|  
|[XmlDsigSHA256Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmlenc#sha256"|  
|[XmlDsigRSASHA256Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|  
|[XmlDsigSHA384Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmldsig-more#sha384"|  
|[XmlDsigRSASHA384Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|  
|[XmlDsigSHA512Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmlenc#sha512"|  
|[XmlDsigRSASHA512Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|  
  
 任何已註冊自訂 [SignatureDescription](assetId:///T:System.Security.Cryptography.SignatureDescription?qualifyHint=False&autoUpgrade=True) 處理常式到 [CryptoConfig](assetId:///T:System.Security.Cryptography.CryptoConfig?qualifyHint=False&autoUpgrade=True) 以新增這些演算法支援的程式，將會繼續如過去一般運作，但是因為現在有平台預設值，所以不再需要 [CryptoConfig](assetId:///T:System.Security.Cryptography.CryptoConfig?qualifyHint=False&autoUpgrade=True) 註冊。  
  
<a name="SQLClient"></a>   
### <a name="sqlclient"></a>SqlClient  
 .NET Framework Data Provider for SQL Server ([System.Data.SqlClient](assetId:///N:System.Data.SqlClient?qualifyHint=True&autoUpgrade=True)) 包含下列 .NET Framework 4.6.2 新功能：  
  
 **Azure SQL 資料庫的連接共用和逾時**  
 如果啟用連接共用且發生逾時或其他登入錯誤，則會快取例外狀況，而在接下來的 5 秒到 1 分鐘，任何後續連接嘗試都會擲回快取的例外狀況。  如需詳細資訊，請參閱 [SQL Server 連接共用 (ADO.NET)](../Topic/SQL%20Server%20Connection%20Pooling%20\(ADO.NET\).md)。  
  
 連接到 Azure SQL 資料庫時，這個行為並不理想，因為連接嘗試可能會因暫時性錯誤而失敗，但暫時性錯誤通常很快就可復原。 為了進一步最佳化連接重試的經驗，在 Azure SQL 資料庫連接失敗時，已移除連接集區封鎖期間行為。  
  
 新增 `PoolBlockingPeriod` 關鍵字可讓您選取最適合您應用程式的封鎖期間。 這些價值包括：  
  
 `Auto`  
 對於連接 Azure SQL 資料庫的應用程式，已停用連接集區封鎖期間，而對於連接任何其他 SQL Server 執行個體的應用程式，已啟用連接集區封鎖期間。 此為預設值。 如果伺服器端點名稱結尾是下列任一項，則會視為 Azure SQL 資料庫︰  
  
-   .database.windows.net  
  
-   .database.chinacloudapi.cn  
  
-   .database.usgovcloudapi.net  
  
-   .database.cloudapi.de  
  
 `AlwaysBlock`  
 一律啟用連接集區的封鎖期間。  
  
 `NeverBlock`  
 一律停用連接集區的封鎖期間。  
  
 **Always Encrypted 的增強功能**  
 SQLClient 導入了兩項一律加密的增強功能︰  
  
-   為了改善對加密資料庫資料行的參數化查詢效能，現在會快取查詢參數的加密中繼資料。 將 [SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled](assetId:///P:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled?qualifyHint=True&autoUpgrade=True) 屬性設為 `true` (此為預設值) 時，若多次呼叫相同的查詢，用戶端只會從伺服器擷取一次參數中繼資料。  
  
-   金鑰快取中的資料行加密金鑰項目現在會在可設定的時間間隔之後收回，而此時間間隔是使用 [SqlConnection.ColumnEncryptionKeyCacheTtl](assetId:///P:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl?qualifyHint=True&autoUpgrade=True) 屬性設定。  
  
<a name="WCF"></a>   
### <a name="windows-communication-foundation"></a>Windows Communication Foundation  
 在 .NET Framework 4.6.2 中，Windows Communication Foundation 已增強下列領域︰  
  
 **支援使用 CNG 儲存之憑證的 WCF 傳輸安全性**  
 WCF 傳輸安全性支援使用 Windows 密碼編譯程式庫 (CNG) 儲存的憑證。 在 .NET Framework 4.6.2 中，這項支援僅限於使用具有公開金鑰的憑證，且指數長度不能超過 32 位元。 當應用程式以 .NET Framework 4.6.2 為目標時，這項功能預設為開啟。  
  
 如果應用程式是以 .NET Framework 4.6.1 和舊版為目標，但卻執行於 .NET Framework 4.6.2 或更新版本當中，則可將下列這一行加入 app.config 或 web.config 檔的 [\<runtime>](../Topic/%3Cruntime%3E%20Element.md) 區段。  
  
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
  
 **更妥善支援 DataContractJsonSerializer 類別的多個日光節約時間調整規則**  
 客戶可以使用應用程式組態設定來判斷 [DataContractJsonSerializer](assetId:///T:System.Runtime.Serialization.Json.DataContractJsonSerializer?qualifyHint=False&autoUpgrade=True) 類別是否支援對單一時區使用多個調整規則。 這是一項選擇性功能。 若要啟用它，請將下列設定加入您的 app.config 檔︰  
  
```xml  
  
<runtime>  
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />  
</runtime>  
  
```  
  
 啟用這項功能時，[DataContractJsonSerializer](assetId:///T:System.Runtime.Serialization.Json.DataContractJsonSerializer?qualifyHint=False&autoUpgrade=True) 物件會使用 [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) 類型，而非使用 [TimeZone](assetId:///T:System.TimeZone?qualifyHint=False&autoUpgrade=True) 類型來還原序列化日期和時間資料。 [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) 支援多個調整規則，可讓您使用歷史時區資料；[TimeZone](assetId:///T:System.TimeZone?qualifyHint=False&autoUpgrade=True) 則否。  
  
 如需 [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) 結構和時區調整的詳細資訊，請參閱[時區概觀](../Topic/Time%20Zone%20Overview.md)。  
  
 **支援在使用 XMLSerializer 類別序列化和還原序列化時保留 UTC 時間**  
 通常，當 [XmlSerializer](assetId:///T:System.Xml.Serialization.XmlSerializer?qualifyHint=False&autoUpgrade=True) 類別用來序列化 UTC [DateTime](assetId:///T:System.DateTime?qualifyHint=False&autoUpgrade=True) 值時，它會建立一個序列化的時間字串保留日期和時間，但假設時間為本機時區。  例如，如果您藉由呼叫下列程式碼，執行個體化 UTC 日期和時間︰  
  
```csharp  
DateTime utc = new DateTime(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc);  
```  
  
```vb  
Dim utc As New Date(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc)  
```  
  
 針對時間晚於 UTC 八小時的系統而言，結果是序列化時間字串 "03:00:00.0000000-08:00"。  序列化值一律會還原序列化為本機日期和時間值。  
  
 您可以使用應用程式組態設定來判斷當序列化和還原序列化 [DateTime](assetId:///T:System.DateTime?qualifyHint=False&autoUpgrade=True) 值時，[XmlSerializer](assetId:///T:System.Xml.Serialization.XmlSerializer?qualifyHint=False&autoUpgrade=True) 是否保留 UTC 時區資訊︰  
  
```xml  
  
<runtime>  
     <AppContextSwitchOverrides   
          value="Switch.System.Runtime.Serialization.DisableSerializeUTCDateTimeToTimeAndDeserializeUTCTimeToUTCDateTime=false" />  
</runtime>  
  
```  
  
 啟用這項功能時，[DataContractJsonSerializer](assetId:///T:System.Runtime.Serialization.Json.DataContractJsonSerializer?qualifyHint=False&autoUpgrade=True) 物件會使用 [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) 類型，而非使用 [TimeZone](assetId:///T:System.TimeZone?qualifyHint=False&autoUpgrade=True) 類型來還原序列化日期和時間資料。 [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) 支援多個調整規則，可讓您使用歷史時區資料；[TimeZone](assetId:///T:System.TimeZone?qualifyHint=False&autoUpgrade=True) 則否。  
  
 如需 [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) 結構和時區調整的詳細資訊，請參閱[時區概觀](../Topic/Time%20Zone%20Overview.md)。  
  
 **NetNamedPipeBinding 最符合項目**  
 WCF 有新的應用程式設定，可以在用戶端應用程式上設定，以確保它們永遠連接至在最符合要求的 URI 上接聽的服務。 當此應用程式設定設為 `false` (預設值) 時，用戶端可以使用 [NetNamedPipeBinding](assetId:///T:System.ServiceModel.NetNamedPipeBinding?qualifyHint=False&autoUpgrade=True) 來嘗試連線到正在接聽所要求 URI 子字串之 URI 的服務。  
  
 例如，用戶端嘗試連接到接聽 `net.pipe://localhost/Service1` 的服務，但該電腦上以系統管理員權限執行的不同服務正在接聽 `net.pipe://localhost`。 當此應用程式設定設為 `false` 時，用戶端會嘗試連接到錯誤的服務。 將應用程式設定設為 `true` 後，用戶端一律都會連接至最符合的服務。  
  
> [!NOTE]
>  使用 [NetNamedPipeBinding](assetId:///T:System.ServiceModel.NetNamedPipeBinding?qualifyHint=False&autoUpgrade=True) 的用戶端會根據服務的基底位址 (如果存在的話) 來尋找服務，而不是根據完整的端點位址。 為了確保此設定一律適用，服務應該使用唯一的基底位址。  
  
 若要啟用這項變更，請先將下列應用程式設定加入用戶端應用程式的 App.config 或 Web.config 檔︰  
  
```xml  
  
<configuration>  
    <appSettings>  
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />  
    </appSettings>  
</configuration>  
  
```  
  
 **SSL 3.0 不是預設的通訊協定**  
 當使用 NetTcp 搭配傳輸安全性和憑證類型的認證時，SSL 3.0 已不再是用來交涉安全連接的預設通訊協定。 在大部分情況下，應該不會影響現有的應用程式，因為 TLS 1.0 已包含在 NetTcp 的通訊協定清單中。 所有現有的用戶端應該能夠使用至少 TLS 1.0 來交涉連接。      如果需要 SSL3，請使用下列組態機制之一，將它加入交涉通訊協定的清單。  
  
-   [SslStreamSecurityBindingElement.SslProtocols](assetId:///P:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?qualifyHint=True&autoUpgrade=True) 屬性  
  
-   [TcpTransportSecurity.SslProtocols](assetId:///P:System.ServiceModel.TcpTransportSecurity.SslProtocols?qualifyHint=True&autoUpgrade=True) 屬性  
  
-   [\<netTcpBinding>](../Topic/%3CnetTcpBinding%3E.md) 區段的 [\<transport>](../Topic/%3Ctransport%3E%20of%20%3CnetTcpBinding%3E.md) 區段  
  
-   [\<customBinding>](../Topic/%3CcustomBinding%3E.md) 區段的 [\<sslStreamSecurity>](../Topic/%3CsslStreamSecurity%3E.md) 區段  
  
<a name="WPF462"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 在 .NET Framework 4.6.2 中，Windows Presentation Foundation 已增強下列領域︰  
  
 **群組排序**  
 使用 [CollectionView](assetId:///T:System.Windows.Data.CollectionView?qualifyHint=False&autoUpgrade=True) 物件來分組資料的應用程式，現在可以明確地宣告如何排序群組。 明確排序可以解決非直覺式排序的問題，此問題發生於應用程式以動態方式新增或移除群組時，或是變更分組時所干涉的項目屬性值時。 它也可以藉由將分組屬性的比較從完整集合排序移至群組排序，改善群組建立程序的效能。  
  
 若要支援群組排序，新的 [GroupDescription.SortDescriptions](assetId:///P:System.ComponentModel.GroupDescription.SortDescriptions?qualifyHint=True&autoUpgrade=True) 和 [GroupDescription.CustomSort](assetId:///P:System.ComponentModel.GroupDescription.CustomSort?qualifyHint=True&autoUpgrade=True) 屬性會描述如何排序 [GroupDescription](assetId:///T:System.ComponentModel.GroupDescription?qualifyHint=False&autoUpgrade=True) 物件所產生的群組集合。 這相當於同名 [ListCollectionView](assetId:///T:System.Windows.Data.ListCollectionView?qualifyHint=False&autoUpgrade=True) 屬性描述如何排序資料項目的方式。  
  
 [PropertyGroupDescription](assetId:///T:System.Windows.Data.PropertyGroupDescription?qualifyHint=False&autoUpgrade=True) 類別的兩個新的靜態屬性 [CompareNameAscending](assetId:///P:System.Windows.Data.PropertyGroupDescription.CompareNameAscending?qualifyHint=False&autoUpgrade=True) 和 [CompareNameDescending](assetId:///P:System.Windows.Data.PropertyGroupDescription.CompareNameDescending?qualifyHint=False&autoUpgrade=True)，可用於大部分常見的案例。  
  
 比方說，下列 XAML 會依年齡將資料分組、以遞增順序排序年齡群組，並依據姓氏將每個年齡群組內項目分組。  
  
```xaml  
  
<GroupDescriptions>  
     \<PropertyGroupDescription   
         PropertyName=”Age”   
         CustomSort=   
              ”{x:Static PropertyGroupDescription.CompareNamesAscending}”/>  
     </PropertyGroupDescription>  
</GroupDescriptions>  
  
<SortDescriptions>  
     \<SortDescription PropertyName=”LastName”/>  
</SortDescriptions>  
  
```  
  
 **螢幕小鍵盤支援**  
 螢幕小鍵盤支援可以啟用 WPF 應用程式中的焦點追蹤，方法是當可接受文字輸入的控制項觸控收到輸入時，自動叫用及關閉 Windows 10 中新的螢幕小鍵盤。  
  
 在舊版的 .NET Framework 中，WPF 應用程式必須停用 WPF 畫筆/觸控筆勢支援，才能參加焦點追蹤。  如此一來，WPF 應用程式必須選擇完整 WPF 觸控支援，或是依賴 Windows 滑鼠升級。  
  
 **個別監視器 DPI**  
 為了針對 WPF 應用程式支援最近激增的高 DPI 和混合式 DPI 環境，.NET Framework 4.6.2 啟用個別監視器感知。 如需如何啟用 WPF 應用程式之個別監視器 DPI 感知功能的詳細資訊，請參閱 GitHub 上的[範例和開發人員指南](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI)。  
  
 在舊版 .NET Framework 中，WPF 應用程式是系統 DPI 感知。 換句話說，應用程式的 UI 會由作業系統進行適當的縮放，視應用程式呈現所在的監視器 DPI 而定。 ,  
  
 若是在 .NET Framework 4.6.2 下執行的應用程式，您可以將組態陳述式加入應用程式組態檔的 [\<runtime>](../Topic/%3Cruntime%3E%20Element.md) 區段，藉此停用 WPF 應用程式中的個別監視器 DPI 變更，如下所示︰  
  
```xml  
  
<runtime>  
   \<AppContextSwitchOverrides value=”Switch.System.Windows.DoNotScaleForDpiChanges=false”/>  
</runtime>  
  
```  
  
<a name="WF462"></a>   
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)  
 在 .NET Framework 4.6.2 中，Windows Workflow Foundation 已增強下列領域︰  
  
 **Re-hosted WF 設計工具中的 C# 運算式和 IntelliSense 支援**  
 從 .NET Framework 4.5 開始，WF 在 Visual Studio 設計工具和程式碼工作流程中都支援 C# 運算式。 Re-hosted 工作流程設計工具是 WF 的重要功能，可讓工作流程設計工具位於 Visual Studio 以外的應用程式中 (例如 WPF 中)。  Windows Workflow Foundation 提供在 Re-hosted 工作流程設計工具中支援 C# 運算式與 IntelliSense 的功能。 如需詳細資訊，請參閱 [Windows Workflow Foundation 部落格](http://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409)。  
  
 `Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`  
 在 .NET Framework 4.6.2 之前的 .NET Framework 版本中，當客戶從 Visual Studio 重建工作流程專案時，WF 設計工具 IntelliSense 會中斷。 雖然專案建置成功，但在設計工具中找不到工作流程類型，來自 IntelliSense 的遺漏工作流程類型警告也會出現在 [錯誤清單] 視窗中。 .NET Framework 4.6.2 解決這個問題，並提供 IntelliSense。  
  
 **開啟工作流程追蹤的工作流程 V1 應用程式現在在 FIPS 模式下執行**  
 啟用 FIPS 相容性模式的電腦，現在可以順利執行工作流程 V1 樣式的應用程式，並開啟工作流程追蹤。 若要啟用這種情況，您必須在 app.config 檔案中進行下列變更︰  
  
```xml  
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />  
```  
  
 如果未啟用這種情況，執行應用程式會繼續產生例外狀況，訊息為：「此實作不屬於 Windows Platform FIPS 已驗證密碼編譯演算法的一部分。」  
  
 **在 Visual Studio 工作流程設計工具中使用動態更新時的工作流程改進**  
 工作流程設計工具、流程圖活動設計工具，以及其他工作流程活動設計工具，現在已順利載入和顯示在呼叫 [DynamicUpdateServices.PrepareForUpdate](assetId:///M:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate(System.Activities.Activity)?qualifyHint=True&autoUpgrade=True) 方法之後儲存的工作流程。 在 .NET Framework 4.6.2 之前的 .NET Framework 的版本中，若要在 Visual Studio 中，針對在呼叫 [DynamicUpdateServices.PrepareForUpdate](assetId:///M:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate(System.Activities.Activity)?qualifyHint=True&autoUpgrade=True) 之後儲存的工作流程載入 XAML 檔案，可能會導致下列問題︰  
  
-   工作流程設計工具無法正確載入 XAML 檔案 (當 [ViewStateData.Id](assetId:///P:System.Activities.Presentation.ViewState.ViewStateData.Id?qualifyHint=True&autoUpgrade=True) 在一行的結尾時)。  
  
-   流程圖活動設計工具或其他工作流程活動設計工具可能會在預設位置顯示所有物件，而不是根據附加的屬性值。  
  
<a name="ClickOnce"></a>   
### <a name="clickonce"></a>ClickOnce  
 ClickOnce 已更新為除了已經支援的 TLS 1.0 通訊協定之外，還支援 TLS 1.1 和 TLS 1.2。 ClickOnce 會自動偵測需要哪個通訊協定。若要啟用 TLS 1.1 和 1.2 支援，並不需要在 ClickOnce 應用程式中執行額外的步驟。  
  
<a name="UWPConvert"></a>   
### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>將 Windows Form 和 WPF 應用程式轉換成 UWP 應用程式  
 Windows 現在提供將現有 Windows 桌面應用程式，包括 WPF 和 Windows Form 應用程式，帶到通用 Windows 平台 (UWP) 的功能。 這項技術可作為橋樑，讓您能逐漸將現有的程式碼基底移轉到 UWP，從而將您的應用程式帶到所有 Windows 10 裝置。  
  
 轉換後的桌面應用程式會取得類似於 UWP 應用程式的應用程式識別，如此便可存取 UWP API，以啟用例如動態磚和通知等功能。 應用程式會繼續和之前一樣運作，而且會以完全信任應用程式執行。 應用程式轉換後，應用程式容器處理序可以加入現有的完全信任處理序，以新增調適性使用者介面。 當所有的功能都移至應用程式容器處理序時，便可以移除完全信任處理序，新的 UWP 應用程式也可以供所有 Windows 10 裝置使用。  
  
<a name="Debug462"></a>   
### <a name="debugging-improvements"></a>偵錯改進  
 .NET Framework 4.6.2 中的 *Unmanaged 偵錯 API* 已增強，可以在擲回 [NullReferenceException](assetId:///T:System.NullReferenceException?qualifyHint=False&autoUpgrade=True) 時執行其他分析，以判斷原始程式碼的單一行中哪個變數為 `null`。   為了支援這種情況，下列 API 已加入 Unmanaged 偵錯 API。  
  
-   [ICorDebugCode4](../Topic/ICorDebugCode4%20Interface.md)、[ICorDebugVariableHome](../Topic/ICorDebugVariableHome%20Interface.md) 和 [ICorDebugVariableHomeEnum](../Topic/ICorDebugVariableHomeEnum%20Interface.md) 介面，它們會公開 Managed 變數的原生主資料夾。 這可讓偵錯工具在 [NullReferenceException](assetId:///T:System.NullReferenceException?qualifyHint=False&autoUpgrade=True) 發生時執行某些程式碼流程分析，以回溯並判斷對應至原生位置為 `null` 的 Managed 變數。  
  
-   [ICorDebugType2::GetTypeID](../Topic/ICorDebugType2::GetTypeID%20Method.md) 方法提供 ICorDebugType 到 [COR_TYPEID](../Topic/COR_TYPEID%20Structure.md) 的對應，可讓偵錯工具取得 [COR_TYPEID](../Topic/COR_TYPEID%20Structure.md)，而不需 ICorDebugType 的執行個體。 [COR_TYPEID](../Topic/COR_TYPEID%20Structure.md) 上的現有 API 便可以用來判斷類型的類別配置。  
  
<a name="v461"></a>   
## <a name="whats-new-in-the-net-framework-461"></a>.NET Framework 4.6.1 的新功能  
 .NET Framework 4.6.1 包含下列領域的新功能：  
  
-   [加密](#Crypto)  
  
-   [ADO.NET](#ADO.NET461)  
  
-   [Windows Presentation Foundation (WPF)](#WPF461)  
  
-   [Windows Workflow Foundation](#WWF461)  
  
-   [程式碼剖析](#Profile461)  
  
-   [NGen](#NGEN461)  
  
 如需 .NET Framework 4.6.1 的詳細資訊，請參閱下列主題：  
  
-   [.NET Framework 4.6.1 變更清單](http://go.microsoft.com/fwlink/?LinkId=622964)  
  
-   [4.6.1 中的應用程式相容性](../Topic/Application%20Compatibility%20in%20the%20.NET%20Framework%204.6.1.md)  
  
-   [.NET Framework API diff](http://go.microsoft.com/fwlink/?LinkId=622989) (於 GitHub)  
  
<a name="Crypto"></a>   
### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>密碼編譯：支援包含 ECDSA 的 X509 憑證  
 加入 X509 憑證 RSACng 支援的 .NET Framework 4.6。 .NET Framework 4.6.1 加入 ECDSA (橢圓曲線數位簽章演算法) X509 憑證的支援。  
  
 ECDSA 提供較佳的效能，其密碼編譯演算法比 RSA 更安全，為傳輸層安全性 (TLS) 的效能和延展性提供了絕佳的選擇。 .NET Framework 實作會將呼叫包裝在現有的 Windows 功能中。  
  
 下列範例程式碼示範使用 .NET Framework 4.6.1 包含的 ECDSA X509 憑證新支援，產生位元組資料流的簽章是多麼的輕鬆。  
  
<!-- TODO: review snippet reference  [!CODE [whatsnew.461.crypto#1](../CodeSnippet/VS_Snippets_CLR/whatsnew.461.crypto#1)]  -->  
  
 這為所需的程式碼提供標記的對比，以在 .NET Framework 4.6 中產生簽章。  
  
<!-- TODO: review snippet reference  [!CODE [whatsnew.461.crypto#2](../CodeSnippet/VS_Snippets_CLR/whatsnew.461.crypto#2)]  -->  
  
<a name="ADO.NET461"></a>   
### ADO.NET ADO.NET 已加入下列項目：  
  
 硬體保護金鑰的「一律加密」支援  
 ADO.NET 現在支援在硬體安全模組 (HSM) 中原有的儲存「一律加密」資料行主要金鑰。 透過這項支援，客戶不需要撰寫自訂的資料行主要金鑰存放區提供者，也不要向應用程式註冊，即可以使用儲存在 HSM 的非對稱金鑰。  
  
 客戶必須在應用程式伺服器或用戶端電腦上安裝 HSM 廠商提供的 CSP 提供者或 CNG 金鑰存放區提供者，才能存取受到儲存在 HSM 之資料行主要金鑰保護的「一律加密」資料。  
  
 改善 AlwaysOn 的 [MultiSubnetFailover](assetId:///P:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover?qualifyHint=False&autoUpgrade=True) 連線行為  
 SqlClient 現在會自動提供更快的 AlwaysOn 可用性群組 (AG) 連線。 它會明確偵測應用程式是否連接到不同子網路上的 AlwaysOn 可用性群組 (AG)，並快速找到目前使用中的伺服器和提供伺服器連線。 在此版本之前，應用程式必須設定連接字串包含 `“MultisubnetFailover=true”`，以表示它要連接到 AlwaysOn 可用性群組。 如果不在 `true` 設定連接關鍵字，應用程式可能會在連接到 AlwaysOn 可用性群組時發生逾時狀況。 在這個版本，應用程式「不必」再將 [MultiSubnetFailover](assetId:///P:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover?qualifyHint=False&autoUpgrade=True) 設定為 `true`。 如需 AlwaysOn 可用性群組的 SqlClient 支援詳細資訊，請參閱[高可用性、嚴重損壞修復的 SqlClient 支援](../Topic/SqlClient%20Support%20for%20High%20Availability,%20Disaster%20Recovery.md)。  
  
<a name="WPF461"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 Windows Presentation Foundation 包含數項改進和變更。  
  
 提升效能  
 .NET Framework 4.6.1 已修正引發觸控事件的延遲。 此外，在 [RichTextBox](assetId:///T:System.Windows.Controls.RichTextBox?qualifyHint=False&autoUpgrade=True) 控制項中輸入也不會在快速輸入期間佔用轉譯執行緒。  
  
 改善拼字檢查  
 Windows 8.1 和更新版本已更新了 WPF 的拼字檢查程式，運用作業系統支援其他語言的拼字檢查。  Windows 8.1 之前的 Windows 版本功能沒有任何變更。  
  
 如同舊版的 .NET Framework，依下列順序尋找資訊會偵測到 [TextBox](assetId:///T:System.Windows.Controls.TextBox?qualifyHint=False&autoUpgrade=True) 控制項或 [RichTextBox](assetId:///T:System.Windows.Controls.RichTextBox?qualifyHint=False&autoUpgrade=True) 區塊的語言：  
  
-   `xml:lang` (如有)。  
  
-   目前的輸入語言。  
  
-   目前的執行緒文化特性。  
  
 如需 WPF 語言支援的其他資訊，請參閱[討論 .NET Framework 4.6.1 功能的 WPF 部落格文章](http://go.microsoft.com/fwlink/?LinkID=691819)。  
  
 每個使用者自訂字典的額外支援  
 在 .NET Framework 4.6.1 中，WPF 能夠辨識已全域註冊的自訂字典。 這是除了依照每個控制項登錄它們之外的可用功能。  
  
 在舊版的 WPF 中，自訂的字典無法辨識 [已排除單字] 和 [自動校正] 清單。 Windows 8.1 和 Windows 10 透過可置於 `%AppData%\Microsoft\Spelling\<language tag>` 目錄之下使用的檔案支援它們。  下列規則適用於這些檔案：  
  
-   檔案應有副檔名：.dic (用於加入的字詞)、.exc (用於排除的字詞) 或 .acl (用於自動校正)。  
  
-   檔案應為以位元組順序標記 (BOM) 開始的 UTF-16 LE 純文字。  
  
-   每一行的組成應為單字 (在新增和排除的字詞清單中)，或以分隔號分隔 (“&#124;”) 的自動校正組合單字 (在 [自動校正] 單字清單中)。  
  
-   系統視這些檔案為唯讀，而且不會加以修改。  
  
> [!NOTE]
>  WPF 拼字檢查應用程式開發介面不直接支援這些新的檔案格式，而應用程式中向 WPF 提供的自訂字典應該繼續使用 .lex 檔案。  
  
 範例  
 MSDN 上有多個 [WPF 範例](https://msdn.microsoft.com/library/ms771633.aspx)。 [開放原始碼 GitHub 存放庫](https://github.com/Microsoft/WPF-Samples)中也將匯入 200 多個最熱門的範例 (根據使用量而定)。 您可以回傳意見調查表或提交 [GitHub 問題](https://github.com/Microsoft/WPF-Samples/issues)，以協助我們改進範例。  
  
 DirectX 擴充功能  
 WPF 包含 [NuGet 封裝](http://go.microsoft.com/fwlink/?LinkID=691342)，提供新的 [D3DImage](assetId:///T:System.Windows.Interop.D3DImage?qualifyHint=False&autoUpgrade=True) 實作，讓您輕鬆地與 DX10 和 Dx11 內容相互作用。 這個套件的程式碼為開放式原始碼，並可於 [GitHub](https://github.com/Microsoft/WPFDXInterop) 取得。  
  
<a name="WWF461"></a>   
### <a name="windows-workflow-foundation-transactions"></a>Windows Workflow Foundation：教學課程  
 [Transaction.EnlistPromotableSinglePhase](assetId:///Overload:System.Transactions.Transaction.EnlistPromotableSinglePhase?qualifyHint=True&autoUpgrade=True) 方法現在可以使用 MSDTC 以外的分散式交易管理員升級交易。 您可以對新的 [Transaction.EnlistPromotableSinglePhase(IPromotableSinglePhaseNotification, Guid)](assetId:///M:System.Transactions.Transaction.EnlistPromotableSinglePhase(System.Transactions.IPromotableSinglePhaseNotification,System.Guid)?qualifyHint=True&autoUpgrade=False) 多載指定 GUID 交易升級程式識別碼來進行。 如果這項作業成功，交易的功能上就會放置一些限制。 一旦登記了非 MSDTC 的交易升級程式，下列方法就會擲回 [TransactionPromotionException](assetId:///T:System.Transactions.TransactionPromotionException?qualifyHint=False&autoUpgrade=True)，因為這些方法需要升級為 MSDTC：  
  
-   [Transaction.EnlistDurable](assetId:///Overload:System.Transactions.Transaction.EnlistDurable?qualifyHint=True&autoUpgrade=True)  
  
-   [TransactionInterop.GetDtcTransaction](assetId:///M:System.Transactions.TransactionInterop.GetDtcTransaction(System.Transactions.Transaction)?qualifyHint=True&autoUpgrade=True)  
  
-   [TransactionInterop.GetExportCookie](assetId:///M:System.Transactions.TransactionInterop.GetExportCookie(System.Transactions.Transaction,System.Byte[])?qualifyHint=True&autoUpgrade=True)  
  
-   [TransactionInterop.GetTransmitterPropagationToken](assetId:///M:System.Transactions.TransactionInterop.GetTransmitterPropagationToken(System.Transactions.Transaction)?qualifyHint=True&autoUpgrade=True)  
  
 一旦登錄了非 MSDTC 的交易升級程式，即必須使用它定義的通訊協定，將它用於未來的永久性登錄。 使用 [PromoterType](assetId:///P:System.Transactions.Transaction.PromoterType?qualifyHint=False&autoUpgrade=True) 屬性可取得交易升級程式的 [Guid](assetId:///T:System.Guid?qualifyHint=False&autoUpgrade=True)。 當交易升級時，交易升級程式會提供 [Byte](assetId:///T:System.Byte?qualifyHint=False&autoUpgrade=True) 陣列，表示升級的語彙基元。 應用程式可以 [GetPromotedToken](assetId:///M:System.Transactions.Transaction.GetPromotedToken?qualifyHint=False&autoUpgrade=True) 方法取得非 MSDTC 已升級交易的已升級語彙基元。  
  
 新的 [Transaction.EnlistPromotableSinglePhase(IPromotableSinglePhaseNotification, Guid)](assetId:///M:System.Transactions.Transaction.EnlistPromotableSinglePhase(System.Transactions.IPromotableSinglePhaseNotification,System.Guid)?qualifyHint=True&autoUpgrade=False) 多載的使用者必須遵循特定的呼叫序列，才能讓升級作業順利完成。 這些規則都會記錄在於方法的文件中。  
  
<a name="Profile461"></a>   
### <a name="profiling"></a>程式碼剖析  
 Unmanaged 程式碼剖析應用程式開發介面已增強下列項目：  
  
 為存取 [ICorProfilerInfo7](../Topic/ICorProfilerInfo7%20Interface.md) 介面中的 PDB 提供更好的支援  
 在 ASP.Net 5 中，Roslyn 把組件編譯到記憶體中變得更加普遍。 對於製作程式碼剖析工具的開發人員，這表示過去在磁碟上序列化的 PDB 可能不再存在。 程式碼分析工具通常會使用 PDB 對應回工作原始程式行的程式碼，例如程式碼涵蓋範圍或逐行效能分析。 [ICorProfilerInfo7](../Topic/ICorProfilerInfo7%20Interface.md) 介面現在包含兩種新方法：[ICorProfilerInfo7::GetInMemorySymbolsLength](../Topic/ICorProfilerInfo7::GetInMemorySymbolsLength%20Method.md) 和 [ICorProfilerInfo7::ReadInMemorySymbols](../Topic/ICorProfilerInfo7::ReadInMemorySymbols.md)，讓這些分析工具能夠存取記憶體中的 PDB 資料。分析工具使用新的 API，即可取得記憶體中的 PDB 內容作為位元組陣列，然後予以處理或序列化至磁碟。  
  
 具有 ICorProfiler 介面的更佳檢測設備  
 使用 `ICorProfiler` 應用程式開發介面的 ReJit 功能進行動態檢測的程式碼分析工具，現在可以修改某些中繼資料。 這類工具過去可以隨時檢測 IL，但只能在模組載入時修改中繼資料。 因為 IL 參考中繼資料，這會限制能夠執行的檢測種類。 我們已新增 [ICorProfilerInfo7::ApplyMetaData](../Topic/ICorProfilerInfo7::ApplyMetaData%20Method.md) 方法，以支援在載入模組之後進行中繼資料子集的編輯；尤其還新增 `AssemblyRef`、`TypeRef`、`TypeSpec`、`MemberRef`、`MemberSpec` 和 `UserString` 記錄，藉此解除上述部分限制。 這項變更讓更大範圍的即時檢測變成可能。  
  
<a name="NGEN461"></a>   
### <a name="native-image-generator-ngen-pdbs"></a>原生映像產生器 PDB  
 跨電腦的事件追蹤可讓客戶分析電腦 A 的程式，並使用電腦 B 上對應的原始程式查看程式碼剖析資料。使用舊版的 .NET Framework 時，使用者會將所有模組和原生映像從剖析的機器複製到包含 IL PDB 的分析機器，建立來源與原生的對應。 雖然這個程序能在檔案較小時運作良好，例如手機的電話應用程式；但是，桌上型系統的檔案可能非常巨大，需要大量的複製時間。  
  
 使用 Ngen PDB，NGen 可以建立包含 IL 與原生對應的 PDB，不必依賴 IL PDB。 在我們的跨電腦事件追蹤案例中，您只需要將電腦 A 產生的原生映像 PDB 複製到電腦 B，並使用[偵錯介面存取 API](https://docs.microsoft.com/en-us/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference)，讀取 IL PDB 的來源與 IL 對應及原生映像 PDB 的 IL 與原生對應。 結合兩個對應可提供來源與原生對應。 由於原生映像 PDB 遠小於所有模組和原生映像，電腦 A 到電腦 B 的複製程序會更快。  
  
<a name="v46"></a>   
## <a name="whats-new-in-net-2015"></a>.NET 2015 的新功能  
 .NET 2015 引進 Framework 4.6 和 .NET Core。 其中一些新功能適用於兩者，另一些功能則專屬於 .NET Framework 4.6 或 .NET Core。  
  
-   **ASP.NET 5**  
  
     .NET 2015 包含用於建置現代化雲端架構應用程式的簡式 .NET 平台 ASP.NET 5。 這個平台已模組化，因此您可以在應用程式中僅包含所需的功能。 這個平台可裝載於 IIS 上或自行裝載於自訂處理序中，並且您可以在同一部伺服器上執行具有不同 .NET Framework 版本的應用程式。 其中所包含的新環境組態系統是專為雲端部署所設計。  
  
     MVC、Web API 和網頁已整合成單一架構，稱為 MVC 6。 您可以透過 Visual Studio 2015 的新工具來建置 ASP.NET 5 應用程式。 您現有的應用程式可在新的 .NET Framework 上運作；不過若要建置使用 MVC 6 或 SignalR 3 的應用程式，您必須使用 Visual Studio 2015 的專案系統。  
  
     如需相關資訊，請參閱 [ASP.NET 5](http://go.microsoft.com/fwlink/?LinkId=518238)。  
  
-   **ASP.NET 的更新**  
  
    -   **可非同步排清回應且以工作為基礎的 API**  
  
         ASP.NET 現在提供一個以工作為基礎的簡單 API 來進行非同步回應清除，亦即 [HttpResponse.FlushAsync](assetId:///M:System.Web.HttpResponse.FlushAsync?qualifyHint=True&autoUpgrade=True)，其可使用您語言的 `async/await` 支援來非同步清除回應。  
  
    -   `Model binding supports task-returning methods`  
  
         在 .NET Framework 4.5 中，ASP.NET 加入「模型繫結」功能，可保障 Web Forms 頁面和使用者控制項中以 CRUD 為基礎之資料作業方式的可延伸性並以程式碼為重心。 模型繫結系統現在支援由 [Task](assetId:///T:System.Threading.Tasks.Task?qualifyHint=False&autoUpgrade=True) 傳回的模型繫結方法。 這項功能可讓 Web Form 開發人員在使用包括 Entity Framework 的較新版 ORM 時，透過簡單的資料繫結系統獲得非同步延展性的優勢。  
  
         非同步模型繫結是由 `aspnet:EnableAsyncModelBinding` 組態設定所控制。  
  
        ```  
  
        <appSettings>  
           <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />  
        </appSettings>  
  
        ```  
  
         若是目標為 .NET Framework 4.6 的應用程式，它會預設為 `true`。 若是在目標為舊版 .NET Framework 但在 .NET Framework 4.6 上執行的應用程式，則預設為 `false`。 您可將組態設定設為 `true` 以將其啟用。  
  
    -   **HTTP/2 支援 (Windows 10)**  
  
         [HTTP/2](http://www.wikipedia.org/wiki/HTTP/2) 是新版的 HTTP 通訊協定，可大幅改善連線的使用情況 (用戶端和伺服器之間較少往返)，並降低使用者網頁載入的延遲情形。  網頁 (與服務相反) 從 HTTP/2 獲益最明顯，因為通訊協定會針對做為單一體驗之一部分之要求的多個成品進行最佳化。 在 .NET Framework 4.6 中，HTTP/2 支援已加入 ASP.NET。 由於網路功能存在於多個層，因此 Windows、IIS 和 ASP.NET中需要新功能以啟用 HTTP/2。 您必須在 Windows 10 上執行才能搭配 ASP.NET 使用 HTTP/2。  
  
         使用 [System.Net.Http.HttpClient](assetId:///T:System.Net.Http.HttpClient?qualifyHint=True&autoUpgrade=True) API 的 Windows 10 通用 Windows 平台 (UWP) 應用程式也支援並預設啟用 HTTP/2。  
  
         為了在 ASP.NET 應用程式中能夠使用 [PUSH_PROMISE](http://http2.github.io/http2-spec/#PUSH_PROMISE) 功能，已在 [HttpResponse](assetId:///T:System.Web.HttpResponse?qualifyHint=False&autoUpgrade=True) 類別中加入含有 [PushPromise(String)](assetId:///M:System.Web.HttpResponse.PushPromise(System.String)?qualifyHint=False&autoUpgrade=False) 和 [PushPromise(String, String, NameValueCollection)](assetId:///M:System.Web.HttpResponse.PushPromise(System.String,System.String,System.Collections.Specialized.NameValueCollection)?qualifyHint=False&autoUpgrade=False) 兩個多載的新方法。  
  
        > [!NOTE]
        >  雖然 ASP.NET 5 支援 HTTP/2，但尚未加入 PUSH PROMISE 功能的支援。  
  
         瀏覽器和網頁伺服器 (Windows 上的 IIS) 會執行所有工作。 您不需要為使用者進行任何繁重工作。  
  
         大部分的[主要瀏覽器都支援 HTTP/2](http://www.wikipedia.org/wiki/HTTP/2)，因此如果您的伺服器也支援 HTTP/2，使用者便很可能獲得其中的益處。  
  
    -   **對權杖繫結通訊協定的支援**  
  
         Microsoft 與 Google 合作推出了驗證的新方法，稱為[權杖繫結通訊協定](https://github.com/TokenBinding/Internet-Drafts)。 其是假設犯罪者可能竊取位於瀏覽器快取中的驗證權杖，並用來存取本應安全無虞的資源 (例如您的銀行帳戶)，而不需要掌握您的密碼或其他特殊權限。 新的通訊協定旨在減輕這個問題。  
  
         語彙基元繫結通訊協定會在 Windows 10 中實作為瀏覽器功能。 ASP.NET 應用程式將會參與通訊協定，以便驗證權杖能驗證為合法。 用戶端和伺服器實作會建立通訊協定所指定的端對端保護。  
  
    -   **隨機字串雜湊演算法**  
  
         .NET Framework 4.5 引進了[隨機字串雜湊演算法](https://msdn.microsoft.com/library/jj152924.aspx)。 不過，由於部分 ASP.NET 功能相依於穩定的雜湊程式碼，因此 ASP.NET 並不支援此演算法。 在 .NET Framework 4.6 中，現已支援隨機字串雜湊演算法。 若要啟用這項功能，請使用 `aspnet:UseRandomizedStringHashAlgorithm` 組態設定。  
  
        ```  
  
        <appSettings>  
           <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />  
        </appSettings>  
  
        ```  
  
-   **ADO.NET**  
  
     ADO.NET 現在支援 SQL Server 2016 Community Technology Preview 2 (CTP2) 提供的「一律加密」功能。 使用「一律加密」，SQL Server 可以對加密資料執行作業，而且最好的是加密金鑰是與應用程式一起位於客戶的受信任環境內，而不是伺服器上。 「一律加密」會保護客戶資料安全，因此，DBA 無法存取純文字資料。 資料的加密和解密透明地在驅動程式層級進行，以將變更現有應用程式的需求降到最少。 如需詳細資訊，請參閱 [Always Encrypted (資料庫引擎)](https://msdn.microsoft.com/library/mt163865\(v=sql.130\).aspx) 和 [Always Encrypted (用戶端開發)](https://msdn.microsoft.com/library/mt147923\(v=sql.130\).aspx)。  
  
-   **Managed 程式碼的 64 位元 JIT 編譯器**  
  
     .NET Framework 4.6 提供 64 位元 JIT 編譯器的新版本 (原本的程式碼名為 RyuJIT)。 全新的 64 位元編譯器比舊版 64 位元 JIT 編譯器更大幅提升效能。 在 .NET Framework 4.6 之上執行的 64 位元處理序即會啟用全新的 64 位元編譯器。 若您的應用程式是編譯為 64 位元或 AnyCPU 並在 64 位元作業系統上執行的話，則會以 64 位元處理序執行。 雖然我們已盡量讓新編譯器的轉換透明化，但仍可能會有行為上的變更。 如果您在使用新的 JIT 編譯器遇到任何問題，歡迎您直接向我們反應。 如果您有任何可能與新的 64 位元 JIT 編譯器相關的問題，請透過 [Microsoft Connect](http://connect.microsoft.com/) 連絡我們。  
  
     新的 64 位元 JIT 編譯器也包含硬體 SIMD 加速功能，這些功能在結合 [System.Numerics](assetId:///N:System.Numerics?qualifyHint=False&autoUpgrade=True) 命名空間中啟用 SIMD 的類型時，可產生良好的效能改進。  
  
-   **組件載入器改進**  
  
     現在，組件載入器會於載入對應的 NGEN 影像之後即卸載 IL 組件，因此可以更有效率地使用記憶體。 這項變更會減少虛擬記憶體，這對大型的 32 位元應用程式 (例如 Visual Studio) 特別有幫助，也可節省實體記憶體。  
  
-   **基底類別程式庫變更**  
  
     .NET Framework 4.6 已新增許多新的 API，以便能在重要情節中使用。 其中包括下列變更和新功能：  
  
    -   **IReadOnlyCollection\<T> 實作**  
  
         其他集合實作 [IReadOnlyCollection\<T>](assetId:///T:System.Collections.Generic.IReadOnlyCollection`1?qualifyHint=False&autoUpgrade=True)，例如 [Queue<T\>](assetId:///T:System.Collections.Generic.Queue`1?qualifyHint=False&autoUpgrade=True) 和 [Stack\<T>](assetId:///T:System.Collections.Generic.Stack`1?qualifyHint=False&autoUpgrade=True)。  
  
    -   **CultureInfo.CurrentCulture 和 CultureInfo.CurrentUICulture**  
  
         [CultureInfo.CurrentCulture](assetId:///P:System.Globalization.CultureInfo.CurrentCulture?qualifyHint=True&autoUpgrade=True) 和 [CultureInfo.CurrentUICulture](assetId:///P:System.Globalization.CultureInfo.CurrentUICulture?qualifyHint=True&autoUpgrade=True) 屬性現在是讀寫，而非唯讀狀態。 如果您將新的 [CultureInfo](assetId:///T:System.Globalization.CultureInfo?qualifyHint=False&autoUpgrade=True) 物件指派給這些屬性，`Thread.CurrentThread.CurrentCulture` 屬性所定義的目前執行緒文化特性和 `Thread.CurrentThread.CurrentUICulture` 屬性所定義的目前 UI 執行緒文化特性也會隨著變更。  
  
    -   **記憶體回收 (GC) 的增強功能**  
  
         [GC](assetId:///T:System.GC?qualifyHint=False&autoUpgrade=True) 類別現在包含 [TryStartNoGCRegion](assetId:///M:System.GC.TryStartNoGCRegion(System.Int64)?qualifyHint=False&autoUpgrade=True) 和 [EndNoGCRegion](assetId:///M:System.GC.EndNoGCRegion?qualifyHint=False&autoUpgrade=True) 方法，可讓您在執行關鍵路徑期間不允許記憶體回收。  
  
         [GC.Collect(Int32, GCCollectionMode, Boolean, Boolean)](assetId:///M:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean,System.Boolean)?qualifyHint=True&autoUpgrade=False) 方法的新多載可讓您控制是否要對小型物件堆積和大型物件堆積進行清理和壓縮，還是只要進行清理。  
  
    -   **啟用 SIMD 的類型**  
  
         [System.Numerics](assetId:///N:System.Numerics?qualifyHint=False&autoUpgrade=True) 命名空間現在包含多種啟用 SIMD 的類型，例如 [Matrix3x2](assetId:///T:System.Numerics.Matrix3x2?qualifyHint=False&autoUpgrade=True)、[Matrix4x4](assetId:///T:System.Numerics.Matrix4x4?qualifyHint=False&autoUpgrade=True)、[Plane](assetId:///T:System.Numerics.Plane?qualifyHint=False&autoUpgrade=True)、[Quaternion](assetId:///T:System.Numerics.Quaternion?qualifyHint=False&autoUpgrade=True)、[Vector2](assetId:///T:System.Numerics.Vector2?qualifyHint=False&autoUpgrade=True)、[Vector3](assetId:///T:System.Numerics.Vector3?qualifyHint=False&autoUpgrade=True) 和 [Vector4](assetId:///T:System.Numerics.Vector4?qualifyHint=False&autoUpgrade=True)。  
  
         因為新的 64 位元 JIT 編譯器也包含硬體 SIMD 加速功能，所以在搭配支援 SIMD 的類型與新的 64 位元 JIT 編譯器時有特別顯著的效能改進。  
  
    -   **加密更新**  
  
         [System.Security.Cryptography](assetId:///N:System.Security.Cryptography?qualifyHint=True&autoUpgrade=True) API 即將更新為支援 [Windows CNG 加密 API](https://msdn.microsoft.com/library/windows/desktop/aa376214.aspx)。 舊版 .NET Framework 完全仰賴[較早版本的 Windows 加密 API](https://msdn.microsoft.com/library/windows/desktop/aa380255.aspx) 做為 [System.Security.Cryptography](assetId:///N:System.Security.Cryptography?qualifyHint=True&autoUpgrade=True) 實作的基礎。 我們已經要求支援 CNG API，因為它支援[現代的加密演算法](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx#suite_b_support)，這些演算法對特定類別的應用程式來說非常重要。  
  
         .NET Framework 4.6 包含下列新的增強功能，可支援 Windows CNG 加密 API：  
  
        -   一組適用於 `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` 和 `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` x509 憑證的擴充方法，其會在可能時傳回以 CNG 為基礎的實作，而不是以 CAPI 為基礎的實作。 (有些智慧卡仍需要 CAPI，因此 API 可處理這類後援。)  
  
        -   [System.Security.Cryptography.RSACng](assetId:///T:System.Security.Cryptography.RSACng?qualifyHint=True&autoUpgrade=True) 類別，可提供 RSA 演算法的 CNG 實作。  
  
        -   RSA API 的增強功能，可讓一般動作不再需要轉型。 例如，使用 [X509Certificate2](assetId:///T:System.Security.Cryptography.X509Certificates.X509Certificate2?qualifyHint=False&autoUpgrade=True) 物件來加密資料時，需使用類似舊版 .NET Framework 的下列程式碼。  
  
<!-- TODO: review snippet reference              [!CODE [WhatsNew.Casting#1](../CodeSnippet/VS_Snippets_CLR/whatsnew.casting#1)]  -->  
  
             Code that uses the new cryptography APIs in the .NET Framework 4.6 can be rewritten as follows to avoid the cast.  
  
<!-- TODO: review snippet reference              [!CODE [WhatsNew.Casting#2](../CodeSnippet/VS_Snippets_CLR/whatsnew.casting#2)]  -->  
  
    -   **支援日期和時間的 UNIX 時間來回轉換**  
  
         [DateTimeOffset](assetId:///T:System.DateTimeOffset?qualifyHint=False&autoUpgrade=True) 結構已加入下列新方法，以支援將日期和時間值與 Unix 時間進行轉換：  
  
        -   [DateTimeOffset.FromUnixTimeSeconds](assetId:///M:System.DateTimeOffset.FromUnixTimeSeconds(System.Int64)?qualifyHint=True&autoUpgrade=True)  
  
        -   [DateTimeOffset.FromUnixTimeMilliseconds](assetId:///M:System.DateTimeOffset.FromUnixTimeMilliseconds(System.Int64)?qualifyHint=True&autoUpgrade=True)  
  
        -   [DateTimeOffset.ToUnixTimeSeconds](assetId:///M:System.DateTimeOffset.ToUnixTimeSeconds?qualifyHint=True&autoUpgrade=True)  
  
        -   [DateTimeOffset.ToUnixTimeMilliseconds](assetId:///M:System.DateTimeOffset.ToUnixTimeMilliseconds?qualifyHint=True&autoUpgrade=True)  
  
    -   **相容性參數**  
  
         新 [AppContext](assetId:///T:System.AppContext?qualifyHint=False&autoUpgrade=True) 類別加入新的相容性功能，可讓程式庫作者為使用者提供新功能的統一退出機制。 它會建立元件之間的鬆散結合合約，以便溝通退出要求。 變更現有的功能時，這項功能通常會特別重要。 相反地，已經有新功能的隱含選擇加入。  
  
         使用 [AppContext](assetId:///T:System.AppContext?qualifyHint=False&autoUpgrade=True) 時，程式庫會定義並公開相容性參數，而相依的程式碼則可以設定這些參數來影響程式庫行為。 根據預設，程式庫可提供新的功能，且它們只會在已設定此參數時變更它 (亦即，它們提供先前的功能)。  
  
         應用程式 (或程式庫) 可以宣告相依程式庫定義之參數的值 (一律為 [Boolean](assetId:///T:System.Boolean?qualifyHint=False&autoUpgrade=True) 值)。 參數一律隱含為 `false`。 將參數設定為 `true` 可啟用它。 明確地將參數設定為 `false` 提供了新的行為。  
  
        ```csharp  
        AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);  
        ```  
  
         程式庫必須檢查取用者是否已宣告參數的值，然後適當地處理它。  
  
        ```  
  
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
  
        -   *參數*.*命名空間*.*參數名稱*  
  
        -   *參數*.*程式庫*.*參數名稱*  
  
    -   **以工作為基礎的非同步模式 (TAP) 的變更**  
  
         在以 .NET Framework 4.6 為目標的應用程式中，[Task](assetId:///T:System.Threading.Tasks.Task?qualifyHint=False&autoUpgrade=True) 和 [Task\<TResult>](assetId:///T:System.Threading.Tasks.Task`1?qualifyHint=False&autoUpgrade=True) 物件會繼承呼叫執行緒的文化特性和 UI 文化特性。 以舊版 .NET Framework 為目標或未以特定 .NET Framework 版本為目標的應用程式行為則不會受到影響。 如需詳細資訊，請參閱 [CultureInfo](assetId:///T:System.Globalization.CultureInfo?qualifyHint=False&autoUpgrade=True) 類別主題的＜文化特性和以工作為基礎的非同步作業＞一節。  
  
         [System.Threading.AsyncLocal\<T>](assetId:///T:System.Threading.AsyncLocal`1?qualifyHint=True&autoUpgrade=True) 類別可讓您表示對指定之非同步控制流程而言為本機的環境資料，例如 `async` 方法。 它可以用來跨執行緒保存資料。 您也可以定義每當因 [AsyncLocal<T\>.Value](assetId:///P:System.Threading.AsyncLocal`1.Value?qualifyHint=True&autoUpgrade=True) 屬性已明確變更或因執行緒發生內容切換時而變更環境資料時，接收通知的回撥方法。  
  
         以工作為基礎的非同步模式 (TAP) 中已加入 [Task.CompletedTask](assetId:///P:System.Threading.Tasks.Task.CompletedTask?qualifyHint=True&autoUpgrade=True)、[Task.FromCanceled](assetId:///M:System.Threading.Tasks.Task.FromCanceled(System.Threading.CancellationToken)?qualifyHint=True&autoUpgrade=True) 和 [Task.FromException](assetId:///M:System.Threading.Tasks.Task.FromException(System.Exception)?qualifyHint=True&autoUpgrade=True) 三種便利的方法，可傳回特定狀態的已完成工作。  
  
         [NamedPipeClientStream](assetId:///T:System.IO.Pipes.NamedPipeClientStream?qualifyHint=False&autoUpgrade=True) 類別現可支援與其新的 [ConnectAsync](assetId:///M:System.IO.Pipes.NamedPipeClientStream.ConnectAsync?qualifyHint=False&autoUpgrade=True) 進行非同步通訊。 方法。  
  
    -   **EventSource 現在支援寫入事件記錄檔**  
  
         除了在電腦上建立的任何現有 ETW 工作階段，您現在還可以使用 [EventSource](assetId:///T:System.Diagnostics.Tracing.EventSource?qualifyHint=False&autoUpgrade=True) 類別，將管理或操作訊息記錄到事件記錄檔中。 以往，您必須使用 Microsoft.Diagnostics.Tracing.EventSource NuGet 套件，才能使用這項功能。 .NET Framework 4.6 現已內建這項功能。  
  
         NuGet 套件和 .NET Framework 4.6 已更新下列功能：  
  
        -   **動態事件**  
  
             可「動態」定義事件，而不需建立事件方法。  
  
        -   **豐富型裝載**  
  
             允許專用類別和陣列，以及基本類型做為裝載傳遞  
  
        -   **活動追蹤**  
  
             可讓開始與結束事件使用識別碼來標記它們之間的事件，以代表目前作用中的所有活動。  
  
         為了支援這些功能，已在 [EventSource](assetId:///T:System.Diagnostics.Tracing.EventSource?qualifyHint=False&autoUpgrade=True) 類別中加入多載的 [Write](assetId:///M:System.Diagnostics.Tracing.EventSource.Write(System.String)?qualifyHint=False&autoUpgrade=True) 方法。  
  
-   **Windows Presentation Foundation (WPF)**  
  
    -   **HDPI 改進**  
  
         現在，WPF 提供比 .NET Framework 4.6 更好的 HDPI 支援。 已變更版面配置進位，以減少含邊界之控制項中的裁剪執行個體。 根據預設，這項功能只有當您將 [TargetFrameworkAttribute](assetId:///T:System.Runtime.Versioning.TargetFrameworkAttribute?qualifyHint=False&autoUpgrade=True) 設為 .NET 4.6 時才會啟用。  如果應用程式是以舊版 Framework 為目標，但卻在 .NET Framework 4.6 上執行，則可在 app.config 檔的 [\<runtime>](../Topic/%3Cruntime%3E%20Element.md) 區段中加入下列這一行，以選擇加入新的行為：  
  
        ```  
  
        <AppContextSwitchOverrides  
        value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"  
        />  
  
        ```  
  
         含不同 DPI 設定 (多 DPI 設定) 且跨多個監視器的 WPF 視窗，現可完全顯示，而不會有被遮蔽的區域。 您可將下列這一行加入 app.config 檔的 `<appSettings>` 區段，以選擇停用這項新的行為：  
  
        ```  
  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
  
        ```  
  
         [System.Windows.Input.Cursor](assetId:///T:System.Windows.Input.Cursor?qualifyHint=True&autoUpgrade=True) 已支援根據 DPI 設定自動載入正確的游標。  
  
    -   **觸控功能較佳**  
  
         .NET Framework 4.6 已將客戶對[連線](https://connect.microsoft.com/VisualStudio/feedback/details/903760/)回報的觸控行為異常問題解決。 Windows 市集應用程式和 WPF 應用程式的點兩下臨界值現與 Windows 8.1 和更新版本相同。  
  
    -   **支援透明的子視窗**  
  
         .NET Framework 4.6 中的 WPF 支援 Windows 8.1 和更新版本的透明子視窗功能。 這可讓您在最上層視窗中建立非矩形和透明的子視窗。 您可以將 [HwndSourceParameters.UsesPerPixelTransparency](assetId:///P:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency?qualifyHint=True&autoUpgrade=True) 屬性設定為 `true` 來啟用此功能。  
  
-   **Windows Communication Foundation (WCF)**  
  
    -   **SSL 支援**  
  
         搭配使用 NetTcp 與傳輸安全性和用戶端驗證時，除了 SSL 3.0 和 TLS 1.0 之外，WCF 現在還支援 TLS 1.1 和 TLS 1.2 的 SSL 版。 現在，您可以選取要使用哪一種通訊協定，或停用較不安全的舊版通訊協定。 若要完成這項作業，您可以設定 [SslProtocols](assetId:///P:System.ServiceModel.TcpTransportSecurity.SslProtocols?qualifyHint=False&autoUpgrade=True) 屬性或在組態檔中加入下列內容。  
  
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
  
    -   **使用不同的 HTTP 連線傳送訊息**  
  
         現在，WCF 可讓使用者使用不同的基礎 HTTP 連線以確保成功傳送特定訊息。 執行這項作業的方法有兩種：  
  
        -   **使用連接群組名稱前置詞**  
  
             使用者可以指定字串，讓 WCF 做為可達到連接群組名稱的前置詞。 系統會使用不同的基礎 HTTP 連線來傳送含有不同前置詞的兩個訊息。 您可以將索引鍵/值組加入訊息的 [Message.Properties](assetId:///P:System.ServiceModel.Channels.Message.Properties?qualifyHint=True&autoUpgrade=True) 屬性，以設定前置詞。 索引鍵是 "HttpTransportConnectionGroupNamePrefix"；值則為所需的前置詞。  
  
        -   **使用不同的通道處理站**  
  
             使用者也可以啟用功能，針對使用不同通道處理器建立之通道所傳送的訊息，使用不同的基礎 HTTP 連線。 若要啟用此功能，使用者必須將下列 `appSetting` 設為 `true`：  
  
            ```  
  
            <appSettings>  
               <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />  
            </appSettings>  
  
            ```  
  
-   **Windows Workflow Foundation (WWF)**  
  
     現在，若有未處理的「非通訊協定」書籤時，您可以指定工作流程服務在不按照順序的作業要求逾時之前會保存該要求的秒數。 「非通訊協定」書籤是指與未處理的 Receive 活動無關的書籤。 有些活動會在其實作中建立非通訊協定書籤，因此可能不容易察覺到非通訊協定書籤的存在。 這些活動包括 State 和 Pick。 因此如果您有使用狀態機器或包含 Pick 活動的工作流程服務實作，就很可能會有非通訊協定書籤。 您可將類似下列一行加入 app.config 檔的 `appSettings` 區段，以指定間隔：  
  
    ```  
    <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>  
    ```  
  
     預設值為 60 秒。 如果 `value` 設為 0，系統會立即拒絕不按照順序的要求，並顯示類似如下的錯誤文字：  
  
    ```Output  
    Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.   
    ```  
  
     如果收到不按照順序的作業訊息，但沒有非通訊協定書籤時，也會收到相同的訊息。  
  
     如果 `FilterResumeTimeoutInSeconds` 項目的值是非零，並有非通訊協定的書籤，而逾時間隔也已過期，則作業會失敗並顯示逾時訊息。  
  
-   **交易**  
  
     現在，若交易導致衍生自 [TransactionException](assetId:///T:System.Transactions.TransactionException?qualifyHint=False&autoUpgrade=True) 的例外狀況擲回時，您可以針對該交易包含分散式的交易識別碼。 您可以在 app.config 檔的`appSettings` 區段中加入下列索引鍵，以完成這項作業：  
  
    ```  
    <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>   
    ```  
  
     預設值是 `false`。  
  
-   **網路功能**  
  
    -   **通訊端重複使用**  
  
         Windows 10 包含新的高延展性網路演算法，其可重複使用對外 TCP 連線的本機連接埠，以更妥善運用電腦資源。 .NET Framework 4.6 支援新的演算法，可讓 .NET 應用程式利用這項新的行為。 在舊版的 Windows 中，並沒有人為的並行連線限制 (通常為動態連接埠範圍的預設大小 16,384)，因此當負載下的連接埠耗盡時，可能會限制服務的延展性。  
  
         為了讓連接埠可以重複使用，在 .NET Framework 4.6 中加入兩個新的 API，有效地移除並行連線的 64K 限制：  
  
        -   [SocketOptionName.ReuseUnicastPort](assetId:///T:System.Net.Sockets.SocketOptionName?qualifyHint=True&autoUpgrade=True) 列舉值。  
  
        -   [ServicePointManager.ReusePort](assetId:///P:System.Net.ServicePointManager.ReusePort?qualifyHint=True&autoUpgrade=True) 屬性。  
  
         除非 `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` 登錄機碼的 `HWRPortReuseOnSocketBind` 值設定為 0x1，否則 [ServicePointManager.ReusePort](assetId:///P:System.Net.ServicePointManager.ReusePort?qualifyHint=True&autoUpgrade=True) 屬性皆預設為 `false`。 若要讓 HTTP 連線的本機連接埠可重複使用，請將 [ServicePointManager.ReusePort](assetId:///P:System.Net.ServicePointManager.ReusePort?qualifyHint=True&autoUpgrade=True) 屬性設為 `true`。 這使得從 [HttpClient](assetId:///T:System.Net.Http.HttpClient?qualifyHint=False&autoUpgrade=True) 和 [HttpWebRequest](assetId:///T:System.Net.HttpWebRequest?qualifyHint=False&autoUpgrade=True) 傳出的所有 TCP 通訊端連線都會使用新的 Windows 10 通訊端選項，即 [SO_REUSE_UNICASTPORT](https://msdn.microsoft.com/library/windows/desktop/ms740532.aspx)，可重複使用本機連接埠。  
  
         如果開發人員撰寫僅限通訊端的應用程式，即可在呼叫 [Socket.SetSocketOption](assetId:///M:System.Net.Sockets.Socket.SetSocketOption(System.Net.Sockets.SocketOptionLevel,System.Net.Sockets.SocketOptionName,System.Byte[])?qualifyHint=True&autoUpgrade=True) 之類的方法時指定 [SocketOptionName.ReuseUnicastPort](assetId:///T:System.Net.Sockets.SocketOptionName?qualifyHint=True&autoUpgrade=True) 選項，讓對外的通訊端在繫結期間重複使用本機連接埠。  
  
    -   **支援國際網域名稱和 PunyCode**  
  
         [Uri](assetId:///T:System.Uri?qualifyHint=False&autoUpgrade=True) 類別中已加入新屬性 [IdnHost](assetId:///P:System.Uri.IdnHost?qualifyHint=False&autoUpgrade=True)，可更妥善支援國際化網域名稱和 PunyCode。  
  
-   **調整 Windows Forms 控制項的大小。**  
  
     .NET Framework 4.6 中已延伸此功能以包含 [DomainUpDown](assetId:///T:System.Windows.Forms.DomainUpDown?qualifyHint=False&autoUpgrade=True)、[NumericUpDown](assetId:///T:System.Windows.Forms.NumericUpDown?qualifyHint=False&autoUpgrade=True)、[DataGridViewComboBoxColumn](assetId:///T:System.Windows.Forms.DataGridViewComboBoxColumn?qualifyHint=False&autoUpgrade=True)、[DataGridViewColumn](assetId:///T:System.Windows.Forms.DataGridViewColumn?qualifyHint=False&autoUpgrade=True) 和 [ToolStripSplitButton](assetId:///T:System.Windows.Forms.ToolStripSplitButton?qualifyHint=False&autoUpgrade=True) 類型，以及繪製 [UITypeEditor](assetId:///T:System.Drawing.Design.UITypeEditor?qualifyHint=False&autoUpgrade=True) 時使用 [Bounds](assetId:///P:System.Drawing.Design.PaintValueEventArgs.Bounds?qualifyHint=False&autoUpgrade=True) 屬性指定的矩形。  
  
     這是一項選擇性功能。 若要啟用這項功能，請將應用程式組態檔 (app.config) 中的 `EnableWindowsFormsHighDpiAutoResizing` 項目設為 `true`：  
  
    ```  
  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
  
    ```  
  
-   **字碼頁編碼方式的支援**  
  
     .NET Core 主要支援 Unicode 編碼方式，並且預設會提供字碼頁編碼方式的有限支援。 您可以使用 [Encoding.RegisterProvider](assetId:///M:System.Text.Encoding.RegisterProvider(System.Text.EncodingProvider)?qualifyHint=True&autoUpgrade=True) 方法註冊字碼頁編碼，加入可在 .NET Framework 中使用但不受 .NET Core 支援的字碼頁編碼支援。 如需詳細資訊，請參閱 [System.Text.CodePagesEncodingProvider](xref:System.Text.CodePagesEncodingProvider) 類別的文件。  
  
-   **.NET Native**  
  
     以 .NET Core 為目標並以 C# 或 Visual Basic 撰寫的 Windows 10 應用程式，現在可以利用將應用程式編譯成機器碼的新技術，而不是使用 IL。 所產生之應用程式的特色是啟動和執行都更快。 如需詳細資訊，請參閱[使用 .NET Native 編譯應用程式](../Topic/Compiling%20Apps%20with%20.NET%20Native.md)。 如需 .NET Native 概觀，請參閱 [.NET Native 和編譯](../Topic/.NET%20Native%20and%20Compilation.md)，其中探討 .NET Native 與 JIT 編譯和 NGEN 之間的差異，以及對您的程式碼所代表的意義。  
  
     當您使用 Visual Studio 2015 編譯您的應用程式時，它們預設會編譯成機器碼。 如需詳細資訊，請參閱 [.NET Native 使用者入門](../Topic/Getting%20Started%20with%20.NET%20Native.md)。  
  
     為了支援對 .NET Native 應用程式進行偵錯，Unmanaged 偵錯 API 已新增許多介面和列舉。 如需詳細資訊，請參閱[偵錯 (Unmanaged API 參考)](../Topic/Debugging%20\(Unmanaged%20API%20Reference\).md) 主題。  
  
-   **開放原始碼 .NET Framework 套件**  
  
     現在，[GitHub](https://github.com/) 上會以開放原始碼套件形式提供不可變的集合、[SIMD API](http://go.microsoft.com/fwlink/?LinkID=518639) 這類 .NET Core 套件，以及可在 [System.Net.Http](assetId:///N:System.Net.Http?qualifyHint=False&autoUpgrade=True) 命名空間中找到的網路 API。 若要存取這些程式碼，請參閱 GitHub 上的 [NetFx](http://go.microsoft.com/fwlink/?LinkID=518634)。 如需詳細資訊以及如何參與這些套件的建立，請前往 GitHub 上的 [.NET 首頁](http://go.microsoft.com/fwlink/?LinkID=518635)，並參閱 [.NET 的核心和開放原始碼](../Topic/.NET%20Core%20and%20Open-Source.md)。  
  
 [回到頁首](#introduction)  
  
<a name="v452"></a>   
## <a name="whats-new-in-the-net-framework-452"></a>.NET Framework 4.5.2 的新功能  
  
-   **ASP.NET 應用程式的全新 API。** 新的 [HttpResponse.AddOnSendingHeaders](assetId:///M:System.Web.HttpResponse.AddOnSendingHeaders(System.Action{System.Web.HttpContext})?qualifyHint=True&autoUpgrade=True) 和 [HttpResponseBase.AddOnSendingHeaders](assetId:///M:System.Web.HttpResponseBase.AddOnSendingHeaders(System.Action{System.Web.HttpContextBase})?qualifyHint=True&autoUpgrade=True) 方法可讓您在將回應排清至用戶端應用程式時，檢查及修改回應標頭和狀態碼。 請考慮使用這些方法來取代 [PreSendRequestHeaders](assetId:///E:System.Web.HttpApplication.PreSendRequestHeaders?qualifyHint=False&autoUpgrade=True) 和 [PreSendRequestContent](assetId:///E:System.Web.HttpApplication.PreSendRequestContent?qualifyHint=False&autoUpgrade=True) 事件，因為這些方法的效率更高且更可靠。  
  
     [HostingEnvironment.QueueBackgroundWorkItem](assetId:///M:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem(System.Action{System.Threading.CancellationToken})?qualifyHint=True&autoUpgrade=True) 方法可讓您排程小型的背景工作項目。 完成所有背景工作項目之前，ASP.NET 會追蹤這些項目，並防止 IIS 突然終止背景工作處理序。 此方法只能在 ASP.NET Managed 應用程式網域內呼叫。  
  
     新的 [HttpResponse.HeadersWritten](assetId:///P:System.Web.HttpResponse.HeadersWritten?qualifyHint=True&autoUpgrade=False) 和 [HttpResponseBase.HeadersWritten](assetId:///P:System.Web.HttpResponseBase.HeadersWritten?qualifyHint=True&autoUpgrade=False) 屬性會傳回布林值，指出是否已寫入回應標頭。 您可以使用這些屬性確定 [HttpResponse.StatusCode](assetId:///P:System.Web.HttpResponse.StatusCode?qualifyHint=True&autoUpgrade=True) 這類的 API 呼叫成功 (如果已寫入標頭，則擲回例外狀況)。  
  
-   **調整 Windows Forms 控制項的大小。** 這項功能已擴充。 您現在可以使用系統 DPI 設定來調整下列其他控制項的元件大小 (例如下拉式方塊中的下拉箭號)：  
  
     [ComboBox](assetId:///T:System.Windows.Forms.ComboBox?qualifyHint=False&autoUpgrade=True)   
     [ToolStripComboBox](assetId:///T:System.Windows.Forms.ToolStripComboBox?qualifyHint=False&autoUpgrade=True)   
     [ToolStripMenuItem](assetId:///T:System.Windows.Forms.ToolStripMenuItem?qualifyHint=False&autoUpgrade=True)   
     [Cursor](assetId:///T:System.Windows.Forms.Cursor?qualifyHint=False&autoUpgrade=True)   
     [DataGridView](assetId:///T:System.Windows.Forms.DataGridView?qualifyHint=False&autoUpgrade=True)   
     [DataGridViewComboBoxColumn](assetId:///T:System.Windows.Forms.DataGridViewComboBoxColumn?qualifyHint=False&autoUpgrade=True)  
  
     這是一項選擇性功能。 若要啟用這項功能，請將應用程式組態檔 (app.config) 中的 `EnableWindowsFormsHighDpiAutoResizing` 項目設為 `true`：  
  
    ```  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
    ```  
  
-   **新工作流程功能。** 使用 [EnlistPromotableSinglePhase](assetId:///M:System.Transactions.Transaction.EnlistPromotableSinglePhase(System.Transactions.IPromotableSinglePhaseNotification)?qualifyHint=False&autoUpgrade=True) 方法 (進而實作 [IPromotableSinglePhaseNotification](assetId:///T:System.Transactions.IPromotableSinglePhaseNotification?qualifyHint=False&autoUpgrade=True) 介面) 的資源管理員可以使用新的 [Transaction.PromoteAndEnlistDurable](assetId:///M:System.Transactions.Transaction.PromoteAndEnlistDurable(System.Guid,System.Transactions.IPromotableSinglePhaseNotification,System.Transactions.ISinglePhaseNotification,System.Transactions.EnlistmentOptions)?qualifyHint=True&autoUpgrade=True) 方法來要求下列項目︰  
  
    -   將交易提升至 Microsoft 分散式交易協調器 (MSDTC) 交易。  
  
    -   以支援單一階段認可的永久性登記 [ISinglePhaseNotification](assetId:///T:System.Transactions.ISinglePhaseNotification?qualifyHint=False&autoUpgrade=True) 取代 [IPromotableSinglePhaseNotification](assetId:///T:System.Transactions.IPromotableSinglePhaseNotification?qualifyHint=False&autoUpgrade=True)。  
  
     您可以在相同的應用程式網域中完成這些作業，而不需要任何額外的 Unmanaged 程式碼來與 MSDTC 互動以進行提升。 僅有在未完成 [System.Transactions](assetId:///N:System.Transactions?qualifyHint=True&autoUpgrade=True) 對 [IPromotableSinglePhaseNotification](assetId:///T:System.Transactions.IPromotableSinglePhaseNotification?qualifyHint=False&autoUpgrade=True)`Promote` 方法 (由可提升的登記所實作) 的呼叫時，才會呼叫此新方法。  
  
-   **程式碼剖析改進。** 下列新的 Unmanaged 程式碼分析 API 提供更強大的程式碼分析功能：  
  
     [COR_PRF_ASSEMBLY_REFERENCE_INFO 結構](../Topic/COR_PRF_ASSEMBLY_REFERENCE_INFO%20Structure.md)   
     [COR_PRF_HIGH_MONITOR 列舉](../Topic/COR_PRF_HIGH_MONITOR%20Enumeration.md)   
     [GetAssemblyReferences 方法](../Topic/ICorProfilerCallback6::GetAssemblyReferences%20Method.md)   
     [GetEventMask2 方法](../Topic/ICorProfilerInfo5::GetEventMask2%20Method.md)   
     [SetEventMask2 方法](../Topic/ICorProfilerInfo5::SetEventMask2%20Method.md)   
     [AddAssemblyReference 方法](../Topic/ICorProfilerAssemblyReferenceProvider::AddAssemblyReference%20Method.md)  
  
     之前的 `ICorProfiler` 實作支援相依組件的延遲載入。 新程式碼分析 API 要求可立即載入分析工具插入的相依組件，而不是在完全初始化應用程式之後才載入。 這項變更不會影響現有 `ICorProfiler` API 的使用者。  
  
-   **偵錯改進。** 下列新的 Unmanaged 偵錯 API 提供與分析工具更佳的整合。 您現在可以存取分析工具插入的中繼資料，並存取偵錯傾印時編譯器 ReJIT 要求所產生的本機變數和程式碼。  
  
     [SetWriteableMetadataUpdateMode 方法](../Topic/ICorDebugProcess7::SetWriteableMetadataUpdateMode%20Method.md)   
     [EnumerateLocalVariablesEx 方法](../Topic/ICorDebugILFrame4::EnumerateLocalVariablesEx%20Method.md)   
     [GetLocalVariableEx 方法](../Topic/ICorDebugILFrame4::GetLocalVariableEx%20Method.md)   
     [GetCodeEx 方法](../Topic/ICorDebugILFrame4::GetCodeEx%20Method.md)   
     [GetActiveReJitRequestILCode 方法](../Topic/ICorDebugFunction3::GetActiveReJitRequestILCode%20Method.md)   
     [GetInstrumentedILMap 方法](../Topic/ICorDebugILCode2::GetInstrumentedILMap%20Method.md)  
  
-   **事件追蹤變更。** .NET Framework 4.5.2 可對更大的表面區域進行 Windows 事件追蹤 (ETW) 的跨處理序活動追蹤。 此功能可讓進階電源管理 (APM) 廠商提供輕量型工具，以正確追蹤跨執行緒之個別要求和活動的成本。  僅當 ETW 控制器啟用這些事件時，才會引發事件；因此，這些變更不會影響之前寫入的 ETW 程式碼或停用 ETW 時所執行的程式碼。  
  
-   **升級交易並將它轉換成永久性登記**  
  
     [Transaction.PromoteAndEnlistDurable](assetId:///M:System.Transactions.Transaction.PromoteAndEnlistDurable(System.Guid,System.Transactions.IPromotableSinglePhaseNotification,System.Transactions.ISinglePhaseNotification,System.Transactions.EnlistmentOptions)?qualifyHint=True&autoUpgrade=True) 是 .NET Framework 4.5.2 與 4.6 中新加入的 API：  
  
    ```  
  
    [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
    public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,  
                                              IPromotableSinglePhaseNotification promotableNotification,  
                                              ISinglePhaseNotification enlistmentNotification,  
                                              EnlistmentOptions enlistmentOptions)  
  
    ```  
  
     先前由 [Transaction.EnlistPromotableSinglePhase](assetId:///M:System.Transactions.Transaction.EnlistPromotableSinglePhase(System.Transactions.IPromotableSinglePhaseNotification)?qualifyHint=True&autoUpgrade=True) 所建立的登記可使用此方法回應 [ITransactionPromoter.Promote](assetId:///M:System.Transactions.ITransactionPromoter.Promote?qualifyHint=True&autoUpgrade=True) 方法。 它會要求 `System.Transactions` 將交易升級為 MSDTC 交易，並將可升級登記「轉換」為永久性登記。 這個方法成功完成之後，[IPromotableSinglePhaseNotification](assetId:///T:System.Transactions.IPromotableSinglePhaseNotification?qualifyHint=False&autoUpgrade=True) 介面將不再受 `System.Transactions` 參考，且會將任何未來的通知傳送至所提供的 [ISinglePhaseNotification](assetId:///T:System.Transactions.ISinglePhaseNotification?qualifyHint=False&autoUpgrade=True) 介面。 登記必須做為永久性登記，才可支援交易記錄和復原。 請參閱 [Transaction.EnlistDurable](assetId:///M:System.Transactions.Transaction.EnlistDurable(System.Guid,System.Transactions.IEnlistmentNotification,System.Transactions.EnlistmentOptions)?qualifyHint=True&autoUpgrade=True) 了解詳細資訊。 此外，登記必須支援 [ISinglePhaseNotification](assetId:///T:System.Transactions.ISinglePhaseNotification?qualifyHint=False&autoUpgrade=True)。  您「僅可」在處理 [ITransactionPromoter.Promote](assetId:///M:System.Transactions.ITransactionPromoter.Promote?qualifyHint=True&autoUpgrade=True) 呼叫時呼叫此方法。 若否，則會擲回 [TransactionException](assetId:///T:System.Transactions.TransactionException?qualifyHint=False&autoUpgrade=True) 例外狀況。  
  
 [回到頁首](#introduction)  
  
<a name="v451"></a>   
## <a name="whats-new-in-the-net-framework-451"></a>.NET Framework 4.5.1 的新功能  
 **2014 年 4 月更新**：  
  
-   [Visual Studio 2013 Update 2](http://go.microsoft.com/fwlink/p/?LinkId=393658) 包含可攜式類別庫範本的更新，以便針對下列情況提供支援：  
  
    -   您可以使用以 Windows 8.1、Windows Phone 8.1 和 Windows Phone Silverlight 8.1 為目標之可攜式類別庫中的 Windows 執行階段 API。  
  
    -   當您以 Windows 8.1 或 Windows Phone 8.1. 為目標時，可將 XAML (Windows.UI.XAML 類別) 加入至可攜式類別庫中。 支援下列 XAML 範本：「空白網頁」、「資源字典」、「樣板化控制項」和「使用者控制項」。  
  
    -   您可以建立可攜式 Windows 執行階段元件 (.winmd 檔案)，以便用於以 Windows 8.1 和 Windows Phone 8.1 為目標的市集應用程式。  
  
    -   您可以像是可攜式類別庫一樣，重定 Windows 市集或 Windows Phone 市集類別庫的目標。  
  
     如需這些變更的詳細資訊，請參閱[可攜式類別庫](../Topic/Cross-Platform%20Development%20with%20the%20Portable%20Class%20Library.md)。  
  
-   .NET Framework 內容集現在包含 .NET Native (用於建置及部署 Windows 應用程式的先行編譯技術) 的文件。 .NET Native 會將您的應用程式直接編譯為機器碼而不是中繼語言 (IL) 以提升效能。 如需詳細資訊，請參閱[使用 .NET Native 編譯應用程式](../Topic/Compiling%20Apps%20with%20.NET%20Native.md)。  
  
-   [.NET Framework 參考來源](http://referencesource.microsoft.com/)提供新瀏覽體驗和增強功能。 您現在可以在線上瀏覽 .NET Framework 原始程式碼、[下載參考](http://referencesource.microsoft.com/download.html)以供離線檢視，並在偵錯時逐步執行原始程式碼 (包含修補程式和更新)。 如需詳細資訊，請參閱部落格文章：[.NET 參考來源的新風貌](http://blogs.msdn.com/b/dotnet/archive/2014/02/24/a-new-look-for-net-reference-source.aspx)。  
  
 .NET Framework 4.5.1 的核心新功能和增強功能包括：  
  
-   組件的自動繫結重新導向。 從 Visual Studio 2013 開始，當您編譯鎖定 .NET Framework 4.5.1 的應用程式時，如果您的應用程式或其元件參考相同組件的多個版本，就可能會將繫結重新導向加入至應用程式組態檔。 您也可以對鎖定舊版 .NET Framework 的專案啟用這項功能。 如需詳細資訊，請參閱[操作說明：啟用和停用自動繫結重新導向](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Binding%20Redirection.md)。  
  
-   可收集診斷資訊，協助開發人員改進伺服器和雲端應用程式效能的功能。 如需詳細資訊，請參閱 [EventSource](assetId:///T:System.Diagnostics.Tracing.EventSource?qualifyHint=False&autoUpgrade=True) 類別中的 [WriteEventWithRelatedActivityId](assetId:///M:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId(System.Int32,System.Guid,System.Object[])?qualifyHint=False&autoUpgrade=True) 和 [WriteEventWithRelatedActivityIdCore](assetId:///M:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore(System.Int32,System.Guid*,System.Int32,System.Diagnostics.Tracing.EventSource.EventData*)?qualifyHint=False&autoUpgrade=True) 方法。  
  
-   可在記憶體回收期間明確壓縮大型物件堆積 (LOH) 的功能。 如需詳細資訊，請參閱 [GCSettings.LargeObjectHeapCompactionMode](assetId:///P:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?qualifyHint=True&autoUpgrade=True) 屬性。  
  
-   其他效能改進功能包括 ASP.NET 應用程式暫止、多核心 JIT 改進功能，以及 .NET Framework 更新後應用程式更快速啟動。 如需詳細資訊，請參閱 [.NET Framework 4.5.1 公告](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx)和 [ASP.NET 應用程式暫止](http://blogs.msdn.com/b/dotnet/archive/2013/10/09/asp-net-app-suspend-responsive-shared-net-web-hosting.aspx)部落格文章。  
  
 Windows Form 的增強功能包括：  
  
-   調整 Windows Form 控制項的大小。 您可以透過在應用程式的應用程式組態檔中選擇加入一個項目，使用系統 DPI 設定來調整控制項的元件大小 (例如屬性方格中出現的圖示)。 目前支援這項功能的 Windows Form 控制項如下：  
  
     [PropertyGrid](assetId:///T:System.Windows.Forms.PropertyGrid?qualifyHint=False&autoUpgrade=True)   
     [TreeView](assetId:///T:System.Windows.Forms.TreeView?qualifyHint=False&autoUpgrade=True)   
     [DataGridView](assetId:///T:System.Windows.Forms.DataGridView?qualifyHint=False&autoUpgrade=True) 的某些部分 (請參閱 [4.5.2 的新功能](#v452)以了解其他支援的控制項)  
  
     若要啟用這項功能，請將新的 \<appSettings> 項目加入組態檔 (app.config) 中，並將 `EnableWindowsFormsHighDpiAutoResizing` 項目設為 `true`：  
  
    ```  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
    ```  
  
 在 Visual Studio 2013 中對您的 .NET Framework 應用程式進行偵錯時的改進功能包括：  
  
-   在 Visual Studio Debugger 中傳回值。 當您在 Visual Studio 2013 中對 Managed 應用程式進行偵錯時，[自動變數] 視窗會顯示方法的傳回類型和值。 這項資訊適用於桌面、Windows 市集和 Windows Phone 應用程式。 如需詳細資訊，請參閱 MSDN Library 中的[檢查方法呼叫的傳回值](http://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f\(v=vs.120\).aspx)。  
  
-   64 位元應用程式的 [編輯後繼續] 功能。 Visual Studio 2013 對桌面、Windows 市集和 Windows Phone 的 64 位元 Managed 應用程式支援 [編輯後繼續] 功能。 對 32 位元和 64 位元應用程式的現有限制仍然有效 (請參閱[支援的程式碼變更 (C#)](http://msdn.microsoft.com/library/ms164927\(v=vs.120\).aspx) 文章的最後一節)。  
  
-   非同步感知偵錯。 為了在 Visual Studio 2013 中更容易對非同步應用程式進行偵錯，呼叫堆疊會隱藏編譯器提供的基礎結構程式碼來支援非同步程式設計，以及提供邏輯父框架中的鍊結，讓您可以更清楚地了解邏輯程式執行的方式。 [工作] 視窗會取代 [平行工作] 視窗，並顯示與特定中斷點相關的工作，同時也會顯示應用程式中目前為作用中或已排程的任何其他工作。 您可以在 [.NET Framework 4.5.1 公告](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx)的＜非同步感知偵錯＞一節中，閱讀這項功能的相關資訊。  
  
-   對 Windows 執行階段元件提供更佳的例外狀況支援。 在 Windows 8.1 中，Windows 市集應用程式所引發的例外狀況會保留造成例外狀況之錯誤的資訊，甚至跨語言界限。 您可以在 [.NET Framework 4.5.1 公告](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx)的＜Windows 市集應用程式開發＞一節中，閱讀這項功能的相關資訊。  
  
 從 Visual Studio 2013 開始，您可以使用 [Managed 特性指引最佳化工具 (Mpgo.exe)](../Topic/Mpgo.exe%20\(Managed%20Profile%20Guided%20Optimization%20Tool\).md)，針對 Windows 8.x 市集應用程式和桌面應用程式進行最佳化。  
  
 如需 ASP.NET 4.5.1 的新功能，請參閱 ASP.NET 網站上的 [ASP.NET 4.5.1 和 Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094)。  
  
 [回到頁首](#introduction)  
  
<a name="core"></a>   
## <a name="whats-new-in-the-net-framework-45"></a>.NET Framework 4.5 的新功能  
  
### <a name="core-new-features-and-improvements"></a>核心新功能和增強功能  
  
-   可透過在部署期間偵測及關閉 .NET Framework 4 應用程式的方式，減少系統重新啟動次數的功能。 請參閱[在 .NET Framework 4.5 安裝期間減少系統重新啟動的次數](../Topic/Reducing%20System%20Restarts%20During%20.NET%20Framework%204.5%20Installations.md)。  
  
-   在 64 位元平台上支援大於 2 GB 的陣列。 這項功能可以在應用程式組態檔中啟用。 請參閱 [\<gcAllowVeryLargeObjects> 項目](../Topic/%3CgcAllowVeryLargeObjects%3E%20Element.md)，其中也有列出物件大小和陣列大小的其他限制。  
  
-   透過伺服器的背景記憶體回收改善效能。 當您在 .NET Framework 4.5 中使用伺服器記憶體回收時，背景記憶體回收會自動啟用。 請參閱[記憶體回收的基本概念](../Topic/Fundamentals%20of%20Garbage%20Collection.md)主題的＜背景伺服器記憶體回收＞一節。  
  
-   背景 Just-in-Time (JIT) 編譯，它可在多核心處理器上選擇性提供，以改善應用程式效能。 請參閱 [ProfileOptimization](assetId:///T:System.Runtime.ProfileOptimization?qualifyHint=False&autoUpgrade=True)。  
  
-   可限制規則運算式引擎在逾時之前，嘗試解析規則運算式之時間長度的功能。 請參閱 [Regex.MatchTimeout](assetId:///P:System.Text.RegularExpressions.Regex.MatchTimeout?qualifyHint=True&autoUpgrade=True) 屬性。  
  
-   可定義應用程式定義域之預設文化特性的功能。 請參閱 [CultureInfo](assetId:///T:System.Globalization.CultureInfo?qualifyHint=False&autoUpgrade=True) 類別。  
  
-   對 Unicode (UTF-16) 編碼的主控台支援。 請參閱 [Console](assetId:///T:System.Console?qualifyHint=False&autoUpgrade=True) 類別。  
  
-   支援文化特性字串順序和比較資料的版本控制。 請參閱 [SortVersion](assetId:///T:System.Globalization.SortVersion?qualifyHint=False&autoUpgrade=True) 類別。  
  
-   改善擷取資源時的效能。 請參閱[封裝和部署資源](../Topic/Packaging%20and%20Deploying%20Resources%20in%20Desktop%20Apps.md)。  
  
-   改善 Zip 壓縮，縮減壓縮檔的大小。 請參閱 [System.IO.Compression](assetId:///N:System.IO.Compression?qualifyHint=True&autoUpgrade=True) 命名空間。  
  
-   可透過 [CustomReflectionContext](assetId:///T:System.Reflection.Context.CustomReflectionContext?qualifyHint=False&autoUpgrade=True) 類別自訂反映內容以覆寫預設反映行為的功能。  
  
-   在 Windows 8 上使用 [System.Globalization.IdnMapping](assetId:///T:System.Globalization.IdnMapping?qualifyHint=True&autoUpgrade=True) 類別時，支援 2008 版的應用程式國際化網域名稱 (IDNA) 標準。  
  
-   對作業系統委派字串比較，該字串比較會在 Windows 8 上使用 .NET Framework 時實作 Unicode 6.0。 在其他平台上執行時，.NET Framework 會包含自己的字串比較資料 (該資料會實作 Unicode 5.x)。 請參閱 [String](assetId:///T:System.String?qualifyHint=False&autoUpgrade=True) 類別以及 [SortVersion](assetId:///T:System.Globalization.SortVersion?qualifyHint=False&autoUpgrade=True) 類別的＜備註＞一節。  
  
-   可用每個應用程式定義域做為基準，計算字串之雜湊碼的功能。 請參閱 [\<UseRandomizedStringHashAlgorithm> 項目](../Topic/%3CUseRandomizedStringHashAlgorithm%3E%20Element.md)。  
  
-   型別反映支援在 [Type](assetId:///T:System.Type?qualifyHint=False&autoUpgrade=True) 和 [TypeInfo](assetId:///T:System.Reflection.TypeInfo?qualifyHint=False&autoUpgrade=True) 類別之間分割。 請參閱[適用於 Windows 市集應用程式之 .NET Framework 中的反映](../Topic/Reflection%20in%20the%20.NET%20Framework%20for%20Windows%20Store%20Apps.md)。  
  
### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)  
 在 .NET Framework 4.5 中，Managed Extensibility Framework (MEF) 提供下列新功能：  
  
-   支援泛型類型。  
  
-   以慣例為基礎的程式撰寫模型，可讓您依命名慣例而非屬性建立組件。  
  
-   多個範圍。  
  
-   可以在建立 Windows 8.x 市集應用程式時使用的 MEF 子集。 您可透過 NuGet Gallery 取得這個子集的[可下載套件](http://go.microsoft.com/fwlink/?LinkId=256238)。 若要安裝套件，請在 Visual Studio 中開啟您的專案，從 [專案] 功能表中選擇 [管理 NuGet 套件]，並於線上搜尋 `Microsoft.Composition` 套件。  
  
 如需詳細資訊，請參閱 [Managed Extensibility Framework (MEF)](../Topic/Managed%20Extensibility%20Framework%20\(MEF\).md)。  
  
### <a name="asynchronous-file-operations"></a>非同步檔案作業  
 在 .NET Framework 4.5 中，C# 和 Visual Basic 語言已加入新的非同步功能。 這些功能會加入執行非同步作業的工作模型。 若要使用這個全新的模型，請在 I/O 類別中使用非同步方法。 請參閱[非同步檔案 I/O](../Topic/Asynchronous%20File%20I-O.md)。  
  
<a name="tools"></a>   
### <a name="tools"></a>工具  
 在 .NET Framework 4.5 中，資源檔產生器 (Resgen.exe) 可讓您從 .NET Framework 組件內嵌的 .resources 檔建立 .resw 檔，以供 Windows 8.x 市集應用程式使用。 如需詳細資訊，請參閱 [Resgen.exe (資源檔產生器)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md)。  
  
 Managed 特性指引最佳化 (Mpgo.exe) 可讓您藉由最佳化原生映像組件，改善應用程式啟動時間、記憶體使用量 (工作集大小) 和輸送量。 命令列工具會產生原生映像應用程式組件的設定檔資料。 請參閱 [Mpgo.exe (Managed 特性指引最佳化工具)](../Topic/Mpgo.exe%20\(Managed%20Profile%20Guided%20Optimization%20Tool\).md)。 從 Visual Studio 2013 開始，您可以使用 Mpgo.exe 針對 Windows 8.x 市集應用程式和桌面應用程式進行最佳化。  
  
<a name="parallel"></a>   
### <a name="parallel-computing"></a>平行運算  
 .NET Framework 4.5 針對平行計算提供許多新功能和改進功能。 這些功能包括提升效能、增強控制、改善非同步程式設計的支援、全新的資料流程程式庫，以及改善平行偵錯與效能分析的支援。 請參閱 .NET 平行程式設計部落格中的[.NET 4.5 平行處理原則的新功能](http://go.microsoft.com/fwlink/?LinkId=235061)這一項。  
  
<a name="web"></a>   
### <a name="web"></a>Web  
 ASP.NET 4.5 和 4.5.1 加入了 Web Form、WebSocket 支援、非同步處理常式、效能增強功能及許多其他功能的模型繫結。 如需詳細資訊，請參閱下列資源：  
  
-   MSDN Library 中的 [ASP.NET 4.5 和 Visual Studio 2012](../Topic/ASP.NET%20Core%20and%20Visual%20Studio%202015.md)。  
  
-   ASP.NET 網站上的 [ASP.NET 4.5.1 和 Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094)。  
  
<a name="networking"></a>   
### <a name="networking"></a>網路功能  
 .NET Framework 4.5 為 HTTP 應用程式提供新的程式設計介面。 如需詳細資訊，請參閱新的 [System.Net.Http](assetId:///N:System.Net.Http?qualifyHint=True&autoUpgrade=True) 和 [System.Net.Http.Headers](assetId:///N:System.Net.Http.Headers?qualifyHint=True&autoUpgrade=True) 命名空間。  
  
 另外還包括對新的程式設計介面的支援，可使用現有的 [HttpListener](assetId:///T:System.Net.HttpListener?qualifyHint=False&autoUpgrade=True) 和相關類別接受 WebSocket 連線並進行互動。 如需詳細資訊，請參閱新的 [System.Net.WebSockets](assetId:///N:System.Net.WebSockets?qualifyHint=False&autoUpgrade=True) 命名空間和 [HttpListener](assetId:///T:System.Net.HttpListener?qualifyHint=False&autoUpgrade=True) 類別。  
  
 此外，.NET Framework 4.5 還包括下列網路改進功能：  
  
-   符合 RFC 標準的 URI 支援。 如需詳細資訊，請參閱 [Uri](assetId:///T:System.Uri?qualifyHint=False&autoUpgrade=True) 和相關類別。  
  
-   支援國際化網域名稱 (IDN) 剖析。 如需詳細資訊，請參閱 [Uri](assetId:///T:System.Uri?qualifyHint=False&autoUpgrade=True) 和相關類別。  
  
-   支援電子郵件地址國際化 (EAI)。 如需詳細資訊，請參閱 [System.Net.Mail](assetId:///N:System.Net.Mail?qualifyHint=False&autoUpgrade=True) 命名空間。  
  
-   改進的 IPv6 支援。 如需詳細資訊，請參閱 [System.Net.NetworkInformation](assetId:///N:System.Net.NetworkInformation?qualifyHint=False&autoUpgrade=True) 命名空間。  
  
-   雙重模式通訊端支援。 如需詳細資訊，請參閱 [Socket](assetId:///T:System.Net.Sockets.Socket?qualifyHint=False&autoUpgrade=True) 和 [TcpListener](assetId:///T:System.Net.Sockets.TcpListener?qualifyHint=False&autoUpgrade=True) 類別。  
  
<a name="client"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 在 .NET Framework 4.5 中，Windows Presentation Foundation (WPF) 包含下列領域的變更與改進功能：  
  
-   新的 [Ribbon](assetId:///T:System.Windows.Controls.Ribbon.Ribbon?qualifyHint=False&autoUpgrade=True) 控制項可以讓您實作功能區使用者介面，其中裝載了快速存取工具列、應用程式功能表及索引標籤。  
  
-   新的 [INotifyDataErrorInfo](assetId:///T:System.ComponentModel.INotifyDataErrorInfo?qualifyHint=False&autoUpgrade=True) 介面支援同步和非同步資料驗證。  
  
-   [VirtualizingPanel](assetId:///T:System.Windows.Controls.VirtualizingPanel?qualifyHint=False&autoUpgrade=True) 和 [Dispatcher](assetId:///T:System.Windows.Threading.Dispatcher?qualifyHint=False&autoUpgrade=True) 類別的新功能。  
  
-   改善顯示大型群組資料集合時的效能，以及透過在非 UI 執行緒上存取集合提升效能。  
  
-   靜態屬性的資料繫結、實作 [ICustomTypeProvider](assetId:///T:System.Reflection.ICustomTypeProvider?qualifyHint=False&autoUpgrade=True) 介面之自訂類型的資料繫結，以及從繫結運算式擷取資料繫結資訊。  
  
-   隨著值變更重新調整資料的位置 (即時繪圖)。  
  
-   可查看項目容器的資料內容是否已中斷連接的功能。  
  
-   可設定屬性變更與資料來源更新之間應該經過之時間長度的功能。  
  
-   改進對實作弱式事件模式的支援。 此外，事件現在可以接受標記延伸。  
  
<a name="windows_communication_foundation"></a>   
### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
 在 .NET Framework 4.5 中已加入下列功能，讓寫入和維護 Windows Communication Foundation (WCF) 應用程式更容易：  
  
-   簡化產生的組態檔。  
  
-   支援合約優先開發。  
  
-   可更輕鬆地設定 ASP.NET 相容性模式的功能。  
  
-   預設傳輸屬性值中所做的變更，可降低必須設定這些屬性的可能性。  
  
-   [XmlDictionaryReaderQuotas](assetId:///T:System.Xml.XmlDictionaryReaderQuotas?qualifyHint=False&autoUpgrade=True) 類別的更新，可降低必須手動設定 XML 字典讀取器配額的可能性。  
  
-   Visual Studio 會在建置流程中驗證 WCF 組態檔，如此您就可以在執行應用程式之前偵測組態錯誤。  
  
-   新增非同步資料流支援。  
  
-   新增 HTTPS 通訊協定對應，如此就能更容易使用 Internet Information Services (IIS) 透過 HTTPS 公開端點。  
  
-   可藉由將 `?singleWSDL` 附加至服務 URL 的方式，在單一 WSDL 文件中產生中繼資料的功能。  
  
-   Websocket 支援，可透過與 TCP 傳輸類似的效能特性在連接埠 80 與 443 之間進行真正的雙向通訊。  
  
-   支援在程式碼中設定服務。  
  
-   XML 編輯器工具提示。  
  
-   [ChannelFactory](assetId:///T:System.ServiceModel.ChannelFactory?qualifyHint=False&autoUpgrade=True) 快取支援。  
  
-   支援二進位編碼器壓縮。  
  
-   支援 UDP 傳輸，可讓開發人員撰寫使用「射後不理」(Fire and Forget) 訊息的服務。 用戶端傳送訊息給服務，而不期待服務發出任何回應。  
  
-   可在使用 HTTP 傳輸和傳輸安全性時，於單一 WCF 端點上支援多種驗證模式的功能。  
  
-   支援使用國際化網域名稱 (IDN) 的 WCF 服務。  
  
 如需詳細資訊，請參閱 [Windows Communication Foundation 的新功能](http://go.microsoft.com/fwlink/?LinkId=228173)。  
  
<a name="windows_workflow_foundation"></a>   
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)  
 在 .NET Framework 4.5 中，Windows Workflow Foundation (WF) 已加入數項新功能，包括：  
  
-   狀態機器工作流程，最初是在 .NET Framework 4.0.1 中引進 ([.NET Framework 4 Platform Update 1](http://go.microsoft.com/fwlink/?LinkID=215092))。 這項更新包括數個可讓開發人員建立狀態機器工作流程的新類別和活動。 這些類別和活動已針對 .NET Framework 4.5 進行更新，包含：  
  
    -   可設定狀態中斷點的功能。  
  
    -   可在工作流程設計工具中複製和貼上轉換的功能。  
  
    -   設計工具支援建立共用的觸發程序轉換。  
  
    -   建立狀態機器工作流程的活動，包括：[StateMachine](assetId:///T:System.Activities.Statements.StateMachine?qualifyHint=False&autoUpgrade=True)、[State](assetId:///T:System.Activities.Statements.State?qualifyHint=False&autoUpgrade=True) 和 [Transition](assetId:///T:System.Activities.Statements.Transition?qualifyHint=False&autoUpgrade=True)。  
  
-   增強的「工作流程設計工具」功能，如下所示：  
  
    -   增強 Visual Studio 中的工作流程搜尋功能，包括 [快速尋找] 和 [檔案中尋找]。  
  
    -   可在第二個子活動加入至容器活動時自動建立序列活動，以及同時將這兩個活動包含在序列活動中的功能。  
  
    -   平移支援，不需使用捲軸就能變更工作流程的可見部分。  
  
    -   新的 [文件大綱] 檢視，這個檢視會以樹狀樣式大綱檢視顯示工作流程的元件，並讓您在 [文件大綱] 檢視中選取元件。  
  
    -   可將註釋加入至活動的功能。  
  
    -   可使用工作流程設計工具定義並取用活動委派的功能。  
  
    -   在狀態機器及流程圖工作流程中自動連接和自動插入活動和轉換。  
  
-   將工作流程的檢視狀態資訊儲存在 XAML 檔案的單一項目中，如此您就可以輕鬆尋找和編輯檢視狀態資訊。  
  
-   NoPersistScope 容器活動，可防止保存子活動。  
  
-   支援 C# 運算式：  
  
    -   使用 Visual Basic 的工作流程專案會使用 Visual Basic 運算式，而 C# 工作流程專案則會使用 C# 運算式。  
  
    -   在 Visual Studio 2010 中建立且具有 Visual Basic 運算式的 C# 工作流程專案，能夠與使用 C# 運算式的 C# 工作流程專案相容。  
  
-   版本控制增強功能：  
  
    -   新的 [WorkflowIdentity](assetId:///T:System.Activities.WorkflowIdentity?qualifyHint=False&autoUpgrade=True) 類別，可提供已保存工作流程執行個體與其工作流程定義之間的對應。  
  
    -   多個工作流程版本在相同主機中並存執行，包括 [WorkflowServiceHost](assetId:///T:System.ServiceModel.Activities.WorkflowServiceHost?qualifyHint=False&autoUpgrade=True)。  
  
    -   在動態更新中，修改所保存工作流程執行個體定義的功能。  
  
-   開發合約優先 (Contract-first) 工作流程服務，可提供自動配合現有服務合約產生活動的支援。  
  
 如需詳細資訊，請參閱 [Windows Workflow Foundation 的新功能](http://go.microsoft.com/fwlink/?LinkId=228176)。  
  
<a name="tailored"></a>   
### <a name="net-for-windows-8x-store-apps"></a>適用於 Windows 8.x 市集應用程式的 .NET  
 Windows 8.x 市集應用程式是專為特定版型規格所設計，而且會利用 Windows 作業系統的強大功能。 .NET Framework 4.5 或 4.5.1 的子集可於使用 C# 或 Visual Basic 建置適用於 Windows 的 Windows 8.x 市集應用程式時提供。 這個子集稱為適用於 Windows 8.x 市集應用程式的 .NET，在 Windows 開發人員中心的[概觀](http://go.microsoft.com/fwlink/?LinkId=228491)中有相關說明。  
  
<a name="portable"></a>   
### <a name="portable-class-libraries"></a>可攜式類別庫  
 在 Visual Studio 2012 (含) 以後版本中的可攜式類別庫專案可讓您撰寫及建置可在多個 .NET Framework 平台上執行的 Managed 組件。 使用可攜式類別庫專案時，可選擇做為目標的平台 (例如 Windows Phone 和適用於 Windows 8.x 市集應用程式的 .NET)。 專案中可用的類型和成員會自動限制為這些平台上的通用類型和成員。 如需詳細資訊，請參閱[可攜式類別庫](../Topic/Cross-Platform%20Development%20with%20the%20Portable%20Class%20Library.md)。  
  
## <a name="see-also"></a>另請參閱  
 [.NET Framework 和不定期發行](~/docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)   
 [Visual Studio 2013 的新功能](http://msdn.microsoft.com/library/bb386063\(v=vs.120\).aspx)   
 [ASP.NET 4.5.1 及 Web Tools for Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094)   
 [ASP.NET 和 Visual Studio for Web](../Topic/ASP.NET%20and%20Visual%20Studio%20for%20Web.md)   
 [Windows Communication Foundation 的新功能](http://go.microsoft.com/fwlink/?LinkId=228173)   
 [Windows Communication Foundation 的新功能](http://go.microsoft.com/fwlink/?LinkId=228176)   
 [Visual C++ 的新功能](http://msdn.microsoft.com/library/hh409293\(v=vs.120\).aspx)


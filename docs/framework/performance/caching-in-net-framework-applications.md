---
title: ".NET Framework 應用程式中的快取 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ASP.NET 快取"
  - "快取 [.NET Framework]"
  - "快取 [ASP.NET]"
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
caps.latest.revision: 26
author: "tdykstra"
ms.author: "tdykstra"
manager: "wpickett"
caps.handback.revision: 26
---
# .NET Framework 應用程式中的快取
快取可讓您將資料儲存在記憶體中，以進行快速存取。  再次存取資料時，應用程式可從快取取得資料，而不需要從原始來源擷取資料。  這樣可以改善效能和延展性。  此外，當資料來源暫時無法使用時，快取也可讓資料可供使用。  
  
 .NET Framework 提供了快取功能，可用來改善 Windows 用戶端與伺服器應用程式 \(包括 ASP.NET\) 的效能和延展性。  
  
> [!NOTE]
>  在 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和之前版本中，ASP.NET 在 <xref:System.Web.Caching> 命名空間中提供了記憶體中快取實作。  在舊版 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中，快取僅能從 <xref:System.Web> 命名空間中使用，因此需要相依於 ASP.NET 類別。  在 .NET Framework 4 中，<xref:System.Runtime.Caching> 命名空間包含同時為 Web 和非 Web 應用程式所設計的 API。  
  
## 快取資料  
 您可以使用 <xref:System.Runtime.Caching> 命名空間中的類別快取資訊。  這個命名空間中的快取類別提供了下列功能：  
  
-   抽象型別，可提供建立自訂快取實作的基礎。  
  
-   具象的記憶體中物件快取實作。  
  
 抽象基底快取類別 \(<xref:System.Runtime.Caching.ObjectCache>\) 會定義下列快取工作：  
  
-   建立與管理快取項目。  
  
-   指定到期和收回資訊。  
  
-   觸發為回應快取項目變更所引發的事件。  
  
 <xref:System.Runtime.Caching.MemoryCache> 類別是 <xref:System.Runtime.Caching.ObjectCache> 類別的記憶體中物件快取實作。  您可以將 <xref:System.Runtime.Caching.MemoryCache> 類別用於大部分快取工作。  
  
> [!NOTE]
>  <xref:System.Runtime.Caching.MemoryCache> 類別會做為 <xref:System.Web.Caching> 命名空間中所定義 ASP.NET 快取物件上的模型。  因此，內部快取邏輯類似舊版 ASP.NET 中提供的邏輯。  
  
 如需如何在 WPF 應用程式中使用快取的範例，請參閱[逐步解說：在 WPF 應用程式中快取應用程式資料](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)。  
  
## 在 ASP.NET 應用程式中快取  
 <xref:System.Runtime.Caching> 命名空間中的快取類別提供了在 ASP.NET 中快取資料的功能。  
  
> [!NOTE]
>  如果您的應用程式是以 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 或之前版本為目標，則必須使用 <xref:System.Web.Caching> 命名空間中定義的快取類別。  如需詳細資訊，請參閱[ASP.NET Caching Overview](../Topic/ASP.NET%20Caching%20Overview.md)。  
  
> [!NOTE]
>  當您開發新的應用程式時，建議您使用 <xref:System.Runtime.Caching.MemoryCache> 類別。  <xref:System.Runtime.Caching> 命名空間中提供的 API 就像是 <xref:System.Web.Caching.Cache> 命名空間中提供的 API。  因此，如果您在舊版 ASP.NET 中使用快取，則 API 將會類似。如需如何在 ASP.NET 應用程式中使用快取的範例，請參閱[Walkthrough: Caching Application Data in ASP.NET](../Topic/Walkthrough:%20Caching%20Application%20Data%20in%20ASP.NET.md)。  
  
### 輸出快取  
 若要手動快取應用程式資料，可以使用 ASP.NET 中的 <xref:System.Runtime.Caching.MemoryCache> 類別。ASP.NET 也支援輸出快取，會將網頁、控制項和 HTTP 回應所產生的輸出儲存在記憶體中。  您可以在 ASP.NET 網頁中以宣告方式或是使用 Web.config 檔中的設定來設定輸出快取。  如需詳細資訊，請參閱[快取的 outputCache 項目 \(ASP.NET 設定結構描述\)](http://msdn.microsoft.com/zh-tw/47cd2b47-316f-4dfd-bbf8-539be3066fee)。  
  
 ASP.NET 可讓您藉由建立自訂輸出快取提供者的方式擴充輸出快取。  藉由使用自訂提供者，您就可以使用其他儲存裝置儲存快取的內容，例如磁碟、雲端儲存及分散式快取引擎。  若要建立自訂輸出快取提供者，您會建立衍生自 <xref:System.Web.Caching.OutputCacheProvider> 類別的類別，並且將應用程式設定為使用自訂輸出快取提供者。  
  
## 在 WCF REST 服務中快取  
 針對 WCF REST 服務，.NET Framework 可讓您利用 ASP.NET 中提供的宣告式輸出快取。這樣您就可以快取來自 WCF REST 服務作業的回應。  當使用者傳送 HTTP GET 要求至設為要快取的服務時，ASP.NET 會傳回快取的回應，且不會呼叫服務方法。  快取到期後，下次使用者傳送 HTTP GET 要求時，會呼叫您的服務方法並且再次快取回應。  
  
 .NET Framework 還可讓您實作條件式 HTTP GET 快取。  在REST案例中，條件式 HTTP GET 要求通常用於實作如 [HTTP 規格](http://go.microsoft.com/fwlink/?LinkId=165800)中所述的智慧型 HTTP快取之服務。  如需詳細資訊，請參閱 [WCF Web HTTP 服務的快取支援](http://go.microsoft.com/fwlink/?LinkId=184598)。  
  
## 擴充 .NET Framework 中的快取  
 .NET Framework 中的快取是專為提供擴充能力所設計。  <xref:System.Runtime.Caching.ObjectCache> 類別可讓您建立自訂快取實作。  這個類別提供了可供所有 Managed 應用程式使用的成員，包括 Windows Form、Windows Presentation Foundation \(WPF\) 和 Windows Communications Foundation \(WCF\)。  當您想要建立使用不同儲存機制的快取類別，或是更進一步掌控快取作業時，就可能會這樣做。  
  
 若要擴充快取，您可以執行下列操作：  
  
-   建立衍生自 <xref:System.Runtime.Caching.ObjectCache> 類別的自訂類別，然後在衍生類別中提供自訂快取實作。  
  
-   建立衍生自 <xref:System.Runtime.Caching.MemoryCache> 類別的類別，並且自訂或擴充衍生類別。  如需執行這項作業的範例，請參閱 [在 ASP.NET 應用程式使用多個快取物件來快取應用程式資料](http://blogs.msdn.com/aspnetue/archive/2010/03/22/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application.aspx)。  
  
-   建立衍生自 <xref:System.Web.Caching.OutputCacheProvider> 類別的類別，然後將應用程式設定為使用自訂輸出快取提供者。  
  
 如需詳細資訊，請參閱 Scott Guthrie 部落格上的 [ASP.NET 4\(VS 2010 和 .NET 4.0 系列\) 中的可擴充輸出快取](http://go.microsoft.com/fwlink/?LinkId=185772) \(英文\) 一文。  
  
## 請參閱  
 <xref:System.Runtime.Caching.ObjectCache>   
 <xref:System.Runtime.Caching.MemoryCache>   
 [逐步解說：在 WPF 應用程式中快取應用程式資料](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)   
 [Walkthrough: Caching Application Data in ASP.NET](../Topic/Walkthrough:%20Caching%20Application%20Data%20in%20ASP.NET.md)
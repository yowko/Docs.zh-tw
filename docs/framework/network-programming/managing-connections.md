---
title: "管理連接 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "網際網路，連接"
  - "HTTP，連接的類別"
  - "從網際網路要求資料，連接"
  - "傳送資料，連接"
  - "接收資料，連接"
  - "ServicePoint 類別，關於 ServicePoint 類別"
  - "網際網路要求回應，連接"
  - "連接 [.NET Framework]，類別"
  - "網路資源，連接"
  - "下載網際網路資源，連接"
  - "ServicePointManager 類別，關於 ServicePointManager 類別"
ms.assetid: 9b3d3de7-189f-4f7d-81ae-9c29c441aaaa
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 管理連接
使用 HTTP 連接至資料來源的應用程式可以使用 .NET Framework 的 <xref:System.Net.ServicePoint> 和 <xref:System.Net.ServicePointManager> 類別管理與網際網路連線和協助他們完成最佳規模和效能。  
  
 **ServicePoint** 類別中提供應用程式與應用程式可以連接存取網際網路資源的端點。  每個 **ServicePoint** 包含說明透過共用連接之間的最佳化資訊改善效能最佳化以網際網路伺服器連接的資訊。  
  
 每個 **ServicePoint** 由統一資源識別元 \(URI\) \(URI\) 判斷及根據 URI 的配置識別項和主機片段分類。  例如，相同的 **ServicePoint** 執行個體將提供給要求 URI http:\/\/www.contoso.com\/index.htm 和 http:\/\/www.contoso.com\/news.htm?date\=today，因為它們具有相同的配置識別項 \(http\) 和主機片段 \(www.contoso.com \(英文\)。  如果應用程式已經有 www.contoso.com 伺服器的持續性連線，則使用該連接擷取兩個要求，以避免必須建立兩個連接。  
  
 **ServicePointManager** 是處理 **ServicePoint** 執行個體的建立和終結的靜態類別。  **ServicePointManager** 建立 **ServicePoint** ，當應用程式需要不會在的現有執行個體的集合 **ServicePoint** 的網際網路資源時。  終結**ServicePoint** 執行個體時，就會超出其最大閒置時間時，或是在現有的執行個體 **ServicePoint** 數目超過 **ServicePoint** 執行個體的最大數目應用程式的時間。  您可以在 **ServicePointManager**的 <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> 和 <xref:System.Net.ServicePointManager.MaxServicePoints%2A> 控制項預設屬性的最大閒置時間和 **ServicePoint** 執行個體的最大數目。  
  
 連接數目用戶端和伺服器之間的可能會對應用程式產能的動態效果的影響。  根據預設，會使用 <xref:System.Net.HttpWebRequest> 類別的應用程式使用較多個具有特定伺服器上的兩個持續性連線，不過，您可以設定連接最大數目是根據每一個應用程式的。  
  
> [!NOTE]
>  HTTP\/1.1 規格限制連接數目從應用程式的每部伺服器上使用兩個連接。  
  
 連接的最佳數目取決於執行應用程式的實際情況。  將可用的連接數目與應用程式可能不會影響應用程式效能。  判斷多個連接的影響，所執行的效能測試變更時，會連接數目時。  如下列程式碼範例所示，您可以變更應用程式藉由變更 **ServicePointManager** 類別的靜態 <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> 屬性是在應用程式初始化連接數目。  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 變更 **ServicePointManager.DefaultConnectionLimit** 屬性不會影響 **ServicePoint** 先前初始化的執行個體。  下列程式碼示範變更現有的 **ServicePoint** 連接限制伺服器的 http:\/\/www.contoso.com 加入至 `newLimit`儲存的值。  
  
```csharp  
Uri uri = new Uri("http://www.contoso.com/");  
ServicePoint sp = ServicePointManager.FindServicePoint(uri);  
sp.ConnectionLimit = newLimit;  
```  
  
```vb  
Dim uri As New Uri("http://www.contoso.com/")  
Dim sp As ServicePoint = ServicePointManager.FindServicePoint(uri)  
sp.ConnectionLimit = newLimit  
```  
  
## 請參閱  
 [連接群組](../../../docs/framework/network-programming/connection-grouping.md)   
 [使用應用程式通訊協定](../../../docs/framework/network-programming/using-application-protocols.md)
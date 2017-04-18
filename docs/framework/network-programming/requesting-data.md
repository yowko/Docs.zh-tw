---
title: "要求資料 | Microsoft Docs"
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
  - "傳送資料"
  - "WebRequest 類別，傳送和接收資料"
  - "從網際網路要求資料，關於要求資料"
  - "WebClient 類別，傳送和接收資料"
  - "網路，要求資料"
  - "接收資料"
  - "傳送資料，關於傳送資料"
  - "回應網際網路要求，關於回應網際網路要求"
  - "資料要求"
  - "接收資料，關於接收資料"
  - "網際網路，要求資料"
ms.assetid: df6f1e1d-6f2a-45dd-8141-4a85c3dafe1d
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# 要求資料
開發今天網際網路的散發的作業環境中執行的應用程式以擷取資料需要更有效率，可用來從所有類型的資源。  可外掛式通訊協定可讓您開發使用單一介面從多個網際網路通訊協定擷取資料的應用程式。  
  
## 上載和下載資料從網際網路伺服器  
 簡單的要求和回應交易的， <xref:System.Net.WebClient> 類別提供上載資料至或下載資料提供最簡單的方法是從網際網路伺服器。  **WebClient** 提供上載和下載檔案，傳送和接收資料流和會將資料緩衝區傳送至伺服器並接收回應的方法。  **WebClient** 使用 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別建立對網際網路資源的實際連接，因此，任何已登錄的可外掛式通訊協定時可供使用。  
  
 需要進行更複雜的交易使用 **WebRequest** 類別及其子系，的用戶端應用程式要求來自伺服器的資料。  **WebRequest** 封裝連接到伺服器時，會將要求傳送和接收回應詳細資料。  **WebRequest** 是定義一組屬性和方法的所有應用程式都可以使用可外掛式通訊協定的抽象類別。  **WebRequest**子代，例如 <xref:System.Net.HttpWebRequest>，執行 **WebRequest** 和方法定義的屬性與基礎通訊協定方法的行為一致。  
  
 **WebRequest** 類別建立 **WebRequest** 子代通訊協定的特定執行個體，使用 URI 的值傳遞給它的 <xref:System.Net.WebRequest.Create%2A> 方法判斷特定衍生類別建立執行個體。  應用程式會指示應該透過向 <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=fullName> 方法子代的建構函式會使用哪一個 **WebRequest** 子代處理要求。  
  
 對網際網路資源是透過呼叫方法 <xref:System.Net.WebRequest.GetResponse%2A> 在 **WebRequest**。  **GetResponse** 方法從 **WebRequest**屬性的通訊協定的特定需求，建立 TCP 或 UDP 通訊端連線到伺服器，並傳送要求。  傳送資料至伺服器，例如 HTTP 或 FTP **Post** **Put** 要求的要求， <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=fullName> 方法提供傳送資料的網路資料流。  
  
 比對 **WebRequest.**的 **GetResponse** 方法傳回通訊協定專屬的 **WebResponse**  
  
 **WebResponse** 類別也會定義屬性和方法的所有應用程式都可以使用可外掛式通訊協定的抽象類別。  **WebResponse** 子代執行這些屬性和方法的基礎通訊協定的。  <xref:System.Net.HttpWebResponse> 類別，例如，實作 HTTP 的 **WebResponse** 類別。  
  
 伺服器傳回的資料會顯示在 \[ <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=fullName> 方法傳回之資料流的應用程式。  如下列範例所示，您可以使用像任何其他的這個資料流。  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## 請參閱  
 [以 .NET Framework 進行網路程式設計](../../../docs/framework/network-programming/index.md)   
 [如何：要求網頁並擷取結果當做資料流](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)   
 [如何：擷取符合 WebRequest 的通訊協定特定 WebResponse](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
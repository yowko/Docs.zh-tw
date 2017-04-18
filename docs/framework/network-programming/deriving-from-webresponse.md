---
title: "衍生自 WebResponse | Microsoft Docs"
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
  - "衍生自 WebResponse"
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# 衍生自 WebResponse
<xref:System.Net.WebResponse> 類別是建立一個通訊協定專屬回應提供基本的方法和屬性調整 .NET Framework 可外掛式通訊協定模型的抽象基底類別。  使用 <xref:System.Net.WebRequest> 類別要求資源的資料的應用程式會收到 **WebResponse**的回應。  通訊協定專屬的 **WebResponse** 子代必須實作 **WebResponse** 類別的抽象成員。  
  
 關聯的 **WebRequest** 類別必須建立 **WebResponse** 子代。  例如，由於呼叫 <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=fullName> 或 <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=fullName>， <xref:System.Net.HttpWebResponse> 執行個體 \(Instance\) 建立。  每個 **WebResponse** 包含要求的結果為資源並不是要重複使用。  
  
## ContentLength 屬性  
 <xref:System.Net.WebResponse.ContentLength%2A> 屬性表示位元組數從 <xref:System.Net.WebResponse.GetResponseStream%2A> 方法所傳回的資料流中所提供的資料。  **ContentLength** 屬性不表示位元組數伺服器或中繼資料資訊傳回的標頭，它會在要求的資源值只位元組數目的資料。  
  
## ContentType 屬性  
 <xref:System.Net.WebResponse.ContentType%2A> 屬性提供任何特殊資訊的通訊協定需要您要傳送到用戶端的識別伺服器傳送的內容類型。  這通常是傳回的所有資料的 MIME 內容類型。  
  
## 標題屬性。  
 <xref:System.Net.WebResponse.Headers%2A> 屬性包含名稱\/值組的選擇性集合關聯的中繼資料 \(Metadata\) 回應。  可以表示為名稱\/值組的通訊協定所需的所有中繼資料儲存在 **Headers** 屬性可以加入中。  
  
 不需要使用 **Headers** 屬性使用標頭中繼資料。  通訊協定專屬中繼資料可以公開 \(Expose\) 為屬性，例如， <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=fullName> 屬性公開 **Last\-Modified** HTTP 標頭。  當您公開標題中繼資料做為屬性時，會使用 **Headers** 屬性，則不應該允許相同的屬性設定為。  
  
## ResponseUri 屬性  
 <xref:System.Net.WebResponse.ResponseUri%2A> 屬性包含實際提供回應資源的 URI。  對於不支援重新導向的通訊協定， **ResponseUri** 會與建立回應 **WebRequest** 的 <xref:System.Net.WebRequest.RequestUri%2A> 屬性。  如果通訊協定支援重新導向要求， **ResponseUri** 會包含回應的 URI。  
  
## Close 方法  
 <xref:System.Net.WebResponse.Close%2A> 方法關閉要求和回應所建立的所有連接並清除回應所使用的資源。  **關閉** 方法結束回應所使用的所有資料流的執行個體，不過，它不會擲回例外狀況，如果回應資料流 <xref:System.IO.Stream.Close%2A?displayProperty=fullName> 由對方法的呼叫之前關閉。  
  
## GetResponseStream 方法  
 <xref:System.Net.WebResponse.GetResponseStream%2A> 方法會傳回包含來自所要求資源的資料流物件。  回應資料流包含資源傳回的資料;應該從回應中移除並公開在回應或中繼資料中包含的所有標頭在應用程式透過通訊協定的特定屬性或 **Headers** 屬性。  
  
 **GetResponseStream** 方法所傳回的資料流執行個體 \(Instance\) 是由應用程式所擁有，且可以關閉，而不需關閉 **WebResponse**。  依照慣例，呼叫 **WebResponse.Close** 方法也會關閉 **GetResponse**傳回的資料流。  
  
## 請參閱  
 <xref:System.Net.WebResponse>   
 <xref:System.Net.HttpWebResponse>   
 <xref:System.Net.FileWebResponse>   
 [可插式通訊協定程式設計](../../../docs/framework/network-programming/programming-pluggable-protocols.md)   
 [衍生自 WebRequest](../../../docs/framework/network-programming/deriving-from-webrequest.md)